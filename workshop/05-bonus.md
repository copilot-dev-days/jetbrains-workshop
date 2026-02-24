# Bonus: Agent Mode + custom instructions

## Goal

Practice a more realistic agent workflow:

1. tighten instructions (so the agent stays within your architecture)
2. run an agent prompt that requires multiple files and iterative verification

## Part A — Strengthen instructions

1. Open [../../.github/copilot-instructions.md](../.github/copilot-instructions.md)
2. Add a short “Do / Don’t” section, for example:
   - Do: follow PetClinic MVC patterns
   - Do: use POST-redirect-GET for state-changing actions (e.g., Adopt)
   - Don’t: introduce a separate frontend framework
   - Don’t: add new build tooling

3. Open specialized instructions in [../../.github/instructions/](../.github/instructions/) and adjust them to match your preferences.

## Part B — Run an agent prompt that depends on those instructions

Use this prompt file as a starting point:

- [../prompts/bonus-agent-custom-instructions.md](./prompts/bonus-agent-custom-instructions.md)

If your Copilot client supports Agent Mode, use it. Otherwise, do the same flow manually:

- Ask Copilot for a plan
- Apply changes in small commits (optional)
- Run `./mvnw test` between steps

## Extra challenges

If you finish early, try one of these (pick one):

- Add a simple filter on the Adoption page (e.g., query param `species=cat|dog|snake`)
- Add a one-click “Undo adopt” action (POST-redirect-GET) to re-enable the button
- Show a small success message after adopting (flash attribute)

## Wrap-up

The key idea: Agent Mode works best when you pair it with clear **constraints** (instructions) and a tight **feedback loop** (build/tests).
|:--------------------------------------------|----------------------------------------------:|
