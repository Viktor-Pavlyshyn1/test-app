# Quiz CLI

## High-Level Description

Quiz CLI is an interactive terminal quiz game implemented in JavaScript using Node.js ES modules. Players choose one of the categories defined in `data/questions.json`, select how many questions to answer, enter numbered choices, and receive a score and review of incorrect answers. The application runs locally in a single Node.js process; quiz content is read from a JSON file and user interaction uses Node.js's built-in `readline` module. Terminal styling is implemented with local ANSI escape-code helpers, so the project has no runtime third-party package dependencies.

The application starts in `index.js`. It loads the question data, manages the category and question-count prompts and replay loop, and delegates input handling to `src/input.js`. `src/quiz.js` shuffles and presents questions, tracks answers and score, and prints results. `src/colors.js` provides terminal text styles.

## Features

- **Topic categories:** Choose JavaScript Basics, Node.js Fundamentals, or General Programming; category content is stored in `data/questions.json`.
- **Selectable quiz length:** Play all questions in the selected category, or choose three or five when the category contains enough questions.
- **Shuffled questions:** The quiz makes a shuffled copy of the selected questions using the Fisher–Yates algorithm.
- **Interactive answering and progress:** Select answers using numbered terminal prompts, view a progress bar, and receive immediate correctness feedback and any available explanation.
- **Results and answer review:** View the score, percentage, and performance message at the end, with the correct answers shown for questions answered incorrectly.
- **Replay and terminal styling:** Choose whether to play another quiz; prompts, feedback, and results use local ANSI color helpers.

## Project Structure

```text
project-root/
├── data/
│   └── questions.json  # Categories, questions, options, answers, and explanations
├── src/
│   ├── colors.js       # ANSI terminal styling helpers
│   ├── input.js        # Readline prompts, selection, confirmation, and pause helpers
│   └── quiz.js         # Question shuffling, quiz state, answer handling, and results
├── index.js            # Application entry point and main game loop
├── package.json        # Project metadata, Node.js requirement, and npm scripts
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 18 or later, as specified by the `engines` field in `package.json`.
- npm to run the scripts defined in `package.json` (distributed with Node.js).

### Installation

Obtain the repository using your usual Git workflow, then from its root directory:

```bash
npm install
```

The project uses Node.js built-in modules and has no declared third-party dependencies. There is no committed package lockfile, so `npm install` does not reproduce a lockfile-pinned dependency tree.

### Environment Configuration

No environment file or environment variables are referenced by the application. No additional configuration is required for the default local run.

### Running the Application

From the repository root, start the interactive quiz with:

```bash
npm start
```

This runs the `start` script in `package.json`, equivalent to `node index.js`. Follow the numbered prompts to choose a category and quiz length, answer questions, and optionally replay. Question data is loaded relative to `index.js` from `data/questions.json`.

### Testing and Validation

The package defines this test command:

```bash
npm test
```

It invokes Node.js's built-in test runner with `node --test`. No test files are present in the inspected repository, so there are no committed test cases to execute. No separate lint, format, or build scripts are defined.

### Verification

A successful launch clears the terminal, displays the Quiz CLI banner, and prompts for a category. Continue through the prompts to verify that questions and results are displayed. The application is an interactive CLI; no web URL or HTTP health-check endpoint is configured.
