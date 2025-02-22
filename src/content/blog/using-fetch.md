---
author: Daniel Ventura de Almeida
pubDatetime: 2025-02-21T23:14:00Z
modDatetime: 
title: Requisições com fetch()
slug: using-fetch-with-react
featured: true
draft: false
tags:
  - react
  - api
  - fetch
description:
  Guia prático para realizar requisições com fetch no React.
---

# Aula: Entendendo a função fetch() no JavaScript

A função `fetch()` é uma API nativa do JavaScript usada para fazer requisições HTTP de forma assíncrona. Com ela, podemos buscar dados de um servidor, enviar informações para uma API e interagir com serviços externos de maneira simples e eficiente.

## Table of contents


## Introdução

No conteúdo a seguir, vamos entender como a `fetch()` funciona, analisando um exemplo prático de requisição de login via `POST`. O foco será compreender o que cada parte da função representa e como manipulamos os dados recebidos.

---

## Como a Função fetch() Funciona?

A `fetch()` retorna uma `Promise`, que resolve em um objeto `Response`. Isso significa que precisamos utilizar `await` ou `then()` para manipular a resposta corretamente.

A estrutura básica de uma requisição `fetch()` é:

```js
fetch(url, options)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Erro:', error));
```

Agora, vamos analisar um exemplo real para um sistema de login em um contexto mais completo, utilizando React e estados para gerenciar os dados.

---

## Exemplo Prático: Requisição de Login com fetch()

### Código Completo

```js
import { useState } from 'react';

function Login() {
    const [registration, setRegistration] = useState('');
    const [password, setPassword] = useState('');
    const [errorApi, setErrorApi] = useState({});
    const [successApi, setSuccessApi] = useState('');

    async function handleLogin() {
        const loginObject = {
            registration: registration,
            password: password
        };

        try {
            const response = await fetch('https://endereco-da-minha-api.com.br/login', {
                method: "POST",
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(loginObject)
            });

            if (response.ok) {
                const data = await response.json();
                setSuccessApi('Login realizado com sucesso. Redirecionando...');
                setErrorApi({});
                return data;
            } else {
                const data = await response.json();
                setErrorApi(data);
                setSuccessApi('');
            }
        } catch (error) {
            setErrorApi('Ocorreu um erro na sua requisição.');
            console.log(error);
        }
    }

    return (
        <div>
            <input type="text" placeholder="Matrícula" value={registration} onChange={(e) => setRegistration(e.target.value)} />
            <input type="password" placeholder="Senha" value={password} onChange={(e) => setPassword(e.target.value)} />
            <button onClick={handleLogin}>Login</button>
            {successApi && <p>{successApi}</p>}
            {errorApi && <p style={{ color: 'red' }}>{errorApi}</p>}
        </div>
    );
}

export default Login;
```

---

## Explicação do Código

### 🔹 `useState`

- Gerencia os estados para armazenar a matrícula, senha, mensagens de erro e sucesso.

### 🔹 `fetch('https://daniel.cddtecnologia.com.br/login', {...})`

- Inicia uma requisição HTTP para a URL especificada.

### 🔹 `method: "POST"`

- Define que estamos enviando dados ao servidor.

### 🔹 `headers: { 'Content-Type': 'application/json' }`

- Define o tipo de dado que estamos enviando, no caso, um JSON.

### 🔹 `body: JSON.stringify({...})`

- Converte o objeto JavaScript em uma string JSON para ser enviado.

### 🔹 `response.ok`

- Verifica se a resposta foi bem-sucedida (`status` 200-299). Se sim, exibe a mensagem de sucesso.
- Caso contrário, captura a mensagem de erro retornada pela API.

### 🔹 `catch(error)`

- Captura erros na requisição, como falha na conexão.

---

## Conclusão

A função `fetch()` é uma ferramenta poderosa para interagir com APIs. Neste exemplo, vimos como enviar dados via `POST`, interpretar a resposta e tratar erros corretamente, aplicando isso dentro de um pequeno sistema de login com React.

---

## Referências

- [Documentação Oficial - Fetch API](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API)

