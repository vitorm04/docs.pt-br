---
title: Migrar para cenários de nuvem híbrida
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Migrar para cenários de nuvem híbrida
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957886"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="3b6c2-103">Migrar para cenários de nuvem híbrida</span><span class="sxs-lookup"><span data-stu-id="3b6c2-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="3b6c2-104">Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas, como o Microsoft Azure ou qualquer nuvem pública devido a normas ou suas próprias políticas.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="3b6c2-105">No entanto, é provável que qualquer organização pode se beneficiar de ter alguns de seus aplicativos na nuvem pública e outros aplicativos no local.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="3b6c2-106">Mas um ambiente misto pode levar a complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em nuvens públicas versus ambientes locais.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="3b6c2-107">A Microsoft fornece a melhor solução de nuvem híbrida, um em que você pode otimizar seus ativos locais e na nuvem pública, enquanto você garante a consistência em uma nuvem híbrida do Azure.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="3b6c2-108">Você pode maximizar os recursos existentes e obter uma abordagem flexível e unificada para a criação de aplicativos que podem ser executados na nuvem ou no local, graças a pilha do Azure (local) e o Azure (nuvem pública).</span><span class="sxs-lookup"><span data-stu-id="3b6c2-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="3b6c2-109">Quando se trata de segurança, você pode centralizar o gerenciamento e segurança em sua nuvem híbrida.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="3b6c2-110">Você pode obter controle sobre todos os ativos, do Data Center na nuvem, fornecendo logon único no local e aplicativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="3b6c2-111">Fazer isso, estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="3b6c2-112">Por fim, você pode distribuir e analisar dados diretamente, usar as mesmas linguagens de consulta para ativos de nuvem e local e aplicar análises e profundo de aprendizagem no Azure para enriquecer seus dados, independentemente de sua origem.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="3b6c2-113">Pilha do Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-113">Azure Stack</span></span>

<span data-ttu-id="3b6c2-114">A pilha do Azure é uma plataforma de nuvem híbrida que lhe permite oferecer serviços do Azure do datacenter de sua organização.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="3b6c2-115">A pilha do Azure foi projetada para dar suporte a novas opções para seus aplicativos modernos em cenários mais importantes, como borda e desconectado de ambientes ou requisitos específicos de segurança e conformidade reunião.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="3b6c2-116">Figura 4-13 mostra uma visão geral da plataforma de nuvem híbrida true oferecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Plataforma de nuvem híbrida Microsoft com a pilha do Azure e o Azure](./media/image13.jpg)

> <span data-ttu-id="3b6c2-118">**Figura 4-13.**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-118">**Figure 4-13.**</span></span> <span data-ttu-id="3b6c2-119">Plataforma de nuvem híbrida Microsoft com a pilha do Azure e o Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="3b6c2-120">A pilha do Azure é oferecida em duas opções de implantação para atender às suas necessidades:</span><span class="sxs-lookup"><span data-stu-id="3b6c2-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="3b6c2-121">Sistemas de pilha integrado do Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="3b6c2-122">Kit de desenvolvimento de pilha do Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="3b6c2-123">Sistemas de pilha integrado do Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="3b6c2-124">Sistemas de pilha integrado do Azure são oferecidos por meio de uma parceria de parceiros da Microsoft e de hardware.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="3b6c2-125">A parceria cria uma solução que oferece inovação individual de nuvem que é equilibrada com simplicidade no gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="3b6c2-126">Como pilha do Azure é oferecida como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adotando inovação da nuvem.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="3b6c2-127">Sistemas de pilha integrado do Azure variam em tamanho de 4 a 12 nós e têm suporte em conjunto de parceiros de hardware e da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="3b6c2-128">Use sistemas de pilha do Azure integradas para implementar novos cenários para suas cargas de trabalho de produção.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="3b6c2-129">Kit de desenvolvimento de pilha do Azure</span><span class="sxs-lookup"><span data-stu-id="3b6c2-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="3b6c2-130">Kit de desenvolvimento de pilha do Microsoft Azure é uma implantação de nó único da pilha do Azure, que você pode usar para avaliar e saber mais sobre a pilha do Azure.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="3b6c2-131">Você também pode usar o Kit de desenvolvimento de pilha do Azure como um ambiente de desenvolvedor, onde você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="3b6c2-132">Kit de desenvolvimento de pilha do Azure não se destina a ser usado como um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="3b6c2-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b6c2-133">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3b6c2-133">Additional resources</span></span>

-   <span data-ttu-id="3b6c2-134">**Nuvem híbrida do Azure**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="3b6c2-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="3b6c2-136">**Contas de serviço do Active Directory para contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="3b6c2-137">**Criar um contêiner com o suporte do Active Directory**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="3b6c2-138">**Licenciamento de benefício híbrido do Azure**</span><span class="sxs-lookup"><span data-stu-id="3b6c2-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="3b6c2-139">[Anterior](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Próximo](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3b6c2-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
