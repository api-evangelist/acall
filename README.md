# Acall

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Acall Inc. (アコール株式会社) is a Japanese workplace-experience software company, founded in 2010 and headquartered in Tokyo with a Kobe office, whose Acall / WorkstyleOS platform runs the physical side of hybrid work for more than 7,000 organizations. The product is a set of check-in surfaces — Acall Reception (iPad visitor reception and entry/exit records), Acall Meeting (meeting-room booking and utilization), Acall Desktop (free-address desk and workspace "spot" reservation / hoteling), Acall Gate (entry-gate integration), AI Meeting, Neat device integration and a multi-tenant building mode — stitched to Microsoft 365 and Google Calendar, Teams/Slack/Chatwork notifications, and SSO/SCIM-style provisioning. Acall publishes a REST "Acall Public API" (v1, bearer token) covering workers, facilities, events, gate access logs, spots and spot reservations, plus an outbound Webhook surface for appointment and internal-meeting events. API access is not self-serve: a token is issued only after a request through the contact form, and the API is unavailable on the multi-tenant plan.

**Areas:** Workplace Management · Visitor Management · Meeting Room Booking · Desk Booking · Hybrid Work · Access Control · Facilities · Smart Office · Japan · Software-as-a-Service

## Acall on APIs.io

Everything profiled for Acall is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/acall/](https://apis.io/providers/acall/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [Acall Event API](https://apis.io/apis/acall/acall-event-api-api/) — The Event API API from Acall — 2 operation(s) for event api.
- [Acall Facility API](https://apis.io/apis/acall/acall-facility-api-api/) — The Facility API API from Acall — 2 operation(s) for facility api.
- [Acall Gate API](https://apis.io/apis/acall/acall-gate-api-api/) — The Gate API API from Acall — 1 operation(s) for gate api.
- [Acall Spot API](https://apis.io/apis/acall/acall-spot-api-api/) — The Spot API API from Acall — 1 operation(s) for spot api.
- [Acall Spot Reservation API](https://apis.io/apis/acall/acall-spot-reservation-api-api/) — The Spot Reservation API API from Acall — 2 operation(s) for spot reservation api.
- [Acall User API](https://apis.io/apis/acall/acall-user-api-api/) — The User API API from Acall — 2 operation(s) for user api.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Acall Webhooks](https://apis.io/asyncapis/acall/acall-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [acall](https://apis.io/servers/acall/acall/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Acall Agentic Access](https://apis.io/agentic-access/acall/acall-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Acall Public Api Overlay](https://apis.io/overlays/acall/acall-public-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Acall Authentication](https://apis.io/security/acall/acall-authentication/)
- [Acall Domain Security](https://apis.io/security/acall/acall-domain-security/)
- [Acall Trust Center](https://apis.io/security/acall/acall-trust-center/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Acall Plans Pricing](https://apis.io/plans/acall/acall-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Acall Rate Limits](https://apis.io/rate-limits/acall/acall-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.acall.inc/)
- [Documentation](https://support.workstyleos.com/faq/show/598?site_domain=default)
- [API reference](https://www.workstyleos.com/publicapi/index.html)
- [Pricing](https://www.workstyleos.com/pricing/)
- [Support](https://support.workstyleos.com/?site_domain=default)
- [Changelog](https://www.workstyleos.com/info/release/)
- [Blog](https://www.acall.inc/news/)
- [Compliance](https://www.workstyleos.com/security/)
- [Terms of service](https://www.workstyleos.com/terms_of_use/)
- [Privacy policy](https://www.acall.inc/privacypolicy)
- [GitHub](https://github.com/acall-inc)
- [Status](https://status.acall.inc/)

## API Evangelist rating

**Kin Score 44.1** — developing · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 53.1 |
| Contract governance | 4.5 |
| Operational transparency | 42.1 |
| Developer ergonomics | 37.5 |
| Access clarity | 46.1 |

**Agent readiness 27.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/acall/](https://apis.io/providers/acall/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Acall: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/acall/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
