---
title: "Coleta de dados de uma unidade de monitoramento"
keywords: requisitos parametros ete
tags: 
  - requisitos
  - desenvolvimento
  - parametros
summary: 

---

O sistema foi projetado para permitir agendar mais de uma coleta para uma certa [unidade de tratamento][unidade_tratamento].

Desta maneira, toda vez que o operador necessitar registrar os dados de uma coleta ele deverá começar informando para o sistema os seguintes dados:

* A unidade de tratamento que foi coletada;
* A data de coleta

O sistema fará a leitura da configuração dos [parâmetros][parametros] que foram definidos para a unidade selecionada e os exibirá para que o responsável pela coleta faça o registro dos dados de cada um dos parâmetros que foram previamente mapeados, conforme definido [aqui][parametro_coletado_unidade_tratamento].

Além disso, cada coleta terá um fluxo para controlar em qual situação ela se encontra. Conforme imagem abaixo, a situação inicia como cadastrada ou agendada quando a data da coleta é futura. A partir do primeiro lançamento de valores dos parâmetros, ela passa para a situação de pendente e só poderá seguir para a situação de finalizada quando todos os [parâmetros mapeados][parametro_coletado_unidade_tratamento] como obrigatórios forem informados. O usuário também poderá cancelar a coleta, invalidando os dados já lançados.

![Estados de uma coleta]({{ "/img/DiagramaEstadosColeta.png" |  prepend: site.baseurl }} )

{% include callout.html content="Atenção: O sistema poderá cancelar uma coleta agendada ou cadastrada caso seja inicializada outra coleta na mesma data e o sistema indentificar que existe uma pendente." type="primary" %}

{% include /siglas_links.md %}