<!-- l10n-sync: source-file="02-explore-project.md" -->
# Explorar el proyecto

## Escenario

Antes de agregar una funcionalidad más grande, necesitas comprender cómo está estructurado PetClinic: dónde se encuentran los controladores, cómo se almacenan los datos y cómo se renderizan las páginas.

Este ejercicio se centra en **obtener contexto** y hacer preguntas de alto valor.

## Usar Copilot Chat para comprender el código base

1. Cierra las pestañas adicionales en IntelliJ para reducir el contexto accidental.
2. Abre Copilot Chat.
   - Si tienes un selector de modelo, elige un modelo más reciente.
   - Si estás en un plan gratuito, selecciona **GPT-5 mini** (está incluido con la cuenta).
3. Inicia un nuevo chat.
4. Haz preguntas como:
   - Si tienes un selector de modelo, también puedes cambiar a **GPT-5 mini** para este paso.

   - "What are the main packages and what does each one do?"
   - "Where are the controllers that render web pages?"
   - "Where is the database schema/data defined for the default H2 database?"
   - "How do owners, pets, and visits relate?"
   - "Where would I add a new feature that introduces new pages + database tables?"

> [!TIP]
> Si tu Copilot Chat admite delimitar el alcance al proyecto/workspace, úsalo para preguntas como "find me the controller that…". De lo contrario, pega nombres de clases y pide pistas de navegación.

## Lo que deberías descubrir

Al finalizar, deberías poder responder:

- Cómo se lanza la aplicación (wrapper de Maven/Gradle)
- Cómo se ve MVC en este proyecto (controladores + plantillas Thymeleaf)
- Dónde se encuentran las entidades JPA y los repositorios
- Cómo funciona la inicialización de la base de datos para H2

## Resumen y próximos pasos

Ahora tienes el contexto para hacer cambios más grandes de forma segura. A continuación le enseñarás a Copilot más sobre tu repositorio agregando **instrucciones de Copilot**, incluyendo instrucciones personalizadas más especializadas.
