<!-- l10n-sync: source-file="05-bonus.md" -->
# Bônus: Agent Mode + instruções personalizadas

## Objetivo

Praticar um fluxo de trabalho de agente mais realista:

1. reforçar as instruções (para que o agente permaneça dentro da sua arquitetura)
2. executar um prompt de agente que requer múltiplos arquivos e verificação iterativa

## Parte A — Fortalecer as instruções

1. Abra [../../.github/copilot-instructions.md](../.github/copilot-instructions.md)
2. Adicione uma pequena seção "Faça / Não faça", por exemplo:
   - Faça: seguir os padrões MVC do PetClinic
   - Faça: usar POST-redirect-GET para ações que alteram estado (ex.: Adopt)
   - Não faça: introduzir um framework de frontend separado
   - Não faça: adicionar novas ferramentas de build

3. Abra as instruções especializadas em [../../.github/instructions/](../.github/instructions/) e ajuste-as conforme suas preferências.

## Parte B — Executar um prompt de agente que depende dessas instruções

Use este arquivo de prompt como ponto de partida:

- [../prompts/bonus-agent-custom-instructions.md](./prompts/bonus-agent-custom-instructions.md)

Se o seu cliente Copilot suportar Agent Mode, use-o. Caso contrário, faça o mesmo fluxo manualmente:

- Peça ao Copilot um plano
- Aplique mudanças em commits pequenos (opcional)
- Execute `./mvnw test` entre os passos

## Desafios extras

Se você terminar cedo, tente um destes (escolha um):

- Adicionar um filtro simples na página de Adoption (ex.: parâmetro de consulta `species=cat|dog|snake`)
- Adicionar uma ação de "Desfazer adoção" com um clique (POST-redirect-GET) para reativar o botão
- Mostrar uma pequena mensagem de sucesso após adotar (flash attribute)

## Conclusão

A ideia central: o Agent Mode funciona melhor quando você o combina com **restrições** claras (instruções) e um **ciclo de feedback** curto (build/testes).
|:--------------------------------------------|----------------------------------------------:|
