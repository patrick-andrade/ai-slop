# Documentos: relatórios, notas técnicas, memorandos, artigos

Use junto com `base.md`. Vale para .docx, PDF, Google Docs e Markdown ou Quarto renderizado. Os códigos D1 a D13 seguem a força do sinal. Aqui entra a formatação do texto (ênfase, listas, títulos, restos), não o vocabulário nem as frases: para isso, use a skill [humanizer](https://github.com/blader/humanizer).

## Onde procurar

- **Renderizado:** exporte para PDF e percorra todas as páginas; capa, sumário e anexos incluídos.
- **.docx** (descompacte o arquivo): `word/styles.xml` dá os estilos de título e corpo; em `word/document.xml`, compare o número de trechos em negrito (`<w:b/>`) com o de parágrafos (`<w:p>`), e procure sombreamento (`<w:shd`) e borda de parágrafo (`<w:pBdr>`), que denunciam caixas e listras.
- **PDF:** `pdffonts` lista as fontes embutidas; `pdftotext` deixa buscar restos.
- **HTML:** `grep -cE '<(strong|b)>'` e o peso das células e rótulos no CSS (D5).
- **Fonte em texto:** `grep -nE '\*\*|^#{1,6} |^---$|\[[A-Z][^]]*\]|oaicite|citeturn|\[cite:|utm_source=chatgpt'` acha markdown cru, placeholders e marcação de ferramenta.

## Restos

Estes saem na primeira ocorrência; nada aqui precisa de contexto.

### D1. Frase do chat no documento

**Sinal:** "Aqui está o relatório…", "Espero que ajude", "Claro!", "Quer que eu detalhe…?", "Posso ajustar o tom se preferir".
**Substituto:** remover a moldura e manter o conteúdo.

### D2. Marcação de citação da ferramenta

**Sinal:** `contentReference[oaicite:0]`, `oai_citation`, `citeturn0search0`, `[cite: 1]`, `【85†L261-269】`, `?utm_source=chatgpt.com` nos links.
**Substituto:** remover a marcação e conferir se a referência existe e diz o que o texto afirma; se não der para conferir, avise o usuário.

### D3. Markdown cru

**Sinal:** `**`, `##`, `---`, `[texto](url)` ou cercas de código visíveis num .docx, PDF ou e-mail.
**Substituto:** a formatação nativa do meio.
**Não agir quando:** o documento é Markdown e vai ser lido assim.

### D4. Placeholder

**Sinal:** "[Inserir nome]", "[Nome da empresa]", "2025-XX-XX", "Lorem ipsum", "INSERT_SOURCE_URL".
**Substituto:** preencher com o dado do usuário ou remover; não inventar.
**Não agir quando:** o documento é um modelo em branco.

## Ênfase e listas

### D5. Negrito espalhado

**Sinal:** frases e termos em negrito em quase todo parágrafo; numa tabela, todas as células numéricas em negrito.
**Problema:** quando tudo é destaque, nada é; a Wikipedia o lista entre os sinais de texto gerado.
**Substituto:** negrito raro, só no que o leitor precisa achar de relance; itálico para termos estrangeiros e títulos de obras.
**Não agir quando:** é material didático com termos-chave marcados por convenção.

### D6. Lista de "**Termo:** descrição"

**Sinal:** cada item abre com um rótulo em negrito e dois-pontos, e o rótulo repete o que a descrição diz.
**Substituto:** parágrafo, ou lista simples sem rótulo.
**Antes:** `- **Desempenho:** O desempenho melhorou com o novo algoritmo.`
**Depois:** `O novo algoritmo melhorou o desempenho.`
**Não agir quando:** é glossário, lista de definições ou ficha técnica.

### D7. Tudo em bullets e títulos demais

**Sinal:** argumento quebrado em listas; um título sobre cada parágrafo; títulos que só contêm outros títulos; níveis pulados (H2 para H4); um H1 que repete o título do documento.
**Substituto:** parágrafos onde há raciocínio; lista só para itens da mesma natureza; hierarquia de dois ou três níveis.
**Não agir quando:** é manual de referência ou documento feito para consulta rápida.

### D8. Emoji em título de seção

**Sinal:** 🎯 Objetivos, 📊 Resultados, ✅ Conclusão.
**Substituto:** título só com texto (ver B13).

## Títulos e seções

### D9. Title Case

**Sinal:** toda palavra principal com maiúscula ("Impacto Da Tecnologia Na Educação"); em português, é anglicismo.
**Substituto:** caixa de frase ("Impacto da tecnologia na educação").
**Não agir quando:** o título está em inglês e o guia de estilo pede Title Case; um título em outra língua segue a regra dessa língua.

### D10. Seções de molde

**Sinal:** títulos que só nomeiam o tema ("Visão geral", "Contexto", "Brasil em foco", "Quadro comparativo"); "Desafios e perspectivas" ou "Considerações finais" que só repetem o que veio antes; a mesma estrutura em qualquer assunto.
**Substituto:** seções nomeadas pelo que contêm ("Por que a arrecadação caiu em 2025"); conclusão só se diz algo novo, senão termine no último fato.
**Não agir quando:** a norma ou o edital exige as seções (ABNT, relatório de projeto, termo de referência).

### D11. Filete entre toda seção

**Sinal:** linha horizontal (`---`, borda inferior) separando cada seção, além do título.
**Substituto:** o título e o espaço já separam; filete só para uma quebra que o título não marca.
*Fraco sozinho.*

## Forma

### D12. Capa e caixas de kit

**Sinal:** capa com degradê ou imagem genérica; caixas de destaque com fundo tingido, listra lateral e ícone (dica, atenção, importante) em toda página; dados em cartões (B6, B16).
**Substituto:** a capa e os estilos do modelo do projeto; destaque raro, sem listra; dados em tabela ou gráfico com fonte.
**Não agir quando:** o modelo institucional define a capa ou as caixas.

### D13. Tabela que era frase

**Sinal:** tabela de duas ou três linhas e duas colunas que cabe numa frase.
**Substituto:** a frase.
*Fraco sozinho.*
