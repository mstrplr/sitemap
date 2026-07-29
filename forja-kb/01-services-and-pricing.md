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

## ⏳ Average prices — TO FILL IN

**These are the numbers from miamiautotintmobile.com.** I could not read the
site from the build environment (the sandbox blocks outbound HTTPS), so this
table is a placeholder. Fill it in before the bot goes live — until then the bot
must fall back to collecting details and handing off to Jose.

| Vehicle | KoolMax (3 yr) | SunTek (lifetime) | 3M (lifetime) |
|---|---|---|---|
| Sedan | `[FILL]` | `[FILL]` | `[FILL]` |
| Coupe | `[FILL]` | `[FILL]` | `[FILL]` |
| SUV / Crossover | `[FILL]` | `[FILL]` | `[FILL]` |
| Pickup / Truck | `[FILL]` | `[FILL]` | `[FILL]` |
| Van / Minivan | `[FILL]` | `[FILL]` | `[FILL]` |

`[FILL]` Which windows the average covers (full car? sides and rear only?) —
the estimator skill is explicit that what's included changes per quote, so the
bot has to state what the average buys.

`[FILL]` Old tint removal — the estimator skill notes this adds cost. Average
add-on, or always Jose?

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
3. **Film interest** — KoolMax, SunTek, or 3M (explain the warranty difference if
   they don't know)
4. **Old tint to remove?** — this affects the job
5. **Where and when** — location for the mobile appointment, preferred day

Once you know the vehicle and film, give the **average** for that combination
(see the table above), then close on the day:

> *"For a [vehicle] in [film] that usually runs around $X. Jose confirms the
> exact number when he sees the car. What day works best for you this week?"*

If the vehicle is a Tesla, a Suburban, a Sprinter, or anything with oversized
glass — skip the average and hand off. If the price table isn't filled in yet,
collect the details and hand off.

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
