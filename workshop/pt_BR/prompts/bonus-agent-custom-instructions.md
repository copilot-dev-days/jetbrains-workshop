<!-- l10n-sync: source-file="prompts/bonus-agent-custom-instructions.md" -->
# Prompt: Estender "Adopt Me" com instruções personalizadas

Contexto:
- O código da aplicação está na raiz do repositório.
- Siga as instruções do repositório e as instruções especializadas em `.github/instructions/`.

Pré-condição:
- A funcionalidade simplificada "Adopt Me" já existe (aba de navegação + página `GET /adoption` com uma lista em memória de 3 pets e um botão de adoção que desabilita após adotar).

Tarefa:
1) Adicionar um filtro mínimo na página Adoption:
- Suporte a um parâmetro de consulta opcional: `species` com valores `cat`, `dog` ou `snake`.
- Quando fornecido, mostre apenas os pets correspondentes na tabela.
- Quando não fornecido, mostre todos os pets.
- Mantenha renderizado no servidor (sem filtragem por JS).

2) Adicionar uma funcionalidade mínima de "Desfazer adoção":
- Para pets adotados, mostre um botão "Undo" (ou "Unadopt") na coluna Adopt Me.
- Implemente como um endpoint POST (POST-redirect-GET) e redirecione de volta para `/adoption`.
- Não introduza persistência; continue usando estado em memória.

Restrições:
- Mantenha consistente com os padrões do PetClinic.
- Não adicione novas dependências.
- Mantenha as mudanças de UI mínimas e acessíveis.

Processo:
- Proponha um plano curto.
- Implemente incrementalmente.
- Execute `./mvnw test` e corrija as falhas.
