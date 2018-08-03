---
title: "Unidade de tratamento"
keywords: requisitos unidade tratamento ete
tags: 
  - requisitos
  - desenvolvimento
  - parametros
summary: Definição de requisitos da {% page.title %}
---

Entende-se como unidade de tratamento uma parte, processo ou [conjunto de parâmetros][parametro_unidade_tratamento] que precisam ser analisados e que fazem parte de uma estação de tratamento.

São exemplos de Unidade de Tratamento:

* Gradeamento
* Remoção de Areia
* Medidor Parshall
* Digestor Anaeróbio
* Leito de Secagem

No {{ site.nome_sistema }}, cada estação de tratamento pode ter mais de uma unidade de tratamento. Sendo que, para cada unidade de tratamento, é necessário definir as seguintes propriedades:

* Nome
* Estação que está vinculada;
* A ordem da unidade no processo da estação de tratamento;
* Situação (ativa/inativa)
* Latitude e Longitude
* Definição do conjunto de [parâmetros que são monitorados][parametro_unidade_tratamento] para a unidade de tratamento.

{% include /siglas_links.md %}