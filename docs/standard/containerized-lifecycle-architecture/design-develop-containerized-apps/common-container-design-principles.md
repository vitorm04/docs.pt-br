---
title: Noções básicas de criação de contêiner comum
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c398e2da979637c450e2c9754ff3c9e8d8233aeb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="common-container-design-principles"></a><span data-ttu-id="5f028-103">Noções básicas de criação de contêiner comum</span><span class="sxs-lookup"><span data-stu-id="5f028-103">Common container design principles</span></span>

<span data-ttu-id="5f028-104">Em frente de obter no processo de desenvolvimento, há alguns conceitos básicos, vale a pena mencionar em relação a como você pode usar contêineres.</span><span class="sxs-lookup"><span data-stu-id="5f028-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="5f028-105">Contêiner é igual a um processo</span><span class="sxs-lookup"><span data-stu-id="5f028-105">Container equals a process</span></span>

<span data-ttu-id="5f028-106">No modelo de contêiner, um contêiner representa um único processo.</span><span class="sxs-lookup"><span data-stu-id="5f028-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="5f028-107">Definindo um contêiner como um limite de processo, você começar a criar os primitivos usados para escala, ou em lotes de lançamento, processos.</span><span class="sxs-lookup"><span data-stu-id="5f028-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="5f028-108">Quando você executa um contêiner do Docker, você verá um [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definição.</span><span class="sxs-lookup"><span data-stu-id="5f028-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="5f028-109">Isso define o processo e o tempo de vida do contêiner.</span><span class="sxs-lookup"><span data-stu-id="5f028-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="5f028-110">Quando o processo for concluído, o ciclo de vida do contêiner será encerrada.</span><span class="sxs-lookup"><span data-stu-id="5f028-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="5f028-111">Há processos de longa execução, como servidores web e processos de curta duração, como trabalhos de lote, que podem ter sido implementados como o Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span><span class="sxs-lookup"><span data-stu-id="5f028-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="5f028-112">Se o processo falhar, o contêiner é encerrado e o orquestrador assume.</span><span class="sxs-lookup"><span data-stu-id="5f028-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="5f028-113">Se o orchestrator instruído para manter a cinco instâncias em execução e um falhar, o orchestrator criará outro contêiner para substituir o processo com falha.</span><span class="sxs-lookup"><span data-stu-id="5f028-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="5f028-114">Em um trabalho em lotes, o processo é iniciado com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5f028-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="5f028-115">Quando o processo é concluído, o trabalho é concluído.</span><span class="sxs-lookup"><span data-stu-id="5f028-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="5f028-116">Você pode encontrar um cenário no qual você deseja que vários processos em execução em um único contêiner.</span><span class="sxs-lookup"><span data-stu-id="5f028-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="5f028-117">Em qualquer documento de arquitetura, nunca há um "nunca", nem sempre há um "sempre".</span><span class="sxs-lookup"><span data-stu-id="5f028-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="5f028-118">Para cenários que exigem vários processos, um padrão comum é usar [Supervisor](http://supervisord.org/).</span><span class="sxs-lookup"><span data-stu-id="5f028-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5f028-119">[Anterior] (design-docker-applications.md) [Avançar] (monolítico applications.md)</span><span class="sxs-lookup"><span data-stu-id="5f028-119">[Previous] (design-docker-applications.md) [Next] (monolithic-applications.md)</span></span>
