# Dynamic Study Guide: AI Usage Levels

A self-scoring study guide for a class slide deck on AI usage levels: L0 through L6, phase transitions, governance by level, and frontier concepts. It has 6 multiple-choice and 4 short-answer questions (24 points), a sticky live scoreboard, and a timed exam mode.

It's plain HTML, CSS, and JavaScript in one file, with no frameworks, build step, or install.

## How to use it

Open `index.html` in Chrome or Safari.

- **Answering:** Pick or type an answer, then click **Check Answer**. Multiple-choice questions are scored automatically. Short-answer questions use keyword matching, so include the core concepts from the slides. Each answer gets immediate feedback with the correct answer and why it's right.
- **Scoreboard:** The score, percent, answered count, and letter grade stay pinned to the top of the screen.
- **Exam Mode** (in the scoreboard):
  - **Start** begins a fresh 5-minute attempt.
  - **Pause / Resume** stops the clock. The quiz is locked while paused, so you can't answer with the clock stopped.
  - **Reset** puts the timer back to 5:00 and clears the quiz.
  - When time runs out, the quiz locks, questions you hadn't checked are marked "Not answered", and your final score appears in the scoreboard. Only checked answers count. If you check every answer first, the exam ends early and shows how much time was left.
- **Show Correct Answers** (under Overall Results) reveals the answers to any questions you haven't checked. Revealed questions are locked, but they don't count as answered and earn no points. It's disabled during a timed exam.

## What changed from the original

The original `Dynamic_Study_Guide.html` is kept in this folder for comparison. `index.html` keeps the same questions, scoring, and look, and adds:

| Original | Now |
| --- | --- |
| No timer | A 5-minute exam mode with Start, Pause/Resume, and Reset, built into the sticky scoreboard |
| Nothing ended the quiz | When time runs out, the quiz locks and shows the final score |
| No way to see answers without answering | **Show Correct Answers** reveals answers without counting them as answered or scored |
| On phones, the scoreboard stacked into one tall column | It stays two boxes across on small screens, so it covers less of the page |

The timer counts down to a fixed end time instead of counting ticks, so it stays accurate even if the browser slows a background tab.

## How I built it with Claude Code

I made the update with [Claude Code](https://claude.com/claude-code), running in the VS Code terminal. I gave it one prompt: rebuild the page as `index.html`, add a real 5-minute exam mode, handle revealed answers correctly, test it, write this README, and walk me through publishing to GitHub.

Here's how the work went:

1. **Reading the code first.** Claude Code read the whole original file before changing anything. It noticed the page had no timer yet, so it built one instead of trying to fix one.
2. **Making the changes.** It put the exam controls in the existing sticky scoreboard, so the time stays visible while scrolling. The exam is modeled as four states (`idle`, `running`, `paused`, `finished`), and each control moves the exam between them.
3. **Testing.** Claude Code wrote a 28-check test script and ran it in headless Chrome on a temporary copy of the page. The script fakes the clock, so the full 5-minute timeout runs in seconds. It checks counting down, pausing and locking, the time-out score, Reset, finishing early, and that revealed answers aren't counted. When one check failed, the problem was the test's own math: the HTML starts the total at 22 points, but the questions add up to 24. Claude Code fixed the test, then took screenshots at desktop and phone widths, which is how it caught the scoreboard taking up half the phone screen.
4. **Git.** Claude Code explained each Git command before running it and asked before pushing to GitHub.

I reviewed each step as it happened, and I'm responsible for the final result.

## Files

- `index.html`: the updated study guide
- `Dynamic_Study_Guide.html`: the original version, kept for comparison
