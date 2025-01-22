---
author: Daniel Ventura de Almeida
pubDatetime: 2025-01-21T18:10:00Z
modDatetime: 
title: Requisições HTTP
slug: http-request
featured: true
draft: false
tags:
  - javascript
  - http
  - requests
description:
  Requisições HTTP, abordagem prática em Javascript.
---

---

# Aula: Requisições HTTP - Estrutura e Funcionamento

## Table of Contents

---

## 1. O que é HTTP?
HTTP (HyperText Transfer Protocol) é um protocolo de comunicação que permite a troca de informações entre clientes (como navegadores) e servidores. Ele é utilizado para transferir documentos, imagens, vídeos, e outros recursos necessários para exibir páginas web.

Características principais:
- **Protocolo sem estado:** Cada requisição é independente, ou seja, o servidor não mantém informações sobre as requisições anteriores (exceto em casos como cookies ou sessões).
- **Baseado em texto:** Todas as mensagens são humanamente legíveis, o que facilita a depuração.

---

## 2. Estrutura de uma Requisição HTTP
Uma requisição HTTP possui três partes principais:

### a) Linha de Requisição
Define a intenção do cliente.

**Formato:**
```
<Método> <URI> <Versão do Protocolo>
```

**Exemplo:**
```
GET /home HTTP/1.1
```
- **Método:** A ação desejada (ex.: GET, POST).
- **URI:** O recurso solicitado (ex.: `/home`).
- **Versão:** Indica a versão do HTTP (ex.: `HTTP/1.1`).

### b) Cabeçalhos de Requisição
Informam detalhes adicionais sobre a requisição.

**Exemplo:**
```
Host: www.exemplo.com
User-Agent: Mozilla/5.0
Content-Type: application/json
```
- **Host:** O domínio do servidor.
- **User-Agent:** Identifica o cliente que está enviando a requisição.
- **Content-Type:** Define o formato dos dados enviados.

### c) Corpo da Requisição (Opcional)
Inclui os dados enviados para o servidor (comum em métodos como POST e PUT).

**Exemplo:**
```json
{
  "username": "daniel",
  "password": "123456"
}
```

---

## 3. Métodos HTTP
Os métodos HTTP determinam a intenção da requisição. Aqui estão os principais:

- **GET:** Solicita um recurso do servidor. (Ex.: Página HTML, JSON, etc.)
- **POST:** Envia dados para o servidor criar um novo recurso.
- **PUT:** Atualiza ou cria um recurso no servidor.
- **DELETE:** Remove um recurso.
- **PATCH:** Atualiza parcialmente um recurso.
- **OPTIONS:** Retorna as opções de comunicação para um recurso.
- **HEAD:** Igual ao GET, mas sem o corpo da resposta (usado para verificar cabeçalhos).

---

## 4. Estrutura de uma Resposta HTTP

Uma resposta HTTP é composta por:

### a) Linha de Status
Fornece informações sobre o estado da requisição.

**Formato:**
```
<Versão HTTP> <Código de Status> <Mensagem Descritiva>
```

**Exemplo:**
```
HTTP/1.1 200 OK
```
- **Versão:** Versão do protocolo (ex.: `HTTP/1.1`).
- **Código de Status:** Indica o resultado (detalhado abaixo).
- **Mensagem Descritiva:** Texto explicativo do código de status.

### b) Códigos de Status HTTP (Detalhamento)

Os códigos de status são divididos em 5 categorias:

1. **1xx - Informacional**
   - **100 Continue:** O servidor está pronto para receber o restante da requisição.

2. **2xx - Sucesso**
   - **200 OK:** A requisição foi bem-sucedida.
   - **201 Created:** Um novo recurso foi criado.

3. **3xx - Redirecionamento**
   - **301 Moved Permanently:** O recurso foi movido para outra URL.
   - **302 Found:** O recurso foi encontrado temporariamente em outra URL.

4. **4xx - Erro do Cliente**
   - **400 Bad Request:** A requisição está malformada.
   - **401 Unauthorized:** É necessário autenticação.
   - **404 Not Found:** O recurso solicitado não foi encontrado.

5. **5xx - Erro do Servidor**
   - **500 Internal Server Error:** Um erro genérico ocorreu no servidor.
   - **503 Service Unavailable:** O servidor está indisponível temporariamente.

### c) Cabeçalhos de Resposta
Contêm informações adicionais sobre os dados retornados.

**Exemplo:**
```
Content-Type: application/json
Content-Length: 123
```
- **Content-Type:** Tipo de dado retornado (ex.: `application/json`, `text/html`).
- **Content-Length:** Tamanho do corpo em bytes.

### d) Corpo da Resposta
Contém os dados retornados (HTML, JSON, etc.).

**Exemplo:**
```json
{
  "id": 1,
  "title": "Hello World",
  "body": "Esta é uma mensagem de exemplo."
}
```

---

## 5. Prática: Requisições HTTP com JavaScript

### Exemplo 1: Requisição GET
```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => {
    if (!response.ok) {
      throw new Error('Erro na requisição: ' + response.status);
    }
    return response.json();
  })
  .then(data => console.log('Dados recebidos:', data))
  .catch(error => console.error('Erro:', error));
```

### Exemplo 2: Requisição POST
```javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    title: 'Novo Post',
    body: 'Conteúdo do post.',
    userId: 1
  })
})
  .then(response => response.json())
  .then(data => console.log('Recurso criado:', data))
  .catch(error => console.error('Erro:', error));
```

---

## Conclusão
Nesta aula, exploramos a estrutura e funcionamento das requisições HTTP, com foco nos elementos de uma resposta HTTP e práticas em JavaScript. Este conhecimento é essencial para desenvolver aplicações web modernas que se comunicam eficientemente com servidores.



**Referências**

- [Documentação MDN - Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [Documentação MDN - HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
