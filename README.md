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
4. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
5. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!
   # Bug fixed
   - copilot Suggested following:
     1. Configured python environment
     2. Also suggested to setup virtual environment for testing
     3. Reviewed requirements.txt and checked pytst installation
     4. UPdate logic_util by updating get_range_for_difficulty, parse_guess, chech_guess, update_score
     5. Updated test_game_logic.py by imported (get_range_for_difficulty, parse_guess, chech_guess, update_score,) from logic_utils import



## 📝 Document Your Experience

- [x] Describe the game's purpose.
      This game let you gues a number and find the un-usual behavior that we experience when we input any guessed number.
- [x] Detail which bugs you found.
      # Bug1
      - There was bug in bug in the if else statement of try section where we need to fix the comment from Go HIGHER! to Go LOWER for the condition if guess is higher than secret. AND VICE VERSA if guess is lower than secret to updat the comment to HIGHER!
      #Bug2
      - There was bug in the except section of TypeError where we need to fix the comment from Go HIGHER! to Go LOWER for the condition if guess is higher than secret.
         AND VICE VERSA if guess is lower than secret to updat the comment to HIGHER!
      #Bug3
      - There was bug that it wasn't updating the value of the score to zero whenever we start the new game.
      Bug4
      - str is  bug that casue glitch. str in secret =str( st.session_state.secrets) code is a bug because on every even‑numbered attempt the secret is converted to a    string,  so when check_guess compares the integer guess to a string secret it triggers the TypeError‑handling code. I also notice that the new game button wasn't working properly due to this error
            
   
- [x] Explain what fixes you applied.
           - To fix the bug in the if else statement of try section I update the comment from Go HIGHER! to Go LOWER AND VICE VERSA
             try:
            if guess > secret:
              return "Too High", "📉 Go LOWER!" 
            else:
              return "Too Low", "📈 Go HIGHER!
          - To fix the bug in the except section of TypeError: I use following
             # I fixed the comment from Go HIGHER! to Go LOWER AND VICE VERSA
             if g > secret:
               return "Too High", "📉 Go LOWER!"
             else:
               return "Too Low", "📈Go HIGHER!"

           - To handle the new. So I'm adding new code to hadle it
             st.session_state.score = 0
           - Removed the str from the  secret =str( st.session_state.secrets) 
             After that the new Game button start to work
             secret = st.session_state.secrets
             The "New Game" button start to work after fixing this problem.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]
-  <img width="599" height="392" alt="image" src="https://github.com/user-attachments/assets/b377d9f3-c95c-461d-a54c-8ddd4e7b74f9" />


## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
