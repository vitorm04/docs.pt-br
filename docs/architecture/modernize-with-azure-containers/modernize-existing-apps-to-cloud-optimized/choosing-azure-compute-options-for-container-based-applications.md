---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318675"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="a58fa-103">Escolher plataformas de computação do Azure para aplicativos baseados em contêiner</span><span class="sxs-lookup"><span data-stu-id="a58fa-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="a58fa-104">Como você observou depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="a58fa-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="a58fa-105">No entanto, você pode usar a melhor opção para atender às suas necessidades. ele também mostra perguntas sobre qual produto/tecnologia você deve usar para seus aplicativos em contêineres.</span><span class="sxs-lookup"><span data-stu-id="a58fa-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="a58fa-106">Como uma recomendação *por padrão* , estes são os principais critérios recomendados nestas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="a58fa-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="a58fa-107">**Aplicativo monolítico único:** Escolher serviço de Azure App</span><span class="sxs-lookup"><span data-stu-id="a58fa-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="a58fa-108">**Aplicativo de N camadas:** Escolha orquestradores como o AKS (serviço de kubernetes do Azure) ou serviço de aplicativo se você tiver um único ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="a58fa-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="a58fa-109">**Microserviços:** Escolher AKS ou aplicativos Web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="a58fa-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="a58fa-110">**Funções sem servidor & manipuladores de eventos:** Escolha Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a58fa-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="a58fa-111">**Lote em larga escala:** Escolher lote do Azure</span><span class="sxs-lookup"><span data-stu-id="a58fa-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="a58fa-112">No entanto, essa recomendação deve ser tomada com um pinça de Salt, pois a seleção do produto dependerá de suas necessidades e características específicas do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a58fa-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="a58fa-113">Nem todos os aplicativos são os mesmos mesmo quando inicialmente podem parecer tipos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="a58fa-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="a58fa-114">Após uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="a58fa-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="a58fa-115">Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e testar com base em determinada prioridade.</span><span class="sxs-lookup"><span data-stu-id="a58fa-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="a58fa-116">Na Figura 1, você pode ver uma análise de diferentes tipos de aplicativos e seus cenários de hospedagem do Azure ideais.</span><span class="sxs-lookup"><span data-stu-id="a58fa-116">In Figure 1, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![Figura 1](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="a58fa-118">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="a58fa-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
