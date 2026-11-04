# Interactive Study Guide: *Live Not By Lies*

A single-page study guide for Alexander Solzhenitsyn's essay *Live Not By Lies*, written for an Internal Auditing course (ACCT 3233). It has a summary, key ideas, a scored practice quiz, short-answer practice with model answers, audit scenarios, and a timed exam mode.

It's plain HTML, CSS, and JavaScript in one file, with no frameworks, build step, or install.

## How to use it

Open `index.html` in Chrome or Safari.

- **Practice Quiz:** Click an answer for each question. You get instant feedback and a running score.
- **Exam Mode:** The bar at the top stays visible while you scroll.
  - **Start** begins a fresh 5-minute attempt at the quiz.
  - **Pause / Resume** stops the clock. The quiz stays locked while paused, so you can't answer with the clock stopped.
  - **Reset** puts the timer back to 5:00 and clears the quiz.
  - When time runs out, the quiz locks, unanswered questions are marked, and your final score appears in the bar. If you answer every question first, the exam ends early and shows how much time you had left.
- **Show Correct Answers** reveals the answers to any questions you haven't answered. Revealed questions are locked, but they don't count as answered and don't add to your score. It's disabled during a timed exam.

## What changed from the original

The original `Study_guide.html` is kept in this folder for comparison. `index.html` keeps the same content and look, with these fixes:

| Original behavior | Now |
| --- | --- |
| The timer showed 05:00 for a full second before counting down | The countdown starts immediately |
| Stop paused the clock without resetting it, and Start always restarted it | Separate Start, Pause/Resume, and Reset controls |
| The timer sat in a card partway down the page | It's in a sticky bar that stays visible while you scroll |
| Nothing happened to the quiz when time ran out | The quiz locks and shows your final score |
| Show Correct Answers counted revealed questions as "answered" | Revealed questions no longer count as answered |
| The timer drifted if the tab was in the background | The countdown runs against a fixed end time, so it stays accurate |

## How I built it with Claude Code

I made the update with [Claude Code](https://claude.com/claude-code), running in the VS Code terminal. I described the changes I wanted in one prompt: rebuild the page as `index.html`, turn the timer into a real exam mode, fix the answer-reveal bug, test it, write this README, and walk me through publishing to GitHub.

Here's how the work went:

1. **Finding and reading the code.** Claude Code found my original file and read through it. It pointed out the existing timer problems before changing anything.
2. **Making the changes.** It edited the page in small steps. The exam is modeled as four states (`idle`, `running`, `paused`, `finished`), and each control moves the exam between them.
3. **Testing.** Claude Code wrote a 26-check test script and ran it in headless Chrome on a temporary copy of the page. The script fakes the clock, so the full 5-minute timeout runs in seconds. It checks counting down, pausing, locking at time-out, the final score, Reset, finishing early, and the reveal fix. It also took screenshots to check the layout.
4. **Docs and Git.** Claude Code drafted this README. Then it walked me through creating the GitHub repository, explaining each Git command before running it and asking before pushing.

I reviewed each step as it happened, and I'm responsible for the final result.

## Files

- `index.html`: the updated study guide
- `Study_guide.html`: the original version, kept for comparison
