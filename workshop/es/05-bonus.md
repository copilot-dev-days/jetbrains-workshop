<!-- l10n-sync: source-file="05-bonus.md" -->
# Bonus: Agent Mode + instrucciones personalizadas

## Objetivo

Practicar un flujo de trabajo con agente más realista:

1. reforzar las instrucciones (para que el agente se mantenga dentro de tu arquitectura)
2. ejecutar un prompt de agente que requiera múltiples archivos y verificación iterativa

## Parte A — Reforzar las instrucciones

1. Abre [../../.github/copilot-instructions.md](../.github/copilot-instructions.md)
2. Agrega una sección breve de "Hacer / No hacer", por ejemplo:
   - Hacer: seguir los patrones MVC de PetClinic
   - Hacer: usar POST-redirect-GET para acciones que cambian estado (por ejemplo, Adopt)
   - No hacer: introducir un framework frontend separado
   - No hacer: agregar nuevas herramientas de compilación

3. Abre las instrucciones especializadas en [../../.github/instructions/](../.github/instructions/) y ajústalas según tus preferencias.

## Parte B — Ejecutar un prompt de agente que dependa de esas instrucciones

Usa este archivo de prompt como punto de partida:

- [../prompts/bonus-agent-custom-instructions.md](./prompts/bonus-agent-custom-instructions.md)

Si tu cliente de Copilot admite Agent Mode, úsalo. De lo contrario, sigue el mismo flujo de forma manual:

- Pide a Copilot un plan
- Aplica los cambios en commits pequeños (opcional)
- Ejecuta `./mvnw test` entre pasos

## Desafíos adicionales

Si terminas antes, prueba uno de estos (elige uno):

- Agregar un filtro sencillo en la página de Adoption (por ejemplo, parámetro de consulta `species=cat|dog|snake`)
- Agregar una acción de "Deshacer adopción" con un clic (POST-redirect-GET) para reactivar el botón
- Mostrar un pequeño mensaje de éxito después de adoptar (flash attribute)

## Cierre

La idea clave: Agent Mode funciona mejor cuando lo combinas con **restricciones** claras (instrucciones) y un **ciclo de retroalimentación** estrecho (compilación/pruebas).
|:--------------------------------------------|----------------------------------------------:|
