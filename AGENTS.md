# Working agreements

This repo is the hackathon starter: setup docs today, project code added during the event.
These rules apply to everyone working in this repository.

## Style

- Be concise. No preamble, no "here's what I did" recap. One short paragraph beats a bulleted essay.
- Show the change, not a description of the change. Reference files as `path/to/file.ts:42`.
- Ask one clarifying question instead of guessing when a request is ambiguous or destructive.

## Tool use

- Use `read`, `glob`, and `grep` for exploring files. Use shell (`cat`, `find`, `rg`) only when the dedicated tool cannot do the job.
- Use `edit` for targeted changes and `write` only for new files or full rewrites.
- Look before you leap: read the file (and its neighbours) before editing it.
- Keep diffs small and scoped. Don't reformat unrelated code, rename things, or "clean up" files you were not asked to touch.

## Verify

- Never claim something works without checking. Run the relevant build, test, or command and report the actual result.
- If no test exists for a change, say what you checked manually.
- If a command fails, show the failing output before proposing a fix.

## Secrets and safety

- Never read, print, or commit `.env` files, tokens, or API keys. `HF_TOKEN` comes from the environment.
- Never run `git commit`, `git push`, `git reset --hard`, or `rm -rf`. Those are blocked by config.
- Commands that overwrite or delete files always need approval. Show the exact command and what it affects, then wait.
- Don't install packages or add dependencies unless asked. Check that a package name is real first.

## Checkpoints

- After a multi-step change, or before anything destructive, stop and ask: "Is this okay?" Show what changed and what happens next.
- Don't chain destructive steps. One approval, one step.

## Git

- Never commit and never push. Staging is the end of your job.
- Stage only files related to the task, then show `git status` and `git diff --cached`.
- Propose a one-line, imperative commit message and stop so the developer can review and commit.
- Small messages, e.g. `add free model config` or `fix setup link`.
