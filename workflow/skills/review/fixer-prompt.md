# Template: Despachar Fixer

Preencha os placeholders e envie como prompt do `workflow:fixer`.

Existem dois templates abaixo — use conforme o contexto:

- **Despacho inicial:** use o Template A — issues vêm do reviewer
- **Re-despacho pós-verificação:** use o Template B — issues vêm da verificação lint/tipos/build

## Placeholders

| Placeholder | Onde encontrar |
|-------------|----------------|
| `{LISTA_DE_ISSUES}` | Output **completo** do reviewer, incluindo issues de checagem técnica. Nunca omitir issues menores |
| `{RESUMO_DO_QUE_FOI_IMPLEMENTADO}` | Contexto do que foi construído — para o fixer entender o propósito do código |
| `{DIRETÓRIO}` | Diretório de trabalho do projeto |
| `{FALHAS_DE_VERIFICAÇÃO}` | Output dos comandos de lint/tipos/build que falharam (Template B) |
| `{TENTATIVA_N}` | Número da tentativa atual de re-despacho: 1, 2 ou 3 (Template B) |

---

## Template A — Despacho Inicial (issues do reviewer)

```markdown
Você está corrigindo issues encontrados na revisão de código.

## Issues

{LISTA_DE_ISSUES — copiar output completo do reviewer, incluindo issues de checagem técnica}

## Contexto

{RESUMO_DO_QUE_FOI_IMPLEMENTADO}

Diretório de trabalho: {DIRETÓRIO}
```

---

## Template B — Re-despacho Pós-Verificação

```markdown
Você está corrigindo problemas introduzidos por correções anteriores.

Esta é a tentativa {TENTATIVA_N} de 3. Corrija os issues abaixo sem introduzir novos problemas.

## Falhas de verificação

{FALHAS_DE_VERIFICAÇÃO — output dos comandos de lint/tipos/build que falharam}

## Contexto

{RESUMO_DO_QUE_FOI_IMPLEMENTADO}

Diretório de trabalho: {DIRETÓRIO}
```
