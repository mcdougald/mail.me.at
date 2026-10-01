<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="mail.me.at landing page" width="880">
  </picture>
</p>

# mail.me.at

Email, starting with the part you cannot undo.

mail.me.at is planned as newsletters and broadcast email on your own Resend or SES account, with deliverability treated as ongoing work. A bad send cannot be recalled, so the refusals were built first: dead addresses suppressed, complaint rate watched per sender, consent checked at send, and SPF, DKIM and DMARC verified before a domain may send. There is no public sending surface yet; what runs today is a set of operator-only pages behind sign-in, and a mailbox (an address and an inbox) is the planned destination, not something that exists.

## Features

- **Bounce suppression**: hard bounces suppress an address at once and soft bounces after repeated events, so a permanently failing address is never retried.
- **Per-sender complaint monitoring**: complaint rate is tracked per sending identity, with a warning threshold and an automatic pause that leaves other identities alone.
- **Consent lifecycle**: consent is a set of states checked at send time, and imports without a consent record are refused.
- **Domain authentication**: SPF, DKIM and DMARC are verified together, DKIM keys rotate through two selectors without a gap in signing, and new identities are warmed up gradually.
- **Safe sending**: List-Unsubscribe and one-click headers on every message, a guard so a retry cannot double-send, and large first sends held for human review.
- **DMARC report ingest**: aggregate reports are parsed and folded per domain, telling spoofing apart from your own senders losing alignment.
- **Operator deliverability dashboard**: send outcomes per identity, complaint posture and suppression by reason, with no invented inbox-placement number.
- **Agents ask, a human releases**: agents can request a single email over MCP; nothing is sent until a signed-in operator releases or rejects it.

## Built with

- Next.js 16 (App Router), React 19, TypeScript
- Tailwind CSS 4
- Drizzle ORM + Postgres
- Better Auth
- oRPC
- Resend (sending provider) and an MCP endpoint for agent requests

## Part of the me.at family

mail.me.at is one of the [`*.me.at`](https://me.at) apps by Trevor McDougald. They share one design system, account, and app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

See [LICENSE](LICENSE).
