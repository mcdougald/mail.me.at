<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="mail.me.at landing page" width="880">
  </picture>
</p>

<h1 align="center">mail.me.at</h1>

<p align="center"><strong>Email, starting with the part you cannot undo.</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/status-in%20development-171717?style=flat-square" alt="Status: in development">
  <img src="https://img.shields.io/badge/license-source--available-404040?style=flat-square" alt="License: source-available">
  <img src="https://img.shields.io/badge/self--host-supported-525252?style=flat-square" alt="Self-host: supported">
  <img src="https://img.shields.io/badge/part%20of-me.at-737373?style=flat-square" alt="Part of me.at">
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#built-with">Built with</a>
</p>

A bad send cannot be recalled: one list without consent or one burst of dead addresses can damage a sending domain's reputation. I am building mail.me.at as newsletters and broadcast email on your own Resend or SES account, with deliverability treated as ongoing work, so I built the refusals first: dead addresses suppressed, complaint rate watched per sender, consent checked at send, and SPF, DKIM and DMARC verified before a domain may send. There is no public sending surface yet. What runs today is a set of operator-only pages behind sign-in, and a mailbox (an address and an inbox) is the planned destination, not something that exists.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/overview-dark.svg">
    <img src=".github/assets/overview.svg" alt="mail.me.at at a glance: dead addresses stay dead, complaints per sender, consent checked at send, domains proven first" width="880">
  </picture>
</p>

## Why mail.me.at

| The usual newsletter tool | mail.me.at |
| --- | --- |
| Imports any list you upload | Refuses imports without a consent record |
| One complaint rate for the whole account | Tracked per sending identity, with a pause that leaves other senders alone |
| An inbox-placement score | Real send outcomes per identity, and no invented placement number |
| An agent with an API key can send | Agents ask over MCP, and nothing is sent until a signed-in operator releases it |

## Features

- **Bounce suppression**: hard bounces suppress an address at once and soft bounces after repeated events, so a permanently failing address is never retried.
- **Per-sender complaint monitoring**: complaint rate is tracked per sending identity, with a warning threshold and an automatic pause that leaves other identities alone.
- **Consent lifecycle**: consent is a set of states checked at send time, and imports without a consent record are refused.
- **Domain authentication**: SPF, DKIM and DMARC are verified together, DKIM keys rotate through two selectors without a gap in signing, and new identities are warmed up gradually.
- **Safe sending**: List-Unsubscribe and one-click headers on every message, a guard so a retry cannot double-send, and large first sends held for human review.
- **DMARC report ingest**: aggregate reports are parsed and folded per domain, telling spoofing apart from your own senders losing alignment.
- **Operator deliverability dashboard**: send outcomes per identity, complaint posture and suppression by reason, with no invented inbox-placement number.
- **Agents ask, a human releases**: agents can request a single email over MCP; nothing is sent until a signed-in operator releases or rejects it.

## How it works

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/flow-dark.svg">
    <img src=".github/assets/flow.svg" alt="How mail.me.at works: verify, check, send, watch, pause" width="880">
  </picture>
</p>

A domain may send only once SPF, DKIM and DMARC verify together. Each message is checked against the recipient's consent state and the suppression list at send time, then handed to your own Resend or SES account with unsubscribe headers attached. Bounces and complaints come back per sending identity, and an identity that crosses its complaint threshold is paused without touching the others.

## Built with

<p>
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React-19-171717?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-5-262626?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-404040?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4">
  <img src="https://img.shields.io/badge/Drizzle-Postgres-525252?style=flat-square&logo=drizzle&logoColor=white" alt="Drizzle ORM and Postgres">
  <img src="https://img.shields.io/badge/Resend-email-737373?style=flat-square&logo=resend&logoColor=white" alt="Resend">
</p>

- Next.js 16 (App Router), React 19, TypeScript
- Tailwind CSS 4
- Drizzle ORM + Postgres
- Better Auth
- oRPC
- Resend (sending provider) and an MCP endpoint for agent requests

## Part of the me.at family

mail.me.at is one of my [`*.me.at`](https://me.at) apps. They share one design system, account, and app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

Source-available. See [LICENSE](LICENSE).
