---
title: Implementando aplicativos resilientes
description: Saiba mais sobre a resiliência, um conceito central na arquitetura de microsserviços. Você deve saber como lidar com falhas transitórias normalmente porque eles ocorrerão.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977687"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="c4dfd-104">Implementar aplicativos resilientes</span><span class="sxs-lookup"><span data-stu-id="c4dfd-104">Implement Resilient Applications</span></span>

<span data-ttu-id="c4dfd-105">*É necessário considerar as falhas parciais que certamente ocorrerão ocasionalmente em seus aplicativos de microsserviços e baseados em nuvem. Você deve projetar seu aplicativo para ser resiliente a essas falhas parciais.*</span><span class="sxs-lookup"><span data-stu-id="c4dfd-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="c4dfd-106">A resiliência é a capacidade de recuperar de falhas e continuar a funcionar.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="c4dfd-107">Não se trata de evitar falhas, mas de aceitar o fato de que as falhas acontecerão, e responder a elas de uma maneira que evite tempo de inatividade ou perda de dados.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="c4dfd-108">A meta de resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="c4dfd-109">Já é um grande desafio criar e implantar um aplicativo baseado em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="c4dfd-110">E você ainda precisa manter o aplicativo em execução em um ambiente em que algum tipo de falha certamente ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="c4dfd-111">Portanto, seu aplicativo precisa ser resiliente.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="c4dfd-112">Ele deve ser projetado para lidar com falhas parciais, como interrupções da rede ou falhas de nós ou de VMs na nuvem.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="c4dfd-113">Até mesmo os microsserviços (contêineres) que estão sendo movidos para outro nó em um cluster podem causar falhas curtas intermitentes no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="c4dfd-114">Os diversos componentes individuais do aplicativo também precisam incorporar recursos de monitoramento de integridade.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="c4dfd-115">Seguindo as diretrizes neste capítulo, você poderá criar um aplicativo que pode funcionar perfeitamente apesar do tempo de inatividade temporário ou das interrupções normais que ocorrem em implantações complexas e baseadas em nuvem.</span><span class="sxs-lookup"><span data-stu-id="c4dfd-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c4dfd-116">[Anterior](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Próximo](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="c4dfd-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>