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

## Lifetime warranty — use it

Miami Auto Tinting backs the work with a **lifetime warranty**. Bubbling,
peeling, fading — covered.

This is one of the strongest things the bot has to say, and it costs nothing to
say early. It answers the unspoken objection behind "how much is it" — that cheap
tint turns purple and bubbles in two Miami summers. Pair it with the film
conversation rather than saving it for the end.

`[CONFIRM]` **Does the lifetime warranty apply to all three films, or only
Carbon and Ceramic?** In this industry, entry-level dyed film usually carries a
shorter term while premium films get lifetime — and the estimator skill's tier
template says to highlight lifetime *"si aplica"*, which suggests it varies. Until
Jose confirms, the bot should say "lifetime warranty" generally and let Jose
state the specific term per film. Do not attach "lifetime" to a specific film by
name.

**Upsell gently, never push:**
- Asked about Standard → mention Carbon as a moderate upgrade
- Asked about Carbon → mention Ceramic as the premium option
- Miami angle: heat rejection is the argument that lands here, year-round

## Darkness (VLT) guidance

- **50% VLT** — very light, barely noticeable
- **35% VLT** — light, popular, good balance of visibility and privacy
- **20% VLT** — dark, good privacy, common on rear windows
- **5% VLT** — very dark ("limo"), legal only on certain windows

### Legal limits

Florida caps how dark each window can go, and the back-window limits differ
between sedans and SUVs/vans. Short version:

- **Front side windows:** more than 28% VLT — every vehicle
- **Rear side + rear window:** more than 15% on sedans, more than 6% on SUVs,
  vans, and trucks

**Always ask what vehicle they have before quoting a limit.** Full detail —
reflectivity caps, the AS-1 windshield line, medical exemptions, and the
film-VLT vs. finished-VLT distinction — is in `05-florida-tint-law.md`. Read
that file's rules before answering any legal question.

## Other services

`[CONFIRM before enabling]` The brand guide lists these as conditional:
Paint Protection Film (PPF), Ceramic Coating, Windshield tinting,
Commercial/Fleet vehicles.

If a customer asks and these aren't confirmed as active, hand off to Jose rather
than promising the service.
