---
author: Daniel Ventura de Almeida
pubDatetime: 2025-01-14T20:22:00Z
modDatetime: 
title: Utilizando Arrays em JavaScript
slug: arrays-in-javascript
featured: true
draft: false
tags:
  - javascript
  - arrays
description:
  Como utilizar arrays em javascript.
---

Principais Funcionalidades de um Array


Criação de Arrays:

const array = [1, 2, 3, 4];
const arrayVazio = new Array(5); // Cria um array com 5 posições vazias



Acesso aos Elementos:

const frutas = ['Maçã', 'Banana', 'Laranja'];
console.log(frutas[0]); // Maçã



Adicionar Elementos:

    push: Adiciona ao final do array.

frutas.push('Manga');


unshift: Adiciona ao início do array.

    frutas.unshift('Uva');



Remover Elementos:

    pop: Remove o último elemento.

frutas.pop(); // Remove 'Manga'

shift: Remove o primeiro elemento.

    frutas.shift(); // Remove 'Uva'



Percorrer Arrays:

    forEach: Executa uma função para cada elemento.

    frutas.forEach((fruta) => console.log(fruta));



Mapeamento:

    map: Cria um novo array transformado.

    const numeros = [1, 2, 3];
    const dobrados = numeros.map((num) => num * 2);



Filtragem:

    filter: Cria um novo array com elementos que passam no teste.

    const maioresQue2 = numeros.filter((num) => num > 2);



Busca:

    find: Retorna o primeiro elemento que passa no teste.

const busca = numeros.find((num) => num > 1);

includes: Verifica se um valor existe no array.

        console.log(numeros.includes(2)); // true



Exercícios com Arrays

    - Crie um array com 10 números e exiba apenas os números pares.
    - Adicione um novo item ao início e ao final de um array.
    - Remova o primeiro e o último item de um array.
    - Crie um array com nomes e filtre apenas os nomes que começam com a letra "A".
    - Faça um array de números e multiplique todos os elementos por 5 usando o map.
    - Inverta a ordem de um array com o método reverse.
    - Verifique se um número está presente no array usando includes.
    - Ordene um array de números em ordem crescente.
    - Faça a soma de todos os números em um array com o método reduce.
    - Encontre o maior número de um array.