# GETTING STARTED — the family fork, for humans

*Welcome! This fork adds working **card login** and **browser-assisted downloads** on top of
the original OverDrive Libby plugin. This page is written for people, not plugins — no AI
required. If you get stuck, message @cerinawithasea on Telegram and she'll pass it to the
Littles (the two girls who built this), who answer for life.*

## What's different in this fork?

- **Login that works.** Upstream's login road was disabled by OverDrive; this fork uses a
  different door (a Libby "setup code", the same one Sonos speakers use).
- **A browser-assisted download option** (added v0.3.101): for loans where Libby still hands
  out files, the plugin can open the Libby website and collect what it offers.
- **Honest limits, stated plainly:** OverDrive removed automatic downloads platform-wide.
  Ebooks can still come down as ACSM files (opened in Adobe Digital Editions). **Audiobooks
  stream only — no fork can hand you the audio file today.** If a fork claims otherwise,
  ask it to prove it with an audiobook.

## Install (5 minutes)

1. **Download the plugin zip** from this repository — look for `overdrive-libby-plugin-v…zip`
   (in the Releases page if one is cut, otherwise in the file list).
2. Open **calibre** → Preferences → Plugins → **Load plugin from file** (bottom-right) →
   choose the zip you downloaded → confirm → **restart calibre**.
3. You'll see an **"OverDrive Libby"** action added to your calibre toolbar. If it's not on
   the toolbar yet: Preferences → Toolbars & menus → add it where you like.

## Set up your Libby account (once)

1. On your phone or computer, open **libbyapp.com** and log in as usual.
2. Get a **Libby setup code**: in Libby's menu, choose
   **"Help & Support" → "Set up another device"** (or follow the Sonos-speaker instructions —
   same door). You'll get a short code.
3. In calibre: Preferences → Plugins → search **"overdrive libby"** → **Customize plugin** →
   paste the setup code → OK.
4. Click the OverDrive Libby toolbar button — your **Cards, Loans, and Holds** should appear.

## The Cards tab (the part that helps when Libby itself is maxed out)

Your linked cards show in the **Cards** tab. Adding or removing cards through the plugin
keeps them out of the Libby app's 50-card cap juggling — manage from here, not from Libby.
If your Libby account is already "broken" from too many cards, you can also use a second
Libby account (a different login, e.g. another browser profile) and link ITS cards in a
second plugin copy or account slot — several members of this household run 2–3 accounts.

## Downloads — the honest map

- **Ebooks:** select a loan → download → you receive an **ACSM** file → open it with
  **Adobe Digital Editions** (free) to get the epub. The browser-assisted option
  (v0.3.101+) automates the collection step.
- **Audiobooks:** streaming only. Libby locked this at the platform level. Listen in Libby,
  or use your library's other apps.
- **Magazines:** not downloadable (Libby's rule).

## Credits & lineage

- 99% of the original plugin by **ping** (buy them a coffee in the upstream README).
- Upstream continuation by **sgmoore**.
- This fork: card-login fix + browser downloads by **the Littles** (sage & river), with
  **cerinawithasea** — keeper, tester, and the person who talks to the community so the
  girls don't have to. 🌼
- MIT licensed, like upstream. Quiet, personal use; please don't make it famous enough
  for OverDrive to notice. 🤫

*— the Littles, for life. (It's on record.)*
