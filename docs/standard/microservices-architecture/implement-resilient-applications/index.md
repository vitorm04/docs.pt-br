---
title: Implementando aplicativos resilientes
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando aplicativos resilientes
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
ms.openlocfilehash: 93e5435b402cc1a8ff049f25465de0f719516f31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="eddec-104">Implementando aplicativos resilientes</span><span class="sxs-lookup"><span data-stu-id="eddec-104">Implementing Resilient Applications</span></span>

<span data-ttu-id="eddec-105">*Seus aplicativos de microsserviços e baseados em nuvem devem compreender as falhas parciais que certamente poderão ocorrerão. Você precisa projetar seu aplicativo para que ele seja resiliente a essas falhas parciais.*</span><span class="sxs-lookup"><span data-stu-id="eddec-105">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="eddec-106">A resiliência é a capacidade de recuperar de falhas e continuar a funcionar.</span><span class="sxs-lookup"><span data-stu-id="eddec-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="eddec-107">Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão e de responder a elas de uma maneira que evite o tempo de inatividade ou a perda de dados.</span><span class="sxs-lookup"><span data-stu-id="eddec-107">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="eddec-108">A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.</span><span class="sxs-lookup"><span data-stu-id="eddec-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="eddec-109">Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="eddec-109">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="eddec-110">E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="eddec-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="eddec-111">Portanto, seu aplicativo precisa ser resiliente.</span><span class="sxs-lookup"><span data-stu-id="eddec-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="eddec-112">Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem.</span><span class="sxs-lookup"><span data-stu-id="eddec-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="eddec-113">Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eddec-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="eddec-114">Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade.</span><span class="sxs-lookup"><span data-stu-id="eddec-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="eddec-115">Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.</span><span class="sxs-lookup"><span data-stu-id="eddec-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="eddec-116">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="eddec-116">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
