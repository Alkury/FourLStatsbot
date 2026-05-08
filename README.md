# 4LDNS DNS Bot — commands and usage

This document describes the commands in `ton_domain_bot.py` and the main ways to use the bot for 4-digit `.ton` DNS domains.

## Quick start

- Open a chat with the bot and send `/start`.
- Check a domain: `/check 1234`
- Search free domains: `/find <pattern>`
- Random free domain by tier: `/random <tier>`

## All commands

- `/start` — command list and short help.
- `/status` — technical bot status (last lt, auctions, purchases today).
- `/stats` — overall 4N domain stats with tier and subcategory navigation.
- `/statschart` — overall stats chart (image + caption).
- `/auctions` — active auctions, bids, and time remaining.
- `/check XXXX` — check one 4-digit domain (example: `/check 0499`).
- `/summary` — interactive summary (periods and sections via buttons).
- `/random <tier>` — random free domain from the chosen tier.
- `/find <pattern>` — search free domains by mask or substring.
- `/top1k` — first-thousand stats (`0000–0999`) + recent sales.
- `/pulse1k` — 1K activity chart + short first-thousand summary.
- `/profile <TON-address|xxxx.ton>` — wallet/domain profile with tier distribution chart.
- `/owners` — unique 4N owner count + top 10 + distribution chart.
- `/top` — 4N holder leaderboard (buttons: Top 5/10/20).
- `/mute` — disable realtime notifications in the group (admins only).
- `/unmute` — enable realtime notifications in the group (admins only).
- `/set_topic` — bind notifications to the current topic/thread (admins only).
- `/unset_topic` — unbind notifications from the topic (admins only).

## Supported tiers for `/random`

Aliases (case-insensitive where applicable):

- `0`, `t0`, `tier0` → `Tier-0`
- `1`, `t1`, `tier1` → `Tier-1`
- `2`, `t2`, `tier2` → `Tier-2`
- `s`, `spec`, `special`, `спец`, `спецколлекция` → `Special`
- `r`, `reg`, `regular` → `Regular`

Examples:

- `/random 2`
- `/random spec`
- `/random regular`

## How to use `/find`

### 1) By tier

- `/find tier0`
- `/find tier1`
- `/find tier2`
- `/find spec`
- `/find regular`

### 2) By substring

- `/find 00` — domains containing `00`.
- `/find 88` — domains containing `88`.

### 3) By mask (4 characters)

Digits are fixed; letters are wildcard positions.

- `/find 19xx` — `19` plus two identical digits.
- `/find xxyy` — pairs (e.g. `1122`, `3344`).
- `/find xyxy` — alternation (e.g. `1212`, `9090`).
- `/find x00x` — shapes like `1001`, `2002`, etc.
- `/find 0xyz` — starts with `0`, then three flexible positions.
- `/find abcd` — “stair” with non-decreasing digits.
- `/find abbc` — another stair-style pattern.
- `/find 1abc` — starts with `1`, then stair-style template.

### 4) Formula stairs

- `/find f` — list all stair types and their codes.
- `/find f CS` — search by a specific code (example with `CS`).

## More flows

### Summary `/summary`

- Opens a menu with sections: Overview, Tiers, Auctions, Purchases.
- Periods via buttons: Today, 12h, 24h, 36h, 48h, Week.
- Charts are available from buttons inside the message where supported.

### Profile `/profile`

- Accepts a TON address (`EQ...` / `UQ...` / raw) or a domain like `7777.ton`.
- Returns a wallet card with domain distribution by tier and a chart.

Examples:

- `/profile UQA2U1fWqfWFKPJfQULI_-b96-b1hlSXXx34Gh5xT3U7GWf9`
- `/profile 7777.ton`

### Owners `/owners` and `/top`

- `/owners` — aggregated unique-owner stats + distribution chart.
- `/top` — 4N holder ranking with Top 5/10/20 buttons.

## Inline mode (via `@bot_username`)

You can use the bot without opening a private chat:

- `@your_bot 00`
- `@your_bot xxyy`
- `@your_bot abcd`
- `@your_bot 0499`

Inline behavior:

- If the query is exactly 4 digits, shows a card for that domain.
- If the query is a pattern/substring, shows a list of free domains.

## Good to know

- 4N domain format: exactly 4 digits (`0000` … `9999`).
- Commands with arguments need a space: `/check 1234`, `/find xxyy`.
- `/profile` requires an argument: `/profile <address|domain>`.
- Admin commands (`/mute`, `/unmute`, `/set_topic`, `/unset_topic`) only work in groups/supergroups and only for admins.
