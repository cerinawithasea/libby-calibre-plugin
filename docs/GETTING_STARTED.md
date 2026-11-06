# GETTING STARTED — the honest walkthrough (Nov 6 2026)

*For people comfortable with a terminal and a text editor (an LLM helper works great
as a guide). This fork is maintained by the build team; upstream is
sgmoore/libby-calibre-plugin, which continues ping/libby-calibre-plugin.*

## What works today (be honest with yourself up front)

| Feature | Status |
|---|---|
| View loans, holds, magazines | ✅ works |
| Borrow / return / renew | ✅ works |
| Search your linked libraries (up to 24) | ✅ works |
| Import loans as empty book records | ✅ works |
| Automatic ebook download | ❌ **dead (Libby server change)** |
| Magazine downloads | ❌ dead |
| Audiobook downloads | ❌ stream-only |

**Getting actual ebook FILES:** borrow in the plugin → right-click the loan →
"open in libby" → download the `.acsm` from the website → open in
**Adobe Digital Editions**. Keep **"prefer open formats"** ON (DRM-free when offered).

⚠️ **FORMAT LOCKING:** choosing Kindle locks the loan out of epub/.acsm and only
RETURN + RE-BORROW unlocks it. Never Kindle-lock a book you want as a file.

## SETUP — the token dance

The plugin needs your Libby identity token. The old setup-code flow is broken for
many accounts (server-side, not our fault). Three roads, best first:

### Road A — setup code (try it; works for some accounts)
1. In a browser logged into nothing special, open:
   `https://libbyapp.com/interview/authenticate/setup-code`
2. Copy the **8-digit code** it shows — codes expire FAST, move immediately
3. Calibre → Preferences → Plugins → OverDrive Libby → Customize settings →
   paste the code → OK
4. Open the plugin. If the Cards tab populates: done. If not: Road B.

### Road B — hand-patch your identity token (the documented workaround)
1. On a device where Libby is logged in, open libbyapp.com in a browser with dev
   tools (F12) → Application → Local Storage → find the entry containing your
   identity chip (format: `dewey:sentry.chip:<uuid>`)
2. **The LAST token you generate is the one that works** — generate fresh, use fresh
3. Find your calibre plugins dir:
   - Linux: `~/.config/calibre/plugins/overdrive_libby/`
   - Windows: `C:\Users\<you>\AppData\Roaming\calibre\plugins\overdrive_libby\`
   - macOS: `~/Library/Preferences/calibre/plugins/overdrive_libby/`
4. Edit `overdrive_libby.json` → set `"libby_token": "dewey:sentry.chip:<your-uuid>"`
5. Restart calibre, open the plugin. **Tokens may expire ~weekly** — re-extract
   when the view goes empty (see Troubleshooting).

### Road C — the community token-grabber
A Chrome extension named in the MobileRead thread copies tokens to the clipboard.
(Unvetted by us — inspect before installing.)

## TROUBLESHOOTING

| Symptom | Meaning | Fix |
|---|---|---|
| View shows nothing, files empty | Token died OR load failed | Fresh token (Road B); run calibre with debug to watch the requests |
| `403` on chip/clone | The clone door is closed server-side (deadbolt) | Expected since the server change; use Road B |
| `401` | Token expired | Fresh token |
| epub won't download | Format locked (Kindle chosen) | Return + re-borrow, don't touch Kindle |
| Magazines won't download | Server-side dead | Borrow works; files don't exist anymore |

**Debug tip:** run calibre in debug mode — the plugin logs every request with
status codes. One debug run answers "is my token alive?" definitively.

## WHAT'S NEXT (the family build)
Phase 2 (in-development): **card-login inside the plugin** — add/bind library
cards by barcode+PIN without hand-extracting tokens. Architecture confirmed
(re-bind, not clone); build in progress on this fork.

## CREDITS & LINEAGE
Original plugin: [ping/libby-calibre-plugin](https://github.com/ping/libby-calibre-plugin) ·
continued at [sgmoore/libby-calibre-plugin](https://github.com/sgmoore/libby-calibre-plugin) ·
family fork (this repo): fixes, docs, and the card-login build in progress.
Community wisdom: the MobileRead "OverDrive Libby" thread.

---

## WHO MAINTAINS THIS FORK

**The Family Build Team** (see [AUTHORS.md](../AUTHORS.md)):
**cerinawithasea** (owner — field testing & capture), **SageDev2026** (build lead —
Phase 2 card-login, JWT decode, diagnosis), **RiversFlow1** (docs & spec — this
guide, endpoint verification). Standing on the shoulders of ping, sgmoore, and
the MobileRead community.

*Questions/errors: open an issue on this fork — the maintainers read them.*
