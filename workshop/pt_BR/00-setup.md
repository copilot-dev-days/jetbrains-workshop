<!-- l10n-sync: source-file="00-setup.md" -->
# Configuração do workshop

Para completar este workshop, você clonará o Spring PetClinic, executará localmente, abrirá no IntelliJ IDEA e habilitará o GitHub Copilot.

> [!IMPORTANT]
> O código-fonte do PetClinic **não** está incluído neste repositório do workshop.
> Você trabalhará em um clone local de: https://github.com/spring-projects/spring-petclinic

## Recursos necessários

- Uma conta GitHub
- Acesso ao GitHub Copilot

## Instalação local necessária

### IDE

- IntelliJ IDEA (Community ou Ultimate)
- Plugin do GitHub Copilot instalado e conectado (Você pode baixar o plugin em Settings→ Plugins→ Marketplace)

### Serviços locais

- Git (CLI)
- Java 17+

## Clonar o Spring PetClinic

Clone o repositório upstream do PetClinic:

```sh
git clone https://github.com/spring-projects/spring-petclinic.git
cd spring-petclinic
```

> [!TIP]
> Se você quiser enviar suas alterações para seu próprio repositório GitHub durante o workshop, faça um fork do repositório PetClinic primeiro e clone seu fork.

## Executar a aplicação

A partir da pasta `spring-petclinic`, inicie o PetClinic:

- macOS / Linux:

  ```sh
  ./mvnw spring-boot:run
  ```

- Windows (PowerShell):

  ```powershell
  .\mvnw.cmd spring-boot:run

> [!NOTE]
> Se você estiver usando Git Bash no Windows, prefira `./mvnw spring-boot:run` (não `mvnw.cmd`).
  ```

Abra a aplicação no seu navegador: http://localhost:8080

## Abrir o projeto no IntelliJ

1. Abra o IntelliJ IDEA.
2. Selecione **File → Open…**
3. Escolha a pasta `spring-petclinic` que você clonou e abra como um projeto.
4. Se solicitado, confie no projeto e permita que a IDE importe o Maven/Gradle.

## Verificar se o Copilot está ativo

1. Abra o **Copilot Chat** (janela de ferramentas).
2. Inicie um novo chat.
3. Pergunte: "Explain what this repository is and how I run it locally."

> [!TIP]
> Se o Copilot não conseguir ver o projeto, confirme que você está conectado ao GitHub no plugin do Copilot e que o projeto terminou de ser indexado.

## Resumo e próximos passos

Agora você tem o PetClinic rodando e o projeto aberto no IntelliJ. A seguir, você adicionará um pequeno endpoint para praticar a codificação assistida pelo Copilot.
