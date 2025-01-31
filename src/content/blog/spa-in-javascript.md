---
author: Daniel Ventura de Almeida
pubDatetime: 2025-01-30T23:45:00Z
modDatetime: 
title: Criando uma SPA com Javascript
slug: spa-in-javascript
featured: true
draft: false
tags:
  - javascript
  - fetch
  - routes
description:
  Como criar uma SPA utilizando javascript Vanilla.
---
# Aula: Criando uma SPA (Single Page Application) com JavaScript Vanilla

## Table of Contents

## Introdução

Single Page Applications (SPA) são aplicações web que carregam uma única página HTML e atualizam dinamicamente o conteúdo conforme necessário, sem recarregar a página. Frameworks como React e Vue facilitam a criação de SPAs, mas também é possível desenvolver uma SPA utilizando apenas JavaScript Vanilla.

Vamos construir uma SPA simples que carrega dinamicamente quatro páginas HTML diferentes utilizando `fetch` e atualiza o conteúdo dentro de uma `<div id="app">`.

---

## Estrutura do Projeto

Nosso projeto será estruturado da seguinte maneira:
```
/spa-project
│──── pages
│────── about.html
│────── contact.html
│────── home.html
│────── 404.html
│── index.html
│── route.js
```

- `index.html`: Página principal que contém a estrutura básica da aplicação.
- `home.html`, `about.html`, `contact.html`, `404.html`: Páginas adicionais cujo conteúdo será carregado dinamicamente.
- `route.js`: Código responsável pela manipulação da SPA.
- `styles.css`: Arquivo de estilos da aplicação.

---

## Passo 1: Criando o index.html

O `index.html` conterá um container `<div id="app">` onde será carregado o conteúdo das outras páginas.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="background-color: #202020; color: #fafafa;">
    <nav>
        <a style="text-decoration: none; color: #fafafa;" href="/" onclick="route()">Home</a>
        <a style="text-decoration: none; color: #fafafa;" href="/about" onclick="route()">Sobre</a>
        <a style="text-decoration: none; color: #fafafa;" href="/contact" onclick="route()">Contato</a>
        <a style="text-decoration: none; color: #fafafa;" href="/404" onclick="route()">404</a>
    </nav>

    <div id="app"></div>

    <script src="/route.js" type="module">
        
    </script>
</body>
</html>
```

---

## Passo 2: Criando as Páginas Adicionais

### home.html
```html
<h1>Home Page</h1>
```

### about.html
```html
<h1>Pagina About</h1>

```
### 404.html
```html
<h1>Página não encontrada !</h1>
```

### contact.html
```html
<h1>Pagina de contato</h1>

<form>
    <input type="text" name="name" id="name" placeholder="Nome">
    <input type="email" name="email" id="email" placeholder="Email">
    <textarea name="text" id="text" placeholder="Insira aqui sua mensagem"></textarea>
    <button id="btn-submit">Enviar</button>
</form>
```

---

## Passo 3: Criando o Script de Manipulação (route.js)

Agora, vamos escrever o código responsável por capturar a mudança na URL e carregar o conteúdo das páginas corretamente.

```javascript
class Route {
    constructor(routes = {}){
        this.routes = routes
    }

    addRoute(route, pathname){
        this.routes[route] = pathname
    }

    route(event) {
        event = event || window.event
        event.preventDefault()
        window.history.pushState({}, "", event.target.href)

        this.handle()
    }

    handle(){
        const { pathname } = window.location
        const route = this.routes[pathname] || this.routes[404] 
        fetch(route)
            .then(data => data.text())
            .then(html => document.querySelector("#app").innerHTML = html)
    }

}

const route = new Route()
route.addRoute('/', '/pages/home.html')
route.addRoute("/contact", '/pages/contact.html')
route.addRoute("/about", '/pages/about.html')
route.addRoute("404", '/pages/404.html')
route.addRoute('/senai', '/pages/contact.html')

route.handle()

window.onpopstate = () => route.handle()
window.route = () => route.route()
```

---

## Conclusão

Agora, sempre que o usuário clicar em um link de navegação, o path da URL mudará, e o JavaScript carregará dinamicamente o conteúdo correto sem recarregar a página.

Dessa forma, conseguimos criar uma SPA básica apenas com JavaScript Vanilla! 🚀

