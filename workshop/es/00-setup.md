<!-- l10n-sync: source-file="00-setup.md" -->
# Configuración del taller

Para completar este taller clonarás Spring PetClinic, lo ejecutarás localmente, lo abrirás en IntelliJ IDEA y habilitarás GitHub Copilot.

> [!IMPORTANT]
> El código fuente de PetClinic **no** está incluido en este repositorio del taller.
> Trabajarás en un clon local de: https://github.com/spring-projects/spring-petclinic

## Recursos necesarios

- Una cuenta de GitHub
- Acceso a GitHub Copilot

## Instalación local requerida

### IDE

- IntelliJ IDEA (Community o Ultimate)
- Plugin de GitHub Copilot instalado e iniciada la sesión (puedes descargar el plugin yendo a Settings→ Plugins→ Marketplace)

### Servicios locales

- Git (CLI)
- Java 17+

## Clonar Spring PetClinic

Clona el repositorio upstream de PetClinic:

```sh
git clone https://github.com/spring-projects/spring-petclinic.git
cd spring-petclinic
```

> [!TIP]
> Si deseas subir tus cambios a tu propio repositorio de GitHub durante el taller, primero haz un fork del repositorio de PetClinic y clona tu fork en su lugar.

## Ejecutar la aplicación

Desde la carpeta `spring-petclinic`, inicia PetClinic:

- macOS / Linux:

  ```sh
  ./mvnw spring-boot:run
  ```

- Windows (PowerShell):

  ```powershell
  .\mvnw.cmd spring-boot:run

> [!NOTE]
> Si estás usando Git Bash en Windows, prefiere `./mvnw spring-boot:run` (no `mvnw.cmd`).
  ```

Abre la aplicación en tu navegador: http://localhost:8080

## Abrir el proyecto en IntelliJ

1. Abre IntelliJ IDEA.
2. Selecciona **File → Open…**
3. Elige la carpeta `spring-petclinic` que clonaste y ábrela como proyecto.
4. Si se te solicita, confía en el proyecto y permite que el IDE importe Maven/Gradle.

## Verificar que Copilot está activo

1. Abre **Copilot Chat** (ventana de herramientas).
2. Inicia un nuevo chat.
3. Pregunta: "Explain what this repository is and how I run it locally."

> [!TIP]
> Si Copilot no puede ver el proyecto, confirma que has iniciado sesión en GitHub en el plugin de Copilot y que el proyecto ha terminado de indexarse.

## Resumen y próximos pasos

Ahora tienes PetClinic en ejecución y el proyecto abierto en IntelliJ. A continuación agregarás un pequeño endpoint para practicar la codificación asistida por Copilot.
