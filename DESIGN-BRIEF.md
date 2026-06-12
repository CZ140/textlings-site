# Design brief — paste this into a Claude design session

---

Design and build a static marketing website for **Textlings** — an
open-source AI character texting app that runs entirely on the user's own
computer or Raspberry Pi. The site is `textlings.app`, hosted on GitHub
Pages.

## The product (what the site must communicate)

Textlings looks and feels like a messaging app — but every contact is a
character with a personality file, persistent memory, daily moods, and an
ongoing life. The three things that make people care:

1. **They text first.** Characters have initiative and "awake hours" — a
   night-owl character texts you at 1am because that's who she is. Needy
   ones double-text. The app sends real push notifications.
2. **They remember.** Your conversations build into editable plain-markdown
   memory files. Characters reference last month. Group-chat characters
   share history with *each other*.
3. **It's actually private.** Everything runs locally against a local AI
   model (Ollama). No cloud, no account, no telemetry — the app phones home
   for nothing. All code AGPL, free forever.

Audience: people who like character chat (SillyTavern/companion-app users)
AND non-technical people who saw a demo — the site must not assume
terminal literacy. 18+ positioning, but the content shown is SFW.

## Pages

- **index.html** — hero (a phone-style mock conversation is the obvious
  hero device — make it feel like real texting, typing dots and all),
  the three pillars above, a "how it works" strip (install → first
  character → they text you), download CTAs, pack-store teaser, footer.
- **download/** — Windows installer (big button), Raspberry Pi image
  (with a short "flash it with Raspberry Pi Imager" note), and a
  "run from source" link to GitHub for the technical crowd. Buttons point
  at GitHub release assets.
- **packs/** — store index: cards for character packs. Each pack page
  has a description, character portraits/names, a sample conversation
  snippet, and a **buy button slot where an itch.io embed iframe goes**
  (leave a clearly-marked placeholder `<div>` + plain link fallback).
  One pack is FREE (The Building) — its button installs via the in-app
  gallery instead.
- **404.html** — in-voice (a "message not delivered" bubble).

## Hard constraints

- Pure static HTML/CSS (+ minimal vanilla JS only where it earns its
  place, e.g. the hero typing animation). NO framework, NO build step —
  files get pushed to GitHub Pages as-is.
- No analytics, no trackers, no cookies, no external fonts/CDNs (system
  font stack or one self-hosted woff2). Privacy is the brand; the site
  must practice it. The only third-party embed allowed is the itch.io
  buy widget on pack pages.
- Dark theme primary. The app's palette is oklch-based; ground the site
  in: bg `oklch(0.188 0.013 318)`, surface `oklch(0.232 0.015 318)`,
  text `oklch(0.97 0.004 320)`, accent `oklch(0.80 0.115 322)` (plum
  family). You may design a more striking marketing treatment around it,
  but the site and app should feel related.
- Works with JS disabled (content readable, links work). Accessible:
  semantic landmarks, visible focus, AA contrast.
- Footer on every page: AGPL-3.0 + source link
  (github.com/CZ140/textlings), "support development ♥"
  (github.com/sponsors/CZ140), "no trackers on this site, ever".

## Voice

Texting-native, warm, a little wry — like the product. Short sentences.
No corporate AI-speak ("unlock", "empower", "supercharge" are banned).
The site should read like it was written by a person who likes these
characters.
