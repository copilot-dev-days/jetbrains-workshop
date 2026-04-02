<!-- l10n-sync: source-file="prompts/agent-add-adoptions.md" -->
# Prompt: Adicionar uma aba "Adopt Me" + página Adoption (PetClinic)

Você está trabalhando em um clone local do Spring PetClinic (raiz do repositório).

Objetivo: Adicionar uma nova aba de navegação de nível superior chamada "Adopt Me" que leva a uma nova página renderizada no servidor chamada "Adoption".

Mantenha isso intencionalmente simples:
- Use Spring MVC + Thymeleaf (sem SPA).
- Evite adicionar bancos de dados, entidades JPA, repositories ou migrations.
- Evite adicionar testes para esta tarefa.
- Mantenha as mudanças mínimas e consistentes com os padrões existentes do PetClinic (templates, layout, navegação).

Critérios de aceitação:
1) Navegação
- Adicione uma entrada de navegação chamada "Adopt Me".
- Posicione-a ao lado da aba existente "Find Owners" (logo após ela).

2) Nova página
- Crie uma nova página intitulada "Adoption".
- Rota: `GET /adoption` (página Thymeleaf renderizada no servidor).

3) Parágrafo descritivo
- Adicione um parágrafo curto no topo chamando para adoção de pets.
- Escreva em primeira pessoa ("Eu", "nós", "nosso"), ex.: "We're looking for loving homes...".

4) Conteúdo da tabela
- Na página Adoption, renderize uma tabela com estas colunas:
  - Species (cat, dog, snake)
  - Gender
  - Age
  - Description
  - Adopt Me (um botão)

5) Comportamento do botão Adopt
- Cada linha tem um botão "Adopt Me".
- Quando clicado, deve marcar aquele pet como adotado e redirecionar de volta para `/adoption`.
- Se um pet já estiver adotado, renderize o botão cinza e não clicável (desabilitado).

Orientações de implementação (mantenha o mínimo):
- Use uma lista em memória de 3 pets (um cat, um dog, um snake) armazenada no controller/service (sem persistência).
- Use um id estável por pet para que a ação de adoção possa direcionar uma linha específica.
- Implemente a adoção como um endpoint `POST /adoption/{id}/adopt` (POST-redirect-GET).
- Use as classes CSS/Bootstrap existentes do PetClinic; não introduza novos sistemas de estilo.

Fluxo de trabalho:
1) Encontre como o PetClinic define o template de navegação superior e adicione "Adopt Me" ao lado de "Find Owners".
2) Adicione um pequeno controller e um template Thymeleaf para a página Adoption.
3) Execute a aplicação e verifique a aba, página, tabela e estado de botão desabilitado.

Formatação:
- Após alterações de código, execute o formatador do projeto (ex.: `spring-javaformat:apply` se configurado).
