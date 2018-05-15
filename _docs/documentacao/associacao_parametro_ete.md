---
title: "Associação de Parâmetros de uma ETE"
keywords: requisitos parametros ete
tags: 
  - requisitos
  - desenvolvimento
  - parametros
summary: Módulo para indicar quais parâmetros uma ETE deve ter.

---
Uma vez definidos os parâmetros de controle possível, faz-se necessário informar quais deles que são utilizados pela ETE em tela. 

Foi com base nesta necessidade que o {{ site.nome_sistema}} projetou esta funcionalidade para permitir controlar melhor as operações de cada uma das ETE de forma independente.

O usuário com permissão de associação de parâmetros deverá selecionar uma ETE para adicionar/remover os parâmetros que ele deseja controlar.

Para cada parâmetro desejado ele deverá informar/ajustar:

- A faixa de valores válidos
- Tipo de coleta    
    - _in situ_
    - Manual (opção padrão)
- Instruções de uso/coleta (texto descritivo, podendo conter imagens)
- Frequência de uso na ETE
    - Contínuo
    - Diário
    - Semanal
    - Mensal

{% include callout.html content="Note: <br> - O sistema irá recuperar as informações cadastradas em cada parâmetro para que não seja necessário informar novamente. Assim, o usuário só informará o que for realmente diferente. <br> <br>- O administrador do sistema poderá realizar qualquer acesso para qualquer item." type="primary" %} 

{% include /siglas_links.md %}