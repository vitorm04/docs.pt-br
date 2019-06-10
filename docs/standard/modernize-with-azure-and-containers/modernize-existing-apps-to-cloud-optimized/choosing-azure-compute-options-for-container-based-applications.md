---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758813"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="f5630-103">Escolher plataformas de computação do Azure para aplicativos baseados em contêiner</span><span class="sxs-lookup"><span data-stu-id="f5630-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="f5630-104">Como você pode ter notado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="f5630-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="f5630-105">Você pode usar o mais adequado para suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.</span><span class="sxs-lookup"><span data-stu-id="f5630-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="f5630-106">Como uma *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:</span><span class="sxs-lookup"><span data-stu-id="f5630-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="f5630-107">**Aplicativo monolítico único:** Escolha o serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="f5630-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="f5630-108">**Aplicativo de N camadas:** Escolha orquestradores, como o serviço de aplicativo ou serviço de Kubernetes do Azure (AKS) se você tiver uma única ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="f5630-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="f5630-109">**Microsserviços do Linux:** Escolha o AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f5630-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="f5630-110">**Microsserviços do Windows:** Escolher aplicativos Web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="f5630-110">**Windows microservices:** Choose Azure Web Apps for Containers</span></span>
- <span data-ttu-id="f5630-111">**Funções sem servidor e manipuladores de eventos:** Escolha o Azure Functions</span><span class="sxs-lookup"><span data-stu-id="f5630-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="f5630-112">**Em grande escala em lote:** Escolha o lote do Azure</span><span class="sxs-lookup"><span data-stu-id="f5630-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="f5630-113">No entanto, essa recomendação deve ser usada com uma situação de emergência de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características.</span><span class="sxs-lookup"><span data-stu-id="f5630-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="f5630-114">Nem todos os aplicativos são os mesmos, mesmo quando inicialmente, elas podem parecer similares.</span><span class="sxs-lookup"><span data-stu-id="f5630-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="f5630-115">Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="f5630-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="f5630-116">Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e teste com base na prioridade de determinados.</span><span class="sxs-lookup"><span data-stu-id="f5630-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="f5630-117">Na figura a seguir, você pode ver uma divisão dos diferentes tipos de aplicativos e seus ideal do Azure em cenários de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="f5630-117">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="f5630-118">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="f5630-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
