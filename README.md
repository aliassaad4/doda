# Lebanon Trails — design

This repository holds the redesigned front end for Lebanon Trails. It is a
complete, running copy of the app, so you can see the design in context and
take what you need into the main project.

The design commit is **`dccdb34`** — everything below lives in that one commit.

## Run it

```bash
npm install
npm run dev
```

## What the design is built on

Lebanon's defining feature is vertical relief: the mountains climb from the
Mediterranean to 3,088 m at Qornet es Sawda in about 35 km, and the regions in
the data ladder from coast to summit to inland plain. So the interface borrows
the vocabulary of a topographic survey map — contour lines, spot labels, a
legend, ranged-left type — rather than generic cards and gradients.

### Colour

The burgundy and olive are unchanged from the original theme. Two colours were
added because something was missing, not to replace anything.

| Token | Value | Use |
| --- | --- | --- |
| `brand` | `#800020` | Burgundy. Headings, primary buttons. |
| `ember` | `#a8324a` | **Added.** Hover and accents on dark backgrounds, where `brand` is too dark to read. |
| `olive` | `#5a6332` | Navbar. |
| `olive-deep` | `#424a24` | **Added.** Raised surfaces in dark mode. |
| `limestone` | `#b9a87f` | **Added.** Secondary text and the contour lines. |
| `stone` / `paper` | `#e2d6bd` / `#f1e9d6` | Light page, text on dark. |
| `ink` / `earth` | `#2a1a14` / `#241c17` | Light-mode text, dark-mode page. |

### Type

- **Fraunces** — display only: page titles, trail names, section headings.
  A soft, low-contrast serif with optical sizing.
- **Archivo** — everything else, with tabular figures so distances, dates and
  spot counts line up in their columns.

Both load from Google Fonts at the top of `src/index.css`.

### Rules the design follows

- **Photographs are never covered by text.** Trail cards put the picture above
  a solid panel instead of printing the name over the image behind a gradient.
  A pale sky can't swallow the trail name.
- **One radius system.** Surfaces are nearly square (3px); only controls are
  fully round.
- **Structure carries meaning.** Contour lines, the map-style legend and the
  three-step difficulty meter encode something. Nothing is there as decoration.
- **Accessible by default.** Visible keyboard focus, `prefers-reduced-motion`
  respected, and both colour schemes defined.

## Files

New:

| File | What it does |
| --- | --- |
| `src/components/Contour.jsx` | The contour linework. Stretches to any width, draws in the current text colour. |
| `src/components/Difficulty.jsx` | Difficulty as a three-step meter. |
| `src/components/TrailCard.jsx` | One trail card, shared by the home page and the trail list. |

`src/index.css` holds the whole system: tokens, the type scale (`display-xl`,
`display-lg`, `display-md`, `label-map`, `prose-measure`) and the shared
component classes (`surface`, `btn`, `field`, `photo`, `bleed`).

Removed: `src/App.css` (184 lines of unused Vite template CSS, imported by
nothing) and two unused SVGs.

## Taking this into the main project

From a clone of the main repository, once:

```bash
git remote add design https://github.com/aliassaad4/doda.git
git fetch design
```

Then take the design commit onto a branch of your own:

```bash
git checkout -b redesign
git cherry-pick dccdb34
```

Both repositories share the same history up to `2bf687f`, so this applies
cleanly. Push the branch to your own repository and open a pull request there
as usual.

One thing worth knowing: the redesign touches 20 files, including `Home.jsx`,
`TrailList.jsx` and `index.css`. Those are the files most likely to be edited
day to day, so the sooner this is brought across, the fewer conflicts there
will be.

## About the data

Trail names, regions and photographs are real. Distances, difficulty ratings
and the group hikes are sample data.
