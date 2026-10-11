# ⚔️ Bot Arena

A small terminal tournament where bots fight each other in 1v1 battles until one champion is left.

The project is also a **Git practice exercise**: each participant adds their own fighter to the roster and opens a Pull Request. Because everyone edits the same spot in the same file, you will run into merge conflicts and have to resolve them.

## Requirements

- Python 3.6+ (uses f-strings)
- No external packages

## Running

```bash
python arena.py
```

## How it works

1. The roster in `ROSTER` is shuffled.
2. The first fighter becomes the current champion.
3. The champion fights each remaining fighter in turn. The winner of each match stays in the arena and faces the next challenger.
4. The last fighter standing is the **Absolute Tournament Champion**.

### Battle rules

- Fighters take turns attacking. The first fighter in the match always attacks first.
- Each attack deals random damage within the attacker's `attack` range (inclusive).
- The first fighter to drop to 0 HP or below loses, and the winner shouts their `phrase`.
- HP is reset for every match, so the champion starts each new fight at full HP.

If the roster has fewer than two fighters, the tournament doesn't start.

## Adding your fighter

Open `arena.py` and add a dictionary to `ROSTER` under the `# --- ADD HERE ---` comment:

```python
ROSTER = [
    {"name": "Python Sensei", "hp": 100, "attack": (5, 20), "phrase": "Where are your PRs?!"},
    {"name": "Cyborg Bob", "hp": 110, "attack": (5, 10), "phrase": "Beep boop!"},
    {"name": "Deadline Student", "hp": 80, "attack": (10, 40), "phrase": "It works on my machine!"},
    {"name": "Your Bot", "hp": 95, "attack": (8, 18), "phrase": "Merge me!"},
    # --- ADD HERE ---
]
```

| Field    | Type             | Description                                      |
|----------|------------------|--------------------------------------------------|
| `name`   | `str`            | Fighter's display name                           |
| `hp`     | `int`            | Starting health points                           |
| `attack` | `(int, int)`     | Min and max damage per hit (min must be ≤ max)   |
| `phrase` | `str`            | Victory shout                                    |

Keep the stats reasonably balanced with the existing fighters.

## Contribution workflow

1. Create a branch: `git checkout -b add-<your-bot-name>`
2. Add your fighter to `ROSTER`.
3. Run `python arena.py` to check it works.
4. Commit, push, and open a Pull Request.
5. If your PR has a conflict, pull the latest `main`, keep **both** your fighter and the others in the list, and push again.
