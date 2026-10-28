# Agent Office — public preview

A visual review of the NetNavi office: the deck (who is on the floor) and the flow (how work actually moves).

- **Deck** — `index.html`: four operators, four NetNavis, Rangers per lane, Megazord on combination.
- **Flow** — `flow.html`: intake → charter check → lane → isolated work → evidence gate → approval gate → record → shipped.

## What is real and what is staged

Real: the shape of the system, the four lanes, the gates, the invariant mapping, and the flow logic — all of it traces to the private `agent-office` repo where `METHODOLOGY.md` v1.0 is enforced by `scripts/check_methodology.py` in CI.

Staged for review: the status lights. `office-state.json` is a synthetic snapshot so the deck has something to draw, and `feed.json` is a curated six-line slice of the log. The production deck reads live state and the full internal log; that data is not published here.

## Why a separate repo

The working repo holds the charter, meeting records, task briefs, and the engine-merge analysis. None of that belongs on a public URL. This repo carries only the two review pages plus their two data files.

## Run it locally

```
python3 -m http.server 8899
# then open http://127.0.0.1:8899/index.html
```

The deck fetches `office-state.json` and `feed.json`, so it needs to be served over HTTP rather than opened as a file.
