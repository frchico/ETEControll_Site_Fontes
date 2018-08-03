# Pendências

* Criar a tabela de localização para armazenar as coordenadas geográficas/endereço das unidades e das estações de tratamento

* Criar a tabela de frequência para exibir para o usuário os dias e frequeências de forma amigável.
    - Utilizar o cromando de execução para o agendamento cron
    - Ver [API]( https://github.com/bradymholt/cron-expression-descriptor)
* Vincular os usuários a uma unidade de tratamento para ser utilizado nos lembretes, coletas e afins.
* Ajustar o tipo de dados das chaves para bigint

# Dúvidas:

* É possível fazer agendamento/coletas retroativo?
* Qual a forma de agendamento em caso falha, isto é, se não foi realizada uma coleta prevista para toda sexta e o técnico ao percebir isso fez na segunda, então impactará nos dias de coletas futuro? Isto é, agora as coletas serão realizadas na segunda e não mais na sexta?
* 