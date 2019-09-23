---
title: Formulários e validação
description: Saiba como criar formulários com a validação do lado do cliente no mais alto nível.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 40b0c4ecce15032b0ae834fe3100414abd7e4e59
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183927"
---
# <a name="forms-and-validation"></a>Formulários e validação

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O ASP.NET Web Forms Framework inclui um conjunto de controles de servidor de validação que lidam com a validação da entrada`RequiredFieldValidator`do `CompareValidator`usuário `RangeValidator`inserida em um formulário (,, e assim por diante). O ASP.NET Web Forms Framework também dá suporte à associação de modelo e à validação do modelo com base`[Required]`em `[StringLength]`anotações `[Range]`de dados (,, e assim por diante). A lógica de validação pode ser imposta tanto no servidor quanto no cliente usando a validação não invasiva baseada em JavaScript. O `ValidationSummary` controle de servidor é usado para exibir um resumo dos erros de validação para o usuário.

O mais novo suporte ao compartilhamento de lógica de validação entre o cliente e o servidor. O ASP.NET fornece implementações de JavaScript predefinidas de muitas validações de servidor comuns. Em muitos casos, o desenvolvedor ainda precisa escrever JavaScript para implementar totalmente a lógica de validação específica do aplicativo. Os mesmos tipos de modelo, anotações de dados e lógica de validação podem ser usados no servidor e no cliente.

O mais claro fornece um conjunto de componentes de entrada. Os componentes de entrada lidam com os dados do campo de associação a um modelo e validam a entrada do usuário quando o formulário é enviado.

|Componente de entrada|Elemento HTML renderizado    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

O `EditForm` componente encapsula esses componentes de entrada e orquestra o processo de validação por meio `EditContext`de um. Ao criar um `EditForm`, especifique a instância de modelo a ser associada usando o `Model` parâmetro. Normalmente, a validação é feita usando as anotações de dados e é extensível. Para habilitar a validação baseada em anotação `DataAnnotationsValidator` `EditForm`de dados, adicione o componente como um filho do. O `EditForm` componente fornece um evento conveniente para lidar com envios válidos (`OnValidSubmit`)`OnInvalidSubmit`e inválidos (). Há também um evento mais genérico `OnSubmit` que permite disparar e lidar com a validação por conta própria.

Para exibir um resumo de erro de validação, `ValidationSummary` use o componente. Para exibir mensagens de validação para um campo de entrada específico, `ValidationMessage` use o componente, especificando uma expressão lambda `For` para o parâmetro que aponta para o membro de modelo apropriado.

O tipo de modelo a seguir define várias regras de validação usando anotações de dados:

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16, 
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000, 
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true", 
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

O componente a seguir demonstra como criar um formulário com mais de alto `Starship` desempenho com base no tipo de modelo:

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => "starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => "starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => "starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => "starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => "starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

Após o envio do formulário, os dados associados ao modelo não foram salvos em nenhum armazenamento de dados, como um banco de dado. Em um aplicativo Webassembly mais incrivelmente, os dados devem ser enviados para o servidor. Por exemplo, usando uma solicitação HTTP POST. Em um aplicativo de servidor mais incrivelmente, os dados já estão no servidor, mas devem persistir. O tratamento de acesso a dados em aplicativos mais incrivelmente é o assunto da seção [lidando com dados](data.md) .

## <a name="additional-resources"></a>Recursos adicionais

Para obter mais informações sobre [formulários e validação](/aspnet/core/blazor/forms-validation) em aplicativos mais incrivelmenteos, consulte a documentação mais bem.

>[!div class="step-by-step"]
>[Anterior](state-management.md)
>[Próximo](data.md)
