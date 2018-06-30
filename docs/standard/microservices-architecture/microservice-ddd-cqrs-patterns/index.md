---
title: Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: af67f94b2c56f6a1ec794abbf7d3dad0d78033ec
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105752"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="47fcc-103">Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS</span><span class="sxs-lookup"><span data-stu-id="47fcc-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="47fcc-104">*Crie um modelo de domínio para cada microsserviço ou contexto limitado que reflita o entendimento do domínio da empresa.*</span><span class="sxs-lookup"><span data-stu-id="47fcc-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="47fcc-105">Esta seção concentra-se em microsserviços mais avançados que você implementa quando precisa lidar com subsistemas complexos ou com microsserviços derivados do conhecimento de especialistas no domínio com mudanças constantes nas regras de negócio.</span><span class="sxs-lookup"><span data-stu-id="47fcc-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="47fcc-106">Os padrões de arquitetura usados nesta seção são baseados nas abordagens DDD (design controlado por domínio) e CQRS (Segregação de Responsabilidade de Comando e Consulta), conforme é ilustrado na Figura 9-1.</span><span class="sxs-lookup"><span data-stu-id="47fcc-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="47fcc-107">**Figura 9-1**.</span><span class="sxs-lookup"><span data-stu-id="47fcc-107">**Figure 9-1**.</span></span> <span data-ttu-id="47fcc-108">Arquitetura externa de microsserviço versus padrões de arquitetura interna para cada microsserviço</span><span class="sxs-lookup"><span data-stu-id="47fcc-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="47fcc-109">No entanto, a maioria das técnicas de microsserviços controlados por dados, incluindo como implementar um serviço de API Web do ASP.NET Core ou como expor metadados do Swagger com o Swashbuckle, também se aplica aos microsserviços mais avançados implementados internamente com padrões DDD.</span><span class="sxs-lookup"><span data-stu-id="47fcc-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="47fcc-110">Esta seção é uma extensão das seções anteriores, pois a maioria das práticas de explicadas anteriormente também se aplicam aqui ou para qualquer tipo de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="47fcc-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="47fcc-111">Esta seção primeiro fornece detalhes sobre os padrões CQRS simplificados usados no aplicativo de referência eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="47fcc-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="47fcc-112">Posteriormente, você obterá uma visão geral das técnicas de DDD que permitem encontrar padrões comuns que podem ser reutilizados em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="47fcc-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="47fcc-113">O DDD é um tópico grande com um conjunto avançado de recursos de aprendizagem.</span><span class="sxs-lookup"><span data-stu-id="47fcc-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="47fcc-114">Você pode iniciar com guias como [Domain-Driven Design](https://domainlanguage.com/ddd/) (Design controlado por domínio) do Eric Evans e os materiais adicionais dos autores Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard e muitos outros especialistas em DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="47fcc-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="47fcc-115">Mas, sobretudo, você precisa tentar aprender como aplicar as técnicas de DDD das sessões de conversa, de quadro de comunicações e de modelagem com os especialistas em seu domínio de negócio concreto.</span><span class="sxs-lookup"><span data-stu-id="47fcc-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="47fcc-116">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="47fcc-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="47fcc-117">DDD (design controlado por domínio)</span><span class="sxs-lookup"><span data-stu-id="47fcc-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="47fcc-118">**Eric Evans. Idioma do domínio**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="47fcc-119">**Martin Fowler. Design orientado por domínio**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="47fcc-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="47fcc-120">**Jimmy Bogard. Reforçando seu domínio: informações elementares**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="47fcc-121">Guias sobre DDD</span><span class="sxs-lookup"><span data-stu-id="47fcc-121">DDD books</span></span>

-   <span data-ttu-id="47fcc-122">**Eric Evans. Design orientado por domínio: lidando com a complexidade no núcleo do software**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="47fcc-123">**Eric Evans. Referência do design orientado por domínio: definições e resumos de padrão**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="47fcc-124">**Vaughn Vernon. Implementando um design controlado por domínio**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="47fcc-125">**Vaughn Vernon. Design orientado por domínio condensado**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="47fcc-126">**Jimmy Nilsson. Aplicando design e padrões orientados por domínio**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="47fcc-127">**Cesar de la Torre. Guia de arquitetura orientado por domínio em N camadas com o .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="47fcc-128">**Abel Avram e Floyd Marinescu. Design orientado por domínio rapidamente**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="47fcc-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="47fcc-129">Treinamento em DDD</span><span class="sxs-lookup"><span data-stu-id="47fcc-129">DDD training</span></span>

-   <span data-ttu-id="47fcc-130">**Julie Lerman e Steve Smith. Conceitos básicos sobre o design orientado por domínio**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="47fcc-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="47fcc-131">[Anterior](../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)
[Próximo](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="47fcc-131">[Previous](../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
