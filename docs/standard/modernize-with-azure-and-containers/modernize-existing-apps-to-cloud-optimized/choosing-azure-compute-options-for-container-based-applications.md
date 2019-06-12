---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833849"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="0a689-103">Escolher plataformas de computação do Azure para aplicativos baseados em contêiner</span><span class="sxs-lookup"><span data-stu-id="0a689-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="0a689-104">Como você pode ter notado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="0a689-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="0a689-105">Você pode usar o mais adequado para suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.</span><span class="sxs-lookup"><span data-stu-id="0a689-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="0a689-106">Como uma *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:</span><span class="sxs-lookup"><span data-stu-id="0a689-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="0a689-107">**Aplicativo monolítico único:** Escolha o serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="0a689-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="0a689-108">**Aplicativo de N camadas:** Escolha orquestradores, como o serviço de aplicativo ou serviço de Kubernetes do Azure (AKS) se você tiver uma única ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="0a689-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="0a689-109">**Microsserviços:** Escolha o AKS ou aplicativos Web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="0a689-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="0a689-110">**Funções sem servidor e manipuladores de eventos:** Escolha o Azure Functions</span><span class="sxs-lookup"><span data-stu-id="0a689-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="0a689-111">**Em grande escala em lote:** Escolha o lote do Azure</span><span class="sxs-lookup"><span data-stu-id="0a689-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="0a689-112">No entanto, essa recomendação deve ser usada com uma situação de emergência de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características.</span><span class="sxs-lookup"><span data-stu-id="0a689-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="0a689-113">Nem todos os aplicativos são os mesmos, mesmo quando inicialmente, elas podem parecer similares.</span><span class="sxs-lookup"><span data-stu-id="0a689-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="0a689-114">Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="0a689-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="0a689-115">Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e teste com base na prioridade de determinados.</span><span class="sxs-lookup"><span data-stu-id="0a689-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="0a689-116">Na figura a seguir, você pode ver uma divisão dos diferentes tipos de aplicativos e seus ideal do Azure em cenários de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="0a689-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="0a689-117">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="0a689-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
