---
title: "Preparação do ambiente de desenvolvimento"
keywords: introdução homepage desenvolvimento
tags: 
  - introdução
  - desenvolvimento
summary: Breves instruções que irão ajudá-lo a começar rapidamente com o ETEControll. Os outros tópicos desta ajuda fornecem informações adicionais e detalhes sobre como trabalhar com outros aspectos desta aplicação.

#sidebar: mydoc_sidebar
#permalink: index.html
---


Siga as instruções a seguir para montar seu ambiente de desenvolvimento.

## Instalando o ambiente de desenvolvimento

### 1. Download do projeto

Primeiro, faça o download dos códigos do projeto em [nosso repositório]. 

### 2. Instale o [Visual Studio 2017][Visual Studio 2017]{: target="_blank"} ou [Visual Studio Code]{: target="_blank"}

{% comment %}
Se você nunca instalou o Visual Studio, veja como fazer:

* [Instalar no Mac][mydoc_install_jekyll_on_mac]
* [Install no Windows][mydoc_install_jekyll_on_windows]
* [Install no Linux][mydoc_install_jekyll_on_windows]
{% endcomment %}

### 3. Git

É interessante que você instale o `GIT` para perceber as mudanças que são realizadas. Recomendamos o uso da ferramenta [source tree]{: target="_blank"} devida a compatibilidade com nosso repositório.

### 4. Configure o banco de dados

Por padrão estamos utilizando o `Sql Server` com o `EntityFramework`. Desta forma, é necessário que seja alterada a string de conexão e execução do comando para criar as tabelas com os dados iniciais. Para tal, Realize:

* O ajuste na string de conexão do arquivo ``appsettings.json`` do projeto `Web` e do `EntityFrawork`.

  A chave utilizada pela aplicação é a `DefaultConnection`, como segue: 
  ```
  "ConnectionStrings": {
      "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=|DataDirectory|\database.mdf;Trusted_Connection=True;MultipleActiveResultSets=true"
    }
  ```
* Crie o banco 

  Utilize o Visual Studio para criar o banco de dados na string de conexão informada.

* Crie as tabelas

  Utilizando o console do Visual Studio, selecione o projeto ``EntityFramework`` e execute os comando `Update-Database`.

### 5. Altere o projeto padrão

Faça com que o projeto `Web` seja o projeto padrão. 



{% include /callout.html content="É interessante o uso de plugins para a construção dos artefatos do projeto. Para tal, recomendamos que você faça uso do plugin <a target='_blank' href='https://github.com/sestek/ABPHelper'>ABP Helper</a> para auxiliar neste *setup*" type="primary" %} 



## Execução da solução

Agora que o ambiente foi configurado, vamos testá-lo.

### 1. Testando a apliação

Para testar a aplicação, faça:
- Primeiro execute-a através do comando Ctrl+F5 (executar sem depuração);
- No site que abriu faça o login com os seguintes dados:

  | Perfil      | Login   | Senha  |
  |:-----------:|:-------:|:------:|
  |Administrador| admin   | 123qwe |
  |Gerente      | gerente | 123qwe |
  |Técnico      | tecnico | 123qwe |

{% include callout.html content="Se você está interessado em participar do projeto entre em contato conosco. Você também poderá sugerir mudanças ou esclarecimentos adicionais. Visite o site do grupo de pesquisa." %}

### 2. Executando o site em contêineres

Apesar do projeto ter o `dockerfile` e o `docker-compose`, a solução ainda não foi testada e não recomendamos o uso desta configuração. Caso consiga executar, nos comunique para que possamos atualizar a documentação.
{% comment %}
You can also use Docker to directly build and run the site on your local machine. Just clone the repo and run the following from your working dir:
```
docker-compose build --no-cache && docker-compose up
```
The site should now be running at [http://localhost:4000/](http://localhost:4000/).

This is perhaps the easiest way to see how your site would actually look.
{% endcomment %}




{% include /siglas_links.md %}