---
title: Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 13abff090d42c5d59476612942560c126836dbb0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104472"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="a1ed0-103">Projetando e desenvolvendo aplicativos .NET baseados em microsserviço e em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="a1ed0-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="a1ed0-104">*Desenvolver aplicativos de microsserviço em contêineres significa criar aplicativos em vários contêineres. No entanto, um aplicativo em vários contêineres também pode ser mais simples, como um aplicativo de três camadas, e talvez não seja criado usando uma arquitetura de microsserviço.*</span><span class="sxs-lookup"><span data-stu-id="a1ed0-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="a1ed0-105">Anteriormente, fizemos a pergunta "O Docker é necessário ao criar uma arquitetura de microsserviço?"</span><span class="sxs-lookup"><span data-stu-id="a1ed0-105">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="a1ed0-106">A resposta é claramente não.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-106">The answer is a clear no.</span></span> <span data-ttu-id="a1ed0-107">O Docker é um habilitador e pode fornecer benefícios significativos, mas os contêineres e o Docker não são um requisito rígido para os microsserviços.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="a1ed0-108">Por exemplo, você pode criar um aplicativo baseado em microsserviços com ou sem o Docker ao usar o Azure Service Fabric, que dá suporte a microsserviços executados como processos simples ou como contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="a1ed0-109">No entanto, se você souber como projetar e desenvolver um aplicativo baseado em microsserviços que também seja baseado em contêineres do Docker, será possível projetar e desenvolver qualquer outro modelo de aplicativo mais simples.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="a1ed0-110">Por exemplo, você pode projetar um aplicativo de três camadas que também exija uma abordagem de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="a1ed0-111">Por esse motivo e como as arquiteturas de microsserviço são uma tendência importante no campo dos contêineres, esta seção concentra-se em uma implementação de arquitetura de microsserviço que usa contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a1ed0-112">[Anterior](../containerize-net-framework-applications/index.md)
[Próximo](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="a1ed0-112">[Previous](../containerize-net-framework-applications/index.md)
[Next](microservice-application-design.md)</span></span>
