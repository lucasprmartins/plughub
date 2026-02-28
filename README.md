<div align="center">

<img src="https://cdn.simpleicons.org/claude" alt="Claude" width="80" />

# Beta Plugins

**Coleção de plugins com skills, agentes e comandos para Claude Code.**

[Plugins](#plugins) · [Instalação](#instalação) · [Uso](#uso) · [Estrutura](#estrutura)

</div>

---

## Sobre

Beta Plugins é um ecossistema de plugins para [Claude Code](https://github.com/anthropics/claude-code) que oferece um pipeline completo de desenvolvimento — da ideação à revisão de código — através de skills orquestradas e subagentes especializados.

## Plugins

### Workflow

Pipeline completo de desenvolvimento com orquestração de subagentes.

| Skill | Descrição |
|-------|-----------|
| `/spec` | Transforma ideias vagas em especificações detalhadas |
| `/roadmap` | Converte especificações em tarefas atômicas e executáveis |
| `/build` | Orquestra subagentes `maker` para execução paralela por fases |
| `/check` | Orquestra subagentes `reviewer` e `fixer` em loop de verificação |

**Subagentes:**

| Agente | Função |
|--------|--------|
| `maker` | Implementa tarefas individuais com commits atômicos |
| `reviewer` | Executa verificações técnicas e revisão de código |
| `fixer` | Aplica correções cirúrgicas nos problemas encontrados |

### Essentials

Utilitários de produtividade para o dia a dia.

| Skill | Descrição |
|-------|-----------|
| `/commit` | Commits atômicos seguindo Conventional Commits |
| `/design` | Criação de interfaces UI/UX profissionais e distintas |
| `/pr` | Pull requests padronizados com checklist de verificação |

**MCP Server:** [Context7](https://mcp.context7.com) — consulta de documentação em tempo real.

## Instalação

**Pré-requisitos:** [Claude Code](https://github.com/anthropics/claude-code) instalado e configurado.

### Adicionar via CLI

```bash
claude plugins:add /caminho/para/beta-plugins/workflow
claude plugins:add /caminho/para/beta-plugins/essentials
```

### Adicionar manualmente

Adicione os caminhos dos plugins no seu arquivo de configuração do Claude Code (`settings.json`):

```json
{
  "plugins": [
    "/caminho/para/beta-plugins/workflow",
    "/caminho/para/beta-plugins/essentials"
  ]
}
```

## Uso

### Fluxo completo de desenvolvimento

```
Ideia → /spec → /roadmap → /build → /check → /commit → /pr
```

#### 1. Especificar a ideia

```
/spec Quero criar um sistema de autenticação com OAuth
```

O spec gera uma especificação em `.workflow/specs/`.

#### 2. Planejar a implementação

```
/roadmap
```

Converte a especificação em tarefas atômicas salvas em `.workflow/plans/`.

#### 3. Executar as tarefas

```
/build
```

Despacha subagentes `maker` que implementam as tarefas em paralelo por fases.

#### 4. Revisar o código

```
/check
```

Despacha `reviewer` para verificação técnica e `fixer` para correções automáticas.

#### 5. Commitar e abrir PR

```
/commit
/pr
```

### Skills independentes

As skills do Essentials podem ser usadas de forma independente a qualquer momento:

```
/commit          # Commit atômico das mudanças atuais
/design          # Criar uma interface UI/UX
/pr              # Abrir um pull request
```

## Estrutura

```
beta-plugins/
├── .claude-plugin/
│   └── marketplace.json          # Registro dos plugins
├── workflow/                     # Plugin: pipeline de desenvolvimento
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── agents/
│   │   ├── maker.md
│   │   ├── reviewer.md
│   │   └── fixer.md
│   └── skills/
│       ├── spec/
│       ├── roadmap/
│       ├── build/
│       └── check/
├── essentials/                   # Plugin: utilitários
│   ├── .claude-plugin/
│   │   └── plugin.json
│   └── skills/
│       ├── commit/
│       ├── design/
│       └── pr/
└── README.md
```

## Autor

Feito por [Lucas Martins](mailto:lucasprmartins@icloud.com).
