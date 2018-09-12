---
title: "Instruções para a Compilação"
keywords: Instruções Compilação
tags: 
  - desenvolvimento
  - manual
summary: Breves instruções que irão ajudá-lo na compilação da solução {{site.nome_sistema}}.
toc: true
#sidebar: mydoc_sidebar
#permalink: index.html
---

Os seguintes passos irão orientá-lo no processo de compilação do projeto.

1. Faça o download do repositório;

2. Crie um arquivo de banco de dados do SQLServer, fazendo o seguinte caminho: *Gerenciador de Servidores -> Adicionar Conexão... -> Arquivo de Banco de dados do Microsoft SQL Server*, após isso será solicitado um caminho para armazenar o arquivo do banco, dê um nome qualquer e pressione **OK**;

3. Após o procedimento anterior, na janela de Gerenciador de Servidores, será mostrado um banco de dados com o nome informado, dê um clique direito na conexão e vá em propriedades, com isso aparecerá uma janela com informações sobre a conexão, copie o campo de *Cadeia de Conexão*;

4. Modifique o arquivo localizado em `*\aspnet-core\src\GPSA.ETESystem.Web.Mvc\appsettings.json`, em **ConnectionStrings** adicione uma chave com o nome de *Default* contendo o caminho de sua conexão, conforme o exemplo abaixo:
    ```json
    "ConnectionStrings": {
        "Default": "Adicione sua conexão aqui",
        "Default1": "Data Source=(LocalDB)\\MSSQLLocalDB;AttachDbFilename=D:\\SincronizadoComGit\\BancoDados\\BancoETESystem.mdf;Integrated Security=True;Connect Timeout=30",
    }
    ```

5. Abra o console do NuGet fazendo o seguinte caminho: *Ferramentas -> Gerenciador de pacotes NuGet -> Console do Gerenciador de pacotes*;

6. Na janela do console, escolha como projeto padrão `GPSA.ETESystem.EntityFrameworkCore`, além de marcar o projeto de inicialização com o mesmo projeto;

7. Execute o seguinte comando: `Update-Database`. Este comando irá preparar o banco de dados para receber todas as tabelas necessárias;

8. Para executar o projeto, marque a inicialização como `GPSA.ETESystem.Web.Mvc` e pressione **Ctrl+F5** ou o caminho *Depurar -> Iniciar Sem Depurar*.
    >   É possível também executar com o depurador ativo, porém este processo poderá demorar bastante tempo.

9. Após a execução, o navegador irá abrir uma página requisitando autenticação, onde o usuário é `admin` e a senha é `123qwe`;
