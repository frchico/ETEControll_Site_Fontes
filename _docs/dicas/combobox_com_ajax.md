---
title: "Combobox com Ajax"
keywords: DTO service mapper AutoMaper ajax
tags: 
  - desenvolvimento
  - dicas
  - combobox
  - ajax
  - Tela

summary: Código de exemplo para mudar a propriedade a ser exibida/prenchida no DTO.
toc: true
---

## O problema

{% include callout.html content="Você precisa exibir/associar o usuário (apenas um) que está responsável por uma estação de tratamento. Além disso, a tela deverá oferecer um módulo busca, para filtrar os dados para a escolha do usuário." %}

Nosso `Entity` seria definido assim:

```cs
public class EstacaoTratamento : Entidade
{
    #region Constantes
        public const int NomeMaxLength = 150;
    #endregion
    #region Atributos do Banco
        [Required, StringLength(NomeMaxLength)]
        public String Nome { get; set; }
        public float? Latitude { get; set; }
        public float? Longitude { get; set; }
        public long? RespTecnicoId { get; set; }
    #endregion

    #region Chaves Estrangeiras
        [ForeignKey("RespTecnicoId")]
        public User RespTecnico { get; set; }
    #endregion
}
```

## Resolução para telas de Create/edit

1. #### Criar um método no `service` para retornar uma lista de `DTO`.

    Este método será utilizado pelo `controller` quando o usuário quiser filtrar os dados da tela.
    
    ```cs
    public async Task<List<UserDto>> GetUsersBy(string nameOrEmail)
    {
        var usersquery = Repository.GetAll()
            .Where(u =>
                u.Name.Contains(nameOrEmail) || u.EmailAddress.Contains(nameOrEmail)
        );
        var users = await usersquery.ToListAsync();

        return ObjectMapper.Map<List<UserDto>>(users);
    }
    ```
1. #### Fazer com que o `controller` utilize o método definido no `service`

    No nosso caso o método responsável por montar a tela de edição (_view_ `_createOrEdit.cshtml`) é o `public async Task<ViewResult> CreateOrEdit(int? id)`.

    Este método, quando invocado, retorna um elemento do tipo `CreateOrEditEstacaoTratamentoModalViewModel`. 

    Assim, nosso método é definido como:

    ```cs
    public async Task<ViewResult> CreateOrEdit(int? id)
    {
        GetEstacaoTratamentoForEditOutput getEstacaoTratamentoForEditOutput;
        //para editar
        if (id.HasValue)
        {
            getEstacaoTratamentoForEditOutput = await _estacaoTratamentoAppService.GetEstacaoTratamentoForEdit(new EntityDto<int> { Id = id.Value });
            if (getEstacaoTratamentoForEditOutput.EstacaoTratamento == null)
            {
                throw new UserFriendlyException(404, L("ItemNotFound"));
            }
        }
        else //novo
        {
            getEstacaoTratamentoForEditOutput = new GetEstacaoTratamentoForEditOutput
            {
                EstacaoTratamento = new CreateOrEditEstacaoTratamentoInput()
            };
        }

        var viewModel = new CreateOrEditEstacaoTratamentoModalViewModel()
        {
            EstacaoTratamento = getEstacaoTratamentoForEditOutput.EstacaoTratamento
        };
        //Como o responsável técnico não é obrigatório, então precisamos verificar se tem algum valor
        if (getEstacaoTratamentoForEditOutput.EstacaoTratamento.RespTecnicoId.HasValue)
        {
            var responsavelTecnico = _userAppService.Get(new EntityDto<long>(getEstacaoTratamentoForEditOutput.EstacaoTratamento.RespTecnicoId.Value)).Result;
            if (responsavelTecnico != null)
            {
                viewModel.Responsaveis = new List<SelectListItem>();
                viewModel.Responsaveis.Add(
                    new SelectListItem(responsavelTecnico.Name, responsavelTecnico.Id.ToString(),true)
                );
            }
            else
            {
                throw new UserFriendlyException(404, L("EstacaoTratamento.RespTecnico.NotFound"));
            }
        }
        return View("_CreateOrEdit", viewModel);
    }
    ```

1. #### Alterar os `DTO` incluindo as propriedades necessárias
   
   * `CreateOrEditEstacaoTratamentoModalViewModel`

    ```cs
    public class CreateOrEditEstacaoTratamentoModalViewModel
    {
        public CreateOrEditEstacaoTratamentoInput EstacaoTratamento { get; set; }
        public bool IsEditMode => EstacaoTratamento != null && EstacaoTratamento.Id != null;
        public List<SelectListItem> Responsaveis { get; set; }
    }
    ```
   * `CreateOrEditEstacaoTratamentoInput`
  
   ```cs
   [AutoMapTo(typeof(EstacaoTratamento))]
    public partial class CreateOrEditEstacaoTratamentoInput
    {
        public int? Id { get; set; }
        [Required]
        [StringLength(EstacaoTratamento.NomeMaxLength)]
        public string Nome { get; set; }
        public Single? Latitude { get; set; }
        public Single? Longitude { get; set; }
        public long? RespTecnicoId { get; set; }
    }
    ```  
1. #### Adicionar o campo na `view` do tipo `select`

    ```HTML
    <div class="col-sm-12">
        <div class="form-group">
            <div class="form-line">
                <label for="RespTecnico" class="form-label">@L("EstacaoTratamento.RespTecnico")</label>
            </div>
            <br />
            <br />
            <div class="form-line">
                <select id="RespTecnico"
                        name="RespTecnicoId"
                        asp-for="EstacaoTratamento.RespTecnicoId"
                        asp-items="Model.Responsaveis"
                        class="form-control"
                        title="Escolha um @L("EstacaoTratamento.RespTecnico")"
                        data-live-search="true"></select>
            </div>
        </div>
    </div>
    ```
   Note que:
     * `id="RespTecnico"` será utilizado pelo _Javascript_ para realizra as consultas ajax;
     * `name="RespTecnicoId"` valor que será enviado no JSON na requisição de salvar/editar;
     * `asp-for="EstacaoTratamento.RespTecnicoId"` é o campo que contém o valor inicial a ser selecionado;
     * `asp-items="Model.Responsaveis"` é a coleção com os valores a serem exibidos inicialmente (no caso de alteração será adicionado o responsável que foi coletado previamente);
     * `data-live-search="true"` informa que o campo é "pesquisável";

1. #### Adicionar a chamada AJAX no JS
   
   No arquivo `_CreateOrEdit.js` adicione a chamada JS para configurar o componente com AJAX.

    ```js
    (function ($) {
        $(function () {
            /** Omitido */
            $('#RespTecnico').ajaxSelectPicker({
                minLength: 2,
                ajax: {
                    url: abp.appPath + 'ETESystem/EstacaoTratamento/GetUsersBy',
                    type: 'POST',
                    dataType: 'json',
                    data: {
                        userNameOrEmail: '{ { { q } } }' //Remova os espaços entre as chaves
                    }
                },
                preprocessData: function (data) {
                    var i, l = data.items.length, array = [];
                    if (l) {
                        for (i = 0; i < l; i++) {
                            array.push($.extend(true, data.items[i], {
                                text: data.items[i].name,
                                value: data.items[i].id,
                                data: {
                                    subtext: data.items[i].emailAddress
                                }
                            }));
                        }
                    }
                    return array;
                }

            });
            /** Omitido */
        });
    })(jQuery);
    ```

---

## Resolução para telas com grid

Caso necessite exibir algum dado de uma entidade relacionada, como por exemplo os dados do usuário que é responsável pela `Estação de Tratamento`, adicione o seguinte código no método do `service` que retorna os dados para o `DTO`.

```cs
public async Task<PagedResultDto<EstacaoTratamentoListDto>> GetAll(GetEstacaoTratamentoInput input)
{

    var query = CreateEstacaoTratamentoQuery(input);
    query = query.Include(x => x.RespTecnico);
    var resultCount = await query.CountAsync();
    var results = await query
        .OrderBy(input.Sorting)
        .PageBy(input)
        .ToListAsync();

    //Exemplo de como alterar o mapeamento para uma view
    var config = new MapperConfiguration(
        cfg => cfg.CreateMap<EstacaoTratamento,
        EstacaoTratamentoListDto>()
        //Ao invés de retornar o Name do usuário, o campo é preenchido como FullName
        .ForMember(d => d.RespTecnicoName, o => o.MapFrom(s => s.RespTecnico.FullName))
    );
    var m = config.CreateMapper();
    var y = m.Map<List<EstacaoTratamento>, List<EstacaoTratamentoListDto>>(results);

    return new PagedResultDto<EstacaoTratamentoListDto>(resultCount, y);
}
```

No _Javascript_ do `grid` use `<Entidade>.<Propriedade>` em `camelCase`.

---
## Referências

Para maiores detalhes consulte:

* <https://automapper.readthedocs.io/en/latest/Custom-value-resolvers.html>
* <https://automapper.readthedocs.io/en/latest/Lists-and-arrays.html>
* <https://aspnetboilerplate.com/Pages/Documents/Data-Transfer-Objects>
* <http://www.4answered.com/questions/view/20caf3c/bootstrap-select-options-not-appearing-in-dropdown>
* <https://celsokitamura.com.br/pascal-case-e-camel-case/>
* <https://www.jqueryscript.net/form/Bootstrap-Dropdown-Select-Enhancement-Plugin-jQuery.html>
* <https://www.jqueryscript.net/form/AJAX-Autocomplete-Bootstrap-Select.html>
