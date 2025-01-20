---
author: Daniel Ventura de Almeida
pubDatetime: 2024-12-19T23:00:00Z
modDatetime: 
title: Flexbox - Guia de utilização
slug: flexbox-layout
featured: true
draft: false
tags:
  - flexbox
  - css
description:
  Desvendando o flexbox layout.
---

# Guia sobre Flexbox Layout

O Flexbox Layout é um modelo de layout no CSS projetado para distribuir espaço de forma eficiente e alinhar itens em um contêiner, mesmo quando suas dimensões são dinâmicas.

## Table of contents

## Propriedades do Contêiner Flex

### `display`
Define o elemento de classe `container` como flex.
```css
.container {
  display: flex;
}
```

### `flex-direction`
Controla a direção principal do eixo.
```css
.container {
  flex-direction: row;      /* padrão */
  flex-direction: row-reverse;
  flex-direction: column;
  flex-direction: column-reverse;
}
```

### `flex-wrap`
Determina se os itens devem quebrar para uma nova linha.
```css
.container {
  flex-wrap: nowrap;        /* padrão */
  flex-wrap: wrap;
  flex-wrap: wrap-reverse;
}
```

### `flex-flow`
Combina `flex-direction` e `flex-wrap`.
```css
.container {
  flex-flow: row wrap;
}
```

### `justify-content`
Alinha os itens ao longo do eixo principal.
```css
.container {
  justify-content: flex-start; /* padrão */
  justify-content: flex-end;
  justify-content: center; /* mais comum */
  justify-content: space-between;
  justify-content: space-around;
  justify-content: space-evenly;
}
```

### `align-items`
Alinha os itens ao longo do eixo transversal.
```css
.container {
  align-items: stretch;     /* padrão */
  align-items: center;      /* mais comum */
  align-items: flex-start;
  align-items: flex-end;
  align-items: baseline;
}
```

### `align-content`
Controla o espaçamento das linhas quando há múltiplas linhas.
```css
.container {
  align-content: stretch;   /* padrão */
  align-content: flex-start;
  align-content: flex-end;
  align-content: center;
  align-content: space-between;
  align-content: space-around;
  align-content: space-evenly;
}
```

---

## Propriedades dos Itens Flex

### `order`
Controla a ordem de exibição dos itens.
```css
.item {
  order: 0; /* padrão */
}
```

### `flex-grow`
Define a proporção de crescimento de um item.
```css
.item {
  flex-grow: 0; /* padrão */
}
```

### `flex-shrink`
Define a proporção de encolhimento de um item.
```css
.item {
  flex-shrink: 1; /* padrão */
}
```

### `flex-basis`
Define o tamanho inicial do item antes da distribuição de espaço.
```css
.item {
  flex-basis: auto; /* padrão */
}
```

### `flex`
Atalho para `flex-grow`, `flex-shrink` e `flex-basis`.
```css
.item {
  flex: 1 1 auto;
}
```

### `align-self`
Alinha individualmente um item ao longo do eixo transversal.
```css
.item {
  align-self: auto; /* padrão */
  align-self: flex-start;
  align-self: flex-end;
  align-self: center;
  align-self: baseline;
  align-self: stretch;
}
```

---

## Exemplo Prático
```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```
```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
}

.item {
  flex: 1;
  padding: 10px;
  text-align: center;
  background-color: #ccc;
  margin: 5px;
}
```

---

## Dicas Úteis
- Utilize `flex: 1;` para que os itens cresçam igualmente dentro do contêiner.
- Combine `justify-content` e `align-items` para centralizar elementos facilmente.
- Lembre-se de testar com diferentes valores de `flex-wrap` para garantir que o layout se adapte a diferentes tamanhos de tela.

Com essas propriedades, você terá o controle completo para criar layouts responsivos e eficientes usando Flexbox!
---