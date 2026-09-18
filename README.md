# multi tenant ai chatbot platform: how agencies white label and re-bill client agents, with real per-message costs

Search "multi tenant AI chatbot platform" and most results fall into two camps: architecture explainers written for developers, and "top 10 white label chatbot" listicles that treat a debranded chat widget as proof of multi-tenancy.

If you run an agency, neither answers the question you actually have. You want to know whether one account can hold twenty client workspaces, whether your clients can upload their own documents without seeing your vendor's logo, and what each client conversation costs you versus what you bill for it.

This piece walks through that. CloseBot is the platform I dug into for the numbers, because its Agency plan is built around exactly this use case, but the pricing math and the checklist apply to whichever platform you end up comparing.

## What "tenant" means when you're the agency

A tenant is a client workspace: their knowledge base, their brand voice, their conversations, their billing. Multi-tenant means one platform instance serves all of them, with each tenant's data scoped away from the others.

The part that trips people up is who is the tenant and who is the vendor. In CloseBot's model, an agency account holds the agents. Each client connection — what the platform calls a *source* — is the tenant. A source is a CRM location, a sub-account, a standalone site. Your clients log into a portal under your brand and see their own dashboards, message volumes and charges. They don't see CloseBot, and they don't see your other clients.

That's the structure. What matters is what it lets each side do.

## The four checks that separate a real reseller platform from a re-skinned widget

A white-label chatbot comparison published by an EU vendor sets a reasonable bar: branding removed everywhere including the login screen and transactional emails, your own domain on the client-facing surface, client sub-accounts you manage as your own product, and the ability to set your own prices and keep the markup. By that standard, several well-known tools are widget-only.

Rather than score CloseBot on those four lines with marketing language, here's what's documented and what isn't:

**Brand removal with a client portal.** The Agency plan includes a white-label client portal and client seats. The blog documenting V2 is explicit that clients see a branded dashboard with performance metrics, messages and charges, and that your agent logic stays hidden.

**Client-side self-service, scoped.** Clients can upload documents to their own knowledge library and fill in variables you predefine — business name, amenities, service areas. They cannot edit the agent's logic or structure. For an agency, that split is the difference between a client personalizing their bot and a client quietly breaking it on a Friday.

**Custom domain.** This is the honest gap. The plans page and product docs describe the white-label portal, and the marketing agencies page shows the flow end to end, but a client-facing domain like `chat.youragency.com` isn't documented as a standard feature. If your pitch depends on the client typing your URL, ask that question directly before you commit.

**Your own pricing.** This is where CloseBot is unambiguous. Agency accounts re-bill usage at whatever markup you choose, through your own Stripe account.

## Inside the CloseBot account model

Two objects run everything. A **Persona** holds the voice — tone, message formatting, typo frequency, agent name and image, and which model provider is behind it. A **Job Flow** holds what the agent actually does: qualify, collect fields, answer objections, book.

In V2, only the agency side builds and edits agents. Clients personalize inside the rails you set.

The reason this matters for multi-tenancy is templates. An agent built for gyms doesn't need to be rebuilt for the second gym. You define a variable for amenities or locations, the client fills it in from their portal, and the same flow serves both. Agencies running a dozen similar local-service clients stop treating each new account as a fresh build.

If you want to see how the split actually feels in practice, 👉 [👉 start on CloseBot's free plan](https://app.closebot.com/a?fpr=li87) and build one agent you'd hand to a client.

## What each client conversation costs you, and what you can bill

This is the section most platform roundups skip, and it's the one that decides whether reselling AI is a business or a hobby.

CloseBot's usage costs sit in three buckets, all documented in the help center:

| Cost item | What CloseBot charges you | Can you re-bill it? |
| --- | --- | --- |
| Message responses | $0.012 per message on Agency accounts; free plan overage at $0.08 per message | Yes on Agency |
| User seats | $5.00 per user per month | Yes on Agency |
| Knowledge storage | $0.006 per MB per day on Agency; $0.10–$3.00 per MB per month as a Business add-on | Yes on Agency |

Business plans work differently: message costs are folded into the base price, so the number on the plans page is closer to your real bill.

For agencies, the rebilling setup is a Stripe Connect account plus a markup field per item. The docs use $0.02 per message, $100 per seat and $0.05 per MB as sample values — treat those as an illustration of the fields, not as benchmarks.

Run a quick example with plausible numbers. A client doing 3,000 messages a month costs you $36 at the wholesale rate. Bill at $0.02 and that's $60, so $24 of gross margin before you've charged for anything else. Add a marked-up seat, add storage the client keeps uploading into, and the per-client spread grows. The plans page cites polled agencies billing an average of $500 per client per month — that's the vendor's own polling, not an audited figure, but it explains why the pricing model is built the way it is.

Two things to plan around. The split-billing reality: on Agency accounts, client wallets pay you and your wallet pays CloseBot, so a client who never tops up their wallet creates friction you have to manage. And the seat math: every client who wants to log in and look at their dashboard consumes a seat, so "let all clients see their portal" has a per-user cost attached even if your markup covers it.

## The full plan lineup, including the free tier

CloseBot's current pricing page (last modified 24 June 2026) shows four tracks. All prices in USD.

| Plan | What you get | Price | Billing | Get it |
| --- | --- | --- | --- | --- |
| Free | 100 AI replies/month, 1 agent, 1 user seat, 1 MB storage, unlimited account connections | $0 | Always free | [ Start free, no card needed](https://app.closebot.com/a?fpr=li87) |
| Core — Business | Message costs included in the base price, 15+ templates, human support, add-on users ($5/seat), add-on storage and agents | From $64/mo, scaling with monthly reply volume; $53/mo billed as $640/yr on annual | Monthly or annual | [ See the Business plan and volume tiers](https://app.closebot.com/a?fpr=li87) |
| Core — Agency | Unlimited agents and sources, white-label client portal, re-bill all costs, client seats, usage markup | $397/mo flat (annual works out to about $331/mo equivalent) | Monthly or annual | [ See the Agency plan and the re-billing setup](https://app.closebot.com/a?fpr=li87) |
| Growth | 50+ templates, HIPAA compliance, quarterly audits, 99.99% priority uptime, priority support | Custom quote | Contract | [ Ask about Growth pricing](https://app.closebot.com/a?fpr=li87) |

Two details worth flagging before you read the table as the whole story.

First, the Business plan scales by message volume, and the plans page runs a slider from 500 replies up past 100,000. A third-party review published in August 2026 recorded the ladder as $64 at 500 messages, $84 at 1,000, $109 at 2,000, $176 at 5,000, $454 at 20,000, $806 at 50,000 and roughly $1,059 at 100,000, with 100K+ quoted custom. Those specific figures come from that review rather than from a page I could read directly, so confirm them on the pricing page before you build a client contract around them.

Second, CloseBot's help center still carries an older structure listing Business plans at $64, $197, $297 and $397 for 1, 3, 10 and unlimited Job Flows. That reads like V1-era documentation that hasn't been rewritten to match the volume-based pricing now shown on the site. If you're comparing quotes, use the plans page.

Free plan limits are worth knowing because they shape what you can test: no live chat support, Job Flows capped at 5 actions, only 2 of the 5 supported AI providers, no extra user seats, and higher per-message costs once you pass 100. It's enough to prove an agent works. It isn't enough to run a client on.

## What the platform does well, and where it gets stuck

CloseBot integrates natively with HighLevel and HubSpot, and works with custom CRMs or standalone. That flexibility cuts both ways: it is not a channel-native tool. It answers the text conversations that land inside your CRM — SMS, web chat, email, and whatever else your CRM routes in. It does not connect to Instagram or WhatsApp on its own, and there's no voice. A third-party review makes that point bluntly, and it's correct.

The practical consequence for a multi-tenant setup: if your client's leads arrive as Instagram DMs and they don't run a CRM, you're selling them two products instead of one. That's an architecture mismatch, not a flaw in the agent.

On quality, the third-party picture is mixed in a useful way. G2 lists it at 4.8/5 across 124 reviews, and the recurring themes in positive reviews are setup speed and conversation handling. The same G2 page's cons section notes limited bot functionality, occasional irrelevant answers and no voice. Reddit threads go further: one r/automation user with two years on the tool describes support cycles where blame moved between the prompt and the CRM's webhooks, and another reports bugs with demo links and knowledge base formatting. In the same thread, other users say it outperforms GoHighLevel's native Conversation AI for booking and rescheduling.

For an agency, the takeaway isn't "avoid it" or "it's flawless." It's that whoever builds your agents needs to test them, and that your client contract should give you room to fix things without eating the retainer. CloseBot ships a testing portal, conversation rollback and the ability to pause the AI mid-conversation for a human takeover — features that exist precisely because agents misbehave sometimes.

HIPAA is Growth-plan-only, which matters if healthcare or dental clients are in your book. The plans page also notes that CloseBot doesn't allow bring-your-own API keys, on security grounds, so your model spend is baked into the plan rather than passed through at cost.

## Deciding which plan, and when this isn't your platform

If you're using it for your own pipeline — real estate team, home services, a clinic — the Business plan pointed at your own CRM is the shape you want. No white labeling, no rebilling, message costs included.

If you're selling AI to clients, the Agency plan is the one whose economics work. The $397 monthly figure only makes sense next to the markup you set, and the free plan plus a 7-day trial on any paid tier is enough time to build one real agent and bill one real client before you commit.

If you're testing the waters, the free tier is genuinely free forever under 100 messages a month. 👉 [👉 Open a free account and build a working agent](https://app.closebot.com/a?fpr=li87) before you look at paid tiers again.

Two situations where a different platform is the better call. If your clients' conversations happen entirely in DMs on Instagram or WhatsApp with no CRM in the middle, a channel-native setter fits the architecture better. And if your clients need SOC 2 or ISO certifications documented for procurement — rather than HIPAA on a custom enterprise tier — you'll want to ask harder questions than a pricing page answers.

One last practical note before you click buy: CloseBot states plainly that it doesn't issue refunds. The free plan and the 7-day trial are the risk window, so use them for the messy part — connecting a real CRM, uploading a real knowledge base, watching what the agent does when a lead asks something awkward. The platform's own current discount code is `CLOSEBOT100OFF` for $100 off a first payment, applicable to both Business and Agency plans. Any other code you find on a coupon site is unverified.

## Frequently asked questions

**Can one CloseBot account hold multiple clients?**

Yes. Agency accounts hold unlimited agents and sources, with each client connection running under its own knowledge base and variables. Clients log into a white-labeled portal to see their own dashboards, message counts and charges.

**Can clients edit the agents?**

They can fill in variables you define and upload documents to their knowledge library. They can't change the agent's logic or structure. That's deliberate — it protects your build and stops clients from breaking working flows.

**What does a client conversation cost the agency?**

$0.012 per message at the wholesale rate, plus $5 per user seat per month and $0.006 per MB per day of storage. All three can be marked up when you re-bill through your Stripe account.

**Is there a free plan?**

Yes, and it's not a trial — 100 AI replies a month, one agent, one user seat, 1 MB of storage, unlimited account connections. Paid plans also come with a 7-day trial before billing starts.

**Does CloseBot replace GoHighLevel or HubSpot?**

No. It sits on top of them or your custom CRM and takes over the text-based conversations running through those channels. Some businesses run it standalone, but it's designed as the conversation layer, not the CRM.
