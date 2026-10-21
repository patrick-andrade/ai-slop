---
name: ai-slop
description: Diagnostica e previne o AI slop visual e estrutural, a "cara de IA" de sites, painéis, apresentações e documentos (azul de framework, tudo em cartão, gradiente roxo, trinca de ícones, slide sempre igual, negrito e emoji em todo item, título-rótulo), trocando cada tique por identidade tirada do próprio projeto. Use quando o usuário pedir para revisar ou produzir um site, deck ou relatório sem cara de IA. Não trata vocabulário nem prosa.
disable-model-invocation: true
license: MIT
metadata:
  author: Patrick Andrade
  version: "1.0.0"
---

# ai-slop

AI slop visual é uma soma de **tiques**: padrões que um gerador, um framework ou um template produz por omissão, sem que o projeto precise deles. Um tique isolado não denuncia nada; a combinação denuncia. O trabalho é trocar cada tique por **identidade**, tirada do material do próprio projeto, e conferir que o substituto não é outro tique.

## Por que o material gerado tem cara de IA

Um modelo escolhe a opção que serve ao maior número de pedidos parecidos. Sem uma direção do projeto, toda página, deck ou relatório converge para a mesma média: a Anthropic chama isso de *distributional convergence*. Cada tique dos catálogos é uma forma dessa escolha por omissão:

- **Paleta de fábrica.** O azul do framework, o gradiente roxo, os cinzas azulados do tema padrão.
- **Kit de componentes.** Tudo em cartão com o mesmo raio e a mesma sombra; um fio colorido na borda para "destacar".
- **Enfeite de template.** Sobrelinha em caixa-alta, ícone em círculo, emoji como marcador, 01/02/03, número grande com legenda.
- **Estrutura por regra.** O mesmo layout em todo slide, três cartões, bullets do mesmo tamanho, título que só nomeia o tema, negrito em todo item.
- **Restos.** Asteriscos de markdown, placeholders, frases do chat, marcação de citação da ferramenta.

Daí o critério: um padrão conta como tique quando é **padrão de fábrica que o projeto não pediu**, não quando "parece IA". Os padrões estão numerados do mais forte ao mais fraco dentro de cada família; um padrão marcado *fraco sozinho* só justifica mudança quando aparece junto de outros tiques na mesma superfície.

## Catálogos

Carregue sempre [references/base.md](references/base.md) (cor, forma, tipografia, enfeite, imagem). Carregue também o do meio:

| Meio | Catálogo |
|---|---|
| Site, painel, relatório web | [references/web.md](references/web.md) |
| Apresentação (.pptx, Google Slides, Keynote, Quarto/reveal.js, slides em HTML) | [references/slides.md](references/slides.md) |
| Documento (.docx, PDF, Google Docs, Markdown ou Quarto renderizado) | [references/documentos.md](references/documentos.md) |

Um relatório publicado como página usa web e documentos. Cada padrão tem código (B3, W2, S5, D7), Sinal, Problema, Substituto, Não agir quando e um exemplo antes e depois. Os catálogos são abertos: quando um diagnóstico achar tique novo, acrescente o padrão com sinal, substituto e exceção.

## Modo revisar

Para um site, deck ou documento que já existe.

1. **Fixe a versão e as fontes de estilo.** Confirme que o arquivo ou checkout é o que circula: na web, compare o branch local com o remoto e o remoto com o site no ar; num deck ou documento, confirme a versão com o usuário. Liste toda fonte de estilo: folha de estilo, variáveis do framework, tokens dos gráficos, tema e mestre do .pptx, estilos e modelo do .docx, template de PDF, cores fixas em código. Pronto quando a versão diagnosticada está identificada e cada arquivo que define cor, tipografia ou forma está na lista.

2. **Diagnostique.** Aplique cada padrão de `base.md` e do catálogo do meio às superfícies renderizadas e às fontes de estilo. Cada catálogo diz onde procurar. Uma **superfície** é um tipo de bloco que o leitor vê (cabeçalho, cartão, tabela, gráfico, callout, rodapé); num deck, também cada slide; num documento, cada seção. Registre cada ocorrência uma vez, no código mais específico; um código composto (W1, D12) cita os de base que contém em vez de contá-los de novo. Uma variante que foge por pouco do sinal (outro tom de azul, 2px em vez de 3px) conta, com a nota "variante". As [armadilhas](#armadilhas) presentes entram como observação, sem código. Registre também [o que fica](#o-que-fica). Entregue o diagnóstico como lista numerada (código, tique, localização, em quantas superfícies) **antes** de editar. Pronto quando todo padrão está marcado presente ou ausente, cada presente tem localização (seletor ou `arquivo:linha`, número do slide ou da página) e contagem de superfícies, os *fracos sozinhos* sem companhia estão marcados como tal e a lista do que fica está escrita.

3. **Meça as referências.** Quando o usuário citar uma referência (uma instituição, uma publicação, um deck), meça, não lembre: na web, `getComputedStyle` de título, corpo, rótulos e links; num .pptx ou .docx, o tema e os estilos; num PDF, as fontes embutidas e as cores. Meça uma página de listagem e uma de conteúdo, ou um slide de abertura e um de conteúdo, porque diferem. Separe **estilo** (hierarquia, rótulos, filetes, proporções) de **fonte** (a família tipográfica): o usuário pode querer um sem o outro. Pronto quando cada referência tem uma tabela medida com título, corpo, rótulos, cor e estrutura.

4. **Decida com o usuário.** São três escolhas, cada uma com recomendação e prévia: direção geral, acento e tipografia dos títulos. Escolha seguindo estas regras:
   - um acento só, tirado do material do projeto (logo, figuras, fotos, uma cor que os dados já usam), em link, foco, item ativo ou destaque;
   - primeiro o estilo, na família de fonte que o projeto já tem; família nova só com pedido do usuário;
   - cada substituto passa pelas [armadilhas](#armadilhas).

   Pronto quando direção, acento (hex) e fonte dos títulos estão decididos pelo usuário e a lista do que não muda está registrada.

5. **Tokenize.** Crie tokens semânticos (tinta, acento, suave, filete, borda de controle, fundo alternativo) numa fonte única, com os mesmos valores em todo lugar que define estilo: CSS, código dos gráficos, tema do .pptx, estilos do .docx, template de PDF. Calcule o contraste de cada token contra o fundo: texto ≥ 4,5:1; texto grande, borda de controle e marca de gráfico ≥ 3:1. Pronto quando a busca pelos valores antigos volta vazia e a tabela de contraste está escrita.

6. **Reestruture.** Aplique o substituto de cada tique presente. Regenere o que depende dos tokens (bundles, figuras, PDFs). Pronto quando cada tique do passo 2 está corrigido ou mantido de propósito, com o motivo escrito.

7. **Prototipe a dúvida.** Quando o usuário hesitar sobre um elemento (a fonte dos títulos, o acento), monte variantes descartáveis lado a lado, com a versão atual entre elas: na web, alternadas por parâmetro na página real; num deck, o mesmo slide em duas ou três versões; num documento, a mesma página. Pronto quando o veredito do usuário está registrado.

8. **Verifique contra a linha de base.** Renderize a versão nova e a anterior no mesmo motor e entregue capturas antes e depois. Na web, rode os testes do projeto e o axe (WCAG 2.1 AA) na página inteira, a 1280px e a 375px, em toda família de página. Num deck, renderize todos os slides como imagem e confira texto vazando, contraste e o sistema constante. Num documento, exporte para PDF e confira todas as páginas. Conta como regressão só o problema que a linha de base não tem; os antigos vão para uma lista à parte. Pronto quando não há regressão, as capturas foram entregues e os problemas antigos estão listados.

## Modo produzir

Para um site, deck ou documento que o agente vai gerar.

1. Antes de gerar, procure no projeto o que já define o visual: template, tema, logo, folha de estilo, figuras, documentos anteriores. Fixe a identidade numa linha: um acento, uma família, um sistema de títulos, uma forma (raio, filete, sombra). Sem material, pergunte ao usuário ou escolha e diga o motivo.
2. Gere usando `base.md` e o catálogo do meio como lista do que não fazer, com o substituto de cada padrão.
3. Ao terminar, renderize o resultado como no passo 8 do modo revisar (num deck em HTML, cada slide no navegador), percorra `base.md` e o catálogo do meio sobre ele e corrija direto, sem relatório prévio. Entregue duas listas curtas: o que corrigiu (com código) e o que ficou de propósito, com o motivo.

## O que fica

- Paletas de dados validadas para daltonismo e contraste (Okabe-Ito, viridis, ColorBrewer): são da leitura dos dados, não do visual.
- Cores semânticas de aviso, erro e sucesso.
- Contorno de foco forte e visível.
- Sublinhado nos links dentro do texto.
- Sombra em elemento que flutua (menu, popover, diálogo).
- Tudo o que a marca, o template institucional ou a norma do projeto define, mesmo que conste num catálogo.

## Armadilhas

Trocas que parecem correção e reintroduzem slop:

- **Creme, serifa de alto contraste e terracota.** É o visual padrão do próprio Claude; num projeto de terceiro, denuncia.
- **Fundo quase preto com um acento ácido** (verde-limão, vermelhão).
- **O "jornal" por regra.** Filete fino, raio zero e colunas densas em tudo também é um padrão de gerador. Os substitutos dos catálogos são direção; a forma final vem do projeto. Teste: se a página ficaria igual com outro assunto e outra instituição, nenhum elemento veio do projeto, e o substituto virou molde.
- **Um azul por outro.** Trocar o azul de framework por um azul institucional qualquer, sem origem no projeto.
- **Azul com laranja ou dourado** como par de identidade (*fraco sozinho*).
- **O estilo da referência com a fonte dela.** Quase sempre o que se quer é a hierarquia e os rótulos da referência na família que o projeto já tem.
- **Família nova sem protótipo** contra a atual.

## Quando não agir

Nenhum sinal isolado prova nada, e pessoas e detectores acertam pouco quando tentam dizer se algo foi gerado. Muito do que os catálogos listam é design ruim anterior à IA; o critério continua sendo o padrão de fábrica sem motivo no projeto. Deixe o padrão onde o projeto ou o meio o pede de propósito: a marca, o template institucional, a norma (ABNT, edital, guia da casa), a peça para rede social. Remover enfeite não obriga a pôr outro no lugar: um slide só de texto é certo quando o conteúdo é argumento; figura entra quando há dado, lugar ou objeto para mostrar. Os tiques mudam com cada geração de modelos; um padrão que deixou de aparecer sai do catálogo.

Consertar a superfície não salva conteúdo fraco: um deck sem argumento continua sem argumento depois da reforma visual. Diga isso ao usuário quando for o caso, sem reescrever o conteúdo.

## Fora do escopo

- **Prosa.** Vocabulário típico, construções como "não é X, é Y", tríades verbais, travessões, tom de venda. Para isso, use a skill [humanizer](https://github.com/blader/humanizer).
- **Autoria.** A skill não detecta nem prova uso de IA.
- **Conteúdo.** Não confere se fatos, números ou referências estão certos. Sinaliza o que se vê na página: número sem fonte ou com precisão inconsistente (B16). Um erro evidente notado de passagem (um sinal trocado, um total que não fecha) vai ao usuário como observação, sem correção.

## Fonte

Os padrões vêm do guia [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantido pelo [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup), e do verbete [AI slop](https://en.wikipedia.org/wiki/AI_slop) da Wikipedia; do texto da Anthropic [Improving frontend design through skills](https://claude.com/blog/improving-frontend-design-through-skills) e das skills [frontend-design](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) e [pptx](https://github.com/anthropics/skills/blob/main/skills/pptx/SKILL.md); do estudo sobre *workslop* da [Harvard Business Review](https://hbr.org/2025/09/ai-generated-workslop-is-destroying-productivity) (2025); e de diagnósticos em sites, decks e relatórios reais.
