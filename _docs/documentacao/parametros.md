---
title: "Parâmetros"
keywords: requisitos parâmetros
tags: 
  - requisitos
  - desenvolvimento
  - parâmetros
summary: Módulo de cadastro de parâmetros para serem associados a uma ETE.

---
O controle da ETE é realizado através de vários parâmetros que podem ser determinados _in situ_ a exemplo da vazão, do OD, SS, pH, SDT, condutividade e salinidade, e outros em laboratório através de coleta de amostras, como DBO, DQO, SST, nitrogênio amoniacal, fósforo, dentre outros.

Além disso, as determinações _in situ_ e as amostras seguem procedimentos específicos para cada parâmetro, o que torna o controle manual suscetível a erros e esquecimentos.

Foi pensando nisso que o {{site.nome_sistema}} identificou a necessidade da construção de uma função que permita o cadastro de parâmetros gerais que são associados e personalizados a uma [unidade de tratamento] de ETE.

É importante destacar que os parâmetros cadastrados neste módulo poderão ser associados a mais de uma [unidade de tratamento][unidade_tratamento] da ETE, pois eles são genéricos. Na função de [associação de parâmetros][associar_parametros_ete] será possível informar como esses parâmetros são utilizados por uma unidade de tratamento de uma ETE.

Desta forma, cada parâmetro disponível no sistema possui as seguintes caracterísiticas:

* Nome
* Sigla
* A unidade de medida utilizada
* Uma descrição e
* O conjunto de valores que são válidos, como texto, inteiro positivo e decimais. 

{% include callout.html content="Note que o administrador do sistema poderá realizar qualquer acesso para qualquer item." type="primary" %} 

{% include /siglas_links.md %}