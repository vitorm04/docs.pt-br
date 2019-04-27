---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: f251aecfeaf2421a5cecf218577369963bc736fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811743"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="968f9-103">Escolher plataformas de computação do Azure para aplicativos baseados em contêiner</span><span class="sxs-lookup"><span data-stu-id="968f9-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="968f9-104">Como você pode ter notado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções.</span><span class="sxs-lookup"><span data-stu-id="968f9-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="968f9-105">Você pode usar o mais adequado para suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.</span><span class="sxs-lookup"><span data-stu-id="968f9-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="968f9-106">Como uma *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:</span><span class="sxs-lookup"><span data-stu-id="968f9-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="968f9-107">**Aplicativo monolítico único:** Escolha o serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="968f9-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="968f9-108">**Aplicativo de N camadas:** Escolha orquestradores como serviço de Kubernetes do Azure (AKS), o Service Fabric (SF) ou o serviço de aplicativo, se você tiver uma única ou alguns serviços de back-end</span><span class="sxs-lookup"><span data-stu-id="968f9-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="968f9-109">**Microsserviços do Linux:** Escolha o AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="968f9-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="968f9-110">**Microsserviços do Windows:** Escolha Service Fabric</span><span class="sxs-lookup"><span data-stu-id="968f9-110">**Windows microservices:** Choose Service Fabric</span></span>
- <span data-ttu-id="968f9-111">**Funções sem servidor e manipuladores de eventos:** Escolha o Azure Functions</span><span class="sxs-lookup"><span data-stu-id="968f9-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="968f9-112">**Em grande escala em lote:** Escolha o lote do Azure</span><span class="sxs-lookup"><span data-stu-id="968f9-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="968f9-113">No entanto, essa recomendação deve ser usada com uma situação de emergência de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características.</span><span class="sxs-lookup"><span data-stu-id="968f9-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="968f9-114">Nem todos os aplicativos são os mesmos, mesmo quando inicialmente, elas podem parecer similares.</span><span class="sxs-lookup"><span data-stu-id="968f9-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="968f9-115">Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="968f9-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="968f9-116">Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e teste com base na prioridade de determinados.</span><span class="sxs-lookup"><span data-stu-id="968f9-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="968f9-117">Na figura a seguir, você pode analisar mais global enquanto a tabela de decisões detalhadas.</span><span class="sxs-lookup"><span data-stu-id="968f9-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="968f9-118">Observe como a base do sistema operacional (Windows vs. Linux) também pode ser um fator de decisão conforme alguns orquestradores são mais maduro em contêineres do Linux e outros em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="968f9-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="968f9-119">Por exemplo, os contêineres do Linux são muito maduros no Kubernetes (AKS no Azure), mas menos maduro no Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="968f9-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="968f9-120">Por outro lado, contêineres do Windows são mais maduro no Service Fabric (lançado em maio de 2017) e menos maduro no AKS.</span><span class="sxs-lookup"><span data-stu-id="968f9-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="968f9-121">No entanto, essas diferenças em maturidade do sistema operacional serão fade in no futuro e várias plataformas terão comparáveis maturidade do sistema operacional e a decisão definirá o layout mais nas preferências com base em recursos específicos do seu aplicativo, talvez seja necessário ou com base no ecossistema de cada plataforma motivos.</span><span class="sxs-lookup"><span data-stu-id="968f9-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="968f9-122">[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="968f9-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
