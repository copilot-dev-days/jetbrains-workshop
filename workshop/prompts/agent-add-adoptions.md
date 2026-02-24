# Prompt: Add an “Adopt Me” tab + Adoption page (PetClinic)

You are working in a local clone of Spring PetClinic (repository root).

Goal: Add a new top-level navigation tab called "Adopt Me" that links to a new server-rendered page called "Adoption".

Keep this intentionally simple:
- Use Spring MVC + Thymeleaf (no SPA).
- Avoid adding databases, JPA entities, repositories, or migrations.
- Avoid adding tests for this task.
- Keep changes minimal and consistent with existing PetClinic patterns (templates, layout, navigation).

Acceptance criteria:
1) Navigation
- Add a nav entry named "Adopt Me".
- Place it next to the existing "Find Owners" tab (right after it).

2) New page
- Create a new page titled "Adoption".
- Route: `GET /adoption` (server-rendered Thymeleaf page).

3) Description paragraph
- Add a short paragraph at the top calling for pet adoption.
- Write it in first-person point of view ("I", "we", "our"), e.g. "We’re looking for loving homes...".

4) Table of content
- On the Adoption page, render a table with these columns:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (a button)

5) Adopt button behavior
- Each row has an "Adopt Me" button.
- When clicked, it should mark that pet as adopted and redirect back to `/adoption`.
- If a pet is already adopted, render the button greyed out and not clickable (disabled).

Implementation guidance (keep minimal):
- Use an in-memory list of 3 pets (one cat, one dog, one snake) stored in the controller/service (no persistence).
- Use a stable id per pet so the adopt action can target a specific row.
- Implement adopt as a `POST /adoption/{id}/adopt` endpoint (POST-redirect-GET).
- Use existing CSS/Bootstrap classes from PetClinic; do not introduce new styling systems.

Workflow:
1) Find how PetClinic defines the top nav template and add "Adopt Me" next to "Find Owners".
2) Add a small controller and a Thymeleaf template for the Adoption page.
3) Run the app and verify the tab, page, table, and disabled button state.

Formatting:
- After code changes, run the project’s formatter (e.g. `spring-javaformat:apply` if configured).
