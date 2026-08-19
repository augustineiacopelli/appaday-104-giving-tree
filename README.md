# AppADay 104 &mdash; Giving Tree

**Live:** https://augustineiacopelli.github.io/appaday-104-giving-tree/

A giving tracker that starts from a percentage of household income rather than a dollar figure, keeps church giving and other charitable giving on separate goals, and shows progress as a tree that fills in: leaves for the church goal, ripening fruit for everything else. The name is a nod to a certain generous tree from a picture book. None of the book's text or artwork appears here; the drawing is original SVG.

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), one complete web app shipped every day.

## What it does

Enter expected household income, annual or monthly, then set two percentages. The defaults are 8 percent to the church and 2 percent to other charity, and everything else is derived from those numbers: dollar targets per year, per month, and per week, shown live as you type.

Log each gift with a date, recipient, category, and optional note. The recipient field learns from what you have already entered, so repeat parishes and charities autocomplete. Every gift feeds two things at once: the ring readouts, which give exact dollars and percent of goal, and the tree, which turns the same numbers into something you can read at a glance.

A pace line compares what you have given against what the calendar says you should have given by today, so being behind in October reads differently from being behind in February. A running share-of-income figure shows what you have actually given as a percentage, which is the number that matters at year end.

The Year and Month toggle reframes the same data as either an annual stewardship picture or a this-month check-in, with the goals scaled to match.

## Importing past giving

Three ways in. Upload a CSV, paste rows straight out of a spreadsheet, or restore a JSON backup made by the app.

The importer reads commas, tabs, semicolons, or pipes; handles quoted fields containing commas; strips dollar signs, thousands separators, and accounting parentheses; and accepts ISO dates, slash dates in either month-first or day-first order, and month-name dates like `Feb 2, 2026`. It guesses whether the first row is a header, guesses which column is which, and then shows you a mapping panel with a live tally and a preview of the first several gifts before anything is committed.

Category can be applied to the whole batch, read from a column, or inferred from the recipient name using words like parish, church, cathedral, diocese, and chapel, which sorts St. Mary Parish to church and Catholic Charities to other.

Duplicates are caught on date plus amount plus recipient, so re-importing an overlapping bank export adds nothing twice. Rows that cannot be read are counted and skipped rather than silently mangled. If the imported gifts fall outside the period you are viewing, the year selector jumps to where they landed.

## Getting data back out

Export the current period to CSV for tax time, with date, recipient, category, amount, and note. Back up everything to JSON, including your income and goal settings, and restore it on another device or after clearing your browser.

## Privacy

Everything stays in your browser. There is no account, no server, and no network call beyond the Google Fonts stylesheet. Data is held in `localStorage` under the key `appaday-104-giving-tree`, wrapped so the app still works for the session if storage is unavailable. Erasing all data from Setup removes it. Income figures and gift records never leave the device.

## Build notes

Single file, vanilla HTML, CSS, and JavaScript. No frameworks, no build step, no dependencies beyond a Google Fonts link.

The tree is hand-drawn SVG. Seventy leaf positions are generated once by a seeded pseudo-random rejection sample inside an ellipse with a minimum-distance check, then sorted bottom to top so the canopy fills upward as giving accumulates. Twelve fruit positions are fixed and sorted the same way, so leaves and fruit grow in the same direction rather than fighting each other. Progress maps to the count of lit elements, with CSS transitions handling the fill.

Fully ASCII source, `min-height: 100dvh` with flex and grid fill rather than fixed heights, and tested from a 375px viewport up.

## Categories

Spirituality. No Claude API.

---

Back to the archive: https://augustineiacopelli.github.io/appaday/
