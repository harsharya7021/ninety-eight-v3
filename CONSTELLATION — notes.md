# Constellation — prototype notes

**File:** `constellation.html` · self-contained, 232 KB, no build step, no server. Double-click it.

All 26 hospitality cases sit in a bounded field with the camera outside it. Nothing is behind you, nothing flies past. Drag to orbit, scroll to zoom, click a plate to open the case.

## Why it changed

v1 was a cipher.tv flythrough. That model works for a studio with a dozen films where the mood *is* the product — it fails for a book of 26 where a prospect needs to find the room that looks like theirs. You couldn't see the set, couldn't hold two cases in view, and discovery was accidental. The tunnel is gone.

## Four arrangements

Same 26 plates, four spatial sorts. They animate between positions; keys `1`–`4` also switch.

| | |
|---|---|
| **Clusters** | Six category groups — fine dining, cafés & all-day, bars & nightlife, Indian, groups, destination. Default. |
| **Network** | Force-directed on the shared-creator graph. Tightly linked rooms pull together; the six isolates drift to the rim. |
| **Scale** | A rising helix ordered by creators activated — Bayroute's single voice at the bottom, Sky Lantern's 22 at the top. |
| **Grid** | Flat, front-on, everything legible at once. Camera locks to face-on and stops drifting. |

## The creator graph

35 links across the book; 20 of 26 cases connect to something. Harteerath Singh alone bridges Farzi, TBSP, Hard Rock, Poetry and Khubani.

Hover any plate and its links light up — in every arrangement, not just Network. The panel lists **Shared voices with**, and those are clickable, so you can walk the roster sideways through the book.

Isolated cases: Bayroute, RIZQ, Monet, Limitless, Flaunt, Punjab Grill.

**One data note.** `@98.entertainment` was tagged in five case rosters — your own handle, not a creator. It was manufacturing five false links (Weekend↔Farzi, Weekend↔Flaunt, Farzi↔Flaunt, Sky Lantern↔Flaunt and more). Excluded from the graph. Worth cleaning at source; it'll skew any roster analysis you run off `casedata`.

## Category filter

The left-hand legend is the standing index. Hover to preview, **click to lock**. A locked category takes the other plates out of play entirely — they stay dim and stop responding to the cursor, so the filter can't be undone by an accidental hover. Click again to clear.

## Where the content comes from

Nothing invented. All of it is pulled from `index.html`:

- **Case copy** — the `#casedata` JSON block (name, kicker, sub, stats, pull-quote, roster).
- **Codes and metrics** — the `.arch-row` archive table.
- **Plates** — `assets/covers/*.jpg`, re-cut to 16:10 and inlined as base64 so the file works from `file://`. Chrome won't upload `file://` images into WebGL, which is why they're embedded rather than linked.

Your covers turned out to be flat brand logo plates, not photographs. Dropped into black at full saturation they read as confetti, so the shader holds every plate at ~15% saturation until you hover it, then the brand colour snaps to full. It doubles as the focus mechanic.

17 cases have cover art. The other 9 (Rooh, Khubani, Daryaganj, Punjab Grill, Tickled Pink, Slique, Local, Nao, YYC) get a typographic plate generated at runtime — add a JPG to `assets/covers/` and set the case's `cover` field to replace it.

**"Open the full case ↗"** links to the pages in `Workshop (build files)/`. 24 of 26 resolve; Limitless and Tickled Pink have no built page yet.

## Verified

Stubbed Three.js harness, no GPU involved:

- All 26 plates land inside the frustum in all four arrangements, at aspect ratios from 0.90 (portrait) to 2.06 (ultrawide). Camera distance is computed from the layout's actual extents, not hardcoded.
- Morph settles to zero drift; no NaN transforms or line colours.
- Nothing highlights before the first pointer move; hover lights exactly the linked cases; locked filter survives hovering.
- Panel opens, cross-links resolve, closes clean.

Caught three real bugs along the way: hover state overriding the locked filter, idle rotation skewing Grid off front-on, and the false agency-handle links above. Not yet run on a real GPU — first open is the test.

## Tuning

Top of the script block:

```
PW      2.45   plate width; height follows 16:10
MODES          arrangement names, in switcher order
```

Layout coordinates are precomputed per case in the `L` field — `[clusters, network, scale, grid]`. Regenerate them rather than hand-editing; the spacing pass guarantees a 2.75-unit minimum separation so plates don't collide from any angle.

## If it goes into the live site

Strip the chrome (`#logo`, `#nav`, `#addr`, `#contact`), mount the canvas in a section, and point `openCase()` at the site's existing case overlay instead of the local panel. Served over HTTP the base64 block goes away and plain `assets/covers/` paths work.

The other 26 F&B clients with cover art but no written case (Adda, Baoji, Baris, Boccon Cheeni, Butter Room, Gastronomica, Thai Mama, Sky House, Spice Station, Rang Punjab…) are a data change, not a code change — but they'd be plates that open nothing, so decide what a click should do first.
