# Forja Knowledge Base — Miami Auto Tinting

Drafted from the existing `window-tint-estimator` and `gbp-media-optimizer`
skills. Drop these files into `member/kb/` in your bot folder after
`forjabot init`, or paste them when the `/configurar-mi-chatbot` skill reaches
**Phase 2 (business / knowledge base)**.

| File | Contents |
|---|---|
| `00-business.md` | Identity, service area, USP, unconfirmed details |
| `01-services-and-pricing.md` | Films, VLT, and the no-quoting rule |
| `02-faq.md` | Bilingual FAQ, ready to use |
| `03-rules-and-handoff.md` | Guardrails and handoff criteria |
| `04-tone.md` | Voice, WhatsApp formatting, seasonal angles |
| `05-florida-tint-law.md` | VLT limits by vehicle class, AS-1 line, reflectivity, exemptions |
| `06-phone-and-callrail.md` | Channel → tracking number map, attribution rules |

## ⏳ Blocking item: the price table is empty

`01-services-and-pricing.md` has a price table that still says `[FILL]`.

The averages come from **miamiautotintmobile.com**, which I could not read — the
build sandbox blocks outbound HTTPS to it (403 from the egress proxy). **Paste
the numbers in and the bot is ready to quote.**

Until that table is filled, the bot falls back to collecting vehicle details and
handing off to Jose. It won't invent a number, but it also won't convert as well.

## How pricing works

The bot gives **averages, never firm quotes** — always *usually / around /
typically*, always followed by "Jose confirms the exact number."

Two carve-outs matter:

- **Teslas and big-glass vehicles** (also Suburban, Sprinter) run higher than the
  averages. The bot never applies the sedan average to these — it explains why
  and hands off. Quoting low and having Jose come back higher loses the customer.
- **Don't use `window-tint-estimator/references/precios.md`.** That file is the
  untouched skill template — business name, phone, and address are still
  `[Tu Nombre de Negocio]` placeholders, and its prices are the author's
  examples, not yours.

## Before you go live — fill these in

Everything marked `[CONFIRM]` in the KB:

- [x] ~~Phone~~ — 786-285-2690
- [x] ~~Website~~ — southmiamitint.com
- [x] ~~Hours~~ — Mon–Sat 9–5, appointment only, some Sundays when available
- [x] ~~Payment methods~~ — cash, Zelle, card
- [x] ~~Films and warranty~~ — KoolMax 3 years, SunTek and 3M lifetime
- [ ] **Check the Twilio ↔ WhatsApp Business conflict** on 786-285-2690 before
      committing to the WhatsApp channel (see `../FORJA-SETUP.md`) — this is the
      one that can take the business line down mid-week
- [ ] **Fill the price table** in `01-services-and-pricing.md` from
      miamiautotintmobile.com — blocks the bot from quoting at all
- [ ] What the average covers (full car? sides and rear only?)
- [ ] Old tint removal — average add-on, or always Jose?
- [ ] Is there a standard Tesla uplift, or always case by case?
- [ ] Which of SunTek or 3M is the top tier vs. the "most popular" middle
- [ ] Which film lines Jose stocks within each brand
- [ ] Whether PPF, ceramic coating, and fleet work are live services
- [ ] Confirm 786-285-2690 has SMS enabled if Jose will text follow-ups
- [ ] **Verify the Florida VLT limits in `05-florida-tint-law.md`** against the
      current FLHSMV statute text. They've been stable for years, but the bot
      states them to customers as fact — worth one check against the source, and
      a re-check annually.

## Ready-to-run init command

Run this on your **local machine** (it can't run in the Claude Code web sandbox —
see `../FORJA-SETUP.md`). Replace the bracketed values first:

```bash
npx forjabot init --yes --lang en \
  --negocio "Miami Auto Tinting" \
  --que "mobile window tinting — we come to the customer, home or office, anywhere in Miami-Dade" \
  --ofrece "Window tint installation, mobile service. Films: KoolMax (3 year warranty), SunTek and 3M (lifetime warranty). Old tint removal. Pricing quoted per vehicle by Jose — the bot never quotes prices." \
  --horario "Monday to Saturday 9am-5pm, by appointment only. Some Sundays when available." \
  --ubicacion "Mobile service across Miami-Dade County: Miami, Hialeah, Doral, Coral Gables, Kendall, Miami Beach, Brickell, Homestead, Cutler Bay, West Miami, Sweetwater" \
  --telefono "786-285-2690" \
  --web "southmiamitint.com" \
  --pagos "Cash, Zelle, card. Paid on site when the job is done." \
  --faq "How much does it cost?, Do you really come to me?, What are your hours?, How long does it take?, What brands do you use?, Is there a warranty?, How dark can I legally go?, Can I wash the car after?" \
  --reglas "Prices are AVERAGES, never firm quotes — always say 'usually around $X' and add that Jose confirms the exact number. NEVER quote a Tesla, Suburban, Sprinter or any big-glass vehicle from the average: bigger glass costs more, explain that and hand off to Jose. Warranty depends on the film: SunTek and 3M are lifetime, KoolMax is 3 years — never say lifetime without naming the brand. Florida tint limits: 28% front sides all vehicles, 15% rear on sedans, 6% rear on SUVs/vans — but never say a specific film will be legal on a specific car, since the law measures film plus factory glass. Service is appointment only Mon-Sat 9-5, some Sundays when available — never promise same-day, walk-ins, or a guaranteed Sunday. Never confirm an appointment time, only collect the preferred day. Hand off on complaints, warranty claims, fleet inquiries, tint tickets, or medical exemptions." \
  --tono cercano \
  --cerebro claude
```

Then load the KB files above in Phase 2 for the depth the flags can't carry.

Note: `--tono cercano` (warm/close) is the nearest match to your brand voice.
Forja's three options are `cercano`, `formal`, and `divertido` — "energetic and
direct, Miami vibes, not corporate" maps to `cercano` over the other two, and
`04-tone.md` carries the nuance.

## Keeping the two in sync

The bot and your `window-tint-estimator` skill should agree. When Jose changes
films, warranty, or service area, update both — otherwise the bot tells
customers one thing and your quotes say another.
