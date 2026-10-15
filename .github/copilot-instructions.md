# Copilot instructions for this workspace

## Project overview

This repository is a small single-page web app built from one file: `index.html`.

The app is a space-themed quiz that renders question cards, tracks score progress, and shows a final result summary when the user completes all questions. There is no framework, package manager, or build pipeline in this workspace.

## Build, test, and lint commands

There are no project-defined build, test, or lint commands because this repository has no `package.json`, `pyproject.toml`, `Cargo.toml`, or similar project manifest.

For local validation, run a static server from the workspace root:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a browser and verify that:
- the quiz loads,
- answer buttons respond,
- the score updates correctly,
- the next-question flow works,
- the results screen appears after the final question, and
- the restart flow resets the quiz.

If this is changed to include scripts or tooling later, prefer the project’s actual commands over any assumed defaults.

## High-level architecture

- `index.html` contains all application logic and styling in one place.
- The CSS is embedded in a `<style>` block and defines the full visual system: dark/light theme support, glass-style cards, gradient accents, responsive layout, and keyframe animations.
- The JavaScript is embedded in a `<script>` block and contains:
  - `questions`: the static dataset for all quiz questions, answers, correct index, and fact text,
  - `current`, `score`, and `locked`: the minimal runtime state,
  - `renderQuestion()`: populates the current question and answer buttons,
  - `chooseAnswer()`: locks the answer, highlights correct/wrong choices, updates the score and feedback,
  - `showResults()`: shows the final score and message based on the total result,
  - restart handling for replaying the quiz.
- The app uses direct DOM APIs rather than a UI framework. It intentionally keeps state local and simple.

## Key conventions

- Keep this project dependency-free unless the user explicitly asks for a framework or tooling setup.
- Preserve the existing visual identity: space/astronomy theme, purple/pink accent palette, rounded card UI, and soft glassmorphism styling.
- Keep question data structured as objects with `question`, `answers`, `correct`, and `fact` in the `questions` array.
- Use the existing UI classes (`.answer.correct`, `.answer.wrong`, `.feedback.good`, `.feedback.bad`, `.result.visible`) rather than inventing a separate styling pattern.
- Prefer semantic HTML and accessible behavior: button controls, keyboard focus, and `aria-live` feedback should remain intact when editing the quiz flow.
- For bug fixes or feature additions, validate in the browser rather than adding a framework-specific test stack.

## Working notes

This repo is intentionally minimal and static. Do not introduce a framework, build step, or package manager unless the user asks for one explicitly. Most changes should remain inside `index.html` unless a new asset or supporting file is clearly required.
