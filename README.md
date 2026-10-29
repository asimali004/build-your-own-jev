# 🧠 Build Your Own Jev

Learn how to make an AI model give **decisions, not text**.
Step by step, from scratch, for beginners.

> **Jev** is a decision model by TypeSafe AI. It is closed (API only).
> This repo rebuilds the **same idea** with a free, open model, so you can understand it and customize it for your own use.
> This project is not made by, and not connected to, TypeSafe AI.

---

## 💡 The big idea

A normal chatbot writes text. We don't want text. We want an answer our code can use.

```
STATE + QUESTION → model (1 run) → logits → keep only our answers → softmax → probabilities
```

**Example:**
- **State:** `"Wrong size AGAIN. Just give me my money back."`
- **Question:** `"Is the customer asking for their money back?"`
- **Answer:** `P(yes) = 0.96`

---

## 📓 The 3 notebooks

| # | Notebook | Method | Question it answers | Run |
|---|---|---|---|---|
| 1 | [Part 1: Noul](build-your-own-jev-part-1-noul-yes-no.ipynb) | **Noul** | Is it true? (yes/no) | [Kaggle](https://www.kaggle.com/code/syedasimalishah/build-your-own-jev-part-1-noul-yes-no) |
| 2 | [Part 2: Choice](build-your-own-jev-part-2-choice-pick-one.ipynb) | **Choice** | Which one? (pick from a list) | [Kaggle](https://www.kaggle.com/code/syedasimalishah/build-your-own-jev-part-2-choice-pick-one) |
| 3 | [Part 3: Score](build-your-own-jev-part-3-score-rate-on-scale.ipynb) | **Score** | How much? (rate on a scale) | [Kaggle](https://www.kaggle.com/code/syedasimalishah/build-your-own-jev-part-3-score-rate-on-scale) |

👉 Start with **Part 1**. Each part builds on the one before it.

---

## 🛒 The example

All notebooks use **6 realistic support tickets** from an online shoe store: wrong sizes, late orders, double charges, app bugs, and bulk orders.

By the end, your code can:
- ✅ find refund requests, legal threats, and card numbers (**Noul**)
- 🔀 send each ticket to the right team (**Choice**)
- 📊 rate urgency and frustration, then sort tickets by priority (**Score**)
- 🧩 run all 3 methods together with one `ask()` function (**Bonus**)

---

## 🧩 What each part teaches

**Part 1: Noul (Yes/No)**
- What logits and softmax are, with real numbers
- Comparing only the "Yes" and "No" tokens → P(yes)
- A checklist of many questions → a table → real actions
- Calibration: finding the best temperature with labeled examples

**Part 2: Choice (Pick One)**
- Options as letters (A, B, C...) → softmax → the best option
- Order bias: why the model may like "A", and how shuffling fixes it
- Confidence: send clear cases automatically and unclear ones to a human

**Part 3: Score (Rate on Scale)**
- Levels as digits (0, 1, 2...) → the expected level (like 2.2)
- Plain levels vs levels with examples
- Mixing scores and customer data with your own weights → a priority list
- A mini-Jev `ask()` function using all 3 methods

---

## 🚀 How to run

### On Kaggle (easiest)
1. Open a notebook from the table above.
2. Click **Copy & Edit**.
3. Go to **Settings**: set **Accelerator → GPU** and **Internet → On**.
4. Click **Run All**.

### On your own computer
```bash
pip install torch transformers accelerate pandas jupyter
jupyter notebook
```
A GPU is recommended. It also works on CPU, just slower.

No API key needed. Everything runs on your machine.

---

## 🔧 Make it your own

Look for `🔧 CHANGE` comments in the code. They tell you **what to edit** and **what happens** when you do.

| Change this | To get this |
|---|---|
| `MODEL_NAME` | A smarter (bigger) or faster (smaller) model |
| `SYSTEM_PROMPT` | Better answers for your domain |
| `TICKETS` | Your own data (emails, reviews, CVs...) |
| `CHECKLIST`, `TEAMS`, levels | Your own questions and options |
| `THRESHOLDS` | When your code should act |
| `temperature` | More honest probabilities |
| `n_orders` | Less order bias (but slower) |
| `WEIGHTS` | What matters most to your business |

---

## 📚 Words used in this repo

| Word | Meaning | Example |
|---|---|---|
| **State** | The data you want judged | A ticket: `{"message": "Wrong size again..."}` |
| **Instructions** | The question you ask | `"Is the customer asking for a refund?"` |
| **Criteria** | The allowed answers | `{"shipping": "Late or lost orders", ...}` |
| **Logits** | Raw scores for every next token | `"Yes" → 18.2`, `"No" → 14.9` |
| **Softmax** | Turns logits into probabilities | `P(Yes) = 0.96` |
| **Temperature** | Makes the model more or less sure | T = 2 → less sure |
| **Confidence** | How clearly one answer wins | 1.0 = very clear |
| **Threshold** | The number where your code acts | Refund only if ≥ 0.8 |

---

## ⚠️ Limits

- This is for **learning**. It is not as accurate or fast as the real Jev.
- Our version runs the model once per question. The real Jev answers many questions in one run.
- Small models make mistakes. Always test on your own data before real use.

---

## 🛠️ Built with
- [Hugging Face Transformers](https://github.com/huggingface/transformers)
- [Qwen2.5-1.5B-Instruct](https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct)
- PyTorch and pandas

---

⭐ If this helped you, please star the repo!
