# Knights & Knaves Solver

Logic puzzles solved by a computer doing propositional logic.

On a fictional island, every person is either a **knight** (always tells the truth) or a **knave** (always lies). Given what each person says, who is who?

> **A** says "We are the same kind."
> **B** says "We are of different kinds."

## How it works

- `logic.py` is a small propositional-logic engine. It has symbols and the connectives `And`, `Or`, `Not`, `Implication` and `Biconditional`, plus a **model-checking** algorithm. To decide whether a fact follows from the knowledge base, model checking tries every combination of true and false values.
- In `puzzle.py`, I translated each puzzle into logic. The main idea is a biconditional: *"A is a knight" is true exactly when what A says is true.*

```python
# A says "We are the same kind."
Biconditional(AKnight, Or(And(AKnight, BKnight), And(AKnave, BKnave)))
Biconditional(AKnave, And(Not(And(AKnight, BKnight)), Not(And(AKnave, BKnave))))
```

The solver then checks which characters must be knights and which must be knaves.

## Output

```
$ python puzzle.py
Puzzle 0
    A is a Knave
Puzzle 1
    A is a Knave
    B is a Knight
Puzzle 2
    A is a Knave
    B is a Knight
Puzzle 3
    A is a Knight
    B is a Knave
    C is a Knight
```

## Run it

No dependencies, just Python 3:

```bash
python puzzle.py
```

## Built with

Python (standard library only)
