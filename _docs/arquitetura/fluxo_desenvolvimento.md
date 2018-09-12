---
title: "Fluxo de trabalho para o desenvolvedor"
keywords: metodologia workflow dev
tags: 
  - metodologia 
  - workflow
  - desenvolvimento
summary: Metodologia de desenvolvimento/fluxo de trabalho para a construção da ferramenta {{site.nome_sistema}}.
toc: true
#sidebar: mydoc_sidebar
#permalink: index.html
---

A metodologia de trabalho utilizada para a construção do {{site.nome_sistema}} utiliza gerenciador de incidentes pertencente ao BitBucket para designação de tarefas bem como itens a serem corrigidos.

## Criando tarefas

O projeto está sendo gerenciado através do gerenciador de incidentes no repositório principal. Todos os erros/solicitações deverão ser reportados nele.

Sugerimos, para uma maior compreensão de como criar uma tarefa, ler a [documentação](https://confluence.atlassian.com/bitbucket/issue-trackers-221449750.html) disponível no BitBucket.

## Obtendo acesso aos arquivos

A primeira etapa a ser realizada é criar um `fork` do repositório principal. Desta maneira será possível enviar e receber os códigos atualizados pela equipe através do `pull request`.

## Atualização do status da tarefa

A atualização é realizada automaticamente ao informar o `id`, representado pelo caracter `#`, no commit.

Algumas marcações como `fix`, `close` e `see` são utilizadas para relacionar uma tarefa a uma ação.

Assim, em cada commit é necessário associar o `id` da tarefa, conforme o [fluxo commit][fluxo_commit] e a rastreabilidade das versões automaticamente.

## Envio para o repositório principal

Uma fez finalizada a tarefa, ou seja, quando o desenvolvedor realiza o commit indicando o `id`, é necessário que ela seja sincronizada com o repositório principal.

Para isso crie um pull request que o QA irá realizar a análise para a sincronização no repositório principal.

## Obter novas versões no meu `fork`

Para obter as atualizações, sugerimos utilizar a tela do BitBucket. Lá existirá uma opção para obter as alterações do repositório principal do projeto e o `merge` será realizado automaticamente.

{% include /siglas_links.md %}