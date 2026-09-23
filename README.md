# CHAPTER 31 — live preview

One self-contained page: the guest build of the invitation, everything inlined.
No build step, no dependencies, no assets to serve. Open `index.html` and it runs.

Only Google Fonts is fetched from the network; the stylesheet, the application
and the photograph are all in the file.

## Publishing it on GitHub Pages

Settings → Pages → Source: *Deploy from a branch* → `main` / `root`.
The page is then served at `https://<user>.github.io/<repo>/`.

## Guests

The link resolves the guest from a `?g=` parameter, and falls back to Saria
when there is none.

| link | guest |
|---|---|
| `/` | Saria |
| `/?g=m4d8v1` | Andrei |
| `/?g=q2r6t5` | Sofia |
| `/?g=Some%20Name` | that name, for older links that carried it directly |

A name is upper-cased and stripped to `A–Z0–9` to build the key on screen 14,
so a name written in a non-Latin script resolves to the literal `GUEST` there.

## What this is not

This is a **snapshot for review**, not the source. The application lives in
`invitation-chapter-31`; this page is built from it and is regenerated, never
edited by hand. Fixes belong in the source repository.

Two things behave differently from a real deployment:

- **The event record is empty.** Date, time, venue and dress code render as
  their preview tokens (`[DD]`, `[RESTAURANT]`, …). Filling in the record in
  the source repository is the whole of the deployment.
- **ADD TO CALENDAR does nothing** while that record is empty — the `.ics` is
  only built once a date, a time and a venue exist.
