# Web: sites, painéis e relatórios publicados como página

Use junto com `base.md`. Os códigos W1 a W6 seguem a força do sinal.

## Onde procurar

Percorra as páginas renderizadas (início, uma página de dados, uma de texto longo, todas também a 375px) e o código. Comece pela busca dos sinais de `base.md` nas fontes de estilo:

```
grep -rnE 'border-(top|left):\s*[2-9]px|box-shadow|border-radius:\s*([6-9]|[1-9][0-9])px|border-radius:\s*[0-9.]+r?em|font-weight:\s*(600|700|800|900|bold)|letter-spacing:\s*-|text-transform:\s*uppercase|linear-gradient|backdrop-filter|font-family:' <estilos>
grep -rniE '#(3B82F6|2563EB|1D4ED8|0D6EFD|6366F1|8B5CF6|A855F7|F8FAFC|F1F5F9|E2E8F0|CBD5E1|64748B)' <estilos e código>
grep -rnE '<(strong|b)>| · |&middot;|→|&rarr;' <html>
```

A lista de hex só pega os valores exatos do framework. Liste também todas as cores do projeto (`grep -oiE '#[0-9a-f]{3,8}\b' <estilos> | sort | uniq -c`) e classifique pelo matiz: azuis saturados entre 200° e 235° contam para B1, cinzas com matiz azul para B3. Inclua tokens dos gráficos e cores fixas em JS. Para títulos que só nomeiam o tema e seções de molde numa página, use D10 de `documentos.md`. Uma regra nova que não pega quase sempre perde para um seletor mais específico do tema: meça o estilo computado (`getComputedStyle`) antes de concluir.

## Padrões

### W1. Hero de landing page

**Sinal:** bloco escuro ou em degradê no topo, com título enorme e dois botões (um cheio, um vazado), ou um número grande com legenda e estatísticas de apoio. Basta uma das duas metades; registre B2 e B16 dentro deste código.
**Problema:** é a abertura de fábrica de qualquer produto; num relatório ou site institucional, não serve ao leitor.
**Substituto:** título e chamada sobre o fundo; uma ação sólida na tinta e a secundária como link de texto. Abra com o que é mais característico do assunto (um dado, uma figura, o texto).
**Não agir quando:** a página é de fato uma landing de produto, e mesmo assim só se o hero tiver conteúdo próprio.

### W2. Página toda em link

**Sinal:** títulos de cartão e de seção como links sublinhados na cor de destaque; tudo clicável parece igual.
**Substituto:** título na tinta, com sublinhado ou mudança de cor só no hover e no foco; link sublinhado no acento só dentro do texto.

### W3. Kit de navegação e painel

**Sinal:** barra lateral com ícone em cada item, item ativo em pílula azul, selos "Novo" ou "Live" pulsando, cabeçalho com avatar e sino sem função.
**Substituto:** navegação em texto, item ativo marcado por peso e um filete do acento; selo só quando há estado real.
*Fraco sozinho.*

### W4. Animação igual em tudo

**Sinal:** cada seção entra com fade e deslize para cima; todo cartão muda no hover; microefeitos espalhados.
**Problema:** a Anthropic lista esse padrão como lido de imediato como gerado.
**Substituto:** um momento de movimento orquestrado, ou nenhum; movimento que responde a uma ação do usuário (abrir, expandir, confirmar) fica.
**Não agir quando:** a animação mostra uma mudança de estado.
*Fraco sozinho.*

### W5. Moldura de template

**Sinal:** metadados unidos por pontos médios (`A · B · C`); rótulos "PALAVRA — fragmento" com travessão; fonte monoespaçada em rótulos que não são código nem dado; seta `→` anexada a todo link e botão.
**Substituto:** metadados em texto suave separados por vírgula ou em linhas; affordance de link pelo sublinhado.
*Fraco sozinho.*

### W6. Modo escuro de fábrica

**Sinal:** fundo `#0B0B0B` ou `#111` no lugar do preto do projeto, com um acento ácido; tema escuro que só inverte as cores, sem rever contraste.
**Substituto:** tema escuro derivado dos tokens do projeto, com contraste recalculado.
*Fraco sozinho.*

## Verificação

Rode os testes do projeto e o axe (WCAG 2.1 AA) na página inteira, com navegação e rodapé, a 1280px e a 375px, em toda família de página, inclusive as que a suíte não cobre. Gere capturas antes e depois no mesmo navegador. Se a pasta do projeto é sincronizada na nuvem e o render falha por trava de disco, renderize de uma cópia fora dela.
