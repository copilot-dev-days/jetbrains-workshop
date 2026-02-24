# Explore the project

## Scenario

Before adding a larger feature, you need to understand how PetClinic is structured: where controllers live, how data is stored, and how pages are rendered.

This exercise focuses on **getting context** and asking high-signal questions.

## Use Copilot Chat to understand the codebase

1. Close extra tabs in IntelliJ to reduce accidental context.
2. Open Copilot Chat.
   - If you have a model selector, choose a newer model.
   - If you’re on a free plan, select **GPT-5 mini** (it’s included with the account).
3. Start a new chat.
4. Ask questions like:
   - If you have a model selector, you can switch to **GPT-5 mini** for this step as well.

   - “What are the main packages and what does each one do?”
   - “Where are the controllers that render web pages?”
   - “Where is the database schema/data defined for the default H2 database?”
   - “How do owners, pets, and visits relate?”
   - “Where would I add a new feature that introduces new pages + database tables?”

> [!TIP]
> If your Copilot Chat supports scoping to the project/workspace, use it for questions like “find me the controller that…”. Otherwise, paste class names and ask for navigation hints.

## What you should discover

By the end, you should be able to answer:

- How the app is launched (Maven/Gradle wrapper)
- What MVC looks like in this project (controllers + Thymeleaf templates)
- Where JPA entities and repositories live
- How database initialization works for H2

## Summary and next steps

You now have the context to make larger changes safely. Next you’ll teach Copilot more about your repo by adding **Copilot instructions**, including more specialized custom instructions.

| [← Add a simple endpoint](./01-add-endpoint.md) | [Next: Copilot instructions →](./03-copilot-instructions.md) |
|:----------------------------------------------|------------------------------------------------------------:|
