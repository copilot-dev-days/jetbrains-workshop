<!-- l10n-sync: source-file="04-add-feature.md" -->
# Agregar una página "Adopt Me" (Agent Mode)

## Escenario

PetClinic gestiona visitas veterinarias, pero la clínica también quiere ayudar a la comunidad con la adopción de mascotas.

En este ejercicio, agregarás una **página única y sencilla renderizada en el servidor** y una pestaña de navegación:

- Una nueva pestaña llamada **Adopt Me** (junto a "Find Owners")
- Una nueva página llamada **Adoption** que muestra una pequeña tabla de mascotas y un botón **Adopt Me** por fila

Esto es intencionalmente "pequeño" para que Copilot pueda tener éxito de forma confiable.

## Contexto: por qué este es un ejercicio de Agent Mode

Aunque esta funcionalidad es pequeña, abarca múltiples archivos (controlador + plantilla Thymeleaf + navegación). Esto la convierte en una buena candidata para **Agent Mode**, porque puedes describir el resultado (criterios de aceptación) y dejar que Copilot itere entre archivos.

## Usar Agent Mode

### Qué significa "Agent Mode"

Agent Mode está diseñado para **tareas de codificación de múltiples pasos**. En lugar de solo responder preguntas o aplicar una única edición, el agente puede:

- Identificar archivos relevantes (y solicitar más contexto cuando sea necesario)
- Proponer y aplicar cambios en múltiples archivos
- Sugerir (y a veces ejecutar) comandos de terminal como formateo, compilación y pruebas
- Iterar basándose en errores (salida de compilación/pruebas) hasta alcanzar el objetivo

La idea clave: das un objetivo y restricciones, y el agente trabaja en un ciclo (planificar → editar → validar → ajustar), mientras tú mantienes el control.

Si deseas más información, consulta: https://docs.github.com/en/copilot/how-tos/chat-with-copilot/chat-in-ide?tool=jetbrains#agent-mode-1

### Cómo usarlo de forma segura

- Prefiere **Agent Mode** para trabajo abierto y entre archivos como esta funcionalidad; usa **Edit** para cambios pequeños y acotados.
- Revisa cada diff propuesto como lo harías con un PR.
- Trata los comandos de terminal como de alto impacto: ejecútalos intencionalmente (especialmente cualquier cosa que instale dependencias o cambie el formateo).
- Itera: si el resultado está cerca pero no es correcto, pide una corrección y vuelve a ejecutar las pruebas.

En esta parte, usa **Copilot Agent Mode** (si tu interfaz de Copilot for JetBrains lo expone), y selecciona un modelo más reciente si es posible. (por ejemplo, GPT-5 mini)

- Si ves un selector de modo como **Ask / Edit / Agent**: elige **Agent**.
- Si tu cliente de Copilot para JetBrains aún no tiene Agent Mode, usa el mismo prompt pero trabaja de forma iterativa:
  - haz que Copilot proponga un plan
  - aplica los cambios en partes más pequeñas
  - ejecuta las pruebas entre cada parte

> [!IMPORTANT]
> Incluso en Agent Mode, tú eres responsable de revisar los diffs y validar la aplicación.

## Criterios de aceptación (mantenlo mínimo)

Usa los criterios de aceptación de esta página como tu **fuente de verdad** y tu lista de verificación para la revisión.

En Agent Mode, también enviarás un prompt (siguiente sección) que resume estos requisitos para que Copilot pueda ejecutarlos.

### Navegación en la interfaz

- Agrega un elemento de navegación de nivel superior: **Adopt Me**.
- Colócalo junto a la pestaña existente **Find Owners** (justo después de ella).
- La funcionalidad debe usar páginas renderizadas en el servidor (Thymeleaf), consistente con PetClinic.

### Página de adopción

- Una nueva página llamada **Adoption** servida en `GET /adoption`.
- Un párrafo descriptivo en la parte superior haciendo un llamado a la adopción de mascotas, escrito en **primera persona**.

### Tabla

- Una tabla con estas columnas:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (botón)

### Botón Adopt Me

- Cada fila tiene un botón **Adopt Me**.
- Al hacer clic, marca esa mascota como adoptada y redirige de vuelta a `/adoption`.
- Si una mascota ya está adoptada, el botón aparece gris y no es clicable (deshabilitado).

### Restricciones

- Mantenlo mínimo: **sin base de datos/JPA**, sin repositorio, sin migraciones.
- Mantén los datos en memoria (por ejemplo, una lista de 3 mascotas).

## Guía de ejecución

- Iniciar la aplicación (desde la raíz de tu clon de PetClinic):
  - macOS/Linux (y Git Bash en Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`
- Ejecutar pruebas (desde la raíz de tu clon de PetClinic):
  - `./mvnw test`

## Prompt para el agente

### ¿Cuál debes seguir?

- Los **criterios de aceptación en este archivo** son la lista de verificación canónica de lo que estás construyendo.
- El **archivo de prompt** es un punto de partida fácil de copiar/pegar para darle a Copilot los mismos requisitos en un solo mensaje.

Si hay alguna discrepancia, actualiza el prompt (o reenvía un prompt corregido) para que coincida con los criterios de aceptación anteriores.

### Envía esto a Agent Mode

Abre el archivo de prompt y pégalo en Agent Mode:

- [../prompts/agent-add-adoptions.md](./prompts/agent-add-adoptions.md)

Si deseas un "mensaje único" explícito para copiar/pegar, usa este (y ajústalo según sea necesario):

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
> No trates el prompt como algo mágico. Léelo, edítalo y agrega restricciones según lo que desees.

## Resumen y próximos pasos

## Verificar

Después de que el agente termine (o hayas completado el trabajo de forma iterativa), realiza una verificación rápida.

### Ejecutar la aplicación

- Inicia la aplicación (desde la raíz de tu clon de PetClinic):
  - macOS/Linux (y Git Bash en Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`

### Verificar la funcionalidad de extremo a extremo

- Abre la aplicación en un navegador (normalmente `http://localhost:8080`).
- Confirma que hay un elemento de navegación de nivel superior **Adopt Me** junto a **Find Owners**.
- Abre `/adoption` y verifica el título de la página y el párrafo en primera persona.
- Verifica que la tabla muestre cat/dog/snake.
- Haz clic en **Adopt Me** en una fila y verifica que se deshabilite al regresar a la página.

### Ejecutar pruebas

- Ejecuta las pruebas (desde la raíz de tu clon de PetClinic): `./mvnw test`

Si las pruebas fallan, pide a Copilot que corrija los fallos manteniendo intactos los criterios de aceptación.

Has usado Agent Mode (o un flujo de trabajo similar al de un agente) para agregar una funcionalidad real de múltiples archivos. A continuación hay un ejercicio de bonificación que combina Agent Mode con instrucciones personalizadas más estrictas.
