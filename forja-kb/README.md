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

## The one design decision worth knowing

**This bot does not quote prices.** It qualifies the lead — year/make/model,
windows, film interest, old tint, location, preferred day — and hands off to
Jose.

That came from your own material, in two places:

- `window-tint-estimator/SKILL.md`: *"NO inventes precios ni asumas qué ventanas
  van — pregúntale a Jose si no los dio. Cada quote es distinto."*
- `brand-voice.md` lists *"Precios exactos"* under phrases to avoid, directing to
  a quote instead.

The price tables in `window-tint-estimator/references/precios.md` are **still
the untouched template defaults** — that file's business name, phone, and
address are literally `[Tu Nombre de Negocio]`, `[Tu número de WhatsApp]`, and
`[Tu dirección]`. Its numbers ($180 sedan, $280 ceramic sedan, "2 años" warranty,
"Lunes a Sábado 8am–6pm") are the skill author's examples, not your rates.
Feeding them to a customer-facing bot would have it quoting prices you never set.

If those numbers *are* actually right, tell me and I'll rewrite the KB to let the
bot quote directly — it's a much stronger bot when it can. But I'm not going to
assume it.

## Before you go live — fill these in

Everything marked `[CONFIRM]` in the KB:

- [x] ~~Phone number~~ — resolved: CallRail tracking number per channel, see
      `06-phone-and-callrail.md`
- [ ] **Create a CallRail tracking number with source "WhatsApp"** before launch,
      so the bot's own calls are attributable
- [ ] Confirm the tracking numbers have SMS enabled if Jose will text follow-ups
- [x] ~~Hours and days of operation~~ — Mon–Sat 9–5, appointment only, some
      Sundays when available
- [ ] **Check the Twilio ↔ WhatsApp Business conflict** on 786-285-2690 before
      committing to the WhatsApp channel (see `../FORJA-SETUP.md`)
- [ ] Website URL and social handles
- [ ] Payment methods accepted
- [ ] Warranty terms per film type
- [ ] Whether PPF, ceramic coating, and fleet work are live services
- [ ] Whether the bot may quote prices (see above)
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
  --ofrece "Window tint installation, mobile service. Films: Standard/Dyed, Carbon, Ceramic. Old tint removal. Pricing quoted per vehicle by Jose — the bot never quotes prices." \
  --horario "Monday to Saturday 9am-5pm, by appointment only. Some Sundays when available." \
  --ubicacion "Mobile service across Miami-Dade County: Miami, Hialeah, Doral, Coral Gables, Kendall, Miami Beach, Brickell, Homestead, Cutler Bay, West Miami, Sweetwater" \
  --telefono "[CallRail WhatsApp tracking number — create it first, see 06-phone-and-callrail.md]" \
  --web "[YOUR SITE OR INSTAGRAM]" \
  --pagos "[YOUR PAYMENT METHODS]" \
  --faq "How much does it cost?, Do you really come to me?, How long does it take?, How long does tint last?, Can I wash the car after?, How dark can I legally go?" \
  --reglas "NEVER quote a price — collect year/make/model, windows, and film interest, then hand off to Jose. Florida tint limits: 28% front sides all vehicles, 15% rear on sedans, 6% rear on SUVs/vans — but never say a specific film will be legal on a specific car, since the law measures film plus factory glass. Phone numbers come from the CallRail channel map — never give a routing number or invent one. Never confirm an appointment time — collect preference only. Never invent hours, warranty terms, or payment methods. Hand off on complaints, warranty claims, fleet inquiries, tint tickets, or medical exemptions." \
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
