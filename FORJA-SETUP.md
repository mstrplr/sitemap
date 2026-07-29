# Forja chatbot setup — Miami Auto Tinting

Status of the attempt made in the Claude Code **web** session, and what to do next.

## What happened

`npx forjabot init` was run and it **failed**, but not because of anything wrong
with the tool:

```
✎ guía de Forja instalada para tu agente → ~/.claude/skills/forja/
  Creating your free license… ✗ fetch failed
```

The CLI downloaded and started fine. It died at the license step because this
remote container's egress policy blocks the hosts Forja needs:

| Host | Result |
|---|---|
| `horizontes-license-server.innovandohorizontes.workers.dev` | 403 (blocked) |
| `forjabots.com` | 403 (blocked) |

This is an organization network policy on the Claude Code web sandbox, not a
Forja bug and not something to route around.

## Why this has to run on your own computer anyway

Even with the network open, the Forja flow can't finish in a web session:

- **The container is ephemeral.** The bot folder and `~/.forja/credentials.json`
  are destroyed when the session ends.
- **`wrangler login` and `forjabot login` open a browser** for OAuth. There's no
  browser here that's yours.
- **The bot lives in *your* Cloudflare account** with *your* AI key. Those
  credentials should be entered on your machine, not typed into a chat session.

So: install **Claude Code on your laptop** and run it there.

## Steps to run locally

1. Install Claude Code — https://claude.com/claude-code
2. Open a terminal in a folder where you want the bot to live (e.g. `~/miami-tint-bot`).
3. Run Claude Code, and tell it: **"install Forja and set up my chatbot"**.

The `forjabot` CLI installs a skill at `~/.claude/skills/forja/` on first run, so
your local Claude Code will already know the whole flow (it interviews you one
question at a time and runs the commands for you).

If you'd rather drive it yourself:

```bash
npx forjabot login    # connects the CLI to your forjabots.com dashboard
npx forjabot init     # interactive wizard: language, license, business type
npx forjabot doctor   # health check once installed
```

You'll need: **Node 18+**, a free **Cloudflare** account (the bot's home,
~$0 to start, ~$5/mo at volume), and an **AI API key** (Anthropic / OpenAI / xAI,
roughly $1–2/mo). The key is stored as a Cloudflare secret via
`wrangler secret put` — it never passes through the Forja CLI.

The free tier gives you the generic **Starter** bot. The 14 niche bots require a
Forja+ key (`HZN-…`) from the Horizontes IA community.

## Channels: WhatsApp yes, Instagram no

This is the part worth knowing before you start.

**Forja's supported channels are WhatsApp (via Twilio), Telegram, and a web chat
widget.** Instagram DMs are **not** a Forja channel. The only two mentions of
Instagram anywhere in the CLI and its agent skill are an example business URL and
the vendor's own support handle — there is no Instagram connector.

### WhatsApp — supported

Connected through **Twilio**, during Phase 3 of the `/configurar-mi-chatbot`
skill. The general shape:

1. Create a Twilio account.
2. Start with the **WhatsApp Sandbox** to test immediately, then move to a real
   WhatsApp sender (this requires Meta Business verification of your business —
   allow a few days).
3. Point the Twilio WhatsApp webhook at your deployed worker's endpoint.
4. Put the Twilio credentials into Cloudflare with `wrangler secret put`.
5. Send a real message to confirm it round-trips.

### ⚠️ Check this before you commit: the number conflict

The business WhatsApp is **786-285-2690**. A phone number can only be registered
to **one** WhatsApp Business setup at a time — either the WhatsApp Business app
on Jose's phone, or the WhatsApp Business API through Twilio. Not both.

So connecting the bot to 786-285-2690 through Twilio most likely means **losing
the WhatsApp Business app on that phone**. Conversations would move to the bot
and its dashboard instead of the phone Jose uses today. For a business where the
owner answers his own messages, that's a significant change, not a technicality.

Three ways through it, worth deciding before any Twilio setup:

1. **Test on the Twilio sandbox first.** Costs nothing, touches no real number,
   and shows exactly how the bot behaves before anything migrates.
2. **Use a second number for the bot.** Keeps 786-285-2690 exactly as it is on
   Jose's phone. Cleanest option, and the new number can be a CallRail tracking
   number so bot conversations are attributable from day one. The tradeoff is
   that customers who already have the old number keep landing on the phone.
3. **Migrate 786-285-2690 to Twilio** and handle everything through the bot with
   human handoff. Strongest long-term setup, but confirm Jose is comfortable
   working out of the dashboard instead of the WhatsApp app.

`[VERIFY]` I could not reach Twilio's or Meta's current docs from the sandbox to
confirm the exact migration path — check this against Twilio's WhatsApp sender
documentation before making the change, since losing access to the business line
mid-week would hurt.

Forja's own walkthrough with video: https://forjabots.com/docs/conexiones/whatsapp.html
— follow that for the exact field names, since it's the authoritative and
current source. (I could not open it from the sandbox to verify the specific
steps, so treat the five points above as the shape, not the click path.)

### Instagram — needs a workaround

Instagram DM automation goes through the **Meta Graph API / Instagram Messaging
API**, which requires:

- An Instagram **Business or Creator** account,
- linked to a **Facebook Page**,
- a Meta app with `instagram_manage_messages` permission,
- and Meta App Review before it works for people who aren't admins of the app.

Realistic options, best first:

1. **Ask Horizontes IA whether an Instagram connector is planned.** DM
   `@sanmunoz.ia` or email `contacto@innovandohorizontes.com`. Cheapest path if
   it's on the roadmap.
2. **Build a custom Instagram webhook** into your bot's worker. The bot is your
   code in your Cloudflare account, so this is possible — a Meta webhook
   endpoint that forwards DMs into the same brain the WhatsApp channel uses. It's
   real work, and it still needs the Meta App Review above.
3. **Use Instagram's native tools** for the simple cases — saved replies, story
   auto-replies, and an FAQ button — and put a "message us on WhatsApp" link in
   your bio so the AI bot handles the real conversations.

Given that most of your customers reach you by text anyway, getting WhatsApp
live first and treating Instagram as phase two is the pragmatic order.

## Business info to have ready

The wizard asks these one at a time. Worth deciding in advance:

- Business name: **Miami Auto Tinting**
- What you do: mobile window tinting — *we come to you, home or office*
- Services and pricing: which films and tiers you want the bot allowed to quote
- Hours, service area, phone
- Website / social links
- Payment methods
- Top 2–3 questions customers actually ask
- **Rules — what the bot must NOT do.** Important for you: it should not invent
  prices. Your quoting process is per-vehicle and you set the numbers, so the
  bot should collect year/make/model and hand off to you rather than commit to a
  figure.
- Tone: friendly and professional, English-first with Spanish when the customer
  writes in Spanish
- Brain: Claude / ChatGPT / Grok

Your existing `window-tint-estimator` skill already encodes the quoting rules and
tier template — reuse that wording for the bot's knowledge base so the two stay
consistent.
