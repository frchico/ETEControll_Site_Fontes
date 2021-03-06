---
title: Dicas 
---

## Dicas de implementação utilizando AspNetBoilerplate

#### Videos
https://www.youtube.com/watch?v=5PKk-FLZ6EU

##### Arquivos de Localização
Os arquivos de Localização são utilizados para traduzir um label para os usuários. No sistema utlizaremos a [API](https://www.aspnetboilerplate.com/Pages/Documents/Localization) para suportar mais de uma linguagem.

Serão criados arquivos em XML e a ordenação das chaves será por data de criação, ou seja, seguirá o proposto pela API

> If you use XML or JSON, we recommend you do not sort the texts by name. Sort them by creation date! This way, when someone translates it to another language, he/she can easily see which texts have been added recently.

##### Usar o padrão [Specifications](https://www.aspnetboilerplate.com/Pages/Documents/Specifications) para definir regras como:

   - listar estações que estão com problemas;
   - listar parametros de um determinado tipo...

##### Configuração do timeout de uma conexão:    

   - [Exemplo](https://www.aspnetboilerplate.com/Pages/Documents/Unit-Of-Work)
        ```
        public class SimpleTaskSystemCoreModule : AbpModule
        {
            public override void PreInitialize()
            {
                Configuration.UnitOfWork.IsolationLevel = IsolationLevel.ReadCommitted;
                Configuration.UnitOfWork.Timeout = TimeSpan.FromMinutes(30);
            }

        //...other module methods
        }
        ```
##### Filtrando dados de um determinado usuário 

Util para fazer com que o usuário não possa ver os dados que outros criaram ou criar filtros de aplicação como limite de inserts
    - [API](https://github.com/zzzprojects/EntityFramework.DynamicFilters)
    - [Exemplo de Implementação no sistema](https://www.aspnetboilerplate.com/Pages/Documents/Data-Filters)

##### Adicionar funcionalidades ao projeto:

Permite validar a permissão se pode ou não exportar alguns dados. Ver como fazer essa personalização por usuário
    - [Link](https://www.aspnetboilerplate.com/Pages/Documents/Feature-Management)    
    - [Como usar as funcionalidades](https://www.aspnetboilerplate.com/Pages/Documents/MVC-Views)

##### Logomarca:

   - [Ideias para logomarca/imagens](https://dribbble.com/search?q=logo)

##### Código de conduta

   - [GitHub](https://opensource.guide/code-of-conduct/)    

##### Auditoria:
   - [Como fazer a auditoria](https://www.aspnetboilerplate.com/Pages/Documents/Entity-History) 
   - Labels em uma ação que é auditada
     - Util para vincular com caso de uso [Reason Property](https://www.aspnetboilerplate.com/Pages/Documents/Entity-History#reason-property)

##### GRID

   - https://forum.aspnetboilerplate.com/viewtopic.php?p=6617    
   - https://github.com/aspnetboilerplate/aspnetboilerplate/issues/2438
   - https://datatables.net/forums/discussion/40690/sample-implementation-of-serverside-processing-in-c-mvc-ef-with-paging-sorting-searching
   - https://shareurcodes.com/blog/dataTables%20server-side%20processing%20with%20custom%20parameters%20in%20codeigniter

##### UI Samples

   - https://gurayyarar.github.io/AdminBSBMaterialDesign/pages/tables/jquery-datatable.html

## VSTS e implantação

- https://visualstudio.microsoft.com/dev-essentials/
- https://azure.microsoft.com/en-us/free/
- https://azure.microsoft.com/en-us/education/
- https://www.microsoft.com/en-us/education