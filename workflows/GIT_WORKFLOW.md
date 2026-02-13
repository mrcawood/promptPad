# GIT_WORKFLOW (Optional)

Use this when the project is managed with git and you want a traceable history.

Requirements:
1) Propose a feature branch name.
2) Propose a commit plan (2-6 commits), each with intent and approximate files touched.
3) Work in small commits. Avoid a mega-commit.
4) After each logical milestone: run tests (or at least lint/unit), then commit.
5) Update PROGRESS.md with branch + commits + tests run.
6) Stop and ask for approval before any push/merge/rebase that rewrites history.

Constraints:
- Never commit secrets.
- Never push/merge or rewrite history without explicit user approval.
- Never use elevated permissions to "fix" git issues.
