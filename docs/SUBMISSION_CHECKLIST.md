# Submission Checklist

Run through this list before turning in your graduation project. It's intentionally general: adapt it to whatever your project actually does.

## Environment & reproducibility
- [ ] `git clone` into a brand-new directory, then `docker compose up --build` works with no manual fixes.
- [ ] `.env.example` lists every environment variable the app needs, with placeholder (not real) values.
- [ ] `uv.lock` is committed and matches `pyproject.toml` (`uv lock --check`).
- [ ] No machine-specific paths, credentials, or local-only assumptions are hardcoded.

## Documentation
- [ ] `README.md` accurately describes what the project does and how to run it, end to end.
- [ ] Architecture docs (whether that's `docs/ARCHITECTURE.md` or your own split across files) cover features, system design, known limitations, and next steps.
- [ ] You (or someone else) have followed the setup instructions on a clean clone, line by line.

## Code & functionality
- [ ] The application starts, and the documented golden-path use case works end to end.
- [ ] Reasonable errors are handled gracefully (no unhandled stack traces on bad input).
- [ ] No leftover debug prints, commented-out code, or dead files.

## Data & secrets
- [ ] Sample/test data contains no real personal or sensitive information.
- [ ] No `.env`, API keys, or other secrets are committed (check `git log` history too, not just the current tree).
- [ ] Large or generated data files are excluded via `.gitignore` rather than committed.

## Submission logistics
- [ ] Final code is on the `main` branch — other branches are not reviewed.
- [ ] The repository builds and runs using only the documented steps, with nothing else needed.
