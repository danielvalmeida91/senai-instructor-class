---
author: Daniel Ventura de Almeida
pubDatetime: 2025-01-31T20:15:00Z
modDatetime: 
title: Iniciando no React
slug: my-first-react-app
featured: true
draft: false
tags:
  - react
  - vite
  - react-router-dom
description:
  Seu primeiro projeto em React
---
# Aula: Primeiros Passos com React e Vite

## Table of Contents

## Introdução

React é uma biblioteca JavaScript amplamente utilizada para a criação de interfaces de usuário dinâmicas e eficientes. Para iniciar um projeto React moderno, uma das ferramentas mais recomendadas é o Vite, um empacotador leve e rápido que melhora a experiência de desenvolvimento.

Neste guia, vamos aprender a instalar e configurar um projeto React utilizando o Vite, seguido de um resumo dos principais conceitos do React.

---

## Passo a Passo: Instalando React com Vite

### 1. Instalando o Node.js

Antes de começar, é necessário ter o Node.js instalado em sua máquina. Para verificar se o Node.js já está instalado, execute o seguinte comando no terminal:

```sh
node -v
```

Se não estiver instalado, faça o download e a instalação a partir do site oficial: [https://nodejs.org/](https://nodejs.org/)

### 2. Criando um Projeto React com Vite

Após garantir que o Node.js está instalado, siga os passos abaixo para criar um projeto React utilizando o Vite:

1. Abra o terminal e execute:

   ```sh
   npm create vite@latest my-react-app
   ```

2. Durante a instalação, será solicitado o nome do projeto (você pode manter "my-react-app" ou escolher outro nome).
3. Selecione "React" como framework.
4. Escolha "JavaScript" ou "TypeScript", conforme sua preferência.
5. Acesse a pasta do projeto:

   ```sh
   cd my-react-app
   ```

6. Instale as dependências do projeto:

   ```sh
   npm install
   ```

### 3. Rodando o Servidor de Desenvolvimento

Agora que o projeto está configurado, execute o seguinte comando para iniciar o servidor de desenvolvimento:

```sh
npm run dev
```

Isso iniciará o servidor local e exibirá a URL no terminal (geralmente `http://localhost:5173`). Abra essa URL no navegador para visualizar seu projeto React funcionando.

---

## Principais Conceitos do React

### 1. Componentes

O React é baseado em **componentes**, que são funções JavaScript que retornam elementos JSX. Cada componente pode ser reutilizado e combinado para criar interfaces complexas.

Exemplo de um componente simples:

```jsx
function Welcome() {
    return <h1>Olá, mundo!</h1>;
}
```

### 2. JSX (JavaScript XML)

JSX é uma sintaxe que permite escrever HTML dentro do JavaScript. Ele facilita a criação da interface do usuário de maneira declarativa.

Exemplo de JSX:

```jsx
const element = <h1>Bem-vindo ao React!</h1>;
```

### 3. Estado e Props

- **Estado (`useState`)**: Permite que componentes armazenem e gerenciem dados dinâmicos.
- **Props (Propriedades)**: Permitem passar dados de um componente pai para um componente filho.

Exemplo de uso do `useState`:

```jsx
import { useState } from 'react';

function Contador() {
    const [contador, setContador] = useState(0);
    
    return (
        <div>
            <p>Contador: {contador}</p>
            <button onClick={() => setContador(contador + 1)}>Incrementar</button>
        </div>
    );
}
```

### 4. Efeitos Colaterais (`useEffect`)

O `useEffect` permite a execução de efeitos colaterais, como chamadas de API ou manipulação do DOM, dentro de um componente funcional.

```jsx
import { useEffect, useState } from 'react';

function DadosAPI() {
    const [dados, setDados] = useState([]);
    
    useEffect(() => {
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then(response => response.json())
            .then(data => setDados(data));
    }, []);

    return (
        <ul>
            {dados.slice(0, 5).map(item => (
                <li key={item.id}>{item.title}</li>
            ))}
        </ul>
    );
}
```

### 5. Roteamento com React Router

Para criar navegação entre páginas no React, utilizamos o **React Router**.

Instale o React Router:
```sh
npm install react-router-dom
```

Exemplo básico de roteamento:

```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
    return (
        <BrowserRouter>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
            </Routes>
        </BrowserRouter>
    );
}
```

---

## Conclusão

Agora você tem um projeto React configurado com Vite e uma compreensão básica dos conceitos fundamentais do React.

---

## Referências

- [Documentação do Vite](https://vitejs.dev/)
- [Documentação do React](https://react.dev/)
- [React Router](https://reactrouter.com/)


