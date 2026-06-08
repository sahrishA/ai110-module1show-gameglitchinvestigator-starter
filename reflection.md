# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

**Objective:** Understand the initial state of the application and identify specific bugs.

- What did the game look like the first time you ran it?
  - *Consider: Did it crash? Did it display incorrectly? Was there unexpected behavior on load?*

- List at least two concrete bugs you noticed at the start  
  - *Example 1: "the secret number kept changing every time I refreshed the page"*
  - *Example 2: "the hints were backwards (showing higher when the guess was too low)"*
  - *Example 3: "the game reset unexpectedly during gameplay"*
  - *Example 4: "the guess input field wasn't accepting my input correctly"*

**Your answer:**
[Write your response here - describe the broken state and list 2+ specific bugs with details]

---

## 2. How did you use AI as a teammate?

**Objective:** Reflect on your AI collaboration process, including both successes and failures.

- Which AI tools did you use on this project?
  - *Example: ChatGPT, GitHub Copilot, Claude, Gemini, etc.*
  - *How often did you use them: for every question, occasional help, brainstorming only?*

- Give one example of an AI suggestion that was **correct** 
  - *Include:*
    - *What problem you asked the AI about*
    - *What the AI specifically suggested (code snippet, approach, explanation)*
    - *How you verified the result was correct (testing, reasoning, comparing to documentation)*
    - *Why this suggestion actually helped you solve the problem*

- Give one example of an AI suggestion that was **incorrect or misleading**
  - *Include:*
    - *What problem you asked the AI about*
    - *What the AI incorrectly suggested*
    - *How you discovered it was wrong (error message, unexpected behavior, testing)*
    - *What you did instead to fix the actual problem*
    - *What you think the AI misunderstood*

**Your answer:**
[Write your response here - show your AI collaboration journey with specific examples]

---

## 3. Debugging and testing your fixes

**Objective:** Demonstrate your testing methodology and how you validated solutions.

- How did you decide whether a bug was really fixed?
  - *Consider: Did you test manually? Check against requirements? Run the game multiple times? Verify in different scenarios?*

- Describe at least one test you ran (manual or using pytest)
  - *Include:*
    - *What you were testing (which bug or feature)*
    - *Exactly what you did (step-by-step actions)*
    - *What you observed (what actually happened)*
    - *How this test proved the bug was fixed (or still broken)*
  - *Example: "I ran the game 5 times without refreshing and verified the secret number stayed the same each time"*

- Did AI help you design or understand any tests?
  - *How did the AI assist: Did it suggest test cases? Explain pytest syntax? Help you think about edge cases?*
  - *Was the AI's testing advice helpful or did it miss important scenarios?*

**Your answer:**
[Write your response here - document your testing process and validation strategy]

---

## 4. What did you learn about Streamlit and state?

**Objective:** Demonstrate understanding of Streamlit's core concepts.

- In your own words, explain why the secret number kept changing in the original app.
  - *Hint: Think about what happens every time a user interacts with a Streamlit app*
  - *Consider: How is the code executed? When does the secret number get reassigned?*
  - *What triggers a "rerun" in Streamlit?*

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  - *Analogy approach: Compare it to something familiar (e.g., a video game checkpoint, a notebook recalculation, etc.)*
  - *Explain: Why does Streamlit rerun all code from top to bottom? What problem does session state solve?*
  - *Keep it simple and concrete*

- What change did you make that finally gave the game a stable secret number?
  - *Describe the specific code change (e.g., using `st.session_state`, moving code into a conditional, etc.)*
  - *Explain why this change solved the problem*
  - *How did this change align with how Streamlit works?*

**Your answer:**
[Write your response here - explain your understanding of Streamlit state management]

---

## 5. Looking ahead: your developer habits

**Objective:** Reflect on personal growth and future practices.

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - *This could be:*
    - *A testing habit* (e.g., "I'll always test edge cases first")
    - *A debugging strategy* (e.g., "I'll print state changes to understand the flow")
    - *A prompting strategy* (e.g., "I'll ask AI for explanations, not just code")
    - *A Git practice* (e.g., "I'll commit after each successful test")
    - *A code organization approach* (e.g., "I'll separate state initialization from logic")*
  - *Why this habit worked well for you on this project?*

- What is one thing you would do differently next time you work with AI on a coding task?
  - *Reflect on: Did you over-rely on AI's first suggestion? Did you ask for explanations instead of just code? Did you verify enough? Did you use AI for rubber-ducking or problem analysis?*
  - *What would improve your AI collaboration?*

- In one or two sentences, describe how this project changed the way you think about AI-generated code.
  - *Consider: Is AI a shortcut or a tool? How reliable is AI? When is AI helpful vs. when should you rely on your own thinking? Did this project change your confidence in AI?*

**Your answer:**
[Write your response here - reflect on your growth and future development practices]

---

## 📝 Tips for strong reflections:
- **Be specific:** Instead of "I used AI," say "I asked Claude to explain Streamlit session state"
- **Be honest:** It's okay if AI gave you wrong answers—that's valuable learning
- **Show your reasoning:** Explain *why* something was broken or *why* your fix worked
- **Connect concepts:** Link your debugging process back to how Streamlit actually works
- **Focus on learning:** This isn't about perfect code—it's about understanding what happened and why
