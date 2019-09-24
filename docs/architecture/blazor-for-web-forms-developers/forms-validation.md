---
title: Formulários e validação
description: Saiba como criar formulários com a validação do lado do cliente no mais alto nível.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 9062e0ab106b7e647646bf5d206106153d7d9009
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214029"
---
# <a name="forms-and-validation"></a><span data-ttu-id="68e8f-103">Formulários e validação</span><span class="sxs-lookup"><span data-stu-id="68e8f-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="68e8f-104">O ASP.NET Web Forms Framework inclui um conjunto de controles de servidor de validação que lidam com a validação da entrada`RequiredFieldValidator`do `CompareValidator`usuário `RangeValidator`inserida em um formulário (,, e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="68e8f-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="68e8f-105">O ASP.NET Web Forms Framework também dá suporte à associação de modelo e à validação do modelo com base`[Required]`em `[StringLength]`anotações `[Range]`de dados (,, e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="68e8f-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="68e8f-106">A lógica de validação pode ser imposta tanto no servidor quanto no cliente usando a validação não invasiva baseada em JavaScript.</span><span class="sxs-lookup"><span data-stu-id="68e8f-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="68e8f-107">O `ValidationSummary` controle de servidor é usado para exibir um resumo dos erros de validação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="68e8f-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="68e8f-108">O mais novo suporte ao compartilhamento de lógica de validação entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="68e8f-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="68e8f-109">O ASP.NET fornece implementações de JavaScript predefinidas de muitas validações de servidor comuns.</span><span class="sxs-lookup"><span data-stu-id="68e8f-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="68e8f-110">Em muitos casos, o desenvolvedor ainda precisa escrever JavaScript para implementar totalmente a lógica de validação específica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68e8f-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="68e8f-111">Os mesmos tipos de modelo, anotações de dados e lógica de validação podem ser usados no servidor e no cliente.</span><span class="sxs-lookup"><span data-stu-id="68e8f-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="68e8f-112">O mais claro fornece um conjunto de componentes de entrada.</span><span class="sxs-lookup"><span data-stu-id="68e8f-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="68e8f-113">Os componentes de entrada lidam com os dados do campo de associação a um modelo e validam a entrada do usuário quando o formulário é enviado.</span><span class="sxs-lookup"><span data-stu-id="68e8f-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="68e8f-114">Componente de entrada</span><span class="sxs-lookup"><span data-stu-id="68e8f-114">Input component</span></span>|<span data-ttu-id="68e8f-115">Elemento HTML renderizado</span><span class="sxs-lookup"><span data-stu-id="68e8f-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="68e8f-116">O `EditForm` componente encapsula esses componentes de entrada e orquestra o processo de validação por meio `EditContext`de um.</span><span class="sxs-lookup"><span data-stu-id="68e8f-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="68e8f-117">Ao criar um `EditForm`, especifique a instância de modelo a ser associada usando o `Model` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="68e8f-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="68e8f-118">Normalmente, a validação é feita usando as anotações de dados e é extensível.</span><span class="sxs-lookup"><span data-stu-id="68e8f-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="68e8f-119">Para habilitar a validação baseada em anotação `DataAnnotationsValidator` `EditForm`de dados, adicione o componente como um filho do.</span><span class="sxs-lookup"><span data-stu-id="68e8f-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="68e8f-120">O `EditForm` componente fornece um evento conveniente para lidar com envios válidos (`OnValidSubmit`)`OnInvalidSubmit`e inválidos ().</span><span class="sxs-lookup"><span data-stu-id="68e8f-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="68e8f-121">Há também um evento mais genérico `OnSubmit` que permite disparar e lidar com a validação por conta própria.</span><span class="sxs-lookup"><span data-stu-id="68e8f-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="68e8f-122">Para exibir um resumo de erro de validação, `ValidationSummary` use o componente.</span><span class="sxs-lookup"><span data-stu-id="68e8f-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="68e8f-123">Para exibir mensagens de validação para um campo de entrada específico, `ValidationMessage` use o componente, especificando uma expressão lambda `For` para o parâmetro que aponta para o membro de modelo apropriado.</span><span class="sxs-lookup"><span data-stu-id="68e8f-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="68e8f-124">O tipo de modelo a seguir define várias regras de validação usando anotações de dados:</span><span class="sxs-lookup"><span data-stu-id="68e8f-124">The following model type defines several validation rules using data annotations:</span></span>

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

<span data-ttu-id="68e8f-125">O componente a seguir demonstra como criar um formulário com mais de alto `Starship` desempenho com base no tipo de modelo:</span><span class="sxs-lookup"><span data-stu-id="68e8f-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
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
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
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

<span data-ttu-id="68e8f-126">Após o envio do formulário, os dados associados ao modelo não foram salvos em nenhum armazenamento de dados, como um banco de dado.</span><span class="sxs-lookup"><span data-stu-id="68e8f-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="68e8f-127">Em um aplicativo Webassembly mais incrivelmente, os dados devem ser enviados para o servidor.</span><span class="sxs-lookup"><span data-stu-id="68e8f-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="68e8f-128">Por exemplo, usando uma solicitação HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="68e8f-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="68e8f-129">Em um aplicativo de servidor mais incrivelmente, os dados já estão no servidor, mas devem persistir.</span><span class="sxs-lookup"><span data-stu-id="68e8f-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="68e8f-130">O tratamento de acesso a dados em aplicativos mais incrivelmente é o assunto da seção [lidando com dados](data.md) .</span><span class="sxs-lookup"><span data-stu-id="68e8f-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="68e8f-131">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="68e8f-131">Additional resources</span></span>

<span data-ttu-id="68e8f-132">Para obter mais informações sobre [formulários e validação](/aspnet/core/blazor/forms-validation) em aplicativos mais incrivelmenteos, consulte a documentação mais bem.</span><span class="sxs-lookup"><span data-stu-id="68e8f-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="68e8f-133">[Anterior](state-management.md)
>[Próximo](data.md)</span><span class="sxs-lookup"><span data-stu-id="68e8f-133">[Previous](state-management.md)
[Next](data.md)</span></span>
