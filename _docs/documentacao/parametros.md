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

Foi pensando nisso que o {{site.nome_sistema}} identificou a necessidade da construção de uma função que permita o cadastro de parâmetros que podem ser associados a uma ETE. 


É importante destacar que os parâmetros cadastrados neste módulo poderão ser associados a mais de uma ETE, pois eles são genéricos. Na função de [associação de parâmetros][associar_parametros_ete] será possível informar quais são os parâmetros monitorados por uma ETE. 



Desta forma, cada parâmetro disponível no sistema possui:

- Nome
- Texto padrão para as instruções de uso/coleta (texto descritivo, podendo conter imagens)
- Faixa de valores válidos (utilizado para validar os dados lançados para uma coleta)
    - Texto 
    - Inteiro
    - Decimal
- Tipo do parâmetro
    - Composto 
    - Simples
    - Sensor
- Frequência de uso habitual
    - Contínuo
    - Diário
    - Semanal
    - Mensal
- Tipo de uso
    - Avaliação de desempenho
    - Controle do processo



{% include callout.html content="Note que o administrador do sistema poderá realizar qualquer acesso para qualquer item." type="primary" %} 

{% include /siglas_links.md %}