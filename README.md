# Forno & Fogo — Monte sua pizza

Landing page de uma pizzaria (fictícia) de forno a lenha, com um **montador de pizza interativo** em que o cliente arrasta os ingredientes até a pizza, um **cardápio tradicional** completo e um **pedido único** que junta as duas coisas.

Site estático: HTML, CSS e JavaScript puros, sem build e sem dependências.

## O que tem no site

- **Hero** com a pizza girando conforme a rolagem e botões para montar ou ver o cardápio.
- **Montador**: tamanho, massa e molho; 24 ingredientes para arrastar e soltar (mouse e toque), limites de porções, desfazer, "Surpreenda-me", conquistas e preço em tempo real.
- **Cardápio**: pizzas com preço por tamanho, adicionais, entradas, bebidas e sobremesas, com botão de adicionar ao pedido.
- **Pedido**: resumo, revisão, formulário com validação (entrega ou retirada, Pix/cartão/dinheiro) e envio do resumo pelo WhatsApp. O pedido é simulado no navegador (não há back-end).
- **Onde estamos**: foto da galera, painel de chamada e cartão com mapa, endereço e horários.
- Animações de entrada ao rolar, layout responsivo e progresso salvo no navegador (`localStorage`).

## Estrutura

```
index.html                       página completa (HTML + CSS + JS)
img/pizza-pepperoni.webp         pizza do hero
img/cliente-comendo-pizza.webp   seção "Como funciona"
img/galera-pizza.webp            seção "Onde estamos"
```

## Rodar no computador

Abra o `index.html` no navegador, ou sirva a pasta para testar como ficará no ar:

```bash
npx serve .
```

## Publicar

### 1. GitHub

Crie um repositório vazio em <https://github.com/new> (sem README, sem .gitignore) e, nesta pasta:

```bash
git remote add origin https://github.com/SEU-USUARIO/forno-e-fogo.git
git push -u origin main
```

### 2. Vercel

1. Entre em <https://vercel.com/new> e importe o repositório do GitHub.
2. **Framework Preset:** `Other`. Deixe **Build Command** vazio e **Output Directory** como está (raiz).
3. Clique em **Deploy**. A cada `git push` na `main`, a Vercel publica de novo sozinha.

## Personalizar

Tudo fica no começo do `<script>` do `index.html`:

| O quê | Onde |
|---|---|
| Tamanhos, massas, molhos e preços do montador | `SIZES`, `CRUSTS`, `SAUCES`, `CATEGORIES` |
| Ingredientes (nome, preço, desenho) | `INGREDIENTS` e `PIECE_ART` |
| Cardápio (sabores, preço por tamanho, disponibilidade, etiquetas) | `MENU` e `MENU_TAGS` |
| Frases da faixa animada | `TICKER` |
| Quais elementos animam ao rolar | `REVEAL_TARGETS` |

Cores e fontes ficam nas variáveis CSS do `:root`, no começo do `<style>`.

## Antes de usar de verdade

- **Preços do cardápio são exemplos** — troque pelos valores reais em `MENU`.
- **Endereço, telefone e horários são fictícios** — estão no rodapé e na seção "Onde estamos" (o link "Ver no mapa" busca esse endereço no Google Maps).
- Os links das redes sociais no rodapé apontam para `#`.
- O pedido não é enviado a um servidor: a confirmação é simulada e o cliente pode mandar o resumo pelo WhatsApp.
