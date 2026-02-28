# Template: Despachar Maker

Preencha os placeholders e envie como prompt do `workflow:maker`.

## Placeholders

| Placeholder | Onde encontrar |
|-------------|----------------|
| `{N}` | Número da tarefa no plano |
| `{NOME}` | Nome da tarefa no plano |
| `{OBJETIVO_DO_PLANO}` | Campo "Objetivo" do cabeçalho do plano |
| `{CONTEXTO_DO_PLANO}` | Campo "Contexto" do cabeçalho do plano |
| `{ARQUITETURA_DO_PLANO}` | Campo "Arquitetura" do cabeçalho do plano |
| `{PILHA_DE_TECNOLOGIAS}` | Campo "Pilha de Tecnologias" do cabeçalho do plano |
| `{TEXTO_COMPLETO_DA_TAREFA}` | Copiar integralmente do plano (nunca fazer o subagente ler o arquivo) |
| `{CONTEXTO_DA_TAREFA}` | Dependências já concluídas, decisões relevantes, SHAs anteriores |
| `{DIRETÓRIO}` | Diretório de trabalho do projeto |

---

```markdown
Você está implementando a **Tarefa {N}: {NOME}**.

## Visão Geral do Plano (somente leitura — não modifique nada fora da seção Tarefa)

**Objetivo:** {OBJETIVO_DO_PLANO}
**Contexto:** {CONTEXTO_DO_PLANO}
**Arquitetura:** {ARQUITETURA_DO_PLANO}
**Pilha de Tecnologias:** {PILHA_DE_TECNOLOGIAS}

## Tarefa

{TEXTO_COMPLETO_DA_TAREFA}

## Contexto da Tarefa

{CONTEXTO_DA_TAREFA}

Diretório de trabalho: {DIRETÓRIO}
```
