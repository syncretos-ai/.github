# Syncretos

> **Multi-model AI research with traceable evidence.**

Currently in closed alpha, focused on the deliberation pipeline.

---

## The problem

Most AI research tools hand you one model's answer, or quietly blend a few together into a
single response. Either way you have no way to tell whether that answer held up under
scrutiny or merely sounds confident.

Syncretos starts somewhere else. Before any model drafts a word, parser scripts turn your
source material into a structured database of claims, each anchored to the page and offset
it came from. The models then reason over captured data rather than their own recollection,
which is where most of the details get lost.

From there, several models draft independent answers, critique each other, revise against
substantiated criticism, and get reconciled by a Fusion judge into one synthesis. Every
step stays inspectable, with the sources behind it. When the evidence isn't there,
Syncretos says so rather than inventing a citation. When a provider times out, the rest of
the panel's work survives.

You connect your own provider accounts or take a managed plan, so you are never locked to
one vendor and you keep control of model choice and cost.

---

## Why I built it

> *I've been obsessed with research since I was a kid, and I'm a maximalist about it. Even
> buying something small like swimming goggles, I'll dig up every review, compare specs,
> and only then pick a pair. When AI tools came out I hoped they'd make that kind of
> digging faster. Instead, even the multi-model ones stayed shallow, repeating marketing
> language back at me dressed up as insight, or simply making things up. So I started
> building my own version of deep research to scratch my own itch.*
>
> *When a friend saw the early prototype and got far more excited than I expected, I ran a
> survey. Over 70% of respondents said they'd want something like this for high-stakes
> work: PhD research, a bachelor's thesis, scientific papers, quarterly executive reports.*
>
> *I don't have formal training in research methodology. What I have is years of practicing
> exhaustive source-checking as a personal habit. Feeling this gap acutely is why I built
> Syncretos instead of waiting for someone else to.*

---

## How it works

```text
Source material / inquiry
  │
  ▼
1. Pre-processing and structured ingestion
   └─ Parser scripts build a claims database, each claim anchored to page and offset
  │
  ▼
2. Independent drafting (parallel panel)
   ├─ Model 1 draft
   ├─ Model 2 draft
   └─ Model N draft
  │
  ▼
3. Adversarial cross-critique and revision
   ├─ Models test each other's claims against the captured database
   └─ Drafts revised where the criticism is substantiated
  │
  ▼
4. Fusion judge reconciliation
   └─ Weighs competing evidence, surfaces caveats and tradeoffs
  │
  ▼
5. Synthesis and follow-ups
   └─ Final report, every claim pointing back to its source
```

A full run takes minutes rather than seconds. Runs are persisted as they go, so losing
your connection or closing the tab doesn't lose the work.

---

## What makes it different

**Sources are structured first.** Parsing happens before drafting, so facts aren't lost to
context limits or reconstructed from memory. This is the part competitors skip.

**The deliberation is inspectable.** Drafts, cross-critiques, revisions, Fusion findings,
and synthesis stay separate and readable. You can see where an answer came from and where
the models disagreed.

**Citations are anchored, not asserted.** Claims point to a page and offset in your source,
not a plausible-looking reference. No evidence produces an explicit empty state.

**Failure doesn't cascade.** A provider timeout, rate limit, or bad tool call costs you
that model's contribution, not the run.

**Roles are tuned independently.** Assign different models to Draft, Debate, Fusion Judge,
and Synthesis according to speed, context size, or reasoning strength.

**Your keys, your costs.** OpenAI, Anthropic, Gemini, OpenRouter, or a custom gateway.

---

## Compared to the alternatives

| | Perplexity Model Council | Open Model Council | ModelCouncil.co | **Syncretos** |
| --- | --- | --- | --- | --- |
| **Structured source database** | No | No | No | **Parsed before drafting** |
| **Adversarial deliberation** | No, search comparison | Single debate, no revision | No | **Multi-stage critique and revision** |
| **Fusion judge** | No | Basic | Yes | **Dedicated reconciliation judge** |
| **Panel size** | 3 models | Uncapped | 4 models | **Uncapped** |
| **Cost model** | $200/mo | BYOK | $99 access fee + BYOK | **Subscription or $10/mo BYOK** |
| **Built for** | Everyday search | Open-source devs | Executives | **High-stakes research** |

The gap that matters is the first row. A fusion step and a debate round both operate on
whatever the models already carry. Without structuring the sources up front, agreement
between models is just as likely to compound a wrong premise as to correct it.

---

## Pricing

| Tier | Price | What you get |
| --- | --- | --- |
| **BYOK** | $10/mo | Your own keys, unlimited runs. The fee covers workspace hosting. |
| **Individual** | $39/mo | 5 managed runs included, provider costs covered. $8 per additional run. |
| **Pro** | $99/mo | 15 managed runs included. $7 per additional run. |
| **Team** | from $499/mo | Pooled credits, shared workspaces, SSO, priority support. |

---

## Roadmap

- **Workspace collections** — persistent document libraries and source databases
- **Decision memory** — verified context carried across research projects
- **Collaborative reports** — shareable review links, Markdown and PDF export, audit trails
- **MCP integrations** — custom external data connectors via Model Context Protocol

---

## Security

- **Encrypted key vault.** Connect a provider key once and reuse it. Keys are stored
  against your account and encrypted at rest, are never shared between accounts or written
  to logs, and can be revoked in one click. Revoking deletes the stored key rather than
  disabling it.
- **Deletable run history.** Runs are stored so they survive a dropped connection and can
  resume where they left off. Stored data is encrypted at rest, retained for 30 days, and
  deletable by you at any time. Deleting removes it rather than hiding it.
- **Origin restriction.** Requests are forwarded only to the provider origin you configured.
- **Payload sanitization.** Provider errors are sanitized before they surface, so nothing
  leaks through an error message.

---

## Repositories

Everything here is private during closed alpha. The work is split across a monorepo for the
platform, its API contract and shared design tokens, plus separate repositories for the
native client, brand assets, and reference material.

---

© Syncretos · [syncretos.com](https://syncretos.com)
