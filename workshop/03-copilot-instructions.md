# Providing custom instructions

There are always key pieces of information anyone generating code for your codebase needs to know: project structure, conventions, and “how we do things here”. Since context is so important for an AI coding assistant, we can provide some of that information via **Copilot instructions**.

## Scenario

Before we begin larger updates to PetClinic with the help of Copilot, we want to ensure Copilot has a good understanding of how we want code to be written.

In this exercise you will:

- run a “baseline” prompt and observe the result
- add workspace-level Copilot instructions in `.github/copilot-instructions.md`
- run the same prompt again and observe how Copilot changes
- keep (and extend) specialized instructions under `.github/instructions/`

## Overview of Copilot instructions

Copilot instructions live in a markdown file placed in `.github/copilot-instructions.md`. It becomes part of your project and is used to guide Copilot Chat.

> [!IMPORTANT]
> Keep this file short and focused on project-wide guidance. If it grows too large, it can crowd out the code context Copilot needs.

## Step 1: Ask Copilot to generate a baseline function

1. In IntelliJ, close extra editor tabs to reduce accidental context.
2. Open Copilot Chat and start a new chat.
3. Send this prompt:

	```
	Create a Java function to validate pet age between 0 and 25.
	Throw an error if it is outside this range.
	```

4. Observe the result.

> [!NOTE]
> In many cases, you’ll notice the generated code only checks that age is **>= 0** and forgets the upper bound. That’s expected: this is exactly the kind of drift instructions help correct.

## Step 2: Add `.github/copilot-instructions.md`

In your local clone of Spring PetClinic, create `.github/copilot-instructions.md`.

Set its content to:

```markdown
# Copilot instructions

When adding a function that validates a pet's age, make sure it is between 0 and 25.
Add a short comment at the beginning of the function explaining what it validates.
```

You can add this file either:

- Manually (create the file under `.github/`), or
- Via IntelliJ settings:
  - **Settings → Tools → GitHub Copilot → Customizations**
  - Click on **workspace** under **Copilot instructions**

## Step 3: Try the prompt again (and check references)

1. Start a new Copilot Chat session.
2. Send the same prompt again:

	```
	Create a Java function to validate pet age.
	Ensure pet age is between 0 and 25.
	Throw an error if it is outside this range.
	```

3. In the Copilot UI, open the **references** area.
4. Confirm that Copilot pulled in **1 reference** from the instructions file.
5. You will observe that the generated function now includes both bounds and a comment.

> [!TIP]
> If you don’t see the instructions referenced, make sure you created the file in the PetClinic clone you have open in IntelliJ (not in this workshop-docs repo).

## Step 4: Specialized instructions (keep these)

In addition to `.github/copilot-instructions.md`, you can add specialized instruction files under `.github/instructions/`. These are useful when you want deeper guidance for a subset of files (Java, tests, templates, etc.).

Keep the specialized instructions sections from this workshop and add a Java-focused example. For example, create `.github/instructions/java-style.instructions.md` with:

```markdown
---
applyTo: "**/*.java"
---

# Java style

- Write comments at the beginning of each class and functions explaining their purpose.
- Prefer Spring MVC + Thymeleaf patterns in PetClinic (use `@Controller` for pages).
- Only use `@RestController` for JSON endpoints (like `/api/...`).
- Prefer constructor injection for Spring components.
- When accepting user input, prefer Bean Validation (e.g., `@Valid` + constraint annotations).
```

## Inspiration: awesome-copilot

If you want examples of good instruction files (and reusable prompts), the community-curated https://github.com/github/awesome-copilot repo is a great place to pull patterns from.

## Summary and next steps

You’ve seen how instructions change Copilot’s output by providing stable, project-specific context. Next you’ll build a new adoption feature using **Agent Mode**.

| [← Explore the project](./02-explore-project.md) | [Next: Add adoption feature (Agent Mode) →](./04-add-feature.md) |
|:-----------------------------------------------|----------------------------------------------------------------:|
