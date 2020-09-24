---
title: Resiliência nativa de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Resiliência nativa na nuvem
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163551"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="07874-103">Resiliência nativa de nuvem</span><span class="sxs-lookup"><span data-stu-id="07874-103">Cloud-native resiliency</span></span>

<span data-ttu-id="07874-104">A resiliência é a capacidade do seu sistema de reagir à falha e ainda continuar funcionando.</span><span class="sxs-lookup"><span data-stu-id="07874-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="07874-105">Não está prestes a evitar falhas, mas aceitando falhas e construindo seus serviços nativos de nuvem para responder a ela.</span><span class="sxs-lookup"><span data-stu-id="07874-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="07874-106">Você deseja retornar a um estado totalmente funcional o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="07874-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="07874-107">Ao contrário dos aplicativos monolíticos tradicionais, onde tudo é executado juntos em um único processo, os sistemas nativos de nuvem adotam uma arquitetura distribuída, como mostrado na Figura 6-1:</span><span class="sxs-lookup"><span data-stu-id="07874-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![Ambiente nativo de nuvem distribuída](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="07874-109">**Figura 6-1.**</span><span class="sxs-lookup"><span data-stu-id="07874-109">**Figure 6-1.**</span></span> <span data-ttu-id="07874-110">Ambiente nativo de nuvem distribuída</span><span class="sxs-lookup"><span data-stu-id="07874-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="07874-111">Na figura anterior, cada microserviço e [serviço de backup](https://12factor.net/backing-services) baseado em nuvem é executado em um processo separado, na infraestrutura de servidor, comunicando-se por meio de chamadas baseadas em rede.</span><span class="sxs-lookup"><span data-stu-id="07874-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="07874-112">Operando nesse ambiente, um serviço deve ser sensível a muitos desafios diferentes:</span><span class="sxs-lookup"><span data-stu-id="07874-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="07874-113">Latência de rede inesperada-o tempo para uma solicitação de serviço viajar para o receptor e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="07874-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="07874-114">[Falhas transitórias](/azure/architecture/best-practices/transient-faults) -erros de conectividade de rede de curta duração.</span><span class="sxs-lookup"><span data-stu-id="07874-114">[Transient faults](/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="07874-115">Bloqueio por uma operação síncrona de execução longa.</span><span class="sxs-lookup"><span data-stu-id="07874-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="07874-116">Um processo de host que falhou e está sendo reiniciado ou movido.</span><span class="sxs-lookup"><span data-stu-id="07874-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="07874-117">Um microserviço sobrecarregado que não pode responder por um curto período de tempo.</span><span class="sxs-lookup"><span data-stu-id="07874-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="07874-118">Uma operação de orquestrador em andamento, como uma atualização sem interrupção ou movendo um serviço de um nó para outro.</span><span class="sxs-lookup"><span data-stu-id="07874-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="07874-119">Falhas de hardware.</span><span class="sxs-lookup"><span data-stu-id="07874-119">Hardware failures.</span></span>

<span data-ttu-id="07874-120">As plataformas de nuvem podem detectar e atenuar muitos desses problemas de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="07874-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="07874-121">Ele pode reiniciar, escalar horizontalmente e até mesmo redistribuir seu serviço para um nó diferente.</span><span class="sxs-lookup"><span data-stu-id="07874-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="07874-122">No entanto, para aproveitar ao máximo essa proteção interna, você deve projetar seus serviços para reagir a ele e prosperar nesse ambiente dinâmico.</span><span class="sxs-lookup"><span data-stu-id="07874-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="07874-123">Nas seções a seguir, exploraremos técnicas defensivas que o serviço e os recursos de nuvem gerenciados podem aproveitar para minimizar o tempo de inatividade e a interrupção.</span><span class="sxs-lookup"><span data-stu-id="07874-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="07874-124">[Anterior](elastic-search-in-azure.md) 
> [Avançar](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="07874-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
