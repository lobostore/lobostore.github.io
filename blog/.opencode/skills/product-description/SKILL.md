---
name: product-description
description: Use when creating or updating a product description in content/produtos/*.md. Follows the mouse.md pattern: full front matter (price in reais, specs, link_afiliado, gallery) plus sales sections (specs, what's in the box, competitors, why it's better, quick summary).
---

# Composição de descrição de produto

Crie ou edite arquivos em `content/produtos/` seguindo o modelo canônico
`content/produtos/mouse.md` — **leia-o antes de começar** e reproduza sua
estrutura e tom.

## Front matter obrigatório

```yaml
---
title: "<Nome completo do produto>"
summary: "<1 frase curta de venda, ~15-20 palavras>"
price: "R$ <preço atual, formato brasileiro R$ 1.234,56>"
old_price: "R$ <preço original, opcional>"
image: "<url da imagem principal ou /images/<nome>.svg>"
featured: true # só no produto em destaque (contorno tracejado + selo)
specs:
  - "<ponto técnico 1>"
  - "<ponto técnico 2>"
link_afiliado: "<link de afiliado real>"
cta_label: "COMPRAR NO MERCADO LIVRE" # ou "COMPRAR NA AMAZON"
gallery:
  - "<url da imagem 1>"
  - "<url da imagem 2>"
---
```

Campos-chave:

- `link_afiliado` é crítico: vira o `href` do botão de compra em
  `layouts/_default/single.html`.
- `price` sempre em **reais** (`R$ 1.234,56`); `old_price` opcional para
  exibir desconto. Obtenha o valor do link de afiliado, nunca invente.
- `specs` são strings curtas, renderizadas como lista.
- `gallery` alimenta as miniaturas clicáveis da página do produto.
- `cta_label` define o texto do botão conforme a loja (Mercado Livre/Amazon).

## Estrutura do corpo (markdown)

Use esta ordem. Cada `##` vira uma faixa de título em largura total (já
estilizada no CSS); o conteúdo abaixo dela flui em 2 colunas.

1. **Parágrafo de abertura** — 2 a 3 frases vendendo o produto, citando 1-2
   números de impacto.
2. `## Especificações e compatibilidade`
   - `### Dimensões` — altura/largura/comprimento/peso. **Sempre compare o
     peso com algo cotidiano entre parênteses** (ex.: `51 g (aproximadamente o
     peso de 2 pilhas AA)`).
   - `### Especificações técnicas` — subgrupos em negrito (`**Geral**`,
     `**Sensor**`, `**Responsividade**`, `**Bateria**`, `**Requisitos do
     sistema**`).
3. `## O que vem na caixa` — lista dos itens inclusos.
4. `## Software e suporte` — como configurar + suporte/garantia do fabricante.
5. `## Com quais mouses ele concorre?` — rivais diretos com nome, peso, sensor
   e diferencial.
6. `## Por que o <produto> é melhor?` — 3 a 5 argumentos de venda em
   subtítulos `###`; cada um com parágrafo + citação `>` no estilo
   "como falar para o cliente".
7. `## Resumo rápido` — citação final `>` pronta para copiar/colar
   (WhatsApp/balcão).

## Regras de escrita

- **Foco em venda**: números e comparações diretas ("mais leve que X",
  "44K DPI contra 35K"), gatilhos de vantagem competitiva.
- **Português do Brasil**, tom profissional.
- **Hiperlinks** em palavras-chave técnicas que precisam de explicação
  (sensor, DPI, PTFE, tecnologia sem fio). Use URLs verificadas (Wikipédia PT
  ou site oficial do fabricante) — nunca adivinhe links.
- **Comparação de peso** sempre com referência cotidiana entre parênteses.
- Não invente dados: use apenas specs/valores fornecidos ou verificados.
- Ao finalizar, rode `hugo --minify` e confirme que a página renderiza sem
  erros (ver `AGENTS.md`).
