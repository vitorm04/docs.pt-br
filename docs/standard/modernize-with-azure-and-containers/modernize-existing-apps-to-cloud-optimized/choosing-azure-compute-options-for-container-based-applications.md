---
title: Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="6dc8d-103">Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner</span><span class="sxs-lookup"><span data-stu-id="6dc8d-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="6dc8d-104">Como você pode ter observado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="6dc8d-105">Você pode usar o mais adequado às suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="6dc8d-106">Como um *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:</span><span class="sxs-lookup"><span data-stu-id="6dc8d-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="6dc8d-107">**Único aplicativo monolítico:** escolher serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="6dc8d-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="6dc8d-108">**Aplicativo de N camadas:** escolha orchestrators como Azure Kubernetes serviço (AKS), serviço de malha (SF) ou do serviço de aplicativo, se você tiver uma única ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="6dc8d-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="6dc8d-109">**Linux microservices:** AKS/Kubernetes escolha</span><span class="sxs-lookup"><span data-stu-id="6dc8d-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="6dc8d-110">**Windows microservices:** escolha Service Fabric</span><span class="sxs-lookup"><span data-stu-id="6dc8d-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="6dc8d-111">**Funções sem servidor e manipuladores de eventos:** escolher funções do Azure</span><span class="sxs-lookup"><span data-stu-id="6dc8d-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="6dc8d-112">**Lotes em larga escala:** escolha lote do Azure</span><span class="sxs-lookup"><span data-stu-id="6dc8d-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="6dc8d-113">No entanto, essa recomendação deve ser usada com um pouco de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="6dc8d-114">Nem todos os aplicativos são as mesmas mesmo quando inicialmente tipos semelhantes podem ser exibidas.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="6dc8d-115">Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="6dc8d-116">Mas, como um ponto de partida, é recomendável diretrizes inicial da onde você pode iniciar a avaliação e teste com base em determinada prioridade.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="6dc8d-117">A figura a seguir, você pode analisar mais global enquanto a tabela de decisões detalhadas.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="6dc8d-118">Observe como a base do sistema operacional (Windows vs. Linux) também pode ser um fator de decisão, assim como alguns orchestrators mais maduro em contêineres do Linux e outros em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="6dc8d-119">Por exemplo, contêineres do Linux são maduros em Kubernetes (AKS no Azure) mas menos maduro na malha do serviço.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="6dc8d-120">Por outro lado, os contêineres do Windows são menos maduro em AKS e mais maduro na malha do serviço (lançado em maio de 2017).</span><span class="sxs-lookup"><span data-stu-id="6dc8d-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="6dc8d-121">No entanto, essas diferenças no vencimento do sistema operacional serão desaparecer no futuro e várias plataformas terá maturidade comparável do sistema operacional e a decisão será apresentar mais informações sobre preferências com base em recursos específicos do seu aplicativo, talvez seja necessário ou com base no ecossistema de cada plataforma motivos.</span><span class="sxs-lookup"><span data-stu-id="6dc8d-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6dc8d-122">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="6dc8d-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
