# ai-slop

Skill para tirar a "cara de IA" de sites, painéis, apresentações e documentos: o azul de framework, tudo em cartão com sombra, o gradiente roxo, a trinca de ícones, o mesmo layout em todo slide, negrito e emoji em todo item, o título que só nomeia o tema.

A skill trata esses padrões como **tiques**: escolhas de fábrica que o gerador, o framework ou o template faz quando o projeto não diz nada. Um tique isolado não denuncia; a combinação denuncia. Ela troca cada tique por identidade tirada do material do próprio projeto e confere que o substituto não é outro tique.

Funciona no [padrão aberto Agent Skills](https://agentskills.io/specification) (`SKILL.md`).

Guia: [Skills na Prática](https://patrick-andrade.github.io/guias/skills-na-pratica.html).

## O que ela faz

- **Revisar:** diagnostica um site, deck ou documento que já existe e entrega a lista numerada de tiques, com local e contagem, antes de editar. Depois mede as referências que você citar, propõe acento e tipografia a partir do material do projeto, tokeniza, reestrutura e verifica contra a versão anterior.
- **Produzir:** quando o agente vai gerar um site, deck ou documento, fixa a identidade antes, usa os catálogos como lista do que não fazer e revisa o próprio resultado no fim.
- Traz um catálogo base (cor, forma, tipografia, enfeite, imagem) e um por meio: web, slides e documentos. Cada padrão tem sinal, problema, substituto, exemplo antes e depois e os casos em que não se aplica.
- Preserva o que a marca, o template institucional ou a norma do projeto definem, mesmo quando aparece num catálogo.

Não trata vocabulário nem prosa ("não é X, é Y", palavras típicas, travessões). Para isso, use junto a [humanizer](https://github.com/blader/humanizer).

A skill também não detecta autoria nem confere fatos e referências.

## Instalar

**Neste projeto:**

```bash
npx skills add patrick-andrade/ai-slop
```

**Em todos os projetos desta máquina:**

```bash
npx skills add patrick-andrade/ai-slop --global
```

`npx` vem com o Node.js e baixa o instalador na hora. Sem isso, copie a pasta da skill para:

```text
.agents/skills/ai-slop/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── base.md
    ├── documentos.md
    ├── slides.md
    └── web.md
```

na raiz do projeto. No Claude Code, o equivalente é `.claude/skills/ai-slop/`. No Cursor, `.agents/skills/` também costuma bastar. Inclua `references/`; o `SKILL.md` sozinho não carrega os catálogos.

Abra um **chat novo** depois de instalar.

## Pedir

Nomeie a skill. No Codex, use `$ai-slop`; no Claude Code, `/ai-slop`; no Cursor, `/ai-slop` ou o nome da skill no pedido.

```text
/ai-slop revise este deck e me mostre o diagnóstico antes de mudar qualquer coisa.
```

```text
/ai-slop produza o relatório trimestral em .docx a partir destes dados,
usando o modelo da pasta templates/.
```

```text
$ai-slop tire a cara de IA deste painel; a referência de estilo é o site do IBGE.
```

## Atualizar

Rode de novo o mesmo comando de instalação (com `--global`, se foi assim que instalou) e abra um chat novo:

```bash
npx skills add patrick-andrade/ai-slop
```

## Licença

[MIT](LICENSE). Você pode usar, copiar e adaptar; mantenha o aviso de copyright e da licença.
