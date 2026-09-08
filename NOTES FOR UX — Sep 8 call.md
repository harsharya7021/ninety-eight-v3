# Ninety-Eight website — notes from the Sep 8 call

Two lists. The first is what is already live in `index.html` (v3.28) so you can see it working before you design over it. The second is what was decided on the call and is waiting on design — the site can't be built further on those points until there is a screen to build from.

---

## Already implemented (v3.28)

**The menu is the curtain.** We agreed not to have two menus on the hero. The existing Menu (effect 035, the category rows) now drops down from the top edge instead of fading in, on solid carbon — not transparent, for the reason you gave: the film is sometimes bright, sometimes dark, and a transparent menu would be accented the wrong way half the time. While it is down, scrolling lifts it away again: the curtain rises with the wheel or the finger, fades as it goes, and the hero film shows through underneath, so "menu → scroll → back on the first screen" is one continuous gesture. Short gesture and it settles back down; past halfway and it lets go. Close still exists.

**The dots.** The header's Menu button is now three dots + "Menu". When the curtain is down, the same button carries over it (middle dot collapses, outer two meet) and reads "Close". One control, two states, same corner — the button carries forward, the text changes, as we said.

**Contact left the header.** It lives in the menu as the last row and on the postcard itself. Because the menu jumps rather than glides, the "Contact scrolls too far" problem is gone with it: the row lands exactly on the drum's settled screen (the postcard), not on the document's raw bottom.

**Menu rows now carry what the hero doesn't.** For the culture · The flywheel (35 cases — opens the flywheel directly) · In their words · On the record · In the building (98 Studio, beta — opens the film) · Contact. "Three verticals" came off the list because the hero already owns the verticals.

**98 Studio is off the hero.** The two verticals stand alone under "Two verticals of scale". The studio survives as one dim mono line in the bottom-right corner — "Something in the building · 98 Studio beta" — which opens the film, and as the menu row above. Subtle and discoverable, not competing.

**The two vertical words now go somewhere.** Before this they pointed at anchors that did not exist (clicks did nothing). Today: hover = the still image; click = jump to that vertical's own card (Talent & Branding → card 01, Marketing → card 02). When the dedicated pages exist (below) the hrefs just change.

**Video-on-hover hooks are wired.** Each word carries `data-video`: `assets/practice/talent.mp4` and `assets/practice/marketing.mp4`. The files don't exist yet — no rendered cuts in the Home page 98 folder, only AE templates — so the still image holds until someone drops the files in. Keep them like the hero film: H.264, muted, 8–15 s, ~1280 px wide, under ~6 MB each.

---

## Waiting on design

### 1. Dedicated pages for each vertical (the big one)
Decision: **Talent & Branding** and **Marketing** each get their own page, as content-heavy as the current landing. **98 Studio** stays a single beta page. Clicking a vertical on the hero opens its page (not a scroll). Marketing's page opens onto the flywheel; from there the visitor picks a room (Launch / Amplify / Convert / Retain / Events) and then a case.

What we need from you first: an **information architecture** — a sitemap and the content blocks per page. Harsh has more content to add than is on the site today, so ask him for a rough dump per vertical before you wireframe. The hero words are the entry points; keep the hero itself uncluttered (film + two words + menu is the non-negotiable set).

### 2. Case-study preview (the intermediate screen)
Decision: no direct jump into a full case. Between the click and the case file there is a **preview** — a short teaser of what the case is about, its reach and the headline numbers — so the visitor chooses to read rather than falling in. This preview also doubles as an **overview** on the main page: a section that shows what cases exist before anyone has to scroll through them next-next-next.

### 3. The flywheel folders need a redo
The Amplify / room folders (the tab drawer) look unfinished — visible clipping, the dossier not sitting properly on top of the folder. Rebuild the folder metaphor properly against the reference (the Ambrosia folders). This is a visual/interaction design task; the wiring behind it (rooms → cases → overlay) stays as is.

### 4. Case pages restructured, with the lead magnet at the end
Each room of the marketing flywheel becomes a mini-page in itself: process first (how the campaign was run), the **result** towards the end, then the case-study folders as the **footer**. The folders are a lead magnet: "Want the full case? Leave your email and we'll send it." — a CTA that captures leads. That email capture is the only thing standing between a reader and the PDF, so it needs a clean, single-field design. (The current "Send the brief" postcard uses Formspree — the same plumbing can take the case-study request.)

### 5. Section-to-section motion
Agreed direction, from the Amaterasu and Indigo references:
- A slight **blur between sections** so the page reads as one continuous flow, not stacked sections — "a whole page going down, not sections going down".
- **Text that emerges into focus** on entry and defocuses on exit (motion-blur feel). GSAP can do this; specify durations and easing in the handoff.
- **Depth on the cards** — a touch of neumorphic/isomorphic lift so cards read as cards, not stickers between two lines. Small, not much.
- The **cursor that tracks the section** (Amaterasu's navigation cue) as the "you are here" — cleaner than the old left-rail indicator. Nice-to-have, not blocking.

### 6. The culture strip (Gurls) — variety per scroll
Every scroll step feels like the same experience because the photographs are too alike. Reorder (or swap a few) so each beat of the strip looks different. Also make the centre text a size smaller — legible, but it doesn't need to be that big. Note from the last handoff: the set has three near-duplicate pairs that could be pruned to fourteen uniques.

### 7. Colour and contrast
One section was called "too bright on the eyes — I can't even read the text". Harsh didn't name it on the call; confirm which one with him and set its palette/typography so the text clears contrast. In the same pass, make the case overlay's colours work across every page's palette, not just the dark home.

### 8. Awwwards — Site of the Day is the target
The bar for all of the above: the site should be good enough to be nominated and win SOTD. Approach is "steal like an artist" — the cursor from Amaterasu, the folders from Ambrosia, the blur/focus from Indigo, plus things of our own. Look into how submissions work (there's a fee and a form; the design credits name the designer, which is yours). Harsh will share the F1 driver's site that won Site of the Year as a reference.

### 9. Later, not now
- Second-opinion review from a senior designer, and a survey to Harsh's designer list — **after** the MVP structure is in place, not before.
- Harsh is following up with the (MIA) kiosk client separately; the one note for that project from the call — don't colour only the middle card, it primes the click; make the three cards equal (blue, maybe at lower opacity) — belongs to that file, not this one.

---

*Backups: `Workshop (build files)/_backup_index_pre-curtain.html` is the file as it was before this pass.*
