# Repository instructions

- Use uv to manage Python dependencies and run Python commands. Keep `pyproject.toml` and `uv.lock` together when changing dependencies.
- For development tools, run `uv sync --locked --only-group dev` and `uv run --locked --only-group dev <command>`. Use the `cpu` group for CPU tests and the `docs` or `docs-test` groups for documentation work; see `CONTRIBUTING.md` and `docs/README.md`.
- Keep VM/container GPU provisioning separate from local uv environments. Preserve the platform-specific packages and pins in the provisioning scripts.
- Use Ruff for Python linting: `uv run --locked --only-group dev ruff check <changed-paths>`. Follow the existing pre-commit hooks for formatting; do not reformat unrelated files.
- New Python files are expected to pass Pyright: run `uv run --locked --only-group dev pyright <new-python-files>` and fix reported errors before finishing.
- Choose the simplest implementation that meets the current requirements. Reuse existing dependencies and remove obsolete paths rather than adding compatibility layers.
- Preserve unrelated local changes. Work in the current checkout unless a second branch needs its own checkout.
- Run focused checks for the changed behavior. Tests must catch a plausible regression, not repeat implementation details or assert their own setup.
- Edit `.github/workflows/pr-test.yml.j2` and regenerate `.github/workflows/pr-test.yml`; do not hand-edit the generated workflow.
- Keep documentation concise and consistent with executable behavior. Update both languages when changing shared documentation behavior.
- Use `trash` instead of `rm -rf`. Do not permanently delete files without explicit authorization.

`CLAUDE.md` is a symlink to this file. Keep shared instructions here.
