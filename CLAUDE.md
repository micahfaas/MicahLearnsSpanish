# Instructions for Claude Code

This repo hosts Micah's Spanish flashcard app on GitHub Pages.

## When Micah says "add today's deck and push" (or similar)

1. **Find the new deck file.** Look in `decks/` for any `day-XX.json` file that is NOT yet listed in `decks/manifest.json`.
   - If multiple new files exist, add all of them.
   - If no new file exists, ask Micah where to find the JSON or whether he needs to paste it first.

2. **Validate the JSON.** Each deck file must be an array of card objects. Each card has either:
   - `type: "vocab"` with `spanish`, `english`, `pronunciation` (optional), `note` (optional), `category`
   - `type: "verb"` with `infinitive`, `meaning`, `tense`, `note` (optional), `forms: { yo, tu, el, nos, ellos }`

3. **Update `decks/manifest.json`** by appending an entry for each new deck:
   ```json
   { "id": "day-XX", "file": "day-XX.json", "date": "YYYY-MM-DD", "title": "Lesson topic" }
   ```
   - Use today's date for `date`
   - For `title`, summarize the lesson topic briefly (e.g., "Estar & Feelings", "Numbers 1-100")
   - Keep entries in chronological order

4. **Commit and push:**
   ```bash
   git add decks/
   git commit -m "Add day-XX: [topic]"
   git push
   ```

5. **Confirm** to Micah:
   - Which day(s) were added
   - How many cards in total
   - Reminder that GitHub Pages takes ~30-60 seconds to update, then a hard refresh (Cmd+Shift+R) will pull the new cards

## Card schema reference

### Vocab card
```json
{
  "type": "vocab",
  "spanish": "¿Cómo estás?",
  "english": "How are you?",
  "pronunciation": "KOH-moh ehs-TAHS",
  "note": "Informal — with peers, friends, family",
  "category": "greetings"
}
```

Valid categories: `greetings`, `courtesy`, `introductions`, `origins`, `food`, `hotel`, `transport`, `hiking`, `numbers`, `time`, `other`

### Verb card
```json
{
  "type": "verb",
  "infinitive": "ser",
  "meaning": "to be (permanent)",
  "tense": "present",
  "note": "Used for identity, origin, nationality",
  "forms": {
    "yo": "soy",
    "tu": "eres",
    "el": "es",
    "nos": "somos",
    "ellos": "son"
  }
}
```

Valid tenses: `present`, `preterite`, `imperfect`, `future`, `conditional`, `subjunctive`

## Common issues

- **Manifest order matters less than completeness** — the app loads all listed decks, but newer entries at the end are conventional.
- **Don't modify existing day-XX.json files** unless Micah explicitly asks. The app dedupes by Spanish text, but historical files should be stable.
- **Don't commit `.DS_Store`, editor temp files, or local dev artifacts** — keep the repo clean.
