<!-- l10n-sync: source-file="03-copilot-instructions.md" -->
# Proporcionar instrucciones personalizadas

Siempre hay piezas clave de información que cualquier persona que genere código para tu base de código necesita conocer: estructura del proyecto, convenciones y "cómo hacemos las cosas aquí". Dado que el contexto es tan importante para un asistente de codificación con IA, podemos proporcionar parte de esa información a través de las **instrucciones de Copilot**.

## Escenario

Antes de comenzar actualizaciones más grandes a PetClinic con la ayuda de Copilot, queremos asegurarnos de que Copilot tenga una buena comprensión de cómo queremos que se escriba el código.

En este ejercicio:

- ejecutarás un prompt de "línea base" y observarás el resultado
- agregarás instrucciones de Copilot a nivel de workspace en `.github/copilot-instructions.md`
- ejecutarás el mismo prompt de nuevo y observarás cómo cambia Copilot
- mantendrás (y extenderás) instrucciones especializadas en `.github/instructions/`

## Descripción general de las instrucciones de Copilot

Las instrucciones de Copilot se encuentran en un archivo markdown ubicado en `.github/copilot-instructions.md`. Se convierte en parte de tu proyecto y se utiliza para guiar Copilot Chat.

> [!IMPORTANT]
> Mantén este archivo corto y enfocado en guías de todo el proyecto. Si crece demasiado, puede desplazar el contexto de código que Copilot necesita.

## Paso 1: Pedir a Copilot que genere una función de línea base

1. En IntelliJ, cierra las pestañas adicionales del editor para reducir el contexto accidental.
2. Abre Copilot Chat e inicia un nuevo chat.
3. Envía este prompt:

	```
	Create a Java function to validate pet age between 0 and 25.
	Throw an error if it is outside this range.
	```

4. Observa el resultado.

> [!NOTE]
> En muchos casos, notarás que el código generado solo verifica que la edad sea **>= 0** y olvida el límite superior. Eso es esperado: este es exactamente el tipo de desviación que las instrucciones ayudan a corregir.

## Paso 2: Agregar `.github/copilot-instructions.md`

En tu clon local de Spring PetClinic, crea `.github/copilot-instructions.md`.

Establece su contenido como:

```markdown
# Copilot instructions

When adding a function that validates a pet's age, make sure it is between 0 and 25.
Add a short comment at the beginning of the function explaining what it validates.
```

Puedes agregar este archivo de dos maneras:

- Manualmente (creando el archivo en `.github/`), o
- A través de la configuración de IntelliJ:
  - **Settings → Tools → GitHub Copilot → Customizations**
  - Haz clic en **workspace** en **Copilot instructions**

## Paso 3: Probar el prompt de nuevo (y revisar las referencias)

1. Inicia una nueva sesión de Copilot Chat.
2. Envía el mismo prompt de nuevo:

	```
	Create a Java function to validate pet age.
	Ensure pet age is between 0 and 25.
	Throw an error if it is outside this range.
	```

3. En la interfaz de Copilot, abre el área de **references**.
4. Confirma que Copilot incorporó **1 referencia** del archivo de instrucciones.
5. Observarás que la función generada ahora incluye ambos límites y un comentario.

> [!TIP]
> Si no ves las instrucciones referenciadas, asegúrate de haber creado el archivo en el clon de PetClinic que tienes abierto en IntelliJ (no en el repositorio de documentación del taller).

## Paso 4: Instrucciones especializadas (consérvalas)

Además de `.github/copilot-instructions.md`, puedes agregar archivos de instrucciones especializadas en `.github/instructions/`. Estos son útiles cuando deseas una guía más detallada para un subconjunto de archivos (Java, tests, plantillas, etc.).

Conserva las secciones de instrucciones especializadas de este taller y agrega un ejemplo enfocado en Java. Por ejemplo, crea `.github/instructions/java-style.instructions.md` con:

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

## Inspiración: awesome-copilot

Si deseas ejemplos de buenos archivos de instrucciones (y prompts reutilizables), el repositorio curado por la comunidad https://github.com/github/awesome-copilot es un excelente lugar para obtener patrones.

## Resumen y próximos pasos

Has visto cómo las instrucciones cambian la salida de Copilot al proporcionar un contexto estable y específico del proyecto. A continuación construirás una nueva funcionalidad de adopción usando **Agent Mode**.
