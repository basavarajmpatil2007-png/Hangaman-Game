# Hangman Game

A Hangman game that comes in two versions: a web app and a Python console app.

## Features (Feature Set A)

| Feature | How it works |
|---|---|
| Random words | A word is chosen at random from a built-in bank. The web version won't repeat a word until all have been used. |
| Limited attempts | 6 wrong guesses are allowed per round. |
| Hints | Each word has a clue. Asking for a hint costs 1 attempt and can be used once per round (the web version lets you re-read it for free). |
| Score | +10 points per correct letter occurrence. A win adds a bonus of 20 + 5 per attempt left. |
| Replay | After each round you can play again. The score carries over; losing a round resets it in the web version. |

## Files

- `hangman.html` is the web version. It is a single self-contained file with HTML, CSS and JavaScript.
- `hangman.py` is the console version, written in Python 3.
- `README.md` is this file.

## How to run

**Web version:** open `hangman.html` in any modern browser. No install or server is needed. Use the on-screen keys or your keyboard.

**Python version:**

```bash
python hangman.py
```

Requires Python 3.6 or newer. It uses only the standard library (`random`).

## How to play

1. A word appears as blanks. Guess one letter at a time.
2. A correct letter is revealed everywhere it appears and scores points.
3. A wrong letter costs one attempt, and the web version draws another part of the hangman.
4. Stuck? Type `hint` (console) or press the Hint button (web) for a clue. It costs one attempt.
5. Reveal the whole word before you run out of attempts to win. Then choose to play again.

## Scoring example

Word: `guitar`. You guess 6 letters correctly with no repeats (+60), then win with 4 attempts left: bonus 20 + 4 x 5 = 40. Round total: 100.

## Customizing

- **Add words:** edit the `WORDS` list in `hangman.html`, or the `WORDS` dictionary in `hangman.py`. Each entry is a word plus a hint.
- **Change difficulty:** change `MAX` (web) or `MAX_ATTEMPTS` (Python) to give more or fewer attempts.
- **Change scoring:** edit `PTS` and `WIN` (web), or `POINTS_PER_LETTER` and `WIN_BONUS` (Python).

## Code structure (web version)

- `pick()` chooses the next random word without repeats.
- `start()` resets the state and builds the keyboard.
- `guess(letter)` handles a guess, updates the score and checks for a win or loss.
- `finish(won)` ends the round, applies the bonus and saves the best score.
- `draw()` redraws the word, attempt dots, hangman drawing and stats.

The best score is saved in the browser's `localStorage`.

## Known limitations

- Words are in English and lowercase letters only.
- The Python version does not save a high score between runs.
