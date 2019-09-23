---
title: Padrões de comunicação nativa de nuvem
description: Saiba mais sobre as principais preocupações de comunicação do serviço em aplicativos nativos de nuvem
author: robvet
ms.date: 08/31/2019
ms.openlocfilehash: 0123d2e3da1bf8df29efcf2595a38c377dd1d1a1
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183374"
---
# <a name="cloud-native-communication-patterns"></a><span data-ttu-id="694a7-103">Padrões de comunicação nativa de nuvem</span><span class="sxs-lookup"><span data-stu-id="694a7-103">Cloud-native communication patterns</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="694a7-104">Ao construir um sistema nativo de nuvem, a comunicação se torna uma decisão de design significativa.</span><span class="sxs-lookup"><span data-stu-id="694a7-104">When constructing a cloud-native system, communication becomes a significant design decision.</span></span> <span data-ttu-id="694a7-105">Como um aplicativo cliente front-end se comunica com um microserviço de back-end?</span><span class="sxs-lookup"><span data-stu-id="694a7-105">How does a front-end client application communicate with a back-end microservice?</span></span> <span data-ttu-id="694a7-106">Como os microserviços de back-end se comunicam entre si?</span><span class="sxs-lookup"><span data-stu-id="694a7-106">How do back-end microservices communicate with each other?</span></span> <span data-ttu-id="694a7-107">Quais são os princípios, padrões e práticas recomendadas a serem considerados ao implementar a comunicação em aplicativos nativos de nuvem?</span><span class="sxs-lookup"><span data-stu-id="694a7-107">What are the principles, patterns, and best practices to consider when implementing communication in cloud-native applications?</span></span>

## <a name="communication-considerations"></a><span data-ttu-id="694a7-108">Considerações de comunicação</span><span class="sxs-lookup"><span data-stu-id="694a7-108">Communication considerations</span></span>

<span data-ttu-id="694a7-109">Em um aplicativo monolítico, a comunicação é simples.</span><span class="sxs-lookup"><span data-stu-id="694a7-109">In a monolithic application, communication is straightforward.</span></span> <span data-ttu-id="694a7-110">Os módulos de código são executados juntos no mesmo espaço executável (processo) em um servidor.</span><span class="sxs-lookup"><span data-stu-id="694a7-110">The code modules execute together in the same executable space (process) on a server.</span></span> <span data-ttu-id="694a7-111">Essa abordagem pode ter vantagens de desempenho à medida que tudo é executado juntos na memória compartilhada, mas resulta em um código rigidamente acoplado que se torna difícil de manter, evoluir e dimensionar.</span><span class="sxs-lookup"><span data-stu-id="694a7-111">This approach can have performance advantages as everything runs together in shared memory, but results in tightly coupled code that becomes difficult to maintain, evolve, and scale.</span></span>

<span data-ttu-id="694a7-112">Os sistemas nativos de nuvem implementam uma arquitetura baseada em microserviço com muitos microserviços pequenos e independentes.</span><span class="sxs-lookup"><span data-stu-id="694a7-112">Cloud-native systems implement a microservice-based architecture with many small, independent microservices.</span></span> <span data-ttu-id="694a7-113">Cada microserviço é executado em um processo separado e normalmente é executado dentro de um contêiner implantado em um *cluster*.</span><span class="sxs-lookup"><span data-stu-id="694a7-113">Each microservice executes in a separate process and typically runs inside a container that is deployed to a *cluster*.</span></span> 

<span data-ttu-id="694a7-114">Um cluster agrupa um pool de máquinas virtuais para formar um ambiente altamente disponível.</span><span class="sxs-lookup"><span data-stu-id="694a7-114">A cluster groups a pool of virtual machines together to form a highly available environment.</span></span> <span data-ttu-id="694a7-115">Eles são gerenciados com uma ferramenta de orquestração, que é responsável por implantar e gerenciar os microserviços em contêineres.</span><span class="sxs-lookup"><span data-stu-id="694a7-115">They're managed with an orchestration tool, which is responsible for deploying and managing the containerized microservices.</span></span> <span data-ttu-id="694a7-116">A Figura 4-1 mostra um cluster [kubernetes](https://kubernetes.io) implantado na nuvem do Azure com os [serviços de kubernetes do Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)totalmente gerenciados.</span><span class="sxs-lookup"><span data-stu-id="694a7-116">Figure 4-1 shows a [Kubernetes](https://kubernetes.io) cluster deployed into the Azure cloud with the fully managed [Azure Kubernetes Services](https://docs.microsoft.com/azure/aks/intro-kubernetes).</span></span>

![Um cluster kubernetes no Azure](./media/kubernetes-cluster-in-azure.png)

<span data-ttu-id="694a7-118">**Figura 4-1**.</span><span class="sxs-lookup"><span data-stu-id="694a7-118">**Figure 4-1**.</span></span> <span data-ttu-id="694a7-119">Um cluster kubernetes no Azure</span><span class="sxs-lookup"><span data-stu-id="694a7-119">A Kubernetes cluster in Azure</span></span>

<span data-ttu-id="694a7-120">No cluster, os microserviços se comunicam entre si por meio de APIs e tecnologias de mensagens.</span><span class="sxs-lookup"><span data-stu-id="694a7-120">Across the cluster, microservices communicate with each other through APIs and messaging technologies.</span></span>

<span data-ttu-id="694a7-121">Embora eles forneçam muitos benefícios, os microserviços não são um almoço gratuito.</span><span class="sxs-lookup"><span data-stu-id="694a7-121">While they provide many benefits, microservices are no free lunch.</span></span> <span data-ttu-id="694a7-122">As chamadas de método local no processo entre componentes agora são substituídas por chamadas de rede.</span><span class="sxs-lookup"><span data-stu-id="694a7-122">Local in-process method calls between components are now replaced with network calls.</span></span> <span data-ttu-id="694a7-123">Cada microserviço deve se comunicar por um protocolo de rede, o que adiciona complexidade ao seu sistema:</span><span class="sxs-lookup"><span data-stu-id="694a7-123">Each microservice must communicate over a network protocol, which adds complexity to your system:</span></span>

- <span data-ttu-id="694a7-124">O congestionamento da rede, a latência e as falhas transitórias são uma preocupação constante.</span><span class="sxs-lookup"><span data-stu-id="694a7-124">Network congestion, latency, and transient faults are a constant concern.</span></span>

- <span data-ttu-id="694a7-125">A resiliência (ou seja, repetindo solicitações com falha) é essencial.</span><span class="sxs-lookup"><span data-stu-id="694a7-125">Resiliency (that is, retrying failed requests) is essential.</span></span>

- <span data-ttu-id="694a7-126">Algumas chamadas devem ser [idempotentes](https://www.restapitutorial.com/lessons/idempotency.html) como para manter o estado consistente.</span><span class="sxs-lookup"><span data-stu-id="694a7-126">Some calls must be [idempotent](https://www.restapitutorial.com/lessons/idempotency.html) as to keep consistent state.</span></span>

- <span data-ttu-id="694a7-127">Cada microserviço deve autenticar e autorizar chamadas.</span><span class="sxs-lookup"><span data-stu-id="694a7-127">Each microservice must authenticate and authorize calls.</span></span>

- <span data-ttu-id="694a7-128">Cada mensagem deve ser serializada e, em seguida, desserializada – o que pode ser caro.</span><span class="sxs-lookup"><span data-stu-id="694a7-128">Each message must be serialized and then deserialized - which can be expensive.</span></span>

- <span data-ttu-id="694a7-129">A criptografia/descriptografia de mensagens se torna importante.</span><span class="sxs-lookup"><span data-stu-id="694a7-129">Message encryption/decryption becomes important.</span></span>

<span data-ttu-id="694a7-130">Os microserviços do Book [.net: A arquitetura para aplicativos](https://docs.microsoft.com/dotnet/standard/microservices-architecture/).net em contêineres, disponível gratuitamente da Microsoft, fornece uma cobertura detalhada dos padrões de comunicação para aplicativos de microatendimento.</span><span class="sxs-lookup"><span data-stu-id="694a7-130">The book [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/), available for free from Microsoft, provides an in-depth coverage of communication patterns for microservice applications.</span></span> <span data-ttu-id="694a7-131">Neste capítulo, fornecemos uma visão geral de alto nível desses padrões, juntamente com as opções de implementação disponíveis na nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="694a7-131">In this chapter, we provide a high-level overview of these patterns along with implementation options available in the Azure cloud.</span></span>

<span data-ttu-id="694a7-132">Neste capítulo, primeiro abordaremos a comunicação entre os aplicativos de front-end e os microserviços de back-end.</span><span class="sxs-lookup"><span data-stu-id="694a7-132">In this chapter, we'll first address communication between front-end applications and back-end microservices.</span></span> <span data-ttu-id="694a7-133">Em seguida, veremos que os microserviços de back-end se comunicam entre si.</span><span class="sxs-lookup"><span data-stu-id="694a7-133">We'll then look at back-end microservices communicate with each other.</span></span> <span data-ttu-id="694a7-134">Exploraremos a tecnologia de comunicação para cima e gRPC.</span><span class="sxs-lookup"><span data-stu-id="694a7-134">We'll explore the up and gRPC communication technology.</span></span> <span data-ttu-id="694a7-135">Por fim, examinaremos os novos padrões de comunicação inovadores usando a tecnologia de malha de serviço.</span><span class="sxs-lookup"><span data-stu-id="694a7-135">Finally, we'll look new innovative communication patterns using service mesh technology.</span></span> <span data-ttu-id="694a7-136">Também veremos como a nuvem do Azure fornece diferentes tipos de *serviços de backup* para dar suporte à comunicação nativa de nuvem.</span><span class="sxs-lookup"><span data-stu-id="694a7-136">We'll also see how the Azure cloud provides different kinds of *backing services* to support cloud-native communication.</span></span>  


>[!div class="step-by-step"]
><span data-ttu-id="694a7-137">[Anterior](other-deployment-options.md)
>[Próximo](front-end-communication.md)</span><span class="sxs-lookup"><span data-stu-id="694a7-137">[Previous](other-deployment-options.md)
[Next](front-end-communication.md)</span></span>
