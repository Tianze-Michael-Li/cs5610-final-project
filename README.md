# CS5610 Final Project

Kambaz Quizzes for CS5610 Web Development.

This repository currently contains a Next.js frontend and an Express API scaffold. A5 integration and quiz features will be added in separate pull requests.

Requirements: [Kambaz Quizzes](https://kambaz.dev/2026/fall/webdev/project/quizzes).

## Structure

- `client/`: Next.js, React, TypeScript, and Tailwind CSS
- `server/`: Express and TypeScript
- `.github/`: pull request template and automated checks

## Local setup

Use Node.js 24, as specified in `.nvmrc`. Start from the repository root in each terminal.

Start the API:

```bash
cd server
cp .env.example .env
npm ci
npm run dev
```

Check <http://localhost:4000/api/health>. It should return `{"status":"ok"}`.

In another terminal, start the frontend:

```bash
cd client
cp .env.example .env.local
npm ci
npm run dev
```

Open <http://localhost:3000>. Make sure ports 3000 and 4000 are available.

## Working together

Keep `main` runnable. After the initial setup commit, develop each small feature on its own branch:

```bash
git switch main
git pull --ff-only
git switch -c feature/quiz-list
```

Agree on the feature owner and API fields before starting. Commit complete, focused changes and push the feature branch. Open a pull request to `main`, describe what changed and how it was checked, and ask the other teammate to review it. Merge after the review and automated checks pass.

Use descriptive branch names such as `feature/quiz-list` or `fix/quiz-title-validation`. Keep environment files local and update `.env.example` when configuration changes.

## Checks

Run from the repository root:

```bash
npm --prefix client run lint
npm --prefix client run build
npm --prefix server run typecheck
```

GitHub Actions runs these checks for pull requests into `main` and pushes to `main` once the workflow is pushed. This workflow does not deploy the application.
