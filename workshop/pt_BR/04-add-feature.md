<!-- l10n-sync: source-file="04-add-feature.md" -->
# Adicionar uma página "Adopt Me" (Agent Mode)

## Cenário

O PetClinic gerencia visitas veterinárias, mas a clínica também quer ajudar a comunidade com a adoção de pets.

Neste exercício, você adicionará uma **única página renderizada no servidor** e uma aba de navegação:

- Uma nova aba chamada **Adopt Me** (ao lado de "Find Owners")
- Uma nova página chamada **Adoption** que mostra uma pequena tabela de pets e um botão **Adopt Me** por linha

Isso é intencionalmente "pequeno" para que o Copilot possa ter sucesso de forma confiável.

## Contexto: por que este é um exercício de Agent Mode

Embora esta funcionalidade seja pequena, ela ainda abrange múltiplos arquivos (controller + template Thymeleaf + navegação). Isso a torna uma boa candidata para o **Agent Mode**, porque você pode descrever o resultado (critérios de aceitação) e deixar o Copilot iterar entre os arquivos.

## Usar o Agent Mode

### O que significa "Agent Mode"

O Agent Mode é projetado para **tarefas de codificação com múltiplas etapas**. Em vez de apenas responder perguntas ou aplicar uma única edição, o agente pode:

- Identificar arquivos relevantes (e pedir mais contexto quando necessário)
- Propor e aplicar mudanças em múltiplos arquivos
- Sugerir (e às vezes executar) comandos de terminal como formatação, builds e testes
- Iterar com base em erros (saída de compilação/testes) até atingir o objetivo

A ideia central: você define um objetivo e restrições, e o agente trabalha em um loop (planejar → editar → validar → ajustar), enquanto você mantém o controle.

Se você quiser mais contexto, veja: https://docs.github.com/en/copilot/how-tos/chat-with-copilot/chat-in-ide?tool=jetbrains#agent-mode-1

### Como usá-lo com segurança

- Prefira o **Agent Mode** para trabalhos abertos e entre múltiplos arquivos como esta funcionalidade; use **Edit** para mudanças pequenas e com escopo definido.
- Revise cada diff proposto como você faria em um PR.
- Trate comandos de terminal como alto impacto: execute-os intencionalmente (especialmente qualquer coisa que instale dependências ou altere formatação).
- Itere: se o resultado estiver próximo mas não correto, peça uma correção e execute os testes novamente.

Nesta parte, use o **Copilot Agent Mode** (se a interface do Copilot for JetBrains disponibilizar), e selecione um modelo mais recente se possível. (ex.: GPT-5 mini)

- Se você vir um seletor de modo como **Ask / Edit / Agent**: escolha **Agent**.
- Se seu cliente JetBrains do Copilot ainda não tiver o Agent Mode, use o mesmo prompt mas trabalhe iterativamente:
  - peça ao Copilot para propor um plano
  - aplique mudanças em blocos menores
  - execute os testes entre os blocos

> [!IMPORTANT]
> Mesmo no Agent Mode, você é responsável por revisar os diffs e validar a aplicação.

## Critérios de aceitação (mantenha o mínimo)

Use os critérios de aceitação desta página como sua **fonte da verdade** e seu checklist de revisão.

No Agent Mode, você também enviará um prompt (próxima seção) que resume esses requisitos para que o Copilot possa executá-los.

### Navegação na interface

- Adicionar um item de navegação de nível superior: **Adopt Me**.
- Posicioná-lo ao lado da aba existente **Find Owners** (logo após ela).
- A funcionalidade deve usar páginas renderizadas no servidor (Thymeleaf), consistente com o PetClinic.

### Página de adoção

- Uma nova página chamada **Adoption** servida em `GET /adoption`.
- Um parágrafo descritivo no topo chamando para adoção de pets, escrito em **primeira pessoa**.

### Tabela

- Uma tabela com estas colunas:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (botão)

### Botão Adopt Me

- Cada linha tem um botão **Adopt Me**.
- Quando clicado, marca aquele pet como adotado e redireciona de volta para `/adoption`.
- Se um pet já estiver adotado, o botão fica cinza e não é clicável (desabilitado).

### Restrições

- Mantenha o mínimo: **sem banco de dados/JPA**, sem repository, sem migrations.
- Mantenha os dados em memória (ex.: uma lista de 3 pets).

## Guia de execução

- Iniciar a aplicação (na raiz do seu clone do PetClinic):
  - macOS/Linux (e Git Bash no Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`
- Executar testes (na raiz do seu clone do PetClinic):
  - `./mvnw test`

## Prompt do agente

### Qual você deve seguir?

- Os **critérios de aceitação neste arquivo** são o checklist canônico do que você está construindo.
- O **arquivo de prompt** é um ponto de partida prático para copiar e colar, dando ao Copilot os mesmos requisitos em uma única mensagem.

Se houver qualquer divergência, atualize o prompt (ou reenvie um prompt corrigido) para que ele corresponda aos critérios de aceitação acima.

### Envie isso para o Agent Mode

Abra o arquivo de prompt e cole-o no Agent Mode:

- [../prompts/agent-add-adoptions.md](./prompts/agent-add-adoptions.md)

Se você quiser uma "mensagem única" explícita para copiar e colar, use esta (e ajuste conforme necessário):

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
> Não trate o prompt como mágica. Leia-o, edite-o e adicione restrições baseadas no que você deseja.

## Resumo e próximos passos

## Verificar

Após o agente terminar (ou você ter completado o trabalho iterativamente), faça uma rápida verificação.

### Executar a aplicação

- Inicie a aplicação (na raiz do seu clone do PetClinic):
  - macOS/Linux (e Git Bash no Windows): `./mvnw spring-boot:run`
  - Windows PowerShell: `.\mvnw.cmd spring-boot:run`

### Verificar a funcionalidade de ponta a ponta

- Abra a aplicação no navegador (normalmente `http://localhost:8080`).
- Confirme que há um item de navegação de nível superior **Adopt Me** ao lado de **Find Owners**.
- Abra `/adoption` e verifique o título da página e o parágrafo em primeira pessoa.
- Verifique se a tabela mostra cat/dog/snake.
- Clique em **Adopt Me** em uma linha e verifique se o botão fica desabilitado ao retornar à página.

### Executar testes

- Execute os testes (na raiz do seu clone do PetClinic): `./mvnw test`

Se os testes falharem, peça ao Copilot para corrigir as falhas mantendo os critérios de aceitação intactos.

Você usou o Agent Mode (ou um fluxo de trabalho similar ao de agente) para adicionar uma funcionalidade real com múltiplos arquivos. A seguir, um exercício bônus combinando o Agent Mode com instruções personalizadas mais rigorosas.
