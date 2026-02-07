# Add a simple endpoint

## Scenario

PetClinic is primarily an MVC app (Thymeleaf + Spring MVC). For internal tooling and integrations, the clinic wants a **tiny JSON endpoint** that provides:

- current server time
- running Java version
- optional personalized message

This is intentionally small: it’s a good way to practice **Copilot code completion** and **small, safe changes**.

> [!NOTE]
> If the app stops working, check the terminal where you ran `spring-boot:run` for errors. Restart it if needed.

## Where you’ll work

All code changes happen in your local clone of Spring PetClinic.

You will create a new controller:

- package: `org.springframework.samples.petclinic.system.api`
- class: `ClinicInfoController`

## Create the endpoint (Copilot-assisted)

1. In IntelliJ, open your `spring-petclinic` project.
2. Create a new Java file:
   - `src/main/java/org/springframework/samples/petclinic/system/api/ClinicInfoController.java`
3. Use Copilot **code completion** to implement a `@RestController` with:
   - `@GetMapping("/api/clinic-info")`
   - response JSON containing:
     - `serverTime` (ISO-8601 string)
     - `javaVersion` (from `System.getProperty("java.version")`)
     - `message` (default: `"Welcome to PetClinic"`)
   - optional query parameter `name`:
     - when present, message becomes `"Welcome to PetClinic, <name>"`

### Function name + sample snippet

Use this function name for the handler:

- `getClinicInfo`

This is a sample implementation (you don't need to follow the exact implementation; type it to experience completions):

```java
package org.springframework.samples.petclinic.system.api;

import java.time.OffsetDateTime;
import java.util.LinkedHashMap;
import java.util.Map;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
class ClinicInfoController {

    @GetMapping("/api/clinic-info")
    Map<String, String> getClinicInfo(@RequestParam(required = false) String name) {
        Map<String, String> result = new LinkedHashMap<>();
        result.put("serverTime", OffsetDateTime.now().toString());
        result.put("javaVersion", System.getProperty("java.version"));
        String message = (name == null || name.isBlank()) ? "Welcome to PetClinic" : "Welcome to PetClinic, " + name;
        result.put("message", message);
        return result;
    }
}
```

> [!IMPORTANT]
> Type the code (don’t paste) so you experience completions.

### Suggested prompt (inline chat)

If you prefer using inline chat in the editor, ask Copilot something like:

```
Create a Spring Boot RestController at /api/clinic-info that returns serverTime, javaVersion, and a message. If query param name is provided, personalize the message.
```
You can access the Inline Chat feature by right‑clicking in the editor and selecting “Open Inline Chat.”
You can also open it using the shortcut Shift + Ctrl + I (Mac) or Shift + Ctrl + G (Windows).

## Validate the endpoint

1. Ensure the app is running.
2. Open:
   - http://localhost:8080/api/clinic-info
   - http://localhost:8080/api/clinic-info?name=Taylor

You should see JSON output.

> [!NOTE]
> After adding new code, the Maven wrapper may fail due to formatting rules (often after code completion). You might see an error like:
>
> ```
> spring-petclinic: Formatting violations found in the following files:
> [ERROR]  * C:\dev\spring-petclinic\src\main\java\org\springframework\samples\petclinic\system\ClinicController.java
> [ERROR]
> [ERROR] Run `spring-javaformat:apply` to fix.
> ```
>
> Fix it by running this from the PetClinic repo root:
> - macOS/Linux (and Git Bash): `./mvnw spring-javaformat:apply`
> - Windows PowerShell: `.\mvnw.cmd spring-javaformat:apply`

## Summary and next steps

You added a small endpoint and validated it end-to-end. Next you’ll explore the project structure using Copilot Chat to build context for larger changes.

| [← Workshop setup](./0-setup.md) | [Next: Explore the project →](./2-explore-project.md) |
|:--------------------------------|------------------------------------------------------:|
