- After each request, add an entry to prompts.md: what I asked, what you changed, and whether it worked.

# Project layout

This is a single-file web app. Keep `index.html` at the repository root so GitHub Pages can serve it. The root also contains `spec.md` for the project specification, `AGENTS.md` for project instructions, and `prompts.md` for request and change notes.

Use the numbered folders for other project files:

- `00_planning/` — planning notes and sketches.
- `01_data/` — data files.
- `02_validation/` — hand calculations and test cases.
- `03_output/` — screenshots and exported results.

Save every new file in the appropriate root location or numbered folder. Add files to a numbered folder's README only when its purpose or contents need clarification; do not put unrelated files at the root.

After each requested change is implemented and validated, commit the files changed for that request without asking. Do not include unrelated work in a commit.