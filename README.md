# Tech Treasure Hunt — Engineering Day 2026 (Streamlit Edition)

A full-screen, 5-question quiz built with Streamlit. Team name entry, score
tracking, a Skip button, and no answers ever shown on screen — built for a
quick faculty demo.

## Files

```
app.py                    the whole app (UI + game logic)
questions.py               the 5 questions — edit THIS file to change quiz content
requirements.txt           Python dependencies
.streamlit/config.toml     dark theme colors
```

---

## 1. Run it locally (2 minutes)

```bash
# 1. Create a virtual environment (optional but recommended)
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the app
streamlit run app.py
```

Streamlit will open `http://localhost:8501` in your browser automatically.

---

## 2. Push it to GitHub

```bash
git init
git add .
git commit -m "Engineering Day quiz app"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo-name>.git
git push -u origin main
```

If you don't have a GitHub repo yet:
1. Go to https://github.com/new
2. Name it (e.g. `engineering-day-quiz`), keep it **Public** (required for the
   free tier of Streamlit Community Cloud), don't add a README (you already
   have one), then click **Create repository**.
3. Copy the `git remote add origin ...` command GitHub shows you and run the
   steps above.

---

## 3. Deploy for free on Streamlit Community Cloud

1. Go to https://share.streamlit.io and sign in with your GitHub account.
2. Click **"Create app"** → **"From an existing repo"**.
3. Pick your repository and branch (`main`), set **Main file path** to
   `app.py`.
4. Click **Deploy**. In under a minute you'll get a public link like:
   `https://your-app-name.streamlit.app`
5. Share that link with your faculty — anyone can open it on their phone or
   laptop, no installation needed.

Any time you `git push` new changes, the deployed app updates automatically.

---

## 4. Editing questions

Open `questions.py`. Each question is a dict with `title`, `prompt`,
`snippet` (optional code/table block, leave `""` to omit), `hint`, `answers`
(list every accepted spelling), and `points`. Add, remove, or edit questions
freely — `app.py` doesn't need to change. `CONFIG` at the top controls the
event name, tagline, and scoring penalties.

---

## 5. How the game works

- Team enters their name and hits **Start Quiz**.
- Each question shows one at a time, full screen.
- **Submit** checks the answer. Wrong answers show "Not quite — try again"
  (no penalty reveal of the answer) and let the player retry.
- **Skip** moves on to the next question immediately without penalty beyond
  not scoring that question.
- **Hint** costs points (see `CONFIG["hint_penalty"]`) if used before a
  correct answer.
- The correct answer / explanation is **never shown on screen** — only
  "Correct!" or "Skipped" feedback.
- After the last question, a summary screen shows score, correct count,
  skipped count, and time taken.
- **Switch Player / Restart** clears the current session and returns to the
  name screen — safe to reuse on the same device between participants.

---

## 6. Before your demo — quick checklist

- [ ] Run `streamlit run app.py` once yourself and play through all 5 questions.
- [ ] Confirm a wrong answer doesn't reveal the solution and lets you retry.
- [ ] Confirm the Skip button moves to the next question.
- [ ] Confirm the final screen shows the correct score/time.
- [ ] If deploying, open the `*.streamlit.app` link from your phone to check
      it looks good full-screen there too.
