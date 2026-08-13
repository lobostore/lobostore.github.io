# Skill: Criar Descrição de Produto

Use esta skill quando o usuário pedir para criar ou atualizar uma descrição de produto em `blog/content/produtos/`.

## Estrutura do arquivo

Cada produto é um arquivo `.md` em `blog/content/produtos/` com front-matter YAML e conteúdo em Markdown.

## Front-matter obrigatório

```yaml
---
title: "Nome Completo do Produto"
summary: "Descrição curta em uma linha com dados-chave."
price: "R$ 000,00"
old_price: "R$ 000,00"  # opcional
image: "URL da imagem principal"
featured: false  # true para produtos em destaque
specs:
  - "Especificação 1"
  - "Especificação 2"
link_afiliado: "URL do link de afiliado"
cta_label: "COMPRAR"
gallery:
  - "URL da imagem 1"
  - "URL da imagem 2"
videos:
  - "URL do vídeo 1"
---
```

## Estrutura do conteúdo Markdown

Seguir esta ordem de seções:

1. **Parágrafo introdutório** — Descrição geral do produto em 2-3 frases, destacando benefícios principais.

2. **## Especificações e compatibilidade**
   - ### Dimensões (se aplicável)
   - ### Especificações técnicas (com subsections por categoria)
   - ### Requisitos do sistema (se aplicável)

3. **## O que vem na caixa**
   - Lista com todos os itens incluídos

4. **## Software e suporte**
   - Informações sobre apps, garantia e suporte do fabricante

5. **## Com quais [categoria] ele concorre?**
   - Comparação com produtos similares
   - Formato: **Nome do Produto** — breve descrição

6. **## Por que o [Nome] é melhor?**
   - Vantagens competitivas detalhadas
   - Usar subsections (###) para cada vantagem
   - Incluir quotes > para dados de impacto

7. **## Resumo rápido**
   - Blocoquote > com resumo executivo em 3-4 linhas

## Convenções

- Texto em **pt-BR** (português brasileiro)
- Usar negrito **para termos técnicos e dados numéricos**
- Links para referências (Wikipedia, sites oficiais) quando relevante
- Preços no formato brasileiro: `R$ 1.234,56`
- Imagens usar URLs absolutas
- Não usar emojis
- Não adicionar comentários HTML
