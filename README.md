# UCL Simulator

A single-file web app that simulates a full UEFA Champions League season — league phase, playoffs, and knockout rounds through to the final.

## How to Run

Open `index.html` in any modern browser. No build tools, no server, no install required. All dependencies are loaded via CDN.

Hosted app [here](https://winf-hsos.github.io/champions-league-simulator/).

## Features

### League Phase (8 Matchdays)
- **Generate Pairings** per matchday or all 8 at once
- Each team plays 8 matches (4 home, 4 away), never the same opponent twice
- **Lock** individual matches before regenerating — locked fixtures are preserved
- Enter scores manually or **simulate** with the dice button (per match or entire matchday)
- Standings table auto-updates on every score change

### Standings
- Full league table: Pos, P, W, D, L, GF, GA, GD, Pts
- Color-coded zones: green (1-8, direct R16), yellow (9-24, playoffs), red (25-36, eliminated)
- Tiebreakers: goal difference, goals for, alphabetical

### Knockout Phase (UEFA Bracket Format)
The knockout bracket follows the real UEFA Champions League tournament tree structure:

- **Playoffs**: Positional pairings from league standings (9/10 vs 23/24, 11/12 vs 21/22, 13/14 vs 19/20, 15/16 vs 17/18)
- **Round of 16**: Top-8 seeded into fixed bracket positions (1/2 faces winner of 15/16 vs 17/18, etc.)
- **Quarter-Finals, Semi-Finals, Final**: Matchups are **predetermined by bracket position** — no separate draw
- The bracket is split into two mirrored sides (A and B), ensuring the top two league finishers can only meet in the Final
- Two-legged ties with aggregate scores; single match for the Final

A single "Draw Bracket" button creates the entire bracket structure from the league standings.

### Teams
- 36 teams from the 2025/26 UCL season, organized in 4 pots
- Editable team names (click to edit) and star ratings (1-5, click stars)
- Star ratings influence simulated match results
- Search/filter

### Match Simulation
- Poisson-based goal generation using team star ratings
- Higher-rated teams have higher expected goals
- Home advantage factored in (+0.3 expected goals)

### Excel Export / Import
- Export the full tournament state to `.xlsx` at any time
- Import a previously exported file to restore the exact state
- Sheets: Teams, League Matches, Bracket (all rounds), State metadata
- Team stars can also be edited directly in the Excel file before re-importing

## Tech Stack

All loaded via CDN — no build step:

| Dependency | Purpose |
|---|---|
| [Tailwind CSS](https://tailwindcss.com/) | Styling |
| [SheetJS (xlsx)](https://sheetjs.com/) | Excel export/import |
| [Lucide Icons](https://lucide.dev/) | UI icons |
| [Google Fonts](https://fonts.google.com/) | Oswald (headings) + Source Sans 3 (body) |

## File Structure

```
index.html    — the entire application (HTML + CSS + JS)
SPECS.md      — original requirements (German)
README.md     — this file
```
