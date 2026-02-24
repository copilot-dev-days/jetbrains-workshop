# Prompt: Extend “Adopt Me” with custom instructions

Context:
- Application code is in the repository root.
- Follow repository instructions and specialized instructions under `.github/instructions/`.

Precondition:
- The simplified “Adopt Me” feature already exists (nav tab + `GET /adoption` page with an in-memory list of 3 pets and an adopt button that disables after adopting).

Task:
1) Add a minimal filter on the Adoption page:
- Support an optional query param: `species` with values `cat`, `dog`, or `snake`.
- When provided, only show matching pets in the table.
- When not provided, show all pets.
- Keep this server-rendered (no JS filtering).

2) Add a minimal “Undo adopt” capability:
- For adopted pets, show an "Undo" button (or "Unadopt") in the Adopt Me column.
- Implement as a POST endpoint (POST-redirect-GET) and redirect back to `/adoption`.
- Do not introduce persistence; keep using in-memory state.

Constraints:
- Keep it consistent with PetClinic patterns.
- Do not add new dependencies.
- Keep UI changes minimal and accessible.

Process:
- Propose a short plan.
- Implement incrementally.
- Run `./mvnw test` and fix failures.
