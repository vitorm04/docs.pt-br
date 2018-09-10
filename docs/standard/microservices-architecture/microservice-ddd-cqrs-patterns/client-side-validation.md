---
title: Validação do lado do cliente (validação nas camadas de apresentação)
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Validação do lado do cliente (validação nas camadas de apresentação)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 70a1f716797e03acdcbf1c58d4b0302449d98fa9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213362"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="e7194-103">Validação do lado do cliente (validação nas camadas de apresentação)</span><span class="sxs-lookup"><span data-stu-id="e7194-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="e7194-104">Mesmo quando a fonte de verdade for o modelo de domínio e, em último caso, você precisar ter validação no nível de modelo de domínio, a validação ainda poderá ser manipulada tanto no nível de modelo de domínio (lado do servidor) quanto do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7194-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="e7194-105">A validação do lado do cliente é uma ótima conveniência para usuários.</span><span class="sxs-lookup"><span data-stu-id="e7194-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="e7194-106">Ela economiza tempo que de outra forma seria gasto aguardando uma viagem de ida e volta que talvez retorne erros de validação.</span><span class="sxs-lookup"><span data-stu-id="e7194-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="e7194-107">Em termos de negócios, até mesmo algumas frações de segundos multiplicadas por centenas de vezes por dia chega a ser muito tempo, despesa e frustração.</span><span class="sxs-lookup"><span data-stu-id="e7194-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="e7194-108">A validação imediata e simples permite que os usuários trabalhem com mais eficiência e façam contribuições e produzam entradas e saídas de melhor qualidade.</span><span class="sxs-lookup"><span data-stu-id="e7194-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="e7194-109">Como o modelo de exibição e o modelo de domínio são diferentes, a validação do modelo de exibição e do modelo de domínio podem ser semelhantes, mas têm um propósito diferente.</span><span class="sxs-lookup"><span data-stu-id="e7194-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="e7194-110">Se estiver preocupado com DRY (o princípio Don't Repeat Yourself), considere que, nesse caso, a reutilização de código poderá significar também acoplamento e, em aplicativos empresariais, será mais importante não acoplar o lado do servidor com o do cliente do que seguir o princípio DRY.</span><span class="sxs-lookup"><span data-stu-id="e7194-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="e7194-111">Mesmo ao usar a validação do lado do cliente, você sempre deve validar seus comandos ou DTOs de entrada no código do servidor, porque as APIs do servidor são um possível vetor de ataque.</span><span class="sxs-lookup"><span data-stu-id="e7194-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="e7194-112">Geralmente, fazer as duas é a melhor opção, porque se você tiver um aplicativo cliente, de uma perspectiva do UX, será melhor ser proativo e não permitir que o usuário insira informações inválidas.</span><span class="sxs-lookup"><span data-stu-id="e7194-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="e7194-113">Portanto, no código do lado do cliente você normalmente valida os ViewModels.</span><span class="sxs-lookup"><span data-stu-id="e7194-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="e7194-114">Você também pode validar os DTOs ou comandos de saída do cliente antes de enviá-los aos serviços.</span><span class="sxs-lookup"><span data-stu-id="e7194-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="e7194-115">A implementação de validação do lado do cliente depende de qual tipo de aplicativo cliente você está criando.</span><span class="sxs-lookup"><span data-stu-id="e7194-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="e7194-116">Será diferente se você estiver validando dados em um aplicativo Web MVC da Web com a maioria do código em .NET, um aplicativo Web SPA com a validação sendo codificada em JavaScript ou TypeScript ou um aplicativo móvel codificado com Xamarin e C#.</span><span class="sxs-lookup"><span data-stu-id="e7194-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e7194-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e7194-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="e7194-118">Validação de aplicativos móveis Xamarin</span><span class="sxs-lookup"><span data-stu-id="e7194-118">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="e7194-119">**Validar entrada de texto e mostrar erros**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="e7194-119">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="e7194-120">**Chamada de retorno de validação**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="e7194-120">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="e7194-121">Validação em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7194-121">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="e7194-122">**Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="e7194-122">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="e7194-123">Validação em aplicativos Web SPA (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="e7194-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="e7194-124">**Ado Kukic. Validação de formulário angular 2**
    [*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="e7194-124">**Ado Kukic. Angular 2 Form Validation**
[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="e7194-125">**Validação de formulário**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="e7194-125">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="e7194-126">**Validação.**</span><span class="sxs-lookup"><span data-stu-id="e7194-126">**Validation.**</span></span> <span data-ttu-id="e7194-127">Documentação da Breeze.</span><span class="sxs-lookup"><span data-stu-id="e7194-127">Breeze documentation.</span></span>
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="e7194-128">Em resumo, estes são os conceitos mais importantes no que diz respeito à validação:</span><span class="sxs-lookup"><span data-stu-id="e7194-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="e7194-129">Entidades e agregações devem impor sua própria consistência e serem "sempre válidas".</span><span class="sxs-lookup"><span data-stu-id="e7194-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="e7194-130">Raízes agregadas são responsáveis pela consistência de várias entidades dentro da mesma agregação.</span><span class="sxs-lookup"><span data-stu-id="e7194-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="e7194-131">Se você acha que uma entidade precisa entrar em um estado inválido, considere usar um modelo de objeto diferente – por exemplo, usar um DTO temporário até criar a entidade de domínio definitiva.</span><span class="sxs-lookup"><span data-stu-id="e7194-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="e7194-132">Se precisar criar vários objetos relacionados, como uma agregação, e eles apenas forem válidos depois que todos tiverem sido criados, considere usar o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="e7194-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="e7194-133">Estruturas de validação são mais bem usadas em camadas específicas, como a camada de apresentação ou a camada de serviço/do aplicativo, mas geralmente não na camada de modelo de domínio, porque você precisaria usar uma dependência de alta segurança em uma estrutura de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="e7194-133">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

- <span data-ttu-id="e7194-134">Na maioria dos casos, ter validação redundante no lado do cliente é bom, porque o aplicativo pode ser proativo.</span><span class="sxs-lookup"><span data-stu-id="e7194-134">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e7194-135">[Anterior](domain-model-layer-validations.md)
[Próximo](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="e7194-135">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>