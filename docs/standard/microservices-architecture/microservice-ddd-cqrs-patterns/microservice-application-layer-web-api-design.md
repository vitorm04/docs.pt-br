---
title: "Criar a camada de aplicativo de microsserviço e a API da Web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar a camada de aplicativo de microsserviço e a API da Web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="08954-104">Criar a camada de aplicativo de microsserviço e a API da Web</span><span class="sxs-lookup"><span data-stu-id="08954-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="08954-105">Usando a injeção de dependência e princípios SÓLIDOS</span><span class="sxs-lookup"><span data-stu-id="08954-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="08954-106">Princípios SÓLIDOS são técnicas críticas a ser usado em qualquer aplicativo moderno e de missão crítica, como desenvolver um microsserviço com padrões DDD.</span><span class="sxs-lookup"><span data-stu-id="08954-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="08954-107">SÓLIDA é um acrônimo que princípios fundamentais de grupos cinco:</span><span class="sxs-lookup"><span data-stu-id="08954-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="08954-108">Princípio da responsabilidade única</span><span class="sxs-lookup"><span data-stu-id="08954-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="08954-109">Abrir/fechado</span><span class="sxs-lookup"><span data-stu-id="08954-109">Open/closed principle</span></span>

-   <span data-ttu-id="08954-110">Substituição de Liskov</span><span class="sxs-lookup"><span data-stu-id="08954-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="08954-111">Princípio de diferenciação de inversão</span><span class="sxs-lookup"><span data-stu-id="08954-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="08954-112">Princípio de inversão de dependência</span><span class="sxs-lookup"><span data-stu-id="08954-112">Dependency Inversion principle</span></span>

<span data-ttu-id="08954-113">SÓLIDO é mais sobre como criar seu aplicativo ou as camadas de microsserviço interno e desacoplamento dependências entre eles.</span><span class="sxs-lookup"><span data-stu-id="08954-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="08954-114">Ele não está relacionado ao domínio, mas ao design técnico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08954-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="08954-115">O princípio final, o princípio de inversão de dependência (DI), permite que você separe a camada de infraestrutura do restante das camadas, que permite uma melhor implementação das camadas DDD separada.</span><span class="sxs-lookup"><span data-stu-id="08954-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="08954-116">Injeção de dependência é uma maneira de implementar o princípio de inversão de dependência.</span><span class="sxs-lookup"><span data-stu-id="08954-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="08954-117">Essa é uma técnica para a obtenção de um acoplamento fraco entre objetos e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="08954-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="08954-118">Em vez de diretamente a instanciação de parceiros, ou usando referências estáticas, os objetos que precisa de uma classe para realizar suas ações são fornecidos para (ou "injetados") a classe.</span><span class="sxs-lookup"><span data-stu-id="08954-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="08954-119">Geralmente, classes irá declarar suas dependências por meio de seu construtor, possibilitando que siga o princípio de dependências explícitas.</span><span class="sxs-lookup"><span data-stu-id="08954-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="08954-120">Injeção de dependência é normalmente com base em contêineres específicos de inversão de controle (IoC).</span><span class="sxs-lookup"><span data-stu-id="08954-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="08954-121">ASP.NET Core fornece um contêiner IoC interno simples, mas você também pode usar o contêiner IoC favorito, como Autofac ou Ninject.</span><span class="sxs-lookup"><span data-stu-id="08954-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="08954-122">Seguindo os princípios SÓLIDOS, suas classes tendem naturalmente sejam pequenos, bem fatorada e facilmente testados.</span><span class="sxs-lookup"><span data-stu-id="08954-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="08954-123">Mas como você sabe se muitas dependências estão sendo injetadas suas classes?</span><span class="sxs-lookup"><span data-stu-id="08954-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="08954-124">Se você usar a DI por meio do construtor, será fácil detectar que, apenas observando o número de parâmetros para o construtor.</span><span class="sxs-lookup"><span data-stu-id="08954-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="08954-125">Se houver muitas dependências, isso geralmente é um sinal (um [código cheiro](http://deviq.com/code-smells/)) que sua classe está tentando fazer muito e provavelmente está violando o princípio da responsabilidade única.</span><span class="sxs-lookup"><span data-stu-id="08954-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="08954-126">Levaria outra guia para cobrir sólido em detalhes.</span><span class="sxs-lookup"><span data-stu-id="08954-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="08954-127">Portanto, este guia exige que você tenha apenas um conhecimento mínimo dos seguintes tópicos.</span><span class="sxs-lookup"><span data-stu-id="08954-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="08954-128">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="08954-128">Additional resources</span></span>

-   <span data-ttu-id="08954-129">**SÓLIDO: Princípios OOP fundamentais**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="08954-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="08954-130">**Inversão de contêineres de controle e o padrão de injeção de dependência**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="08954-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="08954-131">**Steve Smith. Novo é liga**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="08954-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="08954-132">[Anterior] (nosql-banco de dados-persistência-infrastructure.md) [Avançar] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="08954-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
