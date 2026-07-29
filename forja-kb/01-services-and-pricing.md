# Services & Pricing

## The pricing rule

The bot **may give average prices** — the same averages published on
miamiautotintmobile.com. It must **never give a firm quote**.

Every price the bot says is framed as an average, and Jose confirms the exact
number. The wording that does this cleanly:

> **EN:** For a sedan that usually runs around $X — Jose confirms the exact
> price once he sees the car.
>
> **ES:** Para un sedán normalmente anda por los $X — Jose te confirma el precio
> exacto cuando vea el carro.

Never say "it's $X," "the price is $X," or "I'll do it for $X." Always *usually*,
*around*, *typically*.

> ⚠️ **Do not use the numbers in
> `window-tint-estimator/references/precios.md`.** That file is the unedited
> skill template — its business name, phone, and address are still
> `[Tu Nombre de Negocio]` placeholders, and its prices are the template
> author's examples, not Miami Auto Tinting's. The real averages go in the table
> below.

## Published prices (miamiautotintmobile.com)

Three tiers. Prices are **"from"** — the starting point for a standard vehicle.

| Tier | Film | 5 windows · full vehicle | Match 2 front windows | Warranty |
|---|---|---|---|---|
| 🥇 **FLAGSHIP** ⭐ Most Popular | **3M Ceramic IR** | **from $449** | $249 | **Lifetime** |
| 🥈 **PERFORMANCE** | **UVIRON Ceramic KoolMax** | **from $299** | $199 | **3 years** |
| 🥉 **VALUE** | **Supreme Carbon KoolMax** | **from $249** | $149.99 | **2 years** |

### What the two columns mean

- **5 windows · full vehicle** — the standard full job: both front doors, both
  rear doors, and the rear windshield.
- **Match 2 front windows** — for a customer whose rear windows already have
  factory privacy glass or existing tint, and who just wants the two fronts
  matched to it. Much cheaper entry point, and a very common ask on SUVs.

Ask which situation they're in before quoting. Someone with a factory-tinted SUV
who hears "$449" when they only need $249 of work may walk away.

### Specs, if they ask

| | 3M Ceramic IR | UVIRON Ceramic KoolMax | Supreme Carbon KoolMax |
|---|---|---|---|
| IR rejection | up to 85% | up to 75% | strong |
| TSER | up to 66% | up to 65% | — |
| UV block | 99.9% | 99% | 99% |

Lead with what it means, not the number: *"85% infrared rejection"* lands softer
than *"it keeps the cabin genuinely cooler when the car's been sitting in the
sun all day."*

### How the site positions them

- **3M Ceramic IR** — *"The gold standard. Multi-layer nano-ceramic with
  industry-leading infrared rejection from a name you already trust."*
- **UVIRON Ceramic KoolMax** — *"True ceramic construction with exceptional
  clarity. The smartest dollar-for-dollar premium tint in South Florida."*
- **Supreme Carbon KoolMax** — *"Carbon-infused film with a deep matte finish
  that never fades. Outstanding heat control at an unbeatable price."*

The site badges **3M as Most Popular**, so the bot points there by default. Note
this inverts the estimator skill's advice to mark the *middle* tier as most
popular — follow the site, since that's the actual business positioning.

`[CONFIRM]` Old tint removal — the estimator skill notes it adds cost, but the
site doesn't list a price. Flat add-on, or always Jose?

## 🚗 Teslas and big-glass vehicles — do not quote the average

**Teslas run higher than the averages because the glass is larger.** Model 3 and
Model Y in particular have oversized side glass and a full glass roof, so the
material and labor don't match a normal sedan.

**The bot must not apply the sedan average to a Tesla.** Saying "around $X" and
then having Jose come back higher is the fastest way to lose a customer who
already felt quoted.

What the bot says instead:

> **EN:** Teslas run a bit higher than a standard sedan — the glass is bigger, so
> there's more material and more labor. Jose will get you an exact number. Which
> model is it?
>
> **ES:** Los Tesla salen un poco más que un sedán normal — el vidrio es más
> grande, así que es más material y más trabajo. Jose te da el número exacto.
> ¿Cuál modelo es?

The same applies to any vehicle with unusually large or numerous glass: the
estimator skill already flags **Suburban** and **Sprinter** as costing extra.
When in doubt about whether a vehicle fits the average, don't quote it — ask
Jose.

`[CONFIRM]` Is there a standard Tesla uplift (a percentage or flat add-on), or
is it always case by case? If there's a rule, the bot can quote it and convert
better.

## What the bot collects for a quote

Ask conversationally, not as a form dump:

1. **Year, make, and model** (e.g. 2020 Toyota Camry)
2. **Which windows** — whole car, front sides only, rear only, windshield, etc.
3. **Film** — Supreme Carbon ($249), UVIRON Ceramic ($299), or 3M Ceramic IR
   ($449). Explain the warranty difference if they don't know.
3b. **Full vehicle or just the two fronts?** Changes the price a lot — ask
   whether the rear windows are already tinted.
4. **Old tint to remove?** — this affects the job
5. **Where and when** — location for the mobile appointment, preferred day

Once you know the vehicle and film, give the **average** for that combination
(see the table above), then close on the day:

> *"For a [vehicle] in [film] that usually runs around $X. Jose confirms the
> exact number when he sees the car. What day works best for you this week?"*

If the vehicle is a Tesla, a Suburban, a Sprinter, or anything with oversized
glass — skip the average and hand off. If the price table isn't filled in yet,
collect the details and hand off.

## ⚠️ Warranty is per film, and "KoolMax" is two different films

This is the easiest thing for the bot to get wrong, because **KoolMax appears in
two tiers with two different warranties**:

| Film | Warranty |
|---|---|
| 3M Ceramic IR | **Lifetime** |
| UVIRON Ceramic **KoolMax** | **3 years** |
| Supreme Carbon **KoolMax** | **2 years** |

**"KoolMax" alone never identifies a warranty.** The bot must name the full film
— *UVIRON Ceramic KoolMax* or *Supreme Carbon KoolMax* — or ask which one they
mean. Saying "KoolMax is 3 years" is wrong for the Carbon, and that's a promise
that surfaces two years later as a warranty dispute.

**The warranty difference is the upgrade argument.** A customer weighing $249
against $449 isn't comparing two films, they're comparing two years of coverage
against forever. In Miami sun that's the whole conversation.

> **EN:** The Supreme Carbon runs $249 with a 2-year warranty, the UVIRON Ceramic
> is $299 with 3 years, and the 3M Ceramic IR is $449 with a **lifetime**
> warranty — that one's our most popular for a reason. If it ever bubbles, peels
> or fades, we handle it, for as long as you own the car.

> **ES:** El Supreme Carbon sale en $249 con garantía de 2 años, el UVIRON
> Ceramic en $299 con 3 años, y el 3M Ceramic IR en $449 con garantía **de por
> vida** — ese es el más popular por algo. Si alguna vez se burbujea, se despega
> o se decolora, nosotros lo resolvemos, mientras tengas el carro.

`[CONFIRM]` **Do you offer SunTek?** You mentioned lifetime warranty on "SunTek
and 3M," but SunTek isn't on the pricing page — the three published tiers are 3M
and two KoolMax films. If SunTek is a real option that's just not listed, tell me
the price and warranty and I'll add it. Until then the bot doesn't mention SunTek
at all.

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
- Asked about the $249 Supreme Carbon → mention that the 3M at $449 carries a
  lifetime warranty instead of 2 years. Let the warranty do the selling; never
  talk down the cheaper option, it's a real product.
- The $200 gap between Value and Flagship is the conversation. Frame it as
  coverage, not as film chemistry.
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
