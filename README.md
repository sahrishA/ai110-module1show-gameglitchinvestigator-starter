# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
   - The secret shouldn't change on each submit—Streamlit's st.session_state persists variables across reruns.
   - secret = st.session_state.secrets  # ❌ 'secrets' (plural) doesn't exist. It should be secret = st.session_state.secret
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

### Game Purpose
This game lets you guess a number and discover the unusual behavior that occurs when you input any guessed number. It serves as a hands-on debugging exercise to understand Streamlit's session state management and common logic errors.

### 🐛 Bugs Found

| Bug # | Issue | Location | Fix |
|-------|-------|----------|-----|
| 1 | Reversed hint logic in try block | `check_guess()` function | Swapped "Go HIGHER/LOWER" messages: if `guess > secret` → "Go LOWER!", else → "Go HIGHER!" |
| 2 | Reversed hint logic in except block | `check_guess()` TypeError handler | Swapped error handling messages to match try block logic |
| 3 | Score not resetting on new game | `app.py` new game logic | Added `st.session_state.score = 0` when "New Game" button is clicked |
| 4 | Secret number changes each submit | Session state initialization | Removed `str()` wrapper and fixed typo: changed `st.session_state.secrets` (incorrect) to `st.session_state.secret` (correct). Type must remain `int` throughout |
| 5 | Game history not clearing | New game reset logic | Added `st.session_state.history = []` to clear guesses when starting a new game |

### ✅ Fixes Applied

**Bug 1 & 2: Reversed Hint Logic**
- Updated the `check_guess()` function in `logic_utils.py`:
  ```python
  try:
      if guess > secret:
          return "Too High", "📉 Go LOWER!"
      else:
          return "Too Low", "📈 Go HIGHER!"
  except TypeError:
      if guess > secret:
          return "Too High", "📉 Go LOWER!"
      else:
          return "Too Low", "📈 Go HIGHER!"
  ```

**Bug 3: Score Not Resetting**
- Added score reset in the new game handler:
  ```python
  st.session_state.score = 0
  ```

**Bug 4: Secret Number Type Consistency**
- Fixed the session state initialization:
  ```python
  # ❌ Before (caused string conversion):
  secret = st.session_state.secrets
  
  # ✅ After (maintains int type):
  secret = st.session_state.secret
  ```
  - Removed unnecessary `str()` wrapper that was causing type inconsistency
  - This fix resolved the issue where the secret number appeared to change on even-numbered attempts

**Bug 5: History Not Clearing**
- Added history reset in new game logic:
  ```python
  if newgame:
      st.session_state.history = []
  ```

## ✅ Testing

Run the test suite to verify all fixes:

```bash
pytest
```

**Manual testing checklist:**
- [ ] Secret number stays the same across multiple guesses
- [ ] Hints are correct ("Go HIGHER" when guess is too low, "Go LOWER" when too high)
- [ ] Can successfully win the game
- [ ] "New Game" button resets score to 0
- [ ] "New Game" button clears the guess history
- [ ] All pytest tests pass

## 💡 Key Learnings

- **Streamlit Session State**: `st.session_state` persists variables across reruns caused by button clicks and other interactions
- **Type Consistency Matters**: Converting numbers to strings can break comparisons and logic. Keep data types consistent throughout the application
- **Test-Driven Debugging**: Writing and running tests helps catch logic errors early and ensures fixes work correctly
- **Stateful Applications**: Managing state in interactive apps requires careful initialization and reset logic, especially when games have "new" or "reset" features

## 📸 Demo

- [x] Fixed, winning game screenshot:
  ![Game Screenshot](https://github.com/user-attachments/assets/b377d9f3-c95c-461d-a54c-8ddd4e7b74f9)

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
