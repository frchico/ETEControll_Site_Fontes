---
title: "Estação de tratamento de Efluentes"
keywords: requisitos ete
tags: 
  - requisitos
  - desenvolvimento
  - ete
summary: Descrição das necessidades de estação de tratamento de efluetes para o sistema {{site.nome_sistema}}.

---

As Estações de Tratamento de Efluentes (ETE) têm por objetivo  reduzir a carga poluidora e atender aos padrões de exigências de lançamento no corpo receptor sem degradar o meio ambiente {% cite neumann2017 %}. Segundo {% cite menezes2017 %}, a escolha do tipo de tratamento para cada situação é feita considerando-se várias condições, desde a eficiência desejada até o custo final de operação. 

Sabe-se ainda que existem vários processos disponíveis, por esta razão cada ETE possui um arranjo de unidades que varia em função das características desejadas para o efluente, respeitando os limites estabelecidos pela legislação vigente.

Desta forma, o {{ site.nome_sistema }} permite atender mais de uma ETE com configurações de parâmetros independentes, de maneira que um parâmetro cadastrado para uma ETE não atrapalhe o da outra ETE.

## Lista de ETE

Tela inicial para acessar as funcionalidades de uma ETE. Com ela o usuário poderá realizar as seguintes ações:
 - Cadastro de uma ETE;
 - Alterar uma ETE;
 - Excluir uma uma ETE;
 - [Associar parâmetros][associar_parametros_ete] de tratamento para uma ETE;
 - Adicionar/Manter [dados de coleta][dados_coleta_ete] para a ETE

O nível de acesso implementado será conforme o descrito em [nível de permissão] e somente serão exibidas as estações em que o usuário possuir vínculo, seja como gerente ou técnico. 


{% include callout.html content="Note que o administrador do sistema poderá realizar qualquer acesso para qualquer ETE." type="primary" %} 




{% include /siglas_links.md %}