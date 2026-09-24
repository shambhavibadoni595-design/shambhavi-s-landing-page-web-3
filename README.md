# The Shared Ledger — A Web3 Primer

A single-page, self-contained HTML explainer that teaches blockchain and Web3 basics through hands-on, click-and-see interactions instead of walls of text. The whole thing is themed like an old shared record book — parchment paper, wax-stamp reds, ledger typography — and every concept gets a little "bench" you can poke at instead of just reading a definition.

No build step, no dependencies, no backend. Open the file in a browser and it works.

---

## What it's for

This is built for someone who's heard the words "blockchain," "gas fee," "NFT," "DAO," or "smart contract" and wants an actual working mental model — not hype, not jargon. It walks a reader from "what is a block" all the way to "here's how to evaluate whether you need Web3 at all" in about 15–20 minutes, with interactive demos at every stop so the ideas land rather than just get read past.

## How to use it

1. Download/open `The_Shared_Ledger___A_Web3_Primer.html` in any modern browser (Chrome, Safari, Firefox, Edge).
2. Scroll, or use the top navigation bar to jump straight to a section.
3. Click things. Almost every diagram, card, and panel in this page is interactive — that's the point.
4. Your theme choice (day/night) is remembered locally between visits via `localStorage`. Nothing is sent anywhere; there's no server component at all.

You can also just drag the file into a browser tab, host it on any static file host (GitHub Pages, Netlify, S3), or open it via Claude's Artifact preview — it's plain HTML/CSS/JS with no external runtime dependencies beyond two Google Fonts.

## Reader's journey — section by section

| Section | What it teaches | The interactive bit |
|---|---|---|
| **Hero: a ledger everyone keeps together** | The core idea of a blockchain as a chain of sealed, fingerprinted pages | A live mini blockchain — add a block, tamper with block 2, and watch every later block break its seal |
| **What a blockchain actually is** | Hashing / fingerprinting | Type text into a box and watch its "hash" completely change with one letter |
| **Decentralization: who keeps the copy** | Single point of failure vs. distributed copies | Click a "one keeper" vs. "many keepers" diagram and see what happens when a keeper disappears |
| **Cryptocurrency: entries, not coins** | Crypto as ledger entries, not physical coins | — |
| **Smart contracts: rules that run themselves** | Self-executing code on-chain | — |
| **NFTs: unique entries in a fungible world** | Uniqueness/ownership records | A flippable "deed" card you can click to transfer |
| **DAOs: bylaws written as code** | Token-weighted, permissionless voting | A live vote panel where casting a vote moves the tally |
| **Map of the territory** | How all the concepts connect | A clickable concept map (nodes + connecting lines) tying blockchain → wallets → crypto → contracts → NFTs/DAOs/dApps together |
| **A short history of the shared ledger** | Where these ideas came from (1991 → present) | A scrubbable timeline rail with 7 milestone entries |
| **Web2 vs Web3, side by side** | The actual differences and the nuance/caveats | Two-column comparison with a "nuance" callout so it doesn't oversell Web3 |
| **Wallets, keys, and signing** | Seed phrases, public/private keys, signatures | Step-through explainer + a "sign a message" illustration |
| **Follow a transaction** | The full lifecycle of a transaction | A 7-step animated journey from wallet → mempool → sealed block, with a "Start" button and manual step controls |
| **Why a transaction sometimes costs money** | Gas fees | — |
| **dApps: applications with no landlord** | What makes an app "decentralized" | — |
| **Under the hood** | A peek at real code-level concepts | — |
| **Myth & reality** | Common misconceptions, corrected plainly | — |
| **Sign your own ledger entry** | Recap exercise tying it together | — |
| **You just learned** | Summary of everything covered | — |
| **Build your Web3 stack** | Practical "what do I actually need" next-steps | — |

There's also a persistent **Index (glossary)** — a searchable slide-out drawer (open it from the top bar or the hero) covering every term used in the piece, so a reader can jump to a definition without losing their place.

## Design notes

- **Visual language**: parchment background with subtle paper-grain texture, wax-stamp red and verified-green accents, serif/display typefaces (Playfair Display for headers, EB Garamond for body, Courier Prime for anything "code" or hash-like) — deliberately evokes a physical ledger book rather than a typical tech/crypto aesthetic.
- **Day/Night mode**: a full dark theme is built in (`themeToggle` button), respects system preference by default, and remembers the user's explicit choice.
- **Motion**: sections gently reveal on scroll; a progress ribbon at the very top of the page tracks how far through the primer you are (styled like a page-turn indicator, "❧" glyph included).
- **Accessibility**: semantic sections, `aria-live` regions on interactive readouts (block details, vote tally, transaction status), focus-visible outlines, reduced-motion-safe fallbacks, and a skip-friendly sticky nav.
- **Responsive**: single fluid column, safe-area insets handled for notched phones, horizontal nav scrolls on narrow viewports.

## Technical shape

- **One file.** All CSS and JavaScript are inlined — nothing to install, no `npm`, no bundler.
- **External dependencies**: only two Google Fonts loaded over HTTPS (Playfair Display, EB Garamond, Courier Prime). If you need a fully offline copy, swap these for system font stacks — the CSS already defines sane fallbacks (`Georgia`, `Times New Roman`, `ui-monospace`, etc.) so it'll still look reasonable without them.
- **Storage**: uses `localStorage` only, only for the day/night theme preference. Nothing else is persisted, nothing is sent to a server — there is no server.
- **The "hash" and "signing" demos are illustrative, not cryptographic.** The page says this outright (small note under the hash bench) — it's a teaching simplification, not real SHA-256 or actual key signing, and shouldn't be used as a reference implementation of either.

## Customizing it

Because it's one flat file, editing is straightforward:
- **Colors/theme**: everything runs off nine CSS custom properties at the top of the `<style>` block (`--ink`, `--paper`, `--rule`, `--verify`, `--stamp`, etc.) plus a dark-mode override block — change those nine values and the whole palette (including all the `color-mix()`-derived tints and shadows) updates.
- **Content**: each concept lives inside its own `<article class="entry" id="...">` or `<section class="band" id="...">` — you can reorder, trim, or extend sections independently since the nav, progress ribbon, and glossary all key off section `id`s.
- **Glossary terms**: defined in a JS data structure feeding the `#glossaryList` drawer — add an entry there and it becomes searchable automatically.

## Suggested next steps

- Want this hosted as a shareable link instead of a static file? I can publish it as an Artifact.
- Want a stripped-down / offline version with system fonts instead of Google Fonts? I can produce that variant.
- Want a PDF or slide-deck version of the same content for non-interactive contexts (print, classroom)? Happy to adapt it.

Just say the word on any of those.
