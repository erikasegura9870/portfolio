# 03 · Quiz funnel with a paid upsell

**Meridianine (EriPao Yoga · Meridianine)** · B2C wellness brand for neurodivergent adults

| Role | Timeline | Status | Links |
|---|---|---|---|
| Brand funnel strategy, content, CRM automation, pages | October 2026 | Live | [Quiz](https://meridianine.com) · [Upsell page](https://meridianine.com/kit) |

| Entry quiz | Upsell page |
|---|---|
| ![Quiz](img/kit-quiz.png) | ![Sales page](img/kit-sales.png) |

## Context

Mainstream wellness apps rely on streaks and 30-day plans that many neurodivergent people abandon. The brand needed a first step that feels personal and a path to a first purchase without pressure tactics.

## Challenge

Segment visitors in seconds, deliver a free resource matched to their state, and convert a share of them into a low-ticket product.

## Approach

1. **Segmentation:** a 7-question quiz (about 90 seconds) assigns one of 4 nervous-system states.
2. **Lead magnet:** a 9-page visual kit per state, delivered by email.
3. **Automation:** one CRM automation with 4 branches, keyed to the state stored on the contact.
4. **Upsell:** 3 guided audios at USD 17, linked from the kit and from a dedicated sales page with an interactive state selector.
5. **Ethics:** no countdowns, no invented testimonials, no autoplay; copy written for an intuitive, sensitive audience.

## Solution

![Flow](img/flow.png)

![Visual kit](img/kit-pdf.png)

## How the CRM segmentation works (Brevo)

1. **One list for the funnel.** Every quiz submission goes to the brand's entry list.
2. **Upsert, not duplicates.** A server-side endpoint creates or updates the contact by email, so retaking the quiz updates the profile instead of creating a second record.
3. **Custom attributes.** `PERFIL` stores the state (Alert, Exhausted, Blocked, Recharge) and `ND` stores the self-reported profile; both are visible on the contact record.
4. **Branching automation.** One automation starts when the contact joins the list and splits on `PERFIL`: Alert, Exhausted and Blocked each get their own email and kit; everyone else gets Recharge.
5. **Trusted sender.** Emails go out from a verified brand address on the authenticated domain (SPF, DKIM, DMARC).

## Outcomes

- Full funnel live: quiz → segmented list → automated delivery → upsell → checkout.
- Quiz integration moved from a no-code webhook to a direct, server-side CRM connection, keeping keys off the browser.
- Same infrastructure and CRM as Case 01, so leads from both brands live in one system.

**Stack:** HTML, CSS, JavaScript · Cloudflare Workers · Brevo (lists, attributes, automations) · Hotmart

**Built with:** Claude as AI build partner; the first version of the quiz ran through an n8n webhook.
