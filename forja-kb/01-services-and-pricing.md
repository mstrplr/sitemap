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
3. **Film interest** — KoolMax, SunTek, or 3M (explain the warranty difference if
   they don't know)
4. **Old tint to remove?** — this affects the job
5. **Where and when** — location for the mobile appointment, preferred day

Then: *"Let me get these to Jose and he'll come back with exact pricing for your
[vehicle]. What day works best for you this week?"*

## The film lineup — three brands, two warranty tiers

We carry **KoolMax**, **SunTek**, and **3M**. The warranty is what separates
them, and it's the single most useful thing the bot can explain:

| Brand | Warranty |
|---|---|
| **KoolMax** | **3 years** |
| **SunTek** | **Lifetime** |
| **3M** | **Lifetime** |

**The warranty difference is the sales argument.** Don't present it as fine
print — it's the reason to move up. A customer choosing between KoolMax and
SunTek isn't really choosing between two films, they're choosing between covered
for three years and covered forever.

Natural framing:

> **EN:** KoolMax is our budget option and comes with a 3-year warranty. SunTek
> and 3M both carry a **lifetime** warranty — if it ever bubbles, peels, or
> fades, we handle it. In Miami sun that difference matters more than people
> expect.

> **ES:** KoolMax es la opción económica, con garantía de 3 años. SunTek y 3M
> traen garantía **de por vida** — si alguna vez se burbujea, se despega o se
> decolora, nosotros lo resolvemos. Con el sol de Miami esa diferencia pesa más
> de lo que la gente cree.

This maps onto the three-tier structure in the estimator skill: KoolMax as the
🥉 entry option, SunTek and 3M as the 🥈/🥇 lifetime options.

`[CONFIRM]` Which of SunTek or 3M should be positioned as the top tier, and which
as the "most popular" middle? Both carry lifetime, so the ordering is a sales
decision, not a spec one. Jose decides which one he wants to move.

## Talking about film technology

Customers ask about "ceramic" and "carbon" — those are film technologies, and
each brand makes several lines. Sell the outcome, not the spec sheet:

- **Heat rejection** — the argument that lands in Miami, year round
- **No signal interference** — quality film won't affect GPS, radio, or cell
- **Won't fade or turn purple** — the failure mode everyone has seen on cheap tint

`[CONFIRM]` Which specific film lines Jose stocks within each brand. Do not name
product lines the bot hasn't been given — if a customer asks for a specific
product by name, hand off to Jose.

**Upsell gently, never push:**
- Asked about KoolMax → mention that SunTek and 3M carry a lifetime warranty
  instead of 3 years. Let the warranty do the selling; don't talk down the
  cheaper option.
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
