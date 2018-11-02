---
title: Projetando a camada de aplicativos de microsserviço e a API Web
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando a camada de aplicativos de microsserviço e a API Web
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a8c03f99accf75f60fe6c21a0f09f304214b4a6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194092"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="156cd-103">Projetando a camada de aplicativos de microsserviço e a API Web</span><span class="sxs-lookup"><span data-stu-id="156cd-103">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="156cd-104">Usando princípios SOLID e injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="156cd-104">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="156cd-105">Os princípios SOLID são técnicas críticas para serem usadas em qualquer aplicativo moderno e crítico, como desenvolver um microsserviço com padrões DDD.</span><span class="sxs-lookup"><span data-stu-id="156cd-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="156cd-106">SOLID é um acrônimo que agrupa cinco princípios fundamentais:</span><span class="sxs-lookup"><span data-stu-id="156cd-106">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="156cd-107">Princípio da Responsabilidade única</span><span class="sxs-lookup"><span data-stu-id="156cd-107">Single Responsibility principle</span></span>

-   <span data-ttu-id="156cd-108">Princípio do aberto/fechado</span><span class="sxs-lookup"><span data-stu-id="156cd-108">Open/closed principle</span></span>

-   <span data-ttu-id="156cd-109">Princípio da Substituição de Liskov</span><span class="sxs-lookup"><span data-stu-id="156cd-109">Liskov substitution principle</span></span>

-   <span data-ttu-id="156cd-110">Princípio da Segregação de interface</span><span class="sxs-lookup"><span data-stu-id="156cd-110">Interface Segregation principle</span></span>

-   <span data-ttu-id="156cd-111">Princípio da Inversão de dependência</span><span class="sxs-lookup"><span data-stu-id="156cd-111">Dependency Inversion principle</span></span>

<span data-ttu-id="156cd-112">SOLID trata-se da maneira como você cria as camadas internas do microsserviço ou do aplicativo e do desacoplamento das dependências entre eles.</span><span class="sxs-lookup"><span data-stu-id="156cd-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="156cd-113">Ele não está relacionado ao domínio, mas ao design técnico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="156cd-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="156cd-114">O princípio final, o princípio de Inversão de dependência, permite a você desacoplar a camada de infraestrutura do restante das camadas, que permite uma melhor implementação desacoplada das camadas DDD.</span><span class="sxs-lookup"><span data-stu-id="156cd-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="156cd-115">DI (Injeção de Dependência) é uma maneira de implementar o princípio de Inversão de Dependência.</span><span class="sxs-lookup"><span data-stu-id="156cd-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="156cd-116">É uma técnica para obter um acoplamento flexível entre objetos e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="156cd-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="156cd-117">Em vez de criar uma instância de colaboradores diretamente, ou usar referências estáticas, os objetos de que uma classe precisa a fim de executar suas ações são fornecidas (ou "injetadas na") classe.</span><span class="sxs-lookup"><span data-stu-id="156cd-117">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="156cd-118">Geralmente, as classes declararão suas dependências por meio de seu construtor, possibilitando que elas sigam o princípio de Dependências Explícitas.</span><span class="sxs-lookup"><span data-stu-id="156cd-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="156cd-119">Geralmente a DI é baseada em contêineres IoC (Inversão de controle) específicos.</span><span class="sxs-lookup"><span data-stu-id="156cd-119">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="156cd-120">O ASP.NET Core fornece um contêiner IoC interno simples, mas também é possível usar seu contêiner IoC favorito, como Autofac ou Ninject.</span><span class="sxs-lookup"><span data-stu-id="156cd-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="156cd-121">Seguindo os princípios SOLID, as classes naturalmente tenderão a ser pequenas, bem fatoradas e facilmente testadas.</span><span class="sxs-lookup"><span data-stu-id="156cd-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="156cd-122">Mas como é possível saber se muitas dependências estão sendo injetadas suas classes?</span><span class="sxs-lookup"><span data-stu-id="156cd-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="156cd-123">Se você usar a DI por meio do construtor, será fácil detectar isso apenas observando o número de parâmetros para o construtor.</span><span class="sxs-lookup"><span data-stu-id="156cd-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="156cd-124">Se houver mais dependências, isso geralmente será um sinal (um [code smell](https://deviq.com/code-smells/)) de que sua classe está tentando fazer muito mais e está provavelmente violando o princípio de Responsabilidade única.</span><span class="sxs-lookup"><span data-stu-id="156cd-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="156cd-125">Seria preciso outro guia para abordar o SOLID em detalhes.</span><span class="sxs-lookup"><span data-stu-id="156cd-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="156cd-126">Portanto, este guia exige que você tenha apenas um conhecimento mínimo sobre estes tópicos.</span><span class="sxs-lookup"><span data-stu-id="156cd-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="156cd-127">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="156cd-127">Additional resources</span></span>

-   <span data-ttu-id="156cd-128">**SOLID: princípios OOP fundamentais**
    [*https://deviq.com/solid/*](https://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="156cd-128">**SOLID: Fundamental OOP Principles**
[*https://deviq.com/solid/*](https://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="156cd-129">**Inversão de Contêineres de Controle e o padrão de Injeção de Dependência**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="156cd-129">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="156cd-130">**Steve Smith. New is Glue (New é como cola)**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="156cd-130">**Steve Smith. New is Glue**
[*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="156cd-131">[Anterior](nosql-database-persistence-infrastructure.md)
[Próximo](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="156cd-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
