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

## How pricing works

Three published tiers, all **"from"** prices:

| Tier | Film | Full vehicle | 2 fronts only | Warranty |
|---|---|---|---|---|
| 🥇 Flagship ⭐ | 3M Ceramic IR | from $449 | $249 | **Lifetime** |
| 🥈 Performance | UVIRON Ceramic KoolMax | from $299 | $199 | 3 years |
| 🥉 Value | Supreme Carbon KoolMax | from $249 | $149.99 | 2 years |

Four rules the bot follows:

- **"Starts at," never "it's."** Every number is a from-price; Jose confirms the
  exact figure when he sees the car.
- **Ask whether the rear windows are already tinted.** Someone who only needs the
  two fronts matched pays $149.99–$249, not $249–$449. Quoting the full job to
  them loses a sale that was already yours.
- **Teslas and big-glass vehicles** (also Suburban, Sprinter) run higher. The bot
  explains why and hands off rather than quoting low — a customer who feels
  quoted and then hears a higher number walks.
- **Name the full film for any warranty claim.** "KoolMax" is two different films
  at two different warranties.

> **Don't use `window-tint-estimator/references/precios.md`.** That file is the
> untouched skill template — its business name, phone, and address are still
> `[Tu Nombre de Negocio]` placeholders, and its prices ($180 sedan, "2 años")
> are the author's examples, not yours.

## Before you go live — fill these in

Everything marked `[CONFIRM]` in the KB:

- [x] ~~Phone~~ — 786-285-2690
- [x] ~~Website~~ — southmiamitint.com
- [x] ~~Hours~~ — Mon–Sat 9–5, appointment only, some Sundays when available
- [x] ~~Payment methods~~ — cash, Zelle, card
- [x] ~~Films, prices and warranty~~ — three tiers, see table above
- [ ] **Check the Twilio ↔ WhatsApp Business conflict** on 786-285-2690 before
      committing to the WhatsApp channel (see `../FORJA-SETUP.md`) — this is the
      one that can take the business line down mid-week
- [x] ~~Price table~~ — filled from miamiautotintmobile.com
- [ ] **Do you offer SunTek?** It's not on the pricing page. The bot doesn't
      mention it until confirmed
- [ ] Old tint removal — flat add-on, or always Jose?
- [ ] Is there a standard Tesla uplift, or always case by case?
- [ ] The site's call banner shows **786-269-8850**, but the bot gives
      786-285-2690 — intentional?
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
  --ofrece "Mobile window tint installation. Three films, full vehicle (5 windows): Supreme Carbon KoolMax from \$249 (2-year warranty), UVIRON Ceramic KoolMax from \$299 (3-year), 3M Ceramic IR from \$449 (LIFETIME warranty, most popular). Matching just the 2 front windows: \$149.99 / \$199 / \$249. Old tint removal available. All prices are FROM prices; Jose confirms exact." \
  --horario "Monday to Saturday 9am-5pm, by appointment only. Some Sundays when available." \
  --ubicacion "Mobile service across Miami-Dade County: Miami, Hialeah, Doral, Coral Gables, Kendall, Miami Beach, Brickell, Homestead, Cutler Bay, West Miami, Sweetwater" \
  --telefono "786-285-2690" \
  --web "southmiamitint.com" \
  --pagos "Cash, Zelle, card. Paid on site when the job is done." \
  --faq "How much does it cost?, Do you really come to me?, What are your hours?, How long does it take?, What brands do you use?, Is there a warranty?, How dark can I legally go?, Can I wash the car after?" \
  --reglas "Every price is a FROM price — say 'starts at \$249', never 'it's \$249', and always add that Jose confirms the exact number. Ask whether the rear windows are already tinted: matching only the 2 front windows is much cheaper than the full vehicle. NEVER quote a Tesla, Suburban, Sprinter or any big-glass vehicle from the published price: bigger glass costs more, explain that and hand off to Jose. Warranty is per film: 3M Ceramic IR is LIFETIME, UVIRON Ceramic KoolMax is 3 years, Supreme Carbon KoolMax is 2 years — never say just 'KoolMax' for a warranty, two films share that name. Never mention SunTek. Florida tint limits: 28% front sides all vehicles, 15% rear on sedans, 6% rear on SUVs/vans — but never say a specific film will be legal on a specific car, since the law measures film plus factory glass. Service is appointment only Mon-Sat 9-5, some Sundays when available — never promise same-day, walk-ins, or a guaranteed Sunday. Never confirm an appointment time, only collect the preferred day. Hand off on complaints, warranty claims, fleet inquiries, tint tickets, or medical exemptions." \
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
