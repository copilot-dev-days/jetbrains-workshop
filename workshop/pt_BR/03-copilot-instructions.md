<!-- l10n-sync: source-file="03-copilot-instructions.md" -->
# Fornecendo instruções personalizadas

Sempre existem informações-chave que qualquer pessoa gerando código para sua base de código precisa saber: estrutura do projeto, convenções e "como fazemos as coisas aqui". Como o contexto é tão importante para um assistente de codificação com IA, podemos fornecer parte dessas informações via **instruções do Copilot**.

## Cenário

Antes de começarmos atualizações maiores no PetClinic com a ajuda do Copilot, queremos garantir que o Copilot tenha um bom entendimento de como queremos que o código seja escrito.

Neste exercício você irá:

- executar um prompt de "baseline" e observar o resultado
- adicionar instruções do Copilot no nível do workspace em `.github/copilot-instructions.md`
- executar o mesmo prompt novamente e observar como o Copilot muda
- manter (e estender) instruções especializadas em `.github/instructions/`

## Visão geral das instruções do Copilot

As instruções do Copilot ficam em um arquivo markdown colocado em `.github/copilot-instructions.md`. Ele se torna parte do seu projeto e é usado para orientar o Copilot Chat.

> [!IMPORTANT]
> Mantenha este arquivo curto e focado em orientações gerais do projeto. Se ele crescer muito, pode ocupar o espaço do contexto de código que o Copilot precisa.

## Passo 1: Pedir ao Copilot para gerar uma função de baseline

1. No IntelliJ, feche abas extras do editor para reduzir contexto acidental.
2. Abra o Copilot Chat e inicie um novo chat.
3. Envie este prompt:

	```
	Create a Java function to validate pet age between 0 and 25.
	Throw an error if it is outside this range.
	```

4. Observe o resultado.

> [!NOTE]
> Em muitos casos, você notará que o código gerado apenas verifica que a idade é **>= 0** e esquece o limite superior. Isso é esperado: este é exatamente o tipo de desvio que as instruções ajudam a corrigir.

## Passo 2: Adicionar `.github/copilot-instructions.md`

No seu clone local do Spring PetClinic, crie `.github/copilot-instructions.md`.

Defina seu conteúdo como:

```markdown
# Copilot instructions

When adding a function that validates a pet's age, make sure it is between 0 and 25.
Add a short comment at the beginning of the function explaining what it validates.
```

Você pode adicionar este arquivo de duas formas:

- Manualmente (crie o arquivo em `.github/`), ou
- Pelas configurações do IntelliJ:
  - **Settings → Tools → GitHub Copilot → Customizations**
  - Clique em **workspace** em **Copilot instructions**

## Passo 3: Testar o prompt novamente (e verificar referências)

1. Inicie uma nova sessão do Copilot Chat.
2. Envie o mesmo prompt novamente:

	```
	Create a Java function to validate pet age.
	Ensure pet age is between 0 and 25.
	Throw an error if it is outside this range.
	```

3. Na interface do Copilot, abra a área de **references**.
4. Confirme que o Copilot utilizou **1 referência** do arquivo de instruções.
5. Você observará que a função gerada agora inclui ambos os limites e um comentário.

> [!TIP]
> Se você não vir as instruções referenciadas, certifique-se de que criou o arquivo no clone do PetClinic que está aberto no IntelliJ (não neste repositório de documentação do workshop).

## Passo 4: Instruções especializadas (mantenha essas)

Além do `.github/copilot-instructions.md`, você pode adicionar arquivos de instruções especializadas em `.github/instructions/`. Estes são úteis quando você quer orientações mais detalhadas para um subconjunto de arquivos (Java, testes, templates, etc.).

Mantenha as seções de instruções especializadas deste workshop e adicione um exemplo focado em Java. Por exemplo, crie `.github/instructions/java-style.instructions.md` com:

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

## Inspiração: awesome-copilot

Se você quer exemplos de bons arquivos de instruções (e prompts reutilizáveis), o repositório curado pela comunidade https://github.com/github/awesome-copilot é um ótimo lugar para buscar padrões.

## Resumo e próximos passos

Você viu como as instruções mudam a saída do Copilot fornecendo contexto estável e específico do projeto. A seguir, você construirá uma nova funcionalidade de adoção usando o **Agent Mode**.
