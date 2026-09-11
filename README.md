# The Rotation Rulebook

Drinking game specifications for the rotation. Controlled, revised, binding at
the table.

**Live site:** https://YOUR-USERNAME.github.io/rulebook/

*(Replace that with your real URL once Pages is live, and paste it into the
**About** panel on the right of the repo page too — GitHub doesn't show the Pages
link anywhere obvious otherwise.)*

---

## One file

Everything is in `index.html` — the games, the design, the code. No build step,
no dependencies, nothing to install. Double-click it and it works offline.

## Changing a rule

1. Click **`index.html`** above.
2. Click the **pencil icon** (top right of the file view).
3. Scroll to the top. Everything you edit is between these two banners:

   ```
   ▼▼▼  EVERYTHING YOU EDIT IS IN THIS BLOCK  ▼▼▼
   ▲▲▲  STOP EDITING HERE  ▲▲▲
   ```

   Below the second banner is design and plumbing. Leave it alone.
4. **Commit changes** at the bottom.
5. Wait about a minute, reload the site.

Works from a phone browser.

## The shape of a game

```js
{
  slug: "beer-pong",                 // unique id, used for the #link
  name: "Beer Pong",
  code: "TBL-01",
  cat:  "table",                     // must match a key in CATEGORIES
  tag:  "Table & throwing",
  spec: { Players: "2v2", Gear: "…", Runtime: "…", Tempo: "…" },
  note: "Optional blue callout at the top of the sheet.",
  setup: [ "First step.", "Second step." ],
  play:  [ "First step.", "Second step." ],
  sections: [ { title: "Extra section", steps: [ "…", "…" ] } ],
  drink: [ "Goes in the red panel on the right." ],
  varies: "One sentence on what changes table to table."
},
```

Only `slug`, `name`, `code`, `cat` and `tag` are required. Leave out whatever you
don't need.

**Multi-phase games** use `phases` instead of `setup`/`play`:

```js
phases: [
  { title: "Phase 1 — The deal", steps: [ "…" ] },
  { title: "Phase 2 — The pyramid", steps: [ "…" ] }
],
```

**Card tables** (Kings Cup) use `cards`:

```js
cards: [
  ["A", "Waterfall — everyone drinks…"],
  ["2", "You — hand out two drinks."]
],
```

## Adding a game

Copy an existing block, paste it inside `GAMES = [ … ]`, change the fields. Put a
comma between blocks. Give it a `slug` nothing else uses.

Sheet codes are `CAT-NN` — pick the next free number in that category.

## Adding a category

Add a line to `CATEGORIES` near the top, then use that `key` as a game's `cat`.
The filter button appears on its own. Categories with no games don't show up.

Cross-references between sheets are written as codes ("see GMB-02"), so if you
move a game to a different category, search for its old code and fix whatever
cites it.

## Bumping the revision

`META` at the top sets the stamp in the title block. Change it when you change
something, so you can tell at a glance whether the version you're looking at is
current.

---

## If the page goes blank

You have a typo. Almost always one of three things:

- a **missing comma** between two games, or a stray one after the last
- a **curly quote** — `"` instead of `"`. Pasting from Notes, Word or iMessage
  does this silently. Type quotes directly in the GitHub editor.
- a **`"` inside your text** that isn't escaped. Use `'` instead, or write `\"`.

To see exactly where: open the site, press **F12**, click the **Console** tab. It
names the line.

To undo: click `index.html`, click **History** at the top, find the last version
that worked, and revert to it. Nothing is ever really lost.

---

## Notes

- The repo is public, which free GitHub Pages requires — and the site is public
  regardless. Don't put anything in it you wouldn't want a stranger reading.
- Turn on two-factor auth for your GitHub account. That's the whole security
  checklist for a static site.
- Fonts load from Google Fonts. If you're ever offline the page still works, it
  just falls back to system fonts.
