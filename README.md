# 🧠 Tech Riddles

> A dark-themed interactive tech quiz web app built with TailwindCSS and JavaScript. Log in, crack 3 tech riddles against the clock, and see how you score.


## Table of Contents
- [About the Project](#about-the-project)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [How to Use](#how-to-use)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)


## About the Project

Tech Riddles is a browser-based quiz application built as part of a course assignment exploring how Generative AI can support software development. The app challenges users with 3 tech-themed riddles, each with a countdown timer, multiple choice answers, instant feedback, and a results screen at the end.

The project was built using only HTML, TailwindCSS (via CDN), and vanilla JavaScript — meaning it requires no installation, no build tools, and no server. Just open the file in a browser and it works.


## Features
- **Login screen** — username and password authentication before accessing the quiz
- **Welcome screen** — displays the logged-in user's name and explains the rules
- **3 tech riddles** — multiple choice questions with 4 answer options each
- **20-second countdown timer** — colour-coded bar that turns amber then red as time runs out
- **Live score tracking** — score updates in real time as you answer
- **Progress bar** — shows how far through the quiz you are
- **Instant feedback** — correct answer highlighted green, wrong answer highlighted red with explanation shown
- **Time expired handling** — if timer runs out, correct answer is revealed automatically
- **Results screen** — final score out of 3, grade badge, and per-question breakdown
- **Play Again** — restart the quiz without logging out
- **Log out** — returns to the login screen and clears all fields
- **Dark mode design** — deep black and purple theme with glowing effects
- **Responsive layout** — works on desktop, tablet, and mobile screens
- **Smooth animations** — fade-in transitions between screens, shake animation on wrong answers


## Technologies Used

| Technology | Version | Purpose |
|---|---|---|
| HTML5 | — | Page structure and content |
| TailwindCSS | v3 (CDN) | All styling and responsive layout |
| JavaScript (Vanilla) | ES6+ | Quiz logic, timer, screen switching, scoring |
| Google Fonts | — | Space Grotesk (body) and Space Mono (titles) |

No frameworks. No npm. No build process. Everything runs directly in the browser.


## Project Structure
```
tailwind-hello-world/
│
├── index.html        ← The entire application (all screens + logic in one file)
└── README.md         ← This file
```

### Inside index.html

The file is organised into clearly commented sections:

```
index.html
│
├── <head>
│     ├── TailwindCSS CDN script
│     ├── Google Fonts link
│     └── Custom CSS (animations, dark theme styles)
│
├── <body>
│     ├── Screen 1 — Login
│     │     └── Username field, password field, sign in button
│     │
│     ├── Screen 2 — Welcome
│     │     └── Player name display, rules list, start button
│     │
│     ├── Screen 3 — Quiz
│     │     └── Question counter, progress bar, timer, question box, answer buttons, feedback, next button
│     │
│     └── Screen 4 — Results
│           └── Score circle, grade badge, question breakdown, play again, logout
│
└── <script>
      ├── CORRECT_USERNAME / CORRECT_PASSWORD  ← credentials
      ├── questions array                      ← all quiz content
      ├── showScreen()                         ← switches between the 4 screens
      ├── doLogin()                            ← checks credentials
      ├── startQuiz()                          ← resets state and begins quiz
      ├── loadQuestion()                       ← renders each question
      ├── startTimer()                         ← countdown logic
      ├── timeExpired()                        ← handles running out of time
      ├── selectAnswer()                       ← handles answer selection
      ├── showFeedback()                       ← shows correct/wrong message
      ├── nextQuestion()                       ← advances to next question
      ├── showResults()                        ← builds and shows results screen
      ├── playAgain()                          ← restarts the quiz
      └── doLogout()                           ← clears fields and returns to login
```

---

## Installation & Setup

There is nothing to install. This project uses the TailwindCSS CDN method, which means TailwindCSS is loaded directly from the internet — no terminal, no npm, no configuration files needed.

### Requirements

- A computer running Windows, macOS, or Linux
- A modern web browser (Google Chrome or Firefox recommended)
- An internet connection (required for TailwindCSS and Google Fonts to load from CDN)
- A code editor if you want to make changes (VS Code recommended — free at code.visualstudio.com)

### Steps to run

1. Download or clone this repository
2. Locate the `index.html` file
3. Double-click `index.html` — it opens directly in your browser
4. That is it. No setup required.

### If you are cloning via Git

```bash
git clone https://github.com/your-username/tailwind-hello-world.git
cd tailwind-hello-world
```

Then double-click `index.html` or open it with:

```bash
# On Windows
start index.html

# On macOS
open index.html

# On Linux
xdg-open index.html
```

---

## How to Use

### Logging in

The default credentials are:

| Field | Value |
|---|---|
| Username | `user1` |
| Password | `123quiz` |

Enter the username and password then click **Sign In** or press **Enter**.

### Playing the quiz

1. Read the welcome screen and click **Start Quiz**
2. Read each riddle carefully — you have **20 seconds** per question
3. Click one of the 4 answer options before the timer runs out
4. Green highlight = correct. Red highlight = wrong (correct answer also revealed)
5. An explanation is shown after every answer
6. Click **Next Question** to continue
7. After question 3, click **See Results**

### Reading your results

- Your score is shown out of 3 in the circle
- A grade badge appears based on your score:
  - 3/3 — Perfect Score (purple)
  - 2/3 — Great Job (green)
  - 1/3 — Keep Going (amber)
  - 0/3 — Don't Give Up (red)
- A breakdown shows each question and whether you got it right or wrong
- Click **Play Again** to retry or **Log out** to return to the login screen


## Configuration

You can customise the app by editing `index.html` in any text editor. All configurable values are clearly marked in the script section at the bottom of the file.

### Changing the login credentials

Find these two lines near the top of the `<script>` section:

```js
const CORRECT_USERNAME = "user1";
const CORRECT_PASSWORD = "123quiz";
```

Replace the values in quotes with whatever username and password you want.

### Changing the questions

Find the `questions` array in the script section. Each question follows this format:

```js
{
  question: "Your riddle or question here?",
  options: ["Option A", "Option B", "Option C", "Option D"],
  correct: 1,
  explanation: "Why this answer is correct."
},
```

The `correct` value is the index of the right answer — 0 means Option A, 1 means Option B, 2 means Option C, 3 means Option D.

### Changing the number of questions
Simply add or remove question objects from the `questions` array. The counter, progress bar, and results screen all update automatically based on however many questions are in the array.

### Changing the timer
Find this line inside the `startTimer()` function:
```js
timeLeft = 20;
```
Change `20` to however many seconds you want per question.

### Changing the colour theme

The dark purple theme is controlled by inline `style` attributes throughout the HTML. The main colours used are:

| Colour | Hex code | Used for |
|---|---|---|
| Deep black | `#0a0a10` | Page background |
| Dark charcoal | `#13131f` | Card backgrounds |
| Purple | `#7c3aed` | Buttons, highlights, timer bar |
| Light purple | `#a78bfa` | Accent text, username display |
| Off white | `#e8e4ff` | Main text |
| Muted gray | `#4d4d6d` | Secondary text |

---

## Troubleshooting

### The page looks unstyled — plain black text on white background

TailwindCSS is not loading. This is almost always caused by one of these:

- No internet connection — the CDN requires internet to load
- A typo in the script tag — check that it reads exactly:
  ```html
  <script src="https://cdn.tailwindcss.com"></script>
  ```
- The script tag is outside the `<head>` section — move it inside `<head>`

### The login is not working

- Check that you are using the exact username and password set in the script
- Usernames are case-sensitive — `User1` is not the same as `user1`
- Make sure there are no accidental spaces before or after what you type

### The hover effect on the button is not working

This is a common Tailwind typo — using a dash instead of a colon:

```
Wrong:   hover-bg-purple-700
Correct: hover:bg-purple-700
```

### The timer is not counting down

This usually means the JavaScript has an error elsewhere stopping execution. Open your browser, press `F12` to open developer tools, click the **Console** tab, and look for any red error messages.

### The fonts are not loading

Google Fonts requires an internet connection. If you are offline the app falls back to your system's default sans-serif font. The app still works — it just looks slightly different.

### My changes are not showing in the browser

You need to save the file AND refresh the browser. Press `Ctrl+S` in VS Code to save, then `F5` in the browser to refresh.

---

## Contributing
This project was created as a personal learning assignment. If you would like to suggest improvements or report issues:

1. Fork the repository on GitHub
2. Create a new branch for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make your changes to `index.html`
4. Commit your changes with a clear message:
   ```bash
   git commit -m "Add: description of what you changed"
   ```
5. Push to your fork and open a Pull Request


## License
This project is submitted as coursework and is intended for educational purposes.
You are free to use this code as a reference or learning resource. If you build on it, please credit the original.

---

*Built with TailwindCSS CDN + Vanilla JavaScript. No frameworks. No build tools. Just open and run.*
