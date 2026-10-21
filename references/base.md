# Base: padrões de todo meio

Vale para site, deck e documento. Os códigos B1 a B18 seguem a força do sinal dentro de cada família. *Fraco sozinho*: só conta junto de outros tiques na mesma superfície. Os valores citados nos sinais são exemplos: o que conta é a família de cor, a faixa de medida e o uso.

Onde procurar: na web, CSS, variáveis do framework e tokens dos gráficos (ver `web.md`); num .pptx, `ppt/theme/theme1.xml` (cores e fontes do tema) e os XML dos slides e layouts; num .docx, `word/styles.xml` e `word/document.xml`; em qualquer meio, as páginas renderizadas.

## Cor

### B1. Azul como cor de tudo

**Sinal:** um azul saturado (matiz entre 200° e 235°, como `#3B82F6`, `#2563EB`, `#0D6EFD`, `#4472C4` do Office, ou um azul-claro vivo) ao mesmo tempo em marca, link, foco, item ativo, ícones, títulos, números e gráficos; às vezes sobre fundo azul-marinho.
**Problema:** é a cor que o framework ou o tema traz de fábrica; não diz nada do projeto.
**Substituto:** tinta quase preta para texto e estrutura; um acento tirado do material do projeto, só em link, foco, item ativo ou destaque.
**Antes:** títulos, botões, ícones e barras do gráfico em `#2563EB`.
**Depois:** títulos e botões em `#1E1E1E`; o acento do projeto só nos links e no item ativo; o gráfico com a paleta de dados.
**Não agir quando:** a marca do projeto é esse azul.

### B2. Gradiente de enfeite

**Sinal:** degradê em capa, hero, botão, faixa, barra de gráfico ou fundo de slide, sem função de dado. O de roxo para azul (ou índigo para rosa) é o mais citado de todos os sinais visuais.
**Problema:** veio do `indigo-500` dos kits de interface e virou assinatura de material gerado.
**Substituto:** cor chapada; degradê só quando codifica algo (uma escala de valores).
**Antes:** capa com `linear-gradient(135deg, #6366F1, #A855F7)`.
**Depois:** capa sobre o fundo, título na tinta; se houver campo de cor, chapado no acento do projeto.
**Não agir quando:** o degradê é da identidade do projeto.

### B3. Cinzas azulados

**Sinal:** fundos, filetes, painéis, texto suave e cabeçalhos de tabela em cinzas com matiz azul (entre 200° e 230°, saturação baixa), como a escala "slate" (`#F8FAFC`, `#E2E8F0`, `#64748B`).
**Problema:** é a escala de cinza do framework; somada a B1, deixa tudo frio e genérico.
**Substituto:** neutros verdadeiros (`#F5F5F5`, `#DDDDDD`, `#5C5C5C`) ou neutros puxados para o matiz do acento do projeto.
**Não agir quando:** o projeto definiu esses cinzas de propósito.

### B4. Acentos demais

**Sinal:** dois ou mais acentos (azul, verde-água, dourado…) colorindo números, rótulos e caixas sem que cada cor signifique algo.
**Substituto:** um acento; cor de dado só no gráfico e na legenda; cores semânticas só para estado.
**Não agir quando:** cada cor corresponde a uma categoria que o leitor precisa distinguir.

## Forma

### B5. Fio colorido na borda

**Sinal:** `border-left` ou `border-top` de 2px ou mais na cor de destaque, em cartão, caixa de valor, citação, callout, selo ou barra de navegação; num deck, listra vertical na borda do slide ou do bloco.
**Problema:** é o jeito de fábrica de "destacar" um bloco; a Anthropic o lista como marca de slide gerado.
**Substituto:** filete de 1px na tinta abrindo o bloco, ou espaço; destaque pela posição e pelo peso, não pela listra.
**Antes:** `.callout { border-left: 4px solid #2563EB; border-radius: 8px; }`
**Depois:** `.callout { border-top: 1px solid var(--tinta); padding-top: 12px; }`
**Não agir quando:** a listra é semântica (aviso, erro) e segue a cor semântica.

### B6. Tudo é cartão

**Sinal:** cada bloco numa caixa com borda ou fundo tingido, raio de 8px ou mais e, muitas vezes, a mesma sombra difusa (`rgba(0,0,0,.1)`); grades de cartões iguais em sequência; o mesmo raio em tudo, qualquer que seja a hierarquia.
**Problema:** o conteúdo vira uma pilha de caixas do mesmo peso; a forma não diz o que importa.
**Substituto:** listas e seções abertas por filete ou por espaço; sombra só no que flutua; caixa só onde agrupa algo que o leitor precisa ver junto.
**Não agir quando:** o sistema de design do projeto define cartões, ou o cartão é um objeto real da interface (item arrastável, produto numa loja).

### B7. Raio generoso e pílulas

**Sinal:** raio de 6px (0,375rem) ou mais em caixas, botões, barras e imagens; selos, botões e barras de gráfico em pílula.
**Substituto:** raio de 0 a 4px, um só valor por nível de hierarquia; círculo só como affordance universal (avatar, ícone "?").
**Não agir quando:** a marca é arredondada.

### B8. Brilho, vidro e neon

**Sinal:** botão com brilho do próprio gradiente, painel de vidro desfocado, borda neon em fundo escuro, bolhas de cor desfocadas ao fundo.
**Substituto:** remover; contraste por cor chapada e peso.
**Não agir quando:** o projeto é de um meio que pede isso (jogo, evento).
*Fraco sozinho.*

## Tipografia

### B9. Título de startup

**Sinal:** `letter-spacing` negativo nos títulos ou nos números grandes; peso 800 ou 900. Os dois juntos são o sinal forte; um só já conta.
**Substituto:** peso 600 ou 700, espaçamento 0; o caráter vem da família ou da largura.
**Antes:** `h1 { font-weight: 800; letter-spacing: -0.035em; }`
**Depois:** `h1 { font-weight: 700; letter-spacing: 0; }`

### B10. Sobrelinha decorativa

**Sinal:** rótulo curto em caixa-alta espaçada (≥ 0,1em), num tom do destaque, acima de todo título.
**Substituto:** se o rótulo não informa nada, texto suave comum ou nada; se informa (seção, data, autor), fica como sistema de rótulos, na tinta ou no tom suave, não no destaque.

### B11. Hierarquia plana

**Sinal:** títulos, números e corpo em tamanhos e pesos parecidos; nada domina a página ou o slide; todas as cores com o mesmo peso visual.
**Substituto:** um elemento dominante por página ou slide; contraste claro de tamanho entre título e corpo; uma cor dominante, o acento raro.

### B12. Fonte por omissão

**Sinal:** Inter, Roboto, Open Sans, Arial, Helvetica, Poppins, Montserrat, DM Sans ou Space Grotesk sem motivo no projeto; Calibri ou Aptos só porque o Office as põe.
**Problema:** é a escolha que serve a qualquer projeto, por isso não identifica nenhum.
**Substituto:** a família que o projeto já usa; sem uma, escolha com motivo (legibilidade no meio, cobertura de acentos, licença) e diga qual.
**Não agir quando:** a marca ou o template institucional usa a fonte. A pilha de reserva (`system-ui, Arial, sans-serif` depois da família escolhida) não conta; conta a família que de fato aparece. Num arquivo que precisa abrir sem baixar nada, a fonte do sistema é uma escolha com motivo: diga qual.
*Fraco sozinho.*

## Enfeite, imagem e dado

### B13. Emoji como marcador ou ícone

**Sinal:** 🚀 ✅ 💡 🎯 🔹 abrindo títulos, itens de lista, cartões ou rótulos.
**Substituto:** marcador tipográfico do sistema ou nenhum; ícone só quando o projeto tem um conjunto próprio.
**Antes:** `🚀 Lançamento: o produto sai no 3º trimestre`
**Depois:** `O produto sai no 3º trimestre.`
**Não agir quando:** a peça é para rede social, mensagem informal ou público infantil.

### B14. Ícone genérico em círculo

**Sinal:** ícone de linha monocromático ("equipe", "crescimento", "alvo") dentro de um círculo colorido, um por cartão ou por item, sem explicar nada.
**Problema:** decora em vez de informar; o mesmo ícone serviria a qualquer assunto.
**Substituto:** sem ícone; ou uma figura, diagrama ou dado que mostra o assunto.
**Não agir quando:** o ícone é affordance de interface (fechar, busca, menu).

### B15. Imagem genérica ou visivelmente gerada

**Sinal:** foto de banco que ilustraria qualquer coisa (aperto de mão, pessoas sorrindo para o notebook); 3D brilhante e saturado, pele de plástico, mãos ou texto deformados; imagem sem relação com o que o texto diz.
**Substituto:** foto ou figura do próprio assunto (o lugar, o objeto, os dados); sem uma, nenhuma imagem.
**Não agir quando:** a imagem gerada é assumida como ilustração e creditada.

### B16. Número de efeito

**Sinal:** 3 ou 4 caixas grandes, cada uma com um número e uma legenda; número grande sem fonte própria; casas decimais que mudam de um número para outro ou que a nota contradiz; estatística redonda e plausível que ninguém pediu.
**Problema:** o número vira enfeite e, sem fonte, pode ser inventado.
**Substituto:** o número na frase ou numa faixa entre filetes, com separadores; toda figura com dado leva uma linha "Fonte:"; precisão uniforme. Sem fonte, pergunte ao usuário; não invente.
**Antes:** três cartões "98% satisfação", "3x mais rápido", "+500 clientes".
**Depois:** "Fonte: pesquisa interna, 412 respostas, mar. 2026" abaixo de uma faixa com os dois números que o usuário confirmou.
**Não agir quando:** o número é a mensagem do slide ou da página e tem fonte. Um número calculado dos dados do usuário (variação, média) é legítimo quando o texto diz que foi calculado e de quê.

### B17. Gráfico de fábrica

**Sinal:** cores padrão da biblioteca ou do Office; barras com degradê ou cantos de pílula; grade de fundo; legenda longe das séries; eixo vertical redundante com rótulos de valor; título que só nomeia a variável; sem linha de fonte.
**Substituto:** paleta de dados do projeto (ou uma validada para daltonismo); barras chapadas e retas; rótulo direto nas séries; sem grade; título com o achado e subtítulo com a unidade; "Fonte:" abaixo.

### B18. Numeração 01 / 02 / 03 sem sequência

**Sinal:** marcadores numerados grandes sobre itens que não são etapas nem ordem.
**Substituto:** sem numeração.
**Não agir quando:** o conteúdo é um processo ou uma linha do tempo.
*Fraco sozinho.*
