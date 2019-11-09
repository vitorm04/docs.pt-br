---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73737009"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="c8563-103">Escolher plataformas de computação do Azure para aplicativos baseados em contêiner</span><span class="sxs-lookup"><span data-stu-id="c8563-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="c8563-104">Como você observou depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="c8563-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="c8563-105">No entanto, você pode usar a melhor opção para atender às suas necessidades. ele também mostra perguntas sobre qual produto/tecnologia você deve usar para seus aplicativos em contêineres.</span><span class="sxs-lookup"><span data-stu-id="c8563-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="c8563-106">Como uma recomendação *por padrão* , estes são os principais critérios recomendados nestas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="c8563-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="c8563-107">**Aplicativo monolítico único:** Escolher serviço de Azure App</span><span class="sxs-lookup"><span data-stu-id="c8563-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="c8563-108">**Aplicativo de N camadas:** Escolha orquestradores como o AKS (serviço de kubernetes do Azure) ou serviço de aplicativo se você tiver um único ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="c8563-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="c8563-109">**Microserviços:** Escolher AKS ou aplicativos Web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="c8563-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="c8563-110">**Funções sem servidor & manipuladores de eventos:** Escolha Azure Functions</span><span class="sxs-lookup"><span data-stu-id="c8563-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="c8563-111">**Lote em larga escala:** Escolher lote do Azure</span><span class="sxs-lookup"><span data-stu-id="c8563-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="c8563-112">No entanto, essa recomendação deve ser tomada com um pinça de Salt, pois a seleção do produto dependerá de suas necessidades e características específicas do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8563-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="c8563-113">Nem todos os aplicativos são os mesmos mesmo quando inicialmente podem parecer tipos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="c8563-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="c8563-114">Após uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="c8563-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="c8563-115">Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e testar com base em determinada prioridade.</span><span class="sxs-lookup"><span data-stu-id="c8563-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="c8563-116">Na Figura 1, você pode ver uma análise de diferentes tipos de aplicativos e seus cenários de hospedagem do Azure ideais.</span><span class="sxs-lookup"><span data-stu-id="c8563-116">In Figure 1, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![Tabela da qual os cenários de hospedagem do Azure são melhores para aplicativos diferentes.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> <span data-ttu-id="c8563-118">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="c8563-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
