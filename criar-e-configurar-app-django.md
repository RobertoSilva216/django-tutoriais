# Django Project Setup Guide

Este guia fornece um passo a passo básico para criar e configurar um projeto Django.

## Requisitos

- Python 3.x
- `pip` para gerenciar pacotes Python

## Passo 1: Instalar o Django

Primeiro, instale o Django usando `pip`. Abra seu terminal e execute:

    ```bash
    python3 -m pip install django
    ```

## Passo 2: Criar um Projeto Django

Após instalar o Django, crie o projeto com o comando:

    ```bash
    django-admin startproject nome_do_projeto
    ```

Substitua `nome_do_projeto` pelo nome desejado para seu projeto.

## Passo 3: Navegar para o Diretório do Projeto

Entre no diretório do projeto que foi criado:

    ```bash
    cd nome_do_projeto
    ```

## Passo 4: Criar um Aplicativo Django

Dentro do projeto, crie um aplicativo. O Django organiza funcionalidades em "apps". Para criar o primeiro app, use:

    ```bash
    python3 manage.py startapp nome_do_app
    ```

Substitua `nome_do_app` pelo nome desejado para o aplicativo.

## Passo 5: Configurar o Banco de Dados

O Django usa SQLite como banco de dados padrão, mas é possível configurar outros, como PostgreSQL ou MySQL. Para isso:

1. Abra o arquivo `settings.py` na pasta do projeto.
2. Localize a seção `DATABASES` e ajuste as configurações conforme o banco de dados desejado.

Para manter as configurações padrão, não é necessário fazer alterações.

## Passo 6: Aplicar as Migrações

Crie as tabelas no banco de dados usando as migrações iniciais:

    ```bash
    python3 manage.py migrate
    ```

## Passo 7: Configurar o Aplicativo no Projeto

1. No arquivo `settings.py`, adicione o nome do aplicativo na lista `INSTALLED_APPS`:

    ```python
    INSTALLED_APPS = [
        # outras apps
        'nome_do_app',
    ]
    ```

2. Salve o arquivo.

## Passo 8: Executar o Servidor

Agora, você pode iniciar o servidor local para testar o projeto:

    ```bash
    python3 manage.py runserver
    ```

Acesse o servidor em seu navegador pelo endereço `http://127.0.0.1:8000/`.

## Passo 9: Instalar Pacotes Adicionais

Caso precise instalar outros pacotes (exemplo: `requests`), faça assim:

    ```bash
    python3 -m pip install requests
    ```

Inclua qualquer biblioteca adicional conforme a necessidade do seu projeto.

## Conclusão

Pronto! Você criou e configurou um projeto Django básico. A partir daqui, pode começar a desenvolver as funcionalidades desejadas no seu projeto.
