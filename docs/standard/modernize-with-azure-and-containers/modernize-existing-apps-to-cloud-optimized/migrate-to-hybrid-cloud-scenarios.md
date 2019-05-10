---
title: Migrar para cenários de nuvem híbrida
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Migrar para cenários de nuvem híbrida
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 6cba29ad654b09b01f9b6969fa6688dd5f165fbb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636586"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="09626-103">Migrar para cenários de nuvem híbrida</span><span class="sxs-lookup"><span data-stu-id="09626-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="09626-104">Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas, como o Microsoft Azure ou qualquer outra nuvem pública devido a normas ou suas próprias políticas.</span><span class="sxs-lookup"><span data-stu-id="09626-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="09626-105">No entanto, é provável que qualquer organização pode se beneficiar de alguns de seus aplicativos na nuvem pública e outros aplicativos no local.</span><span class="sxs-lookup"><span data-stu-id="09626-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="09626-106">Mas um ambiente misto pode levar a complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em nuvens públicas versus ambientes locais.</span><span class="sxs-lookup"><span data-stu-id="09626-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="09626-107">A Microsoft fornece a melhor solução de nuvem híbrida, uma na qual você pode otimizar os ativos existentes no local e na nuvem pública, enquanto você garante a consistência em uma nuvem híbrida do Azure.</span><span class="sxs-lookup"><span data-stu-id="09626-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="09626-108">Você pode maximizar as habilidades existentes e obtenha uma abordagem flexível e unificada para compilar aplicativos que podem ser executados na nuvem ou no local, graças ao Azure Stack (local) e o Azure (nuvem pública).</span><span class="sxs-lookup"><span data-stu-id="09626-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="09626-109">Quando se trata de segurança, você pode centralizar o gerenciamento e segurança em sua nuvem híbrida.</span><span class="sxs-lookup"><span data-stu-id="09626-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="09626-110">Você pode obter controle sobre todos os ativos, do seu datacenter para a nuvem, fornecendo logon único para o local e aplicativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="09626-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="09626-111">Fazer isso, estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.</span><span class="sxs-lookup"><span data-stu-id="09626-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="09626-112">Por fim, você pode distribuir e analise dados perfeitamente, usa as mesmas linguagens de consulta para ativos locais e de nuvem e aplique análise e aprendizagem aprofundada no Azure para enriquecer seus dados, independentemente de sua fonte.</span><span class="sxs-lookup"><span data-stu-id="09626-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="09626-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="09626-113">Azure Stack</span></span>

<span data-ttu-id="09626-114">O Azure Stack é uma plataforma de nuvem híbrida que possibilita entregar serviços do Azure do datacenter da sua organização.</span><span class="sxs-lookup"><span data-stu-id="09626-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="09626-115">O Azure Stack foi projetado para dar suporte a novas opções para seus aplicativos modernos em cenários-chave, como borda e desconectadas ambientes ou requisitos específicos de segurança e conformidade reunião.</span><span class="sxs-lookup"><span data-stu-id="09626-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="09626-116">Figura 4-13 mostra uma visão geral da plataforma em nuvem híbrida real oferecidas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="09626-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Plataforma de nuvem híbrida Microsoft com o Azure Stack e o Azure](./media/image13.jpg)

> <span data-ttu-id="09626-118">**Figura 4-13.**</span><span class="sxs-lookup"><span data-stu-id="09626-118">**Figure 4-13.**</span></span> <span data-ttu-id="09626-119">Plataforma de nuvem híbrida Microsoft com o Azure Stack e o Azure</span><span class="sxs-lookup"><span data-stu-id="09626-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="09626-120">O Azure Stack é oferecido em duas opções de implantação para atender às suas necessidades:</span><span class="sxs-lookup"><span data-stu-id="09626-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="09626-121">Sistemas integrados do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="09626-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="09626-122">Kit de Desenvolvimento do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="09626-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="09626-123">Sistemas integrados do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="09626-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="09626-124">Sistemas de pilha integrado do Azure são oferecidos por meio de uma parceria de parceiros da Microsoft e de hardware.</span><span class="sxs-lookup"><span data-stu-id="09626-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="09626-125">A parceria cria uma solução que oferece inovação conduzida a nuvem que é equilibrada com simplicidade no gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="09626-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="09626-126">Porque o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adotando a inovação da nuvem.</span><span class="sxs-lookup"><span data-stu-id="09626-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="09626-127">Sistemas de pilha integrado do Azure variam de tamanho de 4 a 12 nós e têm suporte em conjunto pela Microsoft e parceiros de hardware.</span><span class="sxs-lookup"><span data-stu-id="09626-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="09626-128">Use sistemas integrados do Azure Stack para implementação de novos cenários para suas cargas de trabalho de produção.</span><span class="sxs-lookup"><span data-stu-id="09626-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="09626-129">Kit de Desenvolvimento do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="09626-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="09626-130">Kit de desenvolvimento do Microsoft Azure Stack é uma implantação de nó único do Azure Stack, que você pode usar para avaliar e saber mais sobre o Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="09626-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="09626-131">Você também pode usar o Kit de desenvolvimento do Azure Stack como um ambiente de desenvolvedor, onde você pode desenvolver usando as APIs e ferramentas que são consistentes com o Azure.</span><span class="sxs-lookup"><span data-stu-id="09626-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="09626-132">Kit de desenvolvimento do Azure Stack não se destina a ser usado como um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="09626-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="09626-133">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="09626-133">Additional resources</span></span>

- <span data-ttu-id="09626-134">**Nuvem híbrida do Azure**</span><span class="sxs-lookup"><span data-stu-id="09626-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="09626-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="09626-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="09626-136">**Contas de serviço do Active Directory para contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="09626-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="09626-137">**Criar um contêiner com suporte do Active Directory**</span><span class="sxs-lookup"><span data-stu-id="09626-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="09626-138">**Licenciamento do benefício híbrido do Azure**</span><span class="sxs-lookup"><span data-stu-id="09626-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="09626-139">[Anterior](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[Próximo](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="09626-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
