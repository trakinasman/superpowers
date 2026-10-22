# Seleção do Superpowers

Skills escolhidas do [obra/superpowers](https://github.com/obra/superpowers) (tag `v7.0.1`,
commit `2ce8aa1`, licença MIT — ver `LICENSE`). Copiadas sem edição.

O Superpowers completo é uma metodologia obrigatória (brainstorming → worktree → plano →
subagentes → TDD → revisão), ligada por um hook em todo início de sessão. Aqui ficam só as skills
que ajudam **sem impor esse fluxo**, porque nossos projetos (`crm-q13`, `hq-firma`) não têm suíte
de testes e boa parte do trabalho é ajuste curto e iterativo.

**Esta pasta só guarda a seleção.** O Claude Code não carrega nada daqui sozinho.

## `skills/` — para instalar

| Skill | Quando dispara | Por que entrou |
|---|---|---|
| `systematic-debugging` | bug, falha ou comportamento inesperado, antes de propor correção | investigação de causa raiz em 4 fases; para de "chutar" após 3 correções que não funcionam |
| `verification-before-completion` | antes de dizer que algo está pronto, corrigido ou passando | exige rodar a verificação e ver a saída antes de afirmar sucesso |
| `receiving-code-review` | ao receber feedback de revisão | avalia cada sugestão com rigor em vez de aceitar tudo; combina com os agentes revisores do ECC |

Notas:
- `systematic-debugging` cita `superpowers:test-driven-development` e
  `superpowers:verification-before-completion`. A segunda está aqui; a primeira não (a própria
  skill aceita "script avulso se não houver framework de testes").
- A pasta dela traz arquivos do processo de criação da skill (`CREATION-LOG.md`,
  `test-pressure-*.md`, `test-academic.md`) e um script bash `find-polluter.sh` (acha qual teste
  deixa sujeira; sem rede, sem apagar nada). São inofensivos; vieram junto para manter a pasta
  original intacta.

## `opcionais/` — guardado, **não instalar globalmente**

- `brainstorming`: muito bom para projetos novos, mas tem uma trava (`HARD-GATE`) que proíbe
  implementar qualquer coisa antes de documento de design aprovado + plano, e encaminha para
  `superpowers:writing-plans`, que não está aqui. A descrição dela ("You MUST use this before any
  creative work") faria disparar em quase todo pedido. O "visual companion" sobe um servidor local
  (`127.0.0.1`) e carrega o logo de `primeradiant.com` (telemetria leve; desliga com
  `SUPERPOWERS_DISABLE_TELEMETRY=1`). Se quiser usar, instale só num projeto específico.

## O que ficou de fora

- **Hook de início de sessão** e `using-superpowers`: é o que torna o fluxo obrigatório.
- `test-driven-development` (apaga código escrito antes do teste), `using-git-worktrees`,
  `writing-plans`, `executing-plans`, `subagent-driven-development`,
  `dispatching-parallel-agents`, `requesting-code-review`, `finishing-a-development-branch`:
  formam o fluxo completo e dependem uns dos outros.
- `writing-skills`: processo pesado de TDD para skills; já temos o `skill-creator`.
- `diagnosing-superpowers`: só serve para depurar o fluxo completo.

## Instalar (quando decidir)

Copie as pastas de `skills/` para `~/.claude/skills/` (todos os projetos) ou
`<projeto>/.claude/skills/` (um projeto). Nenhum nome colide com skills nativas nem com as do ECC
já instaladas.

## Atualizar a partir do original

Compare com a tag nova do upstream e copie de novo só as mesmas pastas.
