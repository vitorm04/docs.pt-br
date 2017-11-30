---
title: "Validação do lado do cliente (validação nas camadas de apresentação)"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Validação do lado do cliente (validação nas camadas de apresentação)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="cf3a4-104">Validação do lado do cliente (validação nas camadas de apresentação)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="cf3a4-105">Mesmo quando a fonte de verdade é o modelo de domínio e, por fim, você deve ter a validação no nível do modelo de domínio, a validação ainda pode ser tratada no nível do modelo de domínio (do lado do servidor) e do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="cf3a4-106">Validação do lado do cliente é uma ótima conveniência para usuários.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="cf3a4-107">Ele salva o tempo que outra forma seriam passam aguardando uma viagem de ida e para o servidor que pode retornar erros de validação.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="cf3a4-108">Em termos de negócios, até mesmo algumas frações de segundos multiplicados centenas de vezes por dia adiciona a muito tempo, despesas e frustração.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="cf3a4-109">Validação de imediata e simples permite que os usuários trabalhem com mais eficiência e produzir a melhor qualidade de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="cf3a4-110">Como o modelo de exibição e o modelo de domínio são diferentes, validação do modelo de exibição e a validação do modelo de domínio podem ser semelhantes, mas têm um propósito diferente.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="cf3a4-111">Se você estiver preocupado sobre simulação (não repita por conta própria entidade de segurança), considere que nesse caso reutilização de código também pode significar acoplamento e aplicativos corporativos é mais importante não acoplar o lado do servidor para o lado do cliente que para siga o princípio seco.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="cf3a4-112">Mesmo ao usar a validação do lado do cliente, você sempre deve validar seus comandos ou DTOs de entrada no código do servidor, porque o servidor APIs são um vetor de ataque.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="cf3a4-113">Geralmente, fazer as duas é a melhor opção porque se você tiver um aplicativo cliente, de uma perspectiva UX, é melhor ser proativo e não permitir que o usuário insira informações inválidas.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="cf3a4-114">Portanto, no código do lado do cliente é geralmente validar ViewModels.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="cf3a4-115">Você também pode validar o cliente DTOs ou comandos de saída antes de enviá-los para os serviços.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="cf3a4-116">A implementação de validação do lado do cliente depende de qual tipo de aplicativo cliente que você está criando.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="cf3a4-117">Ele será diferente se você estiver validando dados em um aplicativo web MVC da web com a maior parte do código no .NET, um aplicativo web que está sendo codificado em JavaScript ou TypeScript, a validação SPA ou codificado de um aplicativo móvel com o Xamarin e C\#.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cf3a4-118">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="cf3a4-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="cf3a4-119">Validação de aplicativos móveis do Xamarin</span><span class="sxs-lookup"><span data-stu-id="cf3a4-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="cf3a4-120">**Validar a entrada de texto e mostrar erros**
    [*https://developer.xamarin.com/recipes/ios/standard\_controles/texto\_campo/Validar\_entrada /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="cf3a4-121">**Retorno de chamada de validação**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="cf3a4-122">Validação em aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cf3a4-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="cf3a4-123">**Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="cf3a4-124">Validação em SPA Web apps (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="cf3a4-125">**Kukic ADO. Validação do formulário angular 2** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="cf3a4-126">**Validação do formulário**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="cf3a4-127">**Validação.**</span><span class="sxs-lookup"><span data-stu-id="cf3a4-127">**Validation.**</span></span> <span data-ttu-id="cf3a4-128">Documentação muito fácil.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-128">Breeze documentation.</span></span>
    [<span data-ttu-id="cf3a4-129">*http://Breeze.GitHub.IO/doc-js/Validation.HTML*</span><span class="sxs-lookup"><span data-stu-id="cf3a4-129">*http://breeze.github.io/doc-js/validation.html*</span></span>](http://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="cf3a4-130">Em resumo, estes são os conceitos mais importantes no que diz respeito à validação:</span><span class="sxs-lookup"><span data-stu-id="cf3a4-130">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="cf3a4-131">Entidades e agregações devem impor sua próprias consistência e ser "sempre válido".</span><span class="sxs-lookup"><span data-stu-id="cf3a4-131">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="cf3a4-132">Raízes agregadas são responsáveis por consistência de várias entidade na mesma agregação.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-132">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="cf3a4-133">Se você achar que precisa de uma entidade para inserir um estado inválido, considere o uso de um modelo de objeto diferente — por exemplo, usando um DTO temporário até que você criar a entidade de domínio final.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-133">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="cf3a4-134">Se você precisar criar vários objetos relacionados, como uma agregação, e eles são válidos somente depois que todos eles foram criados, considere usar o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-134">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="cf3a4-135">Estruturas de validação são melhor usadas em camadas específicas, como a camada de apresentação ou camada de serviço do aplicativo, mas geralmente não na camada de modelo de domínio, porque você precisa executar uma dependência de alta segurança em uma estrutura de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-135">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="cf3a4-136">Na maioria dos casos, ter redundância validação no lado do cliente é bom, porque o aplicativo pode ser proativo.</span><span class="sxs-lookup"><span data-stu-id="cf3a4-136">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="cf3a4-137">[Anterior] (domínio-modelo-camada-validations.md) [Avançar] (domínio-eventos-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="cf3a4-137">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>
