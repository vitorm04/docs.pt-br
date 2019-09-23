---
title: Resiliência nativa de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Resiliência nativa na nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184837"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="e26a6-103">Resiliência nativa de nuvem</span><span class="sxs-lookup"><span data-stu-id="e26a6-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e26a6-104">A resiliência é a capacidade do seu sistema de reagir à falha e ainda continuar funcionando.</span><span class="sxs-lookup"><span data-stu-id="e26a6-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="e26a6-105">Não está prestes a evitar falhas.</span><span class="sxs-lookup"><span data-stu-id="e26a6-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="e26a6-106">Mas trata-se de aceitar que a falha seja inevitável em sistemas baseados em nuvem e criando seu aplicativo para responder a ele.</span><span class="sxs-lookup"><span data-stu-id="e26a6-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="e26a6-107">O objetivo final da resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.</span><span class="sxs-lookup"><span data-stu-id="e26a6-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="e26a6-108">Ao contrário dos aplicativos monolíticos tradicionais, onde tudo é executado juntos em um único processo, os sistemas nativos de nuvem adotam a arquitetura distribuída, conforme mostrado na Figura 6-1:</span><span class="sxs-lookup"><span data-stu-id="e26a6-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Ambiente nativo de nuvem distribuída](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="e26a6-110">**Figura 6-1.**</span><span class="sxs-lookup"><span data-stu-id="e26a6-110">**Figure 6-1.**</span></span> <span data-ttu-id="e26a6-111">Ambiente nativo de nuvem distribuída</span><span class="sxs-lookup"><span data-stu-id="e26a6-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="e26a6-112">Na figura anterior, observe como cada cliente, microserviço e [serviço de backup](https://12factor.net/backing-services) baseado em nuvem é executado como um processo separado, em execução em diferentes servidores, todas comunicando-se por meio de chamadas baseadas em rede.</span><span class="sxs-lookup"><span data-stu-id="e26a6-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="e26a6-113">Então, o que poderia dar errado?</span><span class="sxs-lookup"><span data-stu-id="e26a6-113">So, what could go wrong?</span></span>

- <span data-ttu-id="e26a6-114">[Latência de rede](https://www.techopedia.com/definition/8553/network-latency)inesperada.</span><span class="sxs-lookup"><span data-stu-id="e26a6-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="e26a6-115">[Falhas transitórias](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (erros de conectividade de rede temporários).</span><span class="sxs-lookup"><span data-stu-id="e26a6-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="e26a6-116">Bloqueio por uma operação síncrona de execução longa.</span><span class="sxs-lookup"><span data-stu-id="e26a6-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="e26a6-117">Um processo de host que falhou e está sendo reiniciado ou movido.</span><span class="sxs-lookup"><span data-stu-id="e26a6-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="e26a6-118">Um microserviço sobrecarregado que não pode responder por um curto período de tempo.</span><span class="sxs-lookup"><span data-stu-id="e26a6-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="e26a6-119">Uma operação DevOps em andamento, como uma operação de atualização ou de dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="e26a6-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="e26a6-120">Uma operação de orquestrador, como mover um serviço de um nó para outro.</span><span class="sxs-lookup"><span data-stu-id="e26a6-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="e26a6-121">Falhas de hardware do hardware de mercadoria.</span><span class="sxs-lookup"><span data-stu-id="e26a6-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="e26a6-122">Ao implantar serviços distribuídos em infraestrutura baseada em nuvem, os fatores da lista anterior se tornam muito reais e você deve arquitetar e desenvolver de maneira defensiva para lidar com eles.</span><span class="sxs-lookup"><span data-stu-id="e26a6-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="e26a6-123">Em um sistema distribuído de pequena escala, a falha será menos frequente, mas, à medida que o sistema for expandido e reduzido, você poderá esperar mais desses problemas até um ponto em que a falha parcial se tornará uma operação normal.</span><span class="sxs-lookup"><span data-stu-id="e26a6-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="e26a6-124">Portanto, seu aplicativo e sua infraestrutura devem ser resilientes.</span><span class="sxs-lookup"><span data-stu-id="e26a6-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="e26a6-125">Nas seções a seguir, exploraremos técnicas defensivas que você pode adicionar ao seu aplicativo e recursos de nuvem internos que você pode aproveitar para ajudar a verificar a experiência do usuário na prova de marcadores.</span><span class="sxs-lookup"><span data-stu-id="e26a6-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e26a6-126">[Anterior](azure-data-storage.md)
>[Próximo](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="e26a6-126">[Previous](azure-data-storage.md)
[Next](application-resiliency-patterns.md)</span></span>
