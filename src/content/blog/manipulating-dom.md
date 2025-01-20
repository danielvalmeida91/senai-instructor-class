---
author: Daniel Ventura de Almeida
pubDatetime: 2025-01-19T19:30:00Z
modDatetime: 
title: Manipulando a DOM
slug: manipulating-dom
featured: true
draft: false
tags:
  - javascript
  - dom
description:
  Manipulando a DOM com Javascript.
---
# Aula: Manipulação da DOM com JavaScript

## Introdução
A manipulação da DOM (Document Object Model) é uma das habilidades mais importantes ao trabalhar com JavaScript no desenvolvimento web. Através dela, podemos interagir dinamicamente com os elementos de uma página, alterando seu conteúdo, estilo e comportamento.

### O que é a DOM?
- **DOM**: Representação em forma de árvore do HTML e XML de um documento. Cada elemento do HTML é representado como um nó na árvore.
- O JavaScript pode acessar e modificar essa árvore para atualizar a interface do usuário sem recarregar a página.

### Objetivo da Aula
Ao final desta aula, você será capaz de:
1. Selecionar elementos HTML usando JavaScript.
2. Manipular conteúdo e atributos dos elementos.
3. Adicionar, remover e modificar elementos dinamicamente.
4. Trabalhar com eventos para criar interatividade.

---

## Parte 1: Selecionando Elementos
### Métodos de Seleção
1. **`getElementById`**: Seleciona um elemento pelo seu ID.
   ```javascript
   const titulo = document.getElementById('titulo');
   console.log(titulo.textContent);
   ```
2. **`querySelector`**: Seleciona o primeiro elemento que corresponde a um seletor CSS.
   ```javascript
   const paragrafo = document.querySelector('.texto');
   console.log(paragrafo.innerHTML);
   ```
3. **`querySelectorAll`**: Seleciona todos os elementos que correspondem a um seletor CSS.
   ```javascript
   const itens = document.querySelectorAll('li');
   itens.forEach(item => console.log(item.textContent));
   ```

---

## Parte 2: Manipulando Conteúdo
1. **Alterar Texto**
   ```javascript
   const titulo = document.getElementById('titulo');
   titulo.textContent = 'Novo Título';
   ```
2. **Alterar HTML Interno**
   ```javascript
   const container = document.querySelector('.container');
   container.innerHTML = '<p>Novo parágrafo adicionado!</p>';
   ```
3. **Alterar Atributos**
   ```javascript
   const imagem = document.querySelector('img');
   imagem.src = 'nova-imagem.jpg';
   imagem.alt = 'Descrição alternativa';
   ```

---

## Parte 3: Modificando Elementos
1. **Criar e Adicionar Elementos**
   ```javascript
   const novoElemento = document.createElement('div');
   novoElemento.textContent = 'Este é um novo elemento';
   document.body.appendChild(novoElemento);
   ```
2. **Remover Elementos**
   ```javascript
   const elementoParaRemover = document.querySelector('.remover');
   elementoParaRemover.remove();
   ```
3. **Estilizar Elementos**
   ```javascript
   const titulo = document.getElementById('titulo');
   titulo.style.color = 'blue';
   titulo.style.fontSize = '24px';
   ```

---

## Parte 4: Trabalhando com Eventos
1. **Adicionar Eventos**
   ```javascript
   const botao = document.querySelector('button');
   botao.addEventListener('click', () => {
       alert('Botão clicado!');
   });
   ```
2. **Eventos Mais Comuns**
   - `click`: Clique do mouse.
   - `mouseover`: Mouse passando sobre um elemento.
   - `keydown`: Tecla pressionada.

3. **Exemplo Completo**
   ```javascript
   const input = document.querySelector('input');
   const botao = document.querySelector('button');
   const lista = document.querySelector('ul');

   botao.addEventListener('click', () => {
       const texto = input.value;
       if (texto) {
           const item = document.createElement('li');
           item.textContent = texto;
           lista.appendChild(item);
           input.value = '';
       }
   });
   ```

---

<!-- ## Exercício Proposto
### Objetivo
Criar uma lista de tarefas dinâmica.

### Requisitos
1. Adicione um campo de texto e um botão na página.
2. Quando o botão for clicado, o texto do campo deve ser adicionado como um item da lista.
3. Cada item da lista deve ter um botão para removê-lo.

### Dica
Use os métodos de manipulação de elementos vistos na aula.

**Estrutura HTML Inicial:**
```html
<div>
    <input type="text" id="tarefa" placeholder="Digite uma tarefa">
    <button id="adicionar">Adicionar</button>
</div>
<ul id="lista"></ul>
```

**Script JavaScript:**
```javascript
const input = document.getElementById('tarefa');
const botao = document.getElementById('adicionar');
const lista = document.getElementById('lista');

botao.addEventListener('click', () => {
    const texto = input.value;
    if (texto) {
        const item = document.createElement('li');
        item.textContent = texto;
        const botaoRemover = document.createElement('button');
        botaoRemover.textContent = 'Remover';
        botaoRemover.addEventListener('click', () => {
            item.remove();
        });
        item.appendChild(botaoRemover);
        lista.appendChild(item);
        input.value = '';
    }
});
```

--- -->

## Conclusão
Com essas técnicas, você pode criar páginas interativas e dinâmicas, manipulando a DOM com JavaScript. Experimente aplicar o que aprendeu em projetos próprios e explore mais eventos e métodos disponíveis. 🚀
