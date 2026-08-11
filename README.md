# Eliviz

Turn almost any data file into a single, self-contained, award-caliber
interactive HTML page — with a switchable design identity.

## Components

**Skill — `eliviz`.** Parses CSV/TSV, Excel (per-sheet tabs), SQLite
(per-table tabs), JSON/JSONL (record arrays get a full tabular dashboard;
nested JSON gets a tree explorer), Markdown, plain text, and log files into one
normalized model, then builds a single HTML file: animated hero, stat counters,
SVG charts, column-profiled sortable tables, an outline-navigated reading view,
and a level-filterable log viewer. Deterministic parsing lives in bundled
Python scripts; output is verified headless before delivery.

**Design bank.** Five complete visual identities in
`skills/eliviz/assets/designs/` — `aurora` (dark glass, default),
`editorial` (warm paper serif), `brutalist` (borders + offset shadows),
`terminal` (phosphor CRT), `neon` (cyberpunk glow). The skill auto-picks per
dataset type and request wording; `--design <id>` sets one explicitly.

**Agent — `design-adapter`.** Spawned when a request needs a design the bank
doesn't hold verbatim: brand colors, a new mood, or a blend of styles. It
authors a custom design pack (json + css), rebuilds the page, and
screenshot-verifies legibility and contrast before returning it.

## Installation

In Claude Code:

```shell
/plugin marketplace add costiash/eliviz
/plugin install eliviz@eliviz
```

## Usage

Say things like:

- "Visualize this CSV" — builds with the auto-picked design
- "Make a viewer for these logs" — terminal style, auto-picked
- "Turn this report into a page for the board" — editorial style
- "Visualize this in our brand colors: #0a2540 and gold" — design-adapter crafts a custom pack
- "I want the editorial layout but dark" — design-adapter blends packs

## Setup

No configuration required. Excel input needs `openpyxl` in the sandbox
(`pip install openpyxl --break-system-packages`); everything else is stdlib.
Output files are fully offline-capable (all JS libraries inlined); pass `--cdn`
for smaller files that load libraries from CDNs instead.
