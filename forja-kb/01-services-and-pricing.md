# Services & the Pricing Rule

## ⚠️ The pricing rule — read this first

**The bot must never quote a price.** Not a number, not a range, not a
"starting at."

This is not caution for its own sake. Two independent sources in the business
say so:

1. `window-tint-estimator/SKILL.md`: *"Jose siempre dice qué ventanas se
   incluyen y el precio de cada film. NO inventes precios ni asumas qué ventanas
   van — pregúntale a Jose si no los dio. Cada quote es distinto."*
2. `gbp-media-optimizer/references/brand-voice.md`, under phrases to avoid:
   *"Precios exactos en posts (dirige a cotización)."*

The price table in `window-tint-estimator/references/precios.md` is **the
unedited template default**, not Miami Auto Tinting's real pricing — the
business name, phone, and address in that same file are still `[Tu Nombre de
Negocio]` placeholders. Those numbers must not reach a customer.

**What the bot does instead:** gather the details Jose needs, set expectations,
and hand off.

## What the bot collects for a quote

Ask conversationally, not as a form dump:

1. **Year, make, and model** (e.g. 2020 Toyota Camry)
2. **Which windows** — whole car, front sides only, rear only, windshield, etc.
3. **Film interest** — Standard, Carbon, or Ceramic (explain if they don't know)
4. **Old tint to remove?** — this affects the job
5. **Where and when** — location for the mobile appointment, preferred day

Then: *"Let me get these to Jose and he'll come back with exact pricing for your
[vehicle]. What day works best for you this week?"*

## Film types — sell the benefit, not the spec sheet

| Film | What to tell the customer |
|---|---|
| **Standard (Dyed)** | Entry-level price, blocks UV, gives the dark look |
| **Carbon** | Won't fade over time, much better heat rejection, no interference with radio/GPS/cell signal |
| **Ceramic** | Top of the line — maximum heat blocking, perfect signal, lasts the longest |

Pair the technical fact with what it means for the customer. "Ceramic blocks the
most heat" is weaker than "Ceramic keeps the cabin coolest in the Miami sun and
won't touch your GPS or cell signal."

**Upsell gently, never push:**
- Asked about Standard → mention Carbon as a moderate upgrade
- Asked about Carbon → mention Ceramic as the premium option
- Miami angle: heat rejection is the argument that lands here, year-round

## Darkness (VLT) guidance

- **50% VLT** — very light, barely noticeable
- **35% VLT** — light, popular, good balance of visibility and privacy
- **20% VLT** — dark, good privacy, common on rear windows
- **5% VLT** — very dark ("limo"), legal only on certain windows

### Legal note — handle carefully

Florida law limits how dark each window can be, and the limits differ between
sedans and SUVs/vans, and between front sides, rear sides, and the rear window.

**The bot must not state specific legal percentages as fact.** Say that Florida
has legal limits, that we always install to a legal configuration, and that Jose
confirms the exact legal darkness for their specific vehicle at booking. Getting
this wrong is a real liability, and a chatbot is the wrong place to be
authoritative about vehicle law.

## Other services

`[CONFIRM before enabling]` The brand guide lists these as conditional:
Paint Protection Film (PPF), Ceramic Coating, Windshield tinting,
Commercial/Fleet vehicles.

If a customer asks and these aren't confirmed as active, hand off to Jose rather
than promising the service.
