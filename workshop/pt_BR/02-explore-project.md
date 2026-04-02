<!-- l10n-sync: source-file="02-explore-project.md" -->
# Explorar o projeto

## Cenário

Antes de adicionar uma funcionalidade maior, você precisa entender como o PetClinic está estruturado: onde ficam os controllers, como os dados são armazenados e como as páginas são renderizadas.

Este exercício foca em **obter contexto** e fazer perguntas de alto valor.

## Usar o Copilot Chat para entender a base de código

1. Feche abas extras no IntelliJ para reduzir contexto acidental.
2. Abra o Copilot Chat.
   - Se você tiver um seletor de modelo, escolha um modelo mais recente.
   - Se você estiver no plano gratuito, selecione **GPT-5 mini** (está incluído na conta).
3. Inicie um novo chat.
4. Faça perguntas como:
   - Se você tiver um seletor de modelo, pode mudar para **GPT-5 mini** para esta etapa também.

   - "What are the main packages and what does each one do?"
   - "Where are the controllers that render web pages?"
   - "Where is the database schema/data defined for the default H2 database?"
   - "How do owners, pets, and visits relate?"
   - "Where would I add a new feature that introduces new pages + database tables?"

> [!TIP]
> Se o seu Copilot Chat suportar escopo para o projeto/workspace, use-o para perguntas como "find me the controller that…". Caso contrário, cole nomes de classes e peça dicas de navegação.

## O que você deve descobrir

Ao final, você deve ser capaz de responder:

- Como a aplicação é iniciada (Maven/Gradle wrapper)
- Como o MVC funciona neste projeto (controllers + templates Thymeleaf)
- Onde ficam as entidades JPA e os repositórios
- Como a inicialização do banco de dados funciona para o H2

## Resumo e próximos passos

Agora você tem o contexto para fazer mudanças maiores com segurança. A seguir, você ensinará o Copilot mais sobre seu repositório adicionando **instruções do Copilot**, incluindo instruções personalizadas mais especializadas.
