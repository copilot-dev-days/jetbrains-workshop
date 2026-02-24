# Workshop setup

To complete this workshop you will clone Spring PetClinic, run it locally, open it in IntelliJ IDEA, and enable GitHub Copilot.

> [!IMPORTANT]
> The PetClinic source code is **not** included in this workshop repository.
> You will work in a local clone of: https://github.com/spring-projects/spring-petclinic

## Required resources

- A GitHub account
- Access to GitHub Copilot

## Required local installation

### IDE

- IntelliJ IDEA (Community or Ultimate)
- GitHub Copilot plugin installed and signed in (You can  download the plugin by going to Settings-> Plugins-> Marketplace)

### Local services

- Git (CLI)
- Java 17+

## Clone Spring PetClinic

Clone the upstream PetClinic repository:

```sh
git clone https://github.com/spring-projects/spring-petclinic.git
cd spring-petclinic
```

> [!TIP]
> If you want to push your changes to your own GitHub repo during the workshop, fork the PetClinic repo first and clone your fork instead.

## Run the application

From the `spring-petclinic` folder, start PetClinic:

- macOS / Linux:

  ```sh
  ./mvnw spring-boot:run
  ```

- Windows (PowerShell):

  ```powershell
  .\mvnw.cmd spring-boot:run

> [!NOTE]
> If you are using Git Bash on Windows, prefer `./mvnw spring-boot:run` (not `mvnw.cmd`).
  ```

Open the app in your browser: http://localhost:8080

## Open the project in IntelliJ

1. Open IntelliJ IDEA.
2. Select **File → Open…**
3. Choose the `spring-petclinic` folder you cloned and open it as a project.
4. If prompted, trust the project and allow the IDE to import Maven/Gradle.

## Verify Copilot is active

1. Open **Copilot Chat** (tool window).
2. Start a new chat.
3. Ask: “Explain what this repository is and how I run it locally.”

> [!TIP]
> If Copilot can’t see the project, confirm you’re signed into GitHub in the Copilot plugin and the project has finished indexing.

## Summary and next steps

You now have PetClinic running and the project open in IntelliJ. Next you’ll add a small endpoint to practice Copilot-assisted coding.

| [← Getting started](./README.md) | [Next: Add a simple endpoint →](./01-add-endpoint.md) |
|:--------------------------------|-----------------------------------------------------:|
