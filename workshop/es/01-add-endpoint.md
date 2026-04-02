<!-- l10n-sync: source-file="01-add-endpoint.md" -->
# Agregar un endpoint sencillo

## Escenario

PetClinic es principalmente una aplicación MVC (Thymeleaf + Spring MVC). Para herramientas internas e integraciones, la clínica necesita un **pequeño endpoint JSON** que proporcione:

- hora actual del servidor
- versión de Java en ejecución
- mensaje personalizado opcional

Esto es intencionalmente pequeño: es una buena manera de practicar el **autocompletado de código con Copilot** y realizar **cambios pequeños y seguros**.

> [!NOTE]
> Si la aplicación deja de funcionar, revisa la terminal donde ejecutaste `spring-boot:run` en busca de errores. Reiníciala si es necesario.

## Dónde trabajarás

Todos los cambios de código se realizan en tu clon local de Spring PetClinic.

Crearás un nuevo controlador:

- paquete: `org.springframework.samples.petclinic.system.api`
- clase: `ClinicInfoController`

## Crear el endpoint (asistido por Copilot)

1. En IntelliJ, abre tu proyecto `spring-petclinic`.
2. Crea un nuevo archivo Java:
   - `src/main/java/org/springframework/samples/petclinic/system/api/ClinicInfoController.java`
3. Usa el **autocompletado de código** de Copilot para implementar un `@RestController` con:
   - `@GetMapping("/api/clinic-info")`
   - respuesta JSON que contenga:
     - `serverTime` (cadena ISO-8601)
     - `javaVersion` (de `System.getProperty("java.version")`)
     - `message` (por defecto: `"Welcome to PetClinic"`)
   - parámetro de consulta opcional `name`:
     - cuando esté presente, el mensaje se convierte en `"Welcome to PetClinic, <name>"`

### Nombre de la función + fragmento de ejemplo

Usa este nombre de función para el handler:

- `getClinicInfo`

Esta es una implementación de ejemplo (no es necesario seguir la implementación exacta; escríbela para experimentar las sugerencias de autocompletado):

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
> Escribe el código (no lo pegues) para que puedas experimentar las sugerencias de autocompletado.

### Prompt sugerido (chat en línea)

Si prefieres usar el chat en línea dentro del editor, pide a Copilot algo como:

```
Create a Spring Boot RestController at /api/clinic-info that returns serverTime, javaVersion, and a message. If query param name is provided, personalize the message.
```
Puedes acceder a la función de Inline Chat haciendo clic derecho en el editor y seleccionando "Open Inline Chat."
También puedes abrirlo usando el atajo Shift + Ctrl + I (Mac) o Shift + Ctrl + G (Windows).

## Validar el endpoint

1. Asegúrate de que la aplicación esté en ejecución.
2. Abre:
   - http://localhost:8080/api/clinic-info
   - http://localhost:8080/api/clinic-info?name=Taylor

Deberías ver una salida JSON.

> [!NOTE]
> Después de agregar código nuevo, el wrapper de Maven puede fallar debido a reglas de formato (frecuentemente después del autocompletado de código). Podrías ver un error como:
>
> ```
> spring-petclinic: Formatting violations found in the following files:
> [ERROR]  * C:\dev\spring-petclinic\src\main\java\org\springframework\samples\petclinic\system\ClinicController.java
> [ERROR]
> [ERROR] Run `spring-javaformat:apply` to fix.
> ```
>
> Corrígelo ejecutando esto desde la raíz del repositorio de PetClinic:
> - macOS/Linux (y Git Bash): `./mvnw spring-javaformat:apply`
> - Windows PowerShell: `.\mvnw.cmd spring-javaformat:apply`

## Resumen y próximos pasos

Agregaste un pequeño endpoint y lo validaste de extremo a extremo. A continuación explorarás la estructura del proyecto usando Copilot Chat para construir contexto para cambios más grandes.
