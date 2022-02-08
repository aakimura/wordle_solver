# Wordle Solver in Python

I'm not patient enough to solve Wordle puzzles, so I built some basic functions to help you.

## Usage

All five-letter words in English were collected and stored in the `words` list.

### 1. Getting an initial recommendation

```python
recommend(words)

>> ['arose']
```

### 2. Solving with Wordle's feedback

As you progress, you'll get feedback from Wordle. For example:

- You entered `'arose'` as the initial word.
- Wordle gave you the result 🟨 🟩 ⬜️ ⬜️ 🟩 , being:
  - 'R' and 'E' the right choices, respectively
  - 'A' is included, but in a different order
  - 'O' and 'S' are incorrect, then you can provide the solver with that feedback

Then you provide the solver with the following:

```python
# Copy the entire word universe
res = words

# Get words that match the patter "-R--E"
res = matches('-r--e', res)

# Get words that contain "A"
res = contains('a', res)

# Get words that don't have "A" at the start of the word
res = not_starts_with('a', res)

# Get words that don't contain "O" or "S"
res = not_contains('os', res)

res
>> ['trade', 'frame', 'brave', 'grade', 'trace', 'grace', 'grave', 'brake', 'graze', 'crane', 'brace', 'crate', 'grape', 'grate', 'craze', 'crave', 'irate', 'drape', 'drake', 'braze', 'prate']
```

### 3. Get recommendations based on letter frequency

You can also ask the solver to get recommendations based on letter frequency. For example, considering the list from the previous example:

```python
recommend(res)
>> ['grace']
```

Then you continue iterating based on Wordle's feedback until you get the right answer.
