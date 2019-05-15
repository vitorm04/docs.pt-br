---
title: Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Entenda como lidar com cenários de negócios complexos aplicando padrões DDD e CQRS
ms.date: 10/08/2018
ms.openlocfilehash: d311641e2ac73205c04c3f1147b54991585ce851
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639806"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="d2f65-103">Lidar com a complexidade dos negócios em um microsserviço com padrões DDD e CQRS</span><span class="sxs-lookup"><span data-stu-id="d2f65-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="d2f65-104">*Crie um modelo de domínio para cada microsserviço ou contexto limitado que reflita o entendimento do domínio da empresa.*</span><span class="sxs-lookup"><span data-stu-id="d2f65-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="d2f65-105">Esta seção concentra-se em microsserviços mais avançados que você implementa quando precisa lidar com subsistemas complexos ou com microsserviços derivados do conhecimento de especialistas no domínio com mudanças constantes nas regras de negócio.</span><span class="sxs-lookup"><span data-stu-id="d2f65-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="d2f65-106">Os padrões de arquitetura usados nesta seção são baseados nas abordagens DDD (design controlado por domínio) e CQRS (Segregação de Responsabilidade de Comando e Consulta), conforme é ilustrado na Figura 7-1.</span><span class="sxs-lookup"><span data-stu-id="d2f65-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Diferença entre arquitetura externa: padrões de microsserviço, gateways de API, comunicação resilientes, pub/sub etc. e a arquitetura interna: controlado por dados/CRUD, padrões de DDD, injeção de dependência, várias bibliotecas etc.](./media/image1.png)

<span data-ttu-id="d2f65-108">**Figura 7-1**.</span><span class="sxs-lookup"><span data-stu-id="d2f65-108">**Figure 7-1**.</span></span> <span data-ttu-id="d2f65-109">Arquitetura externa de microsserviço versus padrões de arquitetura interna para cada microsserviço</span><span class="sxs-lookup"><span data-stu-id="d2f65-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="d2f65-110">No entanto, a maioria das técnicas de microsserviços controlados por dados, incluindo como implementar um serviço de API Web do ASP.NET Core ou como expor metadados com Swashbuckle ou NSwag, também se aplica aos microsserviços mais avançados implementados internamente com padrões DDD.</span><span class="sxs-lookup"><span data-stu-id="d2f65-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="d2f65-111">Esta seção é uma extensão das seções anteriores, pois a maioria das práticas de explicadas anteriormente também se aplicam aqui ou para qualquer tipo de microsserviço.</span><span class="sxs-lookup"><span data-stu-id="d2f65-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="d2f65-112">Esta seção primeiro fornece detalhes sobre os padrões CQRS simplificados usados no aplicativo de referência eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="d2f65-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="d2f65-113">Posteriormente, você obterá uma visão geral das técnicas de DDD que permitem encontrar padrões comuns que podem ser reutilizados em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d2f65-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="d2f65-114">O DDD é um tópico grande com um conjunto avançado de recursos de aprendizagem.</span><span class="sxs-lookup"><span data-stu-id="d2f65-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="d2f65-115">Você pode iniciar com guias como [Domain-Driven Design](https://domainlanguage.com/ddd/) (Design controlado por domínio) do Eric Evans e os materiais adicionais dos autores Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard e muitos outros especialistas em DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="d2f65-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="d2f65-116">Mas, sobretudo, você precisa tentar aprender como aplicar as técnicas de DDD das sessões de conversa, de quadro de comunicações e de modelagem com os especialistas em seu domínio de negócio concreto.</span><span class="sxs-lookup"><span data-stu-id="d2f65-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d2f65-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="d2f65-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="d2f65-118">DDD (design controlado por domínio)</span><span class="sxs-lookup"><span data-stu-id="d2f65-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="d2f65-119">**Eric Evans. Idioma do domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-119">**Eric Evans. Domain Language** \\</span></span>
  <https://domainlanguage.com/>

- <span data-ttu-id="d2f65-120">**Martin Fowler. Design orientado por domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="d2f65-121">**Jimmy Bogard. Como reforçar seu domínio: informações elementares** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="d2f65-122">Guias sobre DDD</span><span class="sxs-lookup"><span data-stu-id="d2f65-122">DDD books</span></span>

- <span data-ttu-id="d2f65-123">**Eric Evans. Design orientado por domínio: Lidar com a complexidade no núcleo do software** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="d2f65-124">**Eric Evans. Referências de design controlado por domínio: Resumos de padrão e definições** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="d2f65-125">**Vaughn Vernon. Implementação de um design orientado por domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="d2f65-126">**Vaughn Vernon. Design orientado por domínio condensado** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="d2f65-127">**Jimmy Nilsson. Aplicação de design e padrões orientados por domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="d2f65-128">**Cesar de la Torre. Guia de arquitetura orientado por domínio em N camadas com o .NET** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="d2f65-129">**Abel Avram e Floyd Marinescu. Design orientado por domínio rapidamente** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="d2f65-130">**Scott Millett, Nick Tune – Padrões, princípios e práticas recomendadas do design orientado por domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="d2f65-131">Treinamento em DDD</span><span class="sxs-lookup"><span data-stu-id="d2f65-131">DDD training</span></span>

- <span data-ttu-id="d2f65-132">**Julie Lerman e Steve Smith. Conceitos básicos sobre o design orientado por domínio** \\</span><span class="sxs-lookup"><span data-stu-id="d2f65-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="d2f65-133">[Anterior](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[Próximo](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="d2f65-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
