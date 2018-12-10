---
title: Implementando aplicativos resilientes
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando aplicativos resilientes
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ec79221f0238d61f1ca1b2b7c58b1e16be7f4df4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130788"
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="8bc18-103">Implementando aplicativos resilientes</span><span class="sxs-lookup"><span data-stu-id="8bc18-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="8bc18-104">*É necessário considerar as falhas parciais que certamente ocorrerão ocasionalmente em seus aplicativos de microsserviços e baseados em nuvem. Você precisa projetar seu aplicativo para que ele seja resiliente a essas falhas parciais.*</span><span class="sxs-lookup"><span data-stu-id="8bc18-104">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="8bc18-105">A resiliência é a capacidade de recuperar de falhas e continuar a funcionar.</span><span class="sxs-lookup"><span data-stu-id="8bc18-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="8bc18-106">Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão, e responder a elas de uma maneira que evite tempo de inatividade ou perda de dados.</span><span class="sxs-lookup"><span data-stu-id="8bc18-106">It is not about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="8bc18-107">A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.</span><span class="sxs-lookup"><span data-stu-id="8bc18-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="8bc18-108">Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="8bc18-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="8bc18-109">E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="8bc18-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="8bc18-110">Portanto, seu aplicativo precisa ser resiliente.</span><span class="sxs-lookup"><span data-stu-id="8bc18-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="8bc18-111">Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem.</span><span class="sxs-lookup"><span data-stu-id="8bc18-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="8bc18-112">Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bc18-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="8bc18-113">Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade.</span><span class="sxs-lookup"><span data-stu-id="8bc18-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="8bc18-114">Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.</span><span class="sxs-lookup"><span data-stu-id="8bc18-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8bc18-115">[Anterior](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Próximo](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="8bc18-115">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>