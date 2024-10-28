# Guia de instalação e configuração de um projeto Django
Este guia fornece um passo a passo básico para criar e configurar um projeto Django.

## Requisitos

- Python 3.x
- `pip` para gerenciar pacotes Python

## Passo 1: Instalar o Django

Primeiro, instale o Django usando `pip`. Abra seu terminal e execute:

```bash
python3 -m pip install django
#OU
pip install django
```

## Passo 2: Criar um Projeto Django

Após instalar o Django, crie o projeto com o comando:

```bash
django-admin startproject nome_do_projeto
#OU
python3 -m django startproject nome_do_projeto

# se você já clonou o projeto vazio do git, adicione um ponto ao final do comando, para não criar outra subpasta, assim:

django-admin startproject nome_do_projeto .
#OU
python3 -m django startproject nome_do_projeto .
```

Substitua `nome_do_projeto` pelo nome desejado para seu projeto.

## Passo 3: Navegar para o Diretório do Projeto
Siga esse passo apenas se você não usou o `.` no final do comando anterior

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

Obs.: Para manter as configurações padrão, não é necessário fazer alterações, apenas pule este passo

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

## Passo 8: Criar um Template Básico
- Dentro do diretório do seu aplicativo (`nome_do_app`), crie uma pasta chamada `templates`
- Dentro da pasta `templates`, crie um arquivo HTML chamado `index.html` e adicione o seguinte conteúdo:

```bash
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Primeiro Template Django</title>
</head>
<body>
    <h1>Olá, Mundo!</h1>
    <p>Bem-vindo ao meu primeiro template Django.</p>
</body>
</html>
```

## Passo 9: Criar uma View para Servir o Template
No arquivo `views.py` do seu aplicativo, adicione a seguinte view:

```bash
from django.shortcuts import render

def home(request):
    return render(request, 'nome_do_app/index.html')
```

## Passo 10: Configurar o roteamento no `urls.py` no seu app
- No diretório do seu app, crie o arquivo `urls.py`
- Adicione a importação da view e configure a URL:

```bash
from django.urls import path
from nome_do_app.views import home 

urlpatterns = [
    path('', home, name='home'),  # Rota para a view
]

```

## Passo 11: Incluir no seu projeto o roteamento feito 
- No diretório do seu projeto, abra o arquivo `urls.py`
- Inclua o arquivo de rotas criado anteriormente

```bash
from django.contrib import admin
from django.urls import path, include #adicione 'include' ao final dessa linha

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('nome_do_app.urls')), #adicione essa linha
]
```

## Passo 12: Executar o Servidor
Agora, você pode iniciar o servidor local para testar o projeto

```bash
python3 manage.py runserver
```

Acesse o servidor em seu navegador pelo endereço `http://127.0.0.1:8000/`.

## Passo 13: Instalar Pacotes Adicionais

Caso precise instalar outros pacotes (exemplo: `requests`), faça assim:

```bash
python3 -m pip install requests
#OU
pip install requests
```

Inclua qualquer biblioteca adicional conforme a necessidade do seu projeto.

## Conclusão

Pronto! Você criou e configurou um projeto Django básico. A partir daqui, pode começar a desenvolver as funcionalidades desejadas no seu projeto.
