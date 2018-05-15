---
title: Segurança/Perfil de acesso
---

O sistema de segurança (autenticação e autorização) disponível na aplicação deverá fornecer o nome, e-mail e telefone do usuário que está sendo cadastrado. 
Para acessar as funcionalidades serão definidos 3 perfis de usuário, sendo:
- *Administrador*: que pode gerenciar qualquer função desde o cadastro de uma ETE e a definição de um novo parâmetro disponível no sistema;
- *Engenheiro*: responsável por indicar quais tipos de parâmetros que a ETE possui bem como o processo de coleta utilizado;
- *Técnico*: que realiza os apontamentos das coletas in loco da estação.


Diante destes perfis, o acesso será disponibilizado conforme a tabela abaixo: 


|:------------------------------------------------------------------:|:----------------------------------:|:----------:|
|                            Função/Módulo                           |          Perfil de acesso          | Observação |
|:-------------------------------------------------------------------|:-----------------------------------|:-----------|
| Manutenção de permissões                                           | Administrador                      |            |
| Manutenção de Parâmetros Gerais do sistema                         | Administrador                      |            |
| Pesquisar uma ETE                                                  | Administrador, Engenheiro, Técnico |            | 
| Adicionar uma ETE                                                  | Administrador                      |            |
| Alterar uma ETE                                                    | Administrador, Engenheiro          |            |
| Excluir uma ETE                                                    | Administrador                      |            |
| [Manutenção de parâmetros disponíveis][parametros_disponiveis_para_ete] para ser associados a uma ETE | Administrador                      |            |
| [Associar os parâmetros][associar_parametros_ete] a uma ETE                                   | Administrador, Enegenheiro         |            |
| Criar/Alterar, Pesquisar uma coleta                                | Administrador, Engenheiro, Técnico |            |
| Excluir uma coleta                                                 | Administrador, Engenheiro          |            |
| [Preencher as informações dos parâmetros de uma coleta][dados_coleta_ete]              | Administrador, Engenheiro, Técnico |            |
|:------------------------------------------------------------------:|:----------------------------------:|:----------:|




{% include callout.html content="**Atenção ao uso dos seguintes termos:**<br> <br>- O uso do *Manutenção* significa que o usuário poderá criar (novo), alterar (editar), excluir e pesquisar uma informação." type="primary" %} 


{% include /siglas_links.md %}