# Add an “Adopt Me” page (Agent Mode)

## Scenario

PetClinic handles veterinary visits, but the clinic also wants to help the community with pet adoption.

In this exercise, you’ll add a **single, simple server-rendered page** and a nav tab:

- A new tab called **Adopt Me** (next to “Find Owners”)
- A new page called **Adoption** that shows a small table of pets and an **Adopt Me** button per row

This is intentionally “small” so Copilot can succeed reliably.

## Background: why this is an Agent Mode exercise

Even though this feature is small, it still spans multiple files (controller + Thymeleaf template + navigation). That makes it a good fit for **Agent Mode**, because you can describe the outcome (acceptance criteria) and let Copilot iterate across files.

## Use Agent Mode

### What “Agent Mode” means

Agent Mode is designed for **multi-step coding tasks**. Instead of only answering questions or applying a single edit, the agent can:

- Identify relevant files (and ask for more context when needed)
- Propose and apply changes across multiple files
- Suggest (and sometimes run) terminal commands like formatting, builds, and tests
- Iterate based on errors (compile/test output) until it reaches the goal

The key idea: you give a goal and constraints, and the agent works in a loop (plan → edit → validate → adjust), while you stay in control.

If you want more background, see: https://docs.github.com/en/copilot/how-tos/chat-with-copilot/chat-in-ide?tool=jetbrains#agent-mode-1

### How to use it safely

- Prefer **Agent Mode** for open-ended, cross-file work like this feature; use **Edit** for small, scoped changes.
- Review each proposed diff like you would a PR.
- Treat terminal commands as high-impact: run them intentionally (especially anything that installs dependencies or changes formatting).
- Iterate: if the result is close but not right, ask for a correction and rerun tests.

In this part, use **Copilot Agent Mode** (if your Copilot for JetBrains UI exposes it), and select a newer model if possible. (e.g. GPT-5 mini)

- If you see a mode selector like **Ask / Edit / Agent**: choose **Agent**.
- If your JetBrains Copilot client does not have Agent Mode yet, use the same prompt but work iteratively:
  - have Copilot propose a plan
  - apply changes in smaller chunks
  - run tests between chunks

> [!IMPORTANT]
> Even in Agent Mode, you are responsible for reviewing the diffs and validating the app.

## Acceptance criteria (keep it minimal)

Use the acceptance criteria on this page as your **source of truth** and your review checklist.

In Agent Mode, you’ll also send a prompt (next section) that summarizes these requirements so Copilot can execute against them.

### UI navigation

- Add a top-level navigation item: **Adopt Me**.
- Place it next to the existing **Find Owners** tab (right after it).
- The feature should use server-rendered pages (Thymeleaf), consistent with PetClinic.

### Adoption page

- A new page called **Adoption** served at `GET /adoption`.
- A description paragraph at the top calling for pet adoption, written in **first person**.

### Table

- A table with these columns:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (button)

### Adopt Me button

- Each row has an **Adopt Me** button.
- When clicked, it marks that pet as adopted and redirects back to `/adoption`.
- If a pet is already adopted, the button is greyed out and not clickable (disabled).

### Constraints

- Keep it minimal: **no database/JPA**, no repository, no migrations.
- Keep data in-memory (e.g., a list of 3 pets).

## Runbook

- Start the app (from the root of your PetClinic clone):
  - macOS/Linux (and Git Bash on Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`
- Run tests (from the root of your PetClinic clone):
  - `./mvnw test`

## Agent prompt

### Which should you follow?

- The **acceptance criteria in this file** is the canonical checklist for what you’re building.
- The **prompt file** is a copy/paste-friendly starting point to give Copilot the same requirements in one message.

If there’s any mismatch, update the prompt (or re-send a corrected prompt) so it matches the acceptance criteria above.

### Send this to Agent Mode

Open the prompt file and paste it into Agent Mode:

- [../prompts/agent-add-adoptions.md](./prompts/agent-add-adoptions.md)

If you want an explicit “single message” to copy/paste, use this (and adjust as needed):

```text
You are working in a local clone of Spring PetClinic (repository root).

Goal: Implement the "Adopt Me" tab + "Adoption" page described by the acceptance criteria in workshop/04-add-feature.md.

Constraints:
- Keep changes small and consistent with PetClinic patterns.
- Prefer server-rendered pages (Thymeleaf), not a SPA.
- Do NOT add persistence (no JPA, no repositories, no migrations).
- Do NOT add tests for this task.

Workflow:
1) Inspect existing PetClinic patterns for navigation + Thymeleaf pages.
2) Propose a short plan.
3) Implement incrementally.
4) Run the app and verify the behavior matches acceptance criteria.
```

> [!TIP]
> Don’t treat the prompt as magic. Read it, edit it, and add constraints based on what you want.

## Summary and next steps

## Verify

After the agent finishes (or you’ve completed the work iteratively), do a quick verification pass.

### Run the app

- Start the app (from the root of your PetClinic clone):
  - macOS/Linux (and Git Bash on Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`

### Check the feature end-to-end

- Open the app in a browser (usually `http://localhost:8080`).
- Confirm there is a top-level nav item **Adopt Me** next to **Find Owners**.
- Open `/adoption` and verify the page title and first-person paragraph.
- Verify the table shows cat/dog/snake.
- Click **Adopt Me** for a row and verify it becomes disabled when you return to the page.

### Run tests

- Run tests (from the root of your PetClinic clone): `./mvnw test`

If tests fail, ask Copilot to fix the failures while keeping the acceptance criteria intact.

You’ve used Agent Mode (or an agent-like workflow) to add a real multi-file feature. Next is a bonus exercise combining Agent Mode with tighter custom instructions.


