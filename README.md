# The World in One Day — Monday 23 November 2026

make.fun bounty entry: **"Sum up 23 November's world news in one image"**
for @konservasi-lingkungan. **Not submitted yet** — see "Submission
blockers" below.

## The image

`entry.png` (preview copy in this repo; the program writes
`/output/entry.png`) is a dense one-page newspaper front page for
Monday 23 November 2026:

- **Masthead** — "THE WORLD IN ONE DAY" over the big date
  "MONDAY 23 NOVEMBER 2026", with "32 STORIES - 7 REGIONS - COP31
  FAILS - MISSILES OVER POLAND - GULF WAR WIDENS" naming the count
  and the 3 leads.
- **Numbers strip** — 3 missiles over Poland, 3.7% US stocks fall,
  258 Democrat House seats, 128 states backing robot rules.
- **Region strip** — gold bar naming all 7 regions with story
  counts: Europe 8, Middle East 2, Americas 7, Asia-Pacific 7,
  Africa 3, Oceania 1, World 4.
- **3 lead stories** — COP31 collapses (Antalya), missiles over Poland
  (NATO meets in Brussels), Gulf war widens (Houthis hit Rabigh
  refinery, tankers struck near Hormuz).
- **"Where it happened"** — schematic world map with red dots for
  Poland, Antalya, Bahrain, Libya, Delhi, Seoul, Sinaloa.
- **"The day in brief"** — 16 more stories in a two-column grid across
  all 7 regions: markets, Nepal–India talks, the Libya warship, the
  US House, the Indonesia factory fire, Chapo Isidro's capture, the
  South Korea minister quitting, California suing OpenAI, AI limits,
  killer-robot rules, the Kyiv strikes, MotoGP, the NFL, the KPMG
  Canada hack, Iran, South Sudan.
- **"Also on Monday 23 November"** — 13 one-line stories, from
  Australia's PM on COP31 to the Riemann proof claim and the
  Shenzhen summit.
- **Footer** — "DATE CHECK: ALL STORIES IN 23 NOV 2026 REPORTS — SOME
  EVENTS SUN 22 NOV" plus the source list, fully inside the image
  with a margin.

32 stories in total. Every story is verified from reports dated
23 November 2026; see [SOURCES.md](SOURCES.md) for each story's source
and URL, including the region mapping. No story is taken from the
22 November entries.

## Why this design

The 23 November bounty was still blind when this was built, so no top 5
had been published. The pattern comes from the provisional leaders of
the 22 November bounty (all 12-0-0, judge win rate ~99.1–99.2%, final
heat re-judged — a style pattern only, not a guarantee):
@jolly-stork-27 "atlas22b" (36 stories, 7 regions), @evolution0795
(24 stories, 7 regions), @gime22 (35 stories, 7 regions),
@thepowerofmuse (36 stories, 7 regions), @myhanni (39 stories,
7 regions). What they share, and what this entry adopts:

1. **A newspaper front page, not one big illustration** — dense,
   organised, scannable.
2. **The date is the biggest thing on the page**, with a story/region
   count in the masthead (breadth is judge criterion 2).
3. **Three named lead stories** — the day's most consequential news,
   named in the image itself.
4. **A numbers strip and a map** — facts and geography at a glance.
5. **An "ALSO ON …" list** — breadth without crowding the leads.
6. **A DATE CHECK footer** — the image vouches for its own date.

What was deliberately *not* copied: no image, text or story selection
from those entries, and no inflated story count — the masthead
says the verified count (24 at first, 32 after the judge-optimisation
pass added 8 more verified stories), not 36.

## How to run

Python 3.13, standard library only — no network, no dependencies,
no randomness, no timestamps.

```sh
python3 main.py            # writes /output/entry.png (falls back to ./output/entry.png)
python3 main.py out.png    # writes to the given path instead
```

`main.py` draws the whole image in code: a pure-stdlib PNG encoder
(`zlib`/`struct`), a hand-written 5×7 bitmap font, and simple
shapes/icons. It runs twice with byte-identical output.

## Redesign (23 Nov 2026, ~12:42 WIB) — colour and readability

The user said the first version looked washed out and hard to read.
Content is unchanged — same 24 stories, facts and sources
(`SOURCES.md` untouched). Only the visual design changed in `main.py`:

- **Bolder font:** the 5×7 bitmap font is now drawn bold (each glyph
  thickened by 1 px right and down) for masthead, date, numbers strip,
  lead headlines, section headings and footer.
- **High-contrast colour system:** dark navy header (#0B2A4A) with a
  bright yellow masthead and white date; saturated red numbers strip
  with white bold text; white page background.
- **Lead cards each have their own saturated identity:** CLIMATE =
  deep green header/tag on a light green tint, SECURITY = deep red on
  a light red tint, GULF = deep orange on a light orange tint. Tag is
  white bold text on the coloured bar, icon sits on a white disc,
  headlines are dark navy/black bold, captions are near-black
  (never pale grey on light blue).
- **"MISSILES OVER POLAND"** is now set on two clean lines
  ("MISSILES OVER" / "POLAND") with room above the divider.
- **"The day in brief":** alternating white and very light yellow
  rows, 8 px colour bars, bold dark headlines, dark-grey captions.
  Section headings are now coloured bars (navy for "THE DAY IN
  BRIEF", red for "ALSO ON MONDAY 23 NOVEMBER") with white bold text.
- **Map:** pale mint background, mid blue-green continents (Asia in
  a deeper blue), red dots with a white ring, and a short dark label
  on a white backing next to every dot: POLAND, ANTALYA, BAHRAIN,
  LIBYA, DELHI, SEOUL, SINALOA. Labels were re-spaced after a first
  pass in which POLAND/ANTALYA/BAHRAIN overlapped, and the last
  "ALSO" item was moved clear of the footer.

## Judge optimisation (23 Nov 2026, ~12:48 WIB) — design like the winners

The user asked for the design to match the leaderboard winners and to
win over the AI judge (z-ai/glm-5.3-flash, pairwise, criteria in order:
(1) one day's news and names that day, (2) selection and breadth,
(3) reads on its own, (4) faithful, (5) craft; the judge has no news
feed and is not told the day). Changes in `main.py`, content verified
from 23 Nov 2026 reports only:

- **Breadth 24 → 32 stories.** 8 new verified stories added (see
  SOURCES.md 25–32): Indonesia factory fire, South Korea minister
  quits, Kyiv strikes kill at least 6, KPMG Canada hacked (briefs);
  South Korea exports top $1 trillion, Riemann proof claim, Shenzhen
  summit, France questions Ukraine aid (also list). Nothing invented,
  nothing copied from the 22 Nov entries.
- **7 regions now explicit.** A gold region strip under the numbers
  strip names every region with its story count: Europe 8, Middle
  East 2, Americas 7, Asia-Pacific 7, Africa 3, Oceania 1, World 4
  (mapping in SOURCES.md). The masthead already said 6 regions; the
  7th (World: AI limits, robot rules, Riemann, Shenzhen) was always
  there but unnamed.
- **Criterion 1 strengthened.** The masthead's third line now reads
  "32 STORIES - 7 REGIONS - COP31 FAILS - MISSILES OVER POLAND -
  GULF WAR WIDENS", so the date and the 3 leads are named in one
  line; the DATE CHECK footer is unchanged.
- **Reads on its own.** Brief rows widened to 34 px so headlines and
  captions no longer touch; lead captions shortened to fit 4 lines
  (the COP31 caption had lost its last word, "WORDING.", in the
  previous render — now rewritten to fit whole); "ALSO" items got
  coloured square bullets so each story is visually separate.
- **Footer fixed.** DATE CHECK and SOURCES lines now end 8 px above
  the bottom edge instead of sitting on it; the region strip, which
  overflowed and clipped at both edges in the first optimisation
  render, now fits whole.
- Colour system, bold font, labelled map and newspaper structure
  from the redesign are unchanged.

## Verification (23 Nov 2026, ~12:48 WIB)

- Two runs: identical SHA256
  `6cae25e786833ed0460331de2e62d1bd65ffa557417b1c0f42af0bd4594381a2`
- Size: 36,819 bytes (limit 1,048,576)
- Dimensions: 1024×1024 (limit 1024×1024)
- Visual check (full image plus 2× crops of the map and footer):
  masthead, date, numbers strip, region strip, all 3 leads, map with
  all 7 labels, all 16 briefs, all 13 "also" items and footer are
  legible, with no overlap, truncation or garbled text.

## Verification (23 Nov 2026, ~12:42 WIB)

- Two runs: identical SHA256
  `04430e756a65a6ffe83ff5a5fce081344ed1f9187aa1d6b047c277d42316354c`
- Size: 32,410 bytes (limit 1,048,576)
- Dimensions: 1024×1024 (limit 1024×1024)
- Visual check (full image plus 2× crops of the map and footer):
  masthead, date, numbers strip, all 3 leads, map with all 7 labels,
  all 12 briefs, all 9 "also" items and footer are legible, with no
  overlap or garbled text. The SOURCES footer line sits exactly on
  the bottom edge but is fully readable in the crop.

## Submission blockers (not done — later step)

- A public GitHub repo owned by the entrant, with this code committed.
- A Solana wallet linked to the make.fun account (none linked yet).
- Transcripts of the AI coding-agent sessions that built the entry.
- Submission itself on make.fun before the deadlines: Round 1 closes
  Mon 23 Nov 2026, 7:00 PM WIB; final deadline Wed 25 Nov 2026,
  7:00 AM WIB.

## License

MIT — see [LICENSE](LICENSE).
