---
title: Arquitetura de microsserviços
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Arquitetura de microsserviços
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78d3903e7ed4abf27e78812de87ccbcb9f733663
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="microservices-architecture"></a><span data-ttu-id="54a12-104">Arquitetura de microsserviços</span><span class="sxs-lookup"><span data-stu-id="54a12-104">Microservices architecture</span></span>

<span data-ttu-id="54a12-105">Como o nome implica, uma arquitetura de microsserviços é uma abordagem para criar um aplicativo para servidores como um conjunto de serviços pequenos.</span><span class="sxs-lookup"><span data-stu-id="54a12-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="54a12-106">Cada serviço é executado em seus próprio processo e comunica-se com outros processos usando protocolos como HTTP/HTTPS, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span><span class="sxs-lookup"><span data-stu-id="54a12-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="54a12-107">Cada microsserviço implementa um domínio de ponta a ponta específico ou uma capacidade de negócios dentro de um determinado limite de contexto, e cada um deve ser desenvolvido de forma autônoma e ser implantado independentemente.</span><span class="sxs-lookup"><span data-stu-id="54a12-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="54a12-108">Por fim, cada microsserviço deve ter seu modelo de dados de domínio relacionado e sua lógica de domínio (gerenciamento de dados decentralizados e de soberania) com base em diferentes tecnologias de armazenamento de dados (SQL, NoSQL) e diferentes linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="54a12-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="54a12-109">Que tamanho deve ter um microsserviço?</span><span class="sxs-lookup"><span data-stu-id="54a12-109">What size should a microservice be?</span></span> <span data-ttu-id="54a12-110">Ao desenvolver um microsserviço, o tamanho não deve ser o ponto importante.</span><span class="sxs-lookup"><span data-stu-id="54a12-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="54a12-111">Em vez disso, o ponto importante deve ser criar serviços acoplados livremente para você ter autonomia de desenvolvimento, implantação e escala, para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="54a12-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="54a12-112">É claro que, ao identificar e criar microsserviços, você deve tentar torná-las o menor possível, desde que você não tenha muitas dependências diretas com outros microsserviços.</span><span class="sxs-lookup"><span data-stu-id="54a12-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="54a12-113">Mais importante do que o tamanho do microsserviço é a coesão interna que ele deve ter e sua independência de outros serviços.</span><span class="sxs-lookup"><span data-stu-id="54a12-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="54a12-114">Por que uma arquitetura de microsserviços?</span><span class="sxs-lookup"><span data-stu-id="54a12-114">Why a microservices architecture?</span></span> <span data-ttu-id="54a12-115">Em resumo, ela oferece agilidade de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="54a12-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="54a12-116">Os microsserviços permitem melhor facilidade de manutenção em sistemas complexos, grandes e altamente escalonáveis permitindo a criação de aplicativos com base em muitos serviços implantáveis de maneira independente em que cada um tenha ciclos de vida autônomos e granulares.</span><span class="sxs-lookup"><span data-stu-id="54a12-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="54a12-117">Como uma vantagem adicional, os microsserviços podem ser aumentados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="54a12-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="54a12-118">Em vez de ter um único aplicativo monolítico que você deve aumentar como uma unidade, é possível aumentar microsserviços específicos.</span><span class="sxs-lookup"><span data-stu-id="54a12-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="54a12-119">Desta forma, é possível escalar apenas a área funcional que precisa de mais potência de processamento ou largura de banda de rede para dar suporte à demanda, em vez de aumentar outras áreas do aplicativo que não precisam ser escaladas.</span><span class="sxs-lookup"><span data-stu-id="54a12-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="54a12-120">Isso significa economias de custo, porque você precisa de menos hardware.</span><span class="sxs-lookup"><span data-stu-id="54a12-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="54a12-121">**Figura 4-6**.</span><span class="sxs-lookup"><span data-stu-id="54a12-121">**Figure 4-6**.</span></span> <span data-ttu-id="54a12-122">Implantação monolítica versus a abordagem de microsserviços</span><span class="sxs-lookup"><span data-stu-id="54a12-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="54a12-123">Como mostra a Figura 4-6, a abordagem de microsserviços permite alterações ágeis e rápida iteração de cada microsserviço, porque é possível alterar áreas pequenas específicas de aplicativos grandes, complexos e escalonáveis.</span><span class="sxs-lookup"><span data-stu-id="54a12-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="54a12-124">A arquitetura de aplicativos baseados em microsserviços refinados permite práticas de integração e de entrega contínua.</span><span class="sxs-lookup"><span data-stu-id="54a12-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="54a12-125">Ela também acelera a entrega de novas funções no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54a12-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="54a12-126">A composição refinada de aplicativos também permite a você executar e testar microsserviços em isolamento e evoluí-los de maneira autônoma ao manter contratos claros entre eles.</span><span class="sxs-lookup"><span data-stu-id="54a12-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="54a12-127">Desde que você não altere a interfaces ou contratos, é possível alterar a implementação interna de qualquer microsserviço ou adicionar novas funcionalidades sem interromper outros microsserviços.</span><span class="sxs-lookup"><span data-stu-id="54a12-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="54a12-128">A seguir estão os aspectos importantes para habilitar o sucesso na entrada em produção com um sistema baseado em microsserviços:</span><span class="sxs-lookup"><span data-stu-id="54a12-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="54a12-129">Monitoramento e verificações de integridade dos serviços e da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="54a12-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="54a12-130">Infraestrutura escalonável dos serviços (ou seja, nuvem e orquestradores).</span><span class="sxs-lookup"><span data-stu-id="54a12-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="54a12-131">Design de segurança e implementação em vários níveis: autenticação, autorização, gerenciamento de segredos, comunicação segura, etc.</span><span class="sxs-lookup"><span data-stu-id="54a12-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="54a12-132">Entrega rápida de aplicativos, geralmente com diferentes equipes focando-se em diferentes microsserviços.</span><span class="sxs-lookup"><span data-stu-id="54a12-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="54a12-133">DevOps e práticas e infraestrutura CI/CD.</span><span class="sxs-lookup"><span data-stu-id="54a12-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="54a12-134">Dessas, apenas as três primeiras serão abordadas ou introduzidas neste guia.</span><span class="sxs-lookup"><span data-stu-id="54a12-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="54a12-135">Os dois últimos pontos, que estão relacionados ao ciclo de vida do aplicativo, são abordados no livro eletrônico adicional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida do aplicativo Docker em contêineres com Microsoft Platform e ferramentas).</span><span class="sxs-lookup"><span data-stu-id="54a12-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="54a12-136">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="54a12-136">Additional resources</span></span>

-   <span data-ttu-id="54a12-137">**Mark Russinovich. Microsserviços: Uma revolução de aplicativos com tecnologia de nuvem**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="54a12-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="54a12-138">**Martin Fowler. Microsserviços**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="54a12-138">**Martin Fowler. Microservices**
[*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="54a12-139">**Martin Fowler. Pré-requisitos de microsserviços**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="54a12-139">**Martin Fowler. Microservice Prerequisites**
[*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="54a12-140">**Jimmy Nilsson. Computação em nuvem em partes**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="54a12-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="54a12-141">**Cesar de la Torre. Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft (e-book para download)**[*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="54a12-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="54a12-142">[Anterior] (service-oriented-architecture.md) [Próximo] (data-sovereignty-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="54a12-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
