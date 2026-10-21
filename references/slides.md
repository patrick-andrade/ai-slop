# Slides: apresentações

Use junto com `base.md`. Vale para .pptx, Google Slides, Keynote, Quarto/reveal.js e slides em HTML. Os códigos S1 a S11 seguem a força do sinal.

Algumas skills e ferramentas de geração recomendam ícone em círculo, sombra em cartão e "nunca um slide só de texto" como regra. Aqui esses padrões contam como tique quando aparecem sem motivo no conteúdo.

## Onde procurar

- **Renderizado:** exporte todos os slides como imagem (no .pptx, `soffice --headless --convert-to pdf` e depois `pdftoppm -png -r 60`) e olhe a grade inteira de uma vez; repetição e deriva só aparecem assim.
- **Tema e layouts do .pptx** (descompacte o arquivo): `ppt/theme/theme1.xml` dá as cores (`<a:accent1>`…) e as fontes (`<a:majorFont>`, `<a:minorFont>`); `ppt/slideLayouts/` mostra os layouts disponíveis.
- **Slides do .pptx:** `grep -cE '<a:gradFill|<a:outerShdw|prst="roundRect"|<a:latin typeface=' ppt/slides/*.xml` conta degradês, sombras, cantos arredondados e fontes por slide.
- **Fonte em texto** (Quarto, Markdown, HTML): procure `\*\*[^*]+:\*\*` (rótulo em negrito), títulos com Title Case e emoji no início das linhas.
- **Notas do apresentador:** leia junto com o slide (S9).

Gráficos seguem B17 de `base.md`.

## Estrutura do deck

### S1. Mesmo layout em todo slide

**Sinal:** título e bullets, ou título e três cartões, do primeiro ao último slide, qualquer que seja o conteúdo. O oposto também conta: fontes, cores, rodapé ou estilo de gráfico mudando entre slides; logo só na capa.
**Problema:** o deck foi preenchido por molde; o leitor não vê onde o argumento muda.
**Substituto:** o **sistema** fica constante (cor, tipografia, margens, rodapé, estilo de gráfico) e o **layout** varia com o conteúdo: comparação em duas colunas, dado em gráfico, tese num divisor de seção.
**Antes:** 14 slides "Título + 4 bullets".
**Depois:** divisor para cada seção, gráfico onde há dado, duas colunas na comparação, bullets onde há enumeração.

### S2. Trinca de cartões com ícone

**Sinal:** três caixas iguais lado a lado, cada uma com ícone em círculo, título curto e duas linhas, repetidas em vários slides.
**Problema:** é o layout de fábrica mais reconhecível de deck gerado; força o conteúdo a ter três partes do mesmo peso.
**Substituto:** a forma que o conteúdo tem: lista se é enumeração, tabela se há atributos, diagrama se há relação, um bloco só se há uma ideia.
**Antes:** "Nossos pilares": três cartões "Inovação", "Eficiência", "Pessoas" com ícones.
**Depois:** uma frase com a decisão e, abaixo, a lista dos dois itens que o deck de fato desenvolve.
**Não agir quando:** o conteúdo tem três itens paralelos de fato, e só uma vez no deck.

### S3. Texto demais

**Sinal:** slide que se lê como relatório; mais de sete itens ou mais de dois blocos; fonte do corpo reduzida para caber.
**Substituto:** até sete itens e dois blocos por slide; o que passa vira outro slide, anexo ou nota do apresentador.
**Não agir quando:** o deck é material de leitura (handout) e o usuário o quer assim.

### S4. Título que só nomeia o tema

**Sinal:** "Visão geral", "Contexto", "Resultados", "Próximos passos"; Title Case em português ("Análise De Mercado"); o mesmo molde "Frase: subtítulo" em todo slide.
**Problema:** o título não diz o que o slide conclui; poderia estar em qualquer deck.
**Substituto:** título que afirma, em caixa de frase: "A receita caiu 4% no segundo trimestre".
**Não agir quando:** a convenção do meio pede título temático (aula, por exemplo); então a afirmação vai na primeira linha abaixo do título (primeiro item ou frase de abertura). Fora dessas convenções, prefira o título que afirma.

### S5. Arco de molde e slides redundantes

**Sinal:** agenda, três seções do mesmo tamanho, "Conclusões", "Obrigado"; dois ou três slides que dizem a mesma coisa; slides demais para o tempo.
**Substituto:** cortar os repetidos; a sequência leva a uma conclusão ou a um pedido; a agenda só quando o deck é longo.

## Forma e ênfase no slide

### S6. Fio sob o título e barras de enfeite

**Sinal:** filete curto colorido sob cada título; faixa de cabeçalho ou rodapé de borda a borda; listra vertical na lateral do slide ou num bloco.
**Problema:** a skill de slides da Anthropic chama o fio sob o título de marca de slide gerado.
**Substituto:** espaço e contraste de tamanho; o sistema de rodapé do template, se houver.
**Não agir quando:** o template institucional tem a faixa.

### S7. Rótulo em negrito em todo item

**Sinal:** cada bullet começa com "**Rótulo:**" seguido da explicação; negrito em várias palavras por item; a primeira coluna de uma tabela inteira em negrito.
**Substituto:** texto simples; se o bloco precisa de nome, um parágrafo curto abre o bloco e a lista vem abaixo; negrito raro.
**Antes:** `**Custo:** O custo caiu 12%.` / `**Prazo:** O prazo foi mantido.`
**Depois:** `O custo caiu 12% e o prazo foi mantido.`
**Não agir quando:** o template define um parágrafo em negrito abrindo cada bloco; o tique é o negrito em todo item, não o subtítulo do bloco.

### S8. Final do título em serifa itálica ou palavra recolorida

**Sinal:** título sem serifa cuja última expressão passa para serifa itálica ("Setenta anos, *cinco ondas*"), ou uma palavra pintada no acento em todo título.
**Substituto:** título numa família só; ênfase pelo conteúdo.
*Fraco sozinho.*

### S9. Restos

**Sinal:** asteriscos ou `#` de markdown visíveis; texto vazando da caixa; placeholder ("[Inserir gráfico]", "Lorem ipsum"); caixa de imagem vazia; nota do apresentador que contradiz o slide (47% na nota, 40% no slide).
**Substituto:** corrigir cada um; conferir número entre slide e nota.

### S10. Bullets em ritmo uniforme

**Sinal:** 3 ou 4 itens por slide, todos do mesmo comprimento, todos começando com verbo.
**Substituto:** o número de itens que o conteúdo tem; comprimentos diferentes quando o peso é diferente.
*Fraco sozinho.*

### S11. Slide final vazio

**Sinal:** "Obrigado!", "Perguntas?" ou "Vamos conversar" sem nenhum conteúdo.
**Substituto:** o pedido, a decisão ou a pergunta que o deck quer deixar, com o contato.
**Não agir quando:** o evento pede o slide.
*Fraco sozinho.*
