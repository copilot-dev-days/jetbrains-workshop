<!-- l10n-sync: source-file="README.md" -->
# GitHub Copilot para JetBrains Workshop

Este repositório é um workshop prático para aprender GitHub Copilot **no IntelliJ IDEA** (Copilot for JetBrains), utilizando a aplicação **Spring PetClinic**.

Os materiais do workshop estão em [workshop/README.md](workshop/pt_BR/README.md).

## Estrutura do repositório

- [workshop/](workshop/pt_BR/) — instruções do workshop e prompts reutilizáveis
- [.github/copilot-instructions.md](.github/copilot-instructions.md) — exemplo de instruções do Copilot que você pode copiar para o seu clone do PetClinic

## Pré-requisitos

- Uma conta GitHub com acesso ao GitHub Copilot
- IntelliJ IDEA (Community ou Ultimate)
- Git
- Java 17+

## Início rápido (executar a aplicação)

Clone o Spring PetClinic e execute:

- `git clone https://github.com/spring-projects/spring-petclinic.git`
- `cd spring-petclinic`
- macOS/Linux (e Git Bash no Windows): `./mvnw spring-boot:run`
- Windows (PowerShell): `.\mvnw.cmd spring-boot:run`

Em seguida, abra http://localhost:8080.

## Iniciar o workshop

Siga [workshop/README.md](workshop/pt_BR/README.md).
