<!-- l10n-sync: source-file="prompts/agent-add-adoptions.md" -->
# Prompt: Agregar una pestaña "Adopt Me" + página de Adoption (PetClinic)

Estás trabajando en un clon local de Spring PetClinic (raíz del repositorio).

Objetivo: Agregar una nueva pestaña de navegación de nivel superior llamada "Adopt Me" que enlace a una nueva página renderizada en el servidor llamada "Adoption".

Mantén esto intencionalmente simple:
- Usa Spring MVC + Thymeleaf (sin SPA).
- Evita agregar bases de datos, entidades JPA, repositorios o migraciones.
- Evita agregar pruebas para esta tarea.
- Mantén los cambios mínimos y consistentes con los patrones existentes de PetClinic (plantillas, layout, navegación).

Criterios de aceptación:
1) Navegación
- Agrega una entrada de navegación llamada "Adopt Me".
- Colócala junto a la pestaña existente "Find Owners" (justo después de ella).

2) Nueva página
- Crea una nueva página titulada "Adoption".
- Ruta: `GET /adoption` (página Thymeleaf renderizada en el servidor).

3) Párrafo descriptivo
- Agrega un párrafo corto en la parte superior haciendo un llamado a la adopción de mascotas.
- Escríbelo en primera persona ("I", "we", "our"), por ejemplo: "We're looking for loving homes...".

4) Contenido de la tabla
- En la página de Adoption, renderiza una tabla con estas columnas:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (un botón)

5) Comportamiento del botón Adopt
- Cada fila tiene un botón "Adopt Me".
- Al hacer clic, debe marcar esa mascota como adoptada y redirigir de vuelta a `/adoption`.
- Si una mascota ya está adoptada, renderiza el botón gris y no clicable (deshabilitado).

Guía de implementación (mantener mínimo):
- Usa una lista en memoria de 3 mascotas (un gato, un perro, una serpiente) almacenada en el controlador/servicio (sin persistencia).
- Usa un id estable por mascota para que la acción de adoptar pueda apuntar a una fila específica.
- Implementa la adopción como un endpoint `POST /adoption/{id}/adopt` (POST-redirect-GET).
- Usa las clases CSS/Bootstrap existentes de PetClinic; no introduzcas nuevos sistemas de estilos.

Flujo de trabajo:
1) Encuentra cómo PetClinic define la plantilla de navegación superior y agrega "Adopt Me" junto a "Find Owners".
2) Agrega un pequeño controlador y una plantilla Thymeleaf para la página de Adoption.
3) Ejecuta la aplicación y verifica la pestaña, la página, la tabla y el estado del botón deshabilitado.

Formateo:
- Después de los cambios de código, ejecuta el formateador del proyecto (por ejemplo, `spring-javaformat:apply` si está configurado).
