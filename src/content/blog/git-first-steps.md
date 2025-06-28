---
author: Daniel Ventura de Almeida
pubDatetime: 2025-06-26T21:52:00Z
modDatetime: 2025-06-26T21:24:00Z
title: GIT - Primeiros passos
slug: git-first-steps
featured: true
draft: false
tags:
  - git
description:
  Guia prático para iniciar com github
---

# Guia Prático de Git: Seus Primeiros Passos no Controle de Versão

Bem-vindo ao seu guia inicial de Git! O objetivo deste tutorial é apresentar os conceitos e comandos fundamentais que você precisa para começar a versionar seus projetos. Vamos do zero até a criação do seu primeiro repositório, commit e branch.

## Table of Contents
* [Pré-requisitos: Navegando no Terminal](#pré-requisitos-navegando-no-terminal)
* [Os 3 Estágios do Git](#os-3-estágios-do-git)
* [Passo 1: Configurando sua Identidade](#passo-1-configurando-sua-identidade)
* [Passo 2: Criando seu Primeiro Repositório](#passo-2-criando-seu-primeiro-repositório)
* [Passo 3: Trabalhando com Branches](#passo-3-trabalhando-com-branches)
* [Passo 4: Marcando Versões com Tags](#passo-4-marcando-versões-com-tags)

---

## Pré-requisitos: Navegando no Terminal

Antes de usar o Git, é essencial ter familiaridade com alguns comandos básicos do terminal para navegar entre pastas e arquivos.

* **`cd` (Change Directory):** Muda de diretório (pasta).
    ```bash
    # Entra na pasta 'Documentos'
    cd Documentos
    ```

* **`mkdir` (Make Directory):** Cria um novo diretório.
    ```bash
    # Cria uma pasta chamada 'meu-projeto'
    mkdir meu-projeto
    ```

* **`ls` (List):** Lista os arquivos e pastas no diretório atual.
    ```bash
    ls
    ```

* **`pwd` (Print Working Directory):** Mostra o caminho completo do diretório em que você está.
    ```bash
    pwd
    ```

---

## Os 3 Estágios do Git

Para o Git, seus arquivos podem estar em três estágios principais. Entender isso é a chave para dominar o Git.

1.  **Working Directory (Área de Trabalho):** É a sua pasta de projeto. Qualquer arquivo que você cria ou modifica aqui é visto pelo Git como uma alteração, mas ainda não está sendo rastreado para o próximo "save".
2.  **Staging Area (Área de Preparação):** Pense nisso como uma sala de espera. Depois de fazer alterações, você usa o comando `git add` para mover os arquivos para a Staging Area. É aqui que você prepara o "pacote" de alterações que farão parte do seu próximo ponto de salvamento.
3.  **Repository (Repositório / `.git`):** Após preparar os arquivos, você usa o comando `git commit` para salvá-los permanentemente no histórico do seu projeto. Cada commit é um ponto na linha do tempo, com um identificador único.

---

## Passo 1: Configurando sua Identidade

Antes de tudo, você precisa dizer ao Git quem você é. Isso é importante porque cada commit que você fizer será assinado com seu nome e e-mail.

* **Configuração Global (Recomendado):** Faça isso uma vez para todos os seus projetos.
    ```bash
    git config --global user.name "Seu Nome"
    git config --global user.email "seu-email@exemplo.com"
    ```

* **Configuração Local:** Se precisar usar um nome/e-mail diferente para um projeto específico, vá para a pasta do projeto e execute os comandos sem a flag `--global`.
    ```bash
    git config user.name "Nome Para o Projeto"
    ```

* **Para listar suas configurações:**
    ```bash
    git config --list
    ```

---

## Passo 2: Criando seu Primeiro Repositório

Vamos colocar a mão na massa e criar um projeto do zero.

1.  **Crie e acesse a pasta do projeto:**
    ```bash
    mkdir meu-primeiro-repo
    cd meu-primeiro-repo
    ```

2.  **Inicie o Git na pasta:** Este comando cria um subdiretório oculto `.git` que armazena todo o histórico.
    ```bash
    git init
    ```

3.  **Crie um arquivo:** Vamos criar um arquivo de exemplo.
    ```bash
    echo "# Meu Primeiro Projeto" > README.md
    ```

4.  **Adicione o arquivo à Staging Area:**
    ```bash
    # Adiciona todos os arquivos modificados na pasta atual
    git add .
    
    # Ou, para adicionar um arquivo específico:
    # git add README.md
    ```

5.  **Crie seu primeiro commit:** Salve as alterações no histórico do projeto com uma mensagem descritiva.
    ```bash
    git commit -m "feat: Adiciona o arquivo README inicial"
    ```

6.  **Visualize o histórico:** Para ver o commit que você acabou de criar, use o `git log`.
    ```bash
    git log --oneline
    ```

---

## Passo 3: Trabalhando com Branches

Branches (ramos) permitem que você trabalhe em novas funcionalidades ou correções de bugs de forma isolada, sem afetar a linha de desenvolvimento principal (`main` ou `master`).

* **Criar uma nova branch:**
    * **Comando moderno (recomendado):**
        ```bash
        git switch -c nova-funcionalidade
        ```
    * **Comando tradicional:**
        ```bash
        git checkout -b nova-funcionalidade
        ```

    Ambos os comandos criam a branch e já mudam para ela.

* **Navegar para um commit ou branch específica:**
    * Para voltar para a branch principal:
        ```bash
        git switch main
        ```
    * Para ir para um commit específico (usando o início do seu hash):
        ```bash
        git checkout ac98287
        ```

---

## Passo 4: Marcando Versões com Tags

Quando você atinge um marco importante, como o lançamento da "versão 1.0", você pode criar uma **tag** para marcar aquele commit específico.

1.  **Crie uma tag anotada (com mensagem):**
    ```bash
    # git tag -a <nome_da_tag> <hash_do_commit> -m "Sua mensagem"
    git tag -a v1.0 ac98287 -m "Lançamento da versão 1.0"
    ```
    *Se você não especificar um hash, a tag será criada no commit atual.*

2.  **Envie a tag para o repositório remoto (como o GitHub):** Tags não são enviadas automaticamente com `git push`.
    ```bash
    git push origin v1.0
    ```

3.  **Protegendo branches:** Em plataformas como o GitHub, você pode criar regras (`Rulesets`) para impedir que tags sejam criadas a partir de branches que não sejam a `main`, garantindo que apenas código em produção seja versionado.

---

## Referências

- [Documentação Oficial - GitHub Docs](https://docs.github.com/pt)
