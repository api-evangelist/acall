---
name: Reconcile Acall appointments against entry-gate access logs
description: >-
  Pull a day's appointments and internal meetings out of Acall, pull the entry-gate access log for the same
  window, and join them into a picture of who was expected versus who actually came through the gate.
api: openapi/acall-public-api-openapi.yml
operations:
  - getEvents
  - getEvent
  - getGateLogs
  - getFacilities
  - getFacility
generated: '2026-09-06'
method: generated
source: openapi/acall-public-api-openapi.yml
---

# Reconcile appointments against gate access in Acall

Base URL: `https://api.workstyleos.com/v1/`. Auth: `Authorization: Bearer <token>` on every call.

This is a read-only workflow. Nothing here mutates Acall state.

## Steps

1. **Pull the appointment window.** `getEvents` with `starting_at` and `ending_at` bounding the day, plus
   `limit`/`offset`. Each `Event` carries `title`, `guests`, `attend_users`, `facilities`, `starting_at`,
   `ending_at`, `note`, `agendas`, `mail_template_id` and `access_policy`.

   Paging is limit/offset with **no total count and no next-link** in the response, so keep requesting until
   a page comes back shorter than `limit`. Do not assume the first page is the whole day.

2. **Expand where you need detail.** `getEvent` with an `event_id` returns the `EventDetail`
   representation. There is no `expand` parameter — the detail shape is only available through the
   single-resource read, so this is one extra round trip per event you care about.

3. **Resolve rooms if you need them.** `Event.facilities[]` embeds `facility_id`, `facility_name` and
   `facility_type`. Only call `getFacility` (or list with `getFacilities`) when you need `location`,
   `usage` or `description`, which the embedded form does not carry.

4. **Pull the gate log for the same window.** `getGateLogs` with the same `starting_at`/`ending_at`.
   Each `GateLog` carries `gate_id`, `gate_name`, `status`, `opened_at`, `operators[]` and `passers[]`.

5. **Join — carefully.** This is the part that needs judgement:

   - `Event.attend_users[]` carries a real `user_id` that resolves against `getUser`.
   - `Event.guests[]` carries a `guest_id` and guest PII (names, phonetic names, company, emails). Guests
     have no resource of their own in this API.
   - `GateLog.passers[]` carries a field named **`id`, not `user_id`**, and the spec never states what it
     references. **Do not assume it joins to a worker.** Join on names if you must, mark the match as
     inexact, and say so in whatever you produce.

## What this workflow cannot tell you

- Meeting-room bookings are not exposed. Only workspace (spot) reservations are writable or readable as
  reservations; a room booking is visible only as `Event.facilities[]`.
- There is no group resource, so "which department came in" is not answerable from the gate log alone.

## Handling and hazards

Gate logs and guest records are personal data about identified individuals — names, phonetic names,
employer, email addresses, and the times they physically entered a building. Retain only what the task
needs and do not re-export it beyond the requester.

No rate limits are published and no `RateLimit-*` headers are returned, so pace collection reads
conservatively rather than relying on the server to push back. Errors arrive as plain text, not JSON.
