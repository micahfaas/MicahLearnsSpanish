# Micah Learns Spanish

A personal Spanish flashcard app for a 14-day trip to South America (Buenos Aires → El Chaltén → Lima).

**Live app:** https://micahfaas.github.io/MicahLearnsSpanish/

## How it works

- Daily Spanish lessons happen in Claude Chat
- Each lesson produces a JSON deck file (e.g., `decks/day-03.json`)
- The deck is added to `decks/manifest.json`
- Claude Code (or `git push` manually) deploys to GitHub Pages
- The web app fetches the manifest on load and pulls in any new decks

## Repo structure

```
.
├── index.html              # The flashcard app
├── decks/
│   ├── manifest.json       # Lists all daily decks
│   ├── day-01.json
│   ├── day-02.json
│   └── ...
├── CLAUDE.md               # Instructions for Claude Code
└── README.md
```

## Daily workflow

1. Do the daily lesson in Claude Chat
2. Copy the JSON snippet at the end into a new file: `decks/day-XX.json`
3. Tell Claude Code: *"add today's deck and push"*
4. Refresh the live app — new cards are there

See `CLAUDE.md` for full Claude Code instructions.
