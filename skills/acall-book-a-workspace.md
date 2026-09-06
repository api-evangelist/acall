---
name: Book a workspace for a worker in Acall
description: >-
  Find a bookable spot (desk) in an Acall workplace, check it is free for the window you want, create the
  reservation, and confirm it. Covers the only writable surface in the Acall Public API and the retry hazard
  that comes with it.
api: openapi/acall-public-api-openapi.yml
operations:
  - getUsers
  - getSpots
  - getSpotReservations
  - postSpotReservation
  - getSpotReservation
generated: '2026-09-06'
method: generated
source: openapi/acall-public-api-openapi.yml
---

# Book a workspace in Acall

Base URL: `https://api.workstyleos.com/v1/`

## Before you start

Authentication is a single HTTP bearer token: `Authorization: Bearer <token>`. It applies to every
operation. **There is no self-serve path to a token** — Acall issues one after a request through the
contact form, and the API is unavailable on the multi-tenant plan. If you do not already hold a token,
stop; nothing below will work.

Unauthenticated and bad-token responses are identical plain-text `Unauthenticated` bodies with status 401.
Read `WWW-Authenticate` to tell them apart: `realm="token_required"` means you sent no header,
`error="invalid_token"` means the token was rejected.

## Steps

1. **Resolve the worker.** Call `getUsers` with `freeword` set to the person's name or email, plus
   `limit`/`offset` as needed. Match on `email` rather than name — Acall stores family/given name and
   phonetic variants separately, and free-word search is not exact. Keep `user_id`.
   Retired workers are not returned, so an empty result may mean "no longer employed", not "no such person".

2. **List candidate spots.** Call `getSpots`. If you know which part of the building you want, pass
   `root_spot_id` to scope the subtree; the `Spot` schema has no parent field, so you cannot walk the
   hierarchy upward — you must be given a root. Keep `spot_id`.

3. **Check the window is free.** Call `getSpotReservations` with `starting_at`, `ending_at` and the same
   `root_spot_id`. Filter the result for your `spot_id`. **The API will not do this for you** — there is no
   availability endpoint, and `postSpotReservation` is not documented to reject a clash. Treat this read as
   mandatory, and treat the gap between this read and the write in step 4 as a race you cannot close.

4. **Create the reservation.** `postSpotReservation` with a JSON body carrying `spot_id`, `starting_at`,
   `ending_at`, and optionally `invited_user_ids`, `title`, `description`, and `send_mail`. A `201` means
   created.

   > **Do not retry this call blindly.** Acall documents no idempotency key. A timeout or a dropped
   > connection after the server committed leaves you unable to distinguish "not created" from "created and
   > you missed the response". On any ambiguous failure, go back to `getSpotReservations` for the same spot
   > and window and look for your reservation before issuing a second `POST`.

   Set `send_mail` deliberately: it triggers real email to real people.

5. **Confirm.** Call `getSpotReservation` with the returned `spot_reservation_id` and verify
   `spot_id`, `starting_at`, `ending_at` and `invited_users` match what you asked for.

## Undoing it

`deleteSpotReservation` removes a reservation and returns `204`. Two things the contract tells you:

- There is **no time window** published for the delete, so you cannot promise a user "you can cancel up
  until X".
- A reservation linked to **multiple spots cannot be deleted at all** — the provider states this in the
  operation summary. Check before you promise reversibility.

There is no undelete. Recreating produces a new `spot_reservation_id`.

## Errors

The spec declares no 4xx or 5xx responses for any operation, so expect nothing structured. Observed live
behaviour: `text/plain` bodies, `401 Unauthenticated`, `404 Not found endpoint` for an unrouted path.
See `errors/acall-problem-types.yml`. Do not write a parser that assumes JSON on the failure path.
