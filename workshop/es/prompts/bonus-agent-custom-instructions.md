<!-- l10n-sync: source-file="prompts/bonus-agent-custom-instructions.md" -->
# Prompt: Extender "Adopt Me" con instrucciones personalizadas

Contexto:
- El código de la aplicación está en la raíz del repositorio.
- Sigue las instrucciones del repositorio y las instrucciones especializadas en `.github/instructions/`.

Precondición:
- La funcionalidad simplificada de "Adopt Me" ya existe (pestaña de navegación + página `GET /adoption` con una lista en memoria de 3 mascotas y un botón de adoptar que se deshabilita después de adoptar).

Tarea:
1) Agregar un filtro mínimo en la página de Adoption:
- Admite un parámetro de consulta opcional: `species` con valores `cat`, `dog` o `snake`.
- Cuando se proporciona, muestra solo las mascotas que coincidan en la tabla.
- Cuando no se proporciona, muestra todas las mascotas.
- Mantén esto renderizado en el servidor (sin filtrado con JS).

2) Agregar una capacidad mínima de "Deshacer adopción":
- Para mascotas adoptadas, muestra un botón "Undo" (o "Unadopt") en la columna Adopt Me.
- Implementa como un endpoint POST (POST-redirect-GET) y redirige de vuelta a `/adoption`.
- No introduzcas persistencia; sigue usando estado en memoria.

Restricciones:
- Mantén la consistencia con los patrones de PetClinic.
- No agregues nuevas dependencias.
- Mantén los cambios de interfaz mínimos y accesibles.

Proceso:
- Propón un plan breve.
- Implementa de forma incremental.
- Ejecuta `./mvnw test` y corrige los fallos.
