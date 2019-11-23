---
title: Formulários e validação
description: Saiba como criar formulários com a validação do lado do cliente no mais alto nível.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c30db5e06d36a6d15301835fe782b21058a80592
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088083"
---
# <a name="forms-and-validation"></a><span data-ttu-id="6859b-103">Formulários e validação</span><span class="sxs-lookup"><span data-stu-id="6859b-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6859b-104">O ASP.NET Web Forms Framework inclui um conjunto de controles de servidor de validação que lidam com a validação da entrada do usuário inserida em um formulário (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="6859b-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="6859b-105">O ASP.NET Web Forms Framework também dá suporte à vinculação de modelo e à validação do modelo com base nas anotações de dados (`[Required]`, `[StringLength]`, `[Range]`e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="6859b-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="6859b-106">A lógica de validação pode ser imposta tanto no servidor quanto no cliente usando a validação não invasiva baseada em JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6859b-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="6859b-107">O controle de servidor `ValidationSummary` é usado para exibir um resumo dos erros de validação para o usuário.</span><span class="sxs-lookup"><span data-stu-id="6859b-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

<span data-ttu-id="6859b-108">O mais novo suporte ao compartilhamento de lógica de validação entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="6859b-108">Blazor supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="6859b-109">O ASP.NET fornece implementações de JavaScript predefinidas de muitas validações de servidor comuns.</span><span class="sxs-lookup"><span data-stu-id="6859b-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="6859b-110">Em muitos casos, o desenvolvedor ainda precisa escrever JavaScript para implementar totalmente a lógica de validação específica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6859b-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="6859b-111">Os mesmos tipos de modelo, anotações de dados e lógica de validação podem ser usados no servidor e no cliente.</span><span class="sxs-lookup"><span data-stu-id="6859b-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

<span data-ttu-id="6859b-112">O mais claro fornece um conjunto de componentes de entrada.</span><span class="sxs-lookup"><span data-stu-id="6859b-112">Blazor provides a set of input components.</span></span> <span data-ttu-id="6859b-113">Os componentes de entrada lidam com os dados do campo de associação a um modelo e validam a entrada do usuário quando o formulário é enviado.</span><span class="sxs-lookup"><span data-stu-id="6859b-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="6859b-114">Componente de entrada</span><span class="sxs-lookup"><span data-stu-id="6859b-114">Input component</span></span>|<span data-ttu-id="6859b-115">Elemento HTML renderizado</span><span class="sxs-lookup"><span data-stu-id="6859b-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="6859b-116">O componente `EditForm` encapsula esses componentes de entrada e orquestra o processo de validação por meio de um `EditContext`.</span><span class="sxs-lookup"><span data-stu-id="6859b-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="6859b-117">Ao criar um `EditForm`, você especifica a instância de modelo a ser associada usando o parâmetro `Model`.</span><span class="sxs-lookup"><span data-stu-id="6859b-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="6859b-118">Normalmente, a validação é feita usando as anotações de dados e é extensível.</span><span class="sxs-lookup"><span data-stu-id="6859b-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="6859b-119">Para habilitar a validação baseada em anotação de dados, adicione o componente `DataAnnotationsValidator` como um filho do `EditForm`.</span><span class="sxs-lookup"><span data-stu-id="6859b-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="6859b-120">O componente `EditForm` fornece um evento conveniente para lidar com envios válidos (`OnValidSubmit`) e inválidos (`OnInvalidSubmit`).</span><span class="sxs-lookup"><span data-stu-id="6859b-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="6859b-121">Há também um evento de `OnSubmit` mais genérico que permite que você acione e manipule a validação por conta própria.</span><span class="sxs-lookup"><span data-stu-id="6859b-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="6859b-122">Para exibir um resumo de erro de validação, use o componente `ValidationSummary`.</span><span class="sxs-lookup"><span data-stu-id="6859b-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="6859b-123">Para exibir mensagens de validação para um campo de entrada específico, use o componente `ValidationMessage`, especificando uma expressão lambda para o parâmetro `For` que aponta para o membro de modelo apropriado.</span><span class="sxs-lookup"><span data-stu-id="6859b-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="6859b-124">O tipo de modelo a seguir define várias regras de validação usando anotações de dados:</span><span class="sxs-lookup"><span data-stu-id="6859b-124">The following model type defines several validation rules using data annotations:</span></span>

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

<span data-ttu-id="6859b-125">O componente a seguir demonstra como criar um formulário com base no tipo de modelo de `Starship`:</span><span class="sxs-lookup"><span data-stu-id="6859b-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

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

<span data-ttu-id="6859b-126">Após o envio do formulário, os dados associados ao modelo não foram salvos em nenhum armazenamento de dados, como um banco de dado.</span><span class="sxs-lookup"><span data-stu-id="6859b-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="6859b-127">Em um aplicativo Webassembly mais incrivelmente, os dados devem ser enviados para o servidor.</span><span class="sxs-lookup"><span data-stu-id="6859b-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="6859b-128">Por exemplo, usando uma solicitação HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="6859b-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="6859b-129">Em um aplicativo de servidor mais incrivelmente, os dados já estão no servidor, mas devem persistir.</span><span class="sxs-lookup"><span data-stu-id="6859b-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="6859b-130">O tratamento de acesso a dados em aplicativos mais incrivelmente é o assunto da seção [lidando com dados](data.md) .</span><span class="sxs-lookup"><span data-stu-id="6859b-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6859b-131">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="6859b-131">Additional resources</span></span>

<span data-ttu-id="6859b-132">Para obter mais informações sobre [formulários e validação](/aspnet/core/blazor/forms-validation) em aplicativos mais incrivelmenteos, consulte a documentação mais bem.</span><span class="sxs-lookup"><span data-stu-id="6859b-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6859b-133">[Anterior](state-management.md)
>[Próximo](data.md)</span><span class="sxs-lookup"><span data-stu-id="6859b-133">[Previous](state-management.md)
[Next](data.md)</span></span>
