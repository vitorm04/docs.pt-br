---
title: Migrar para cenários de nuvem híbrida
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Migrar para cenários de nuvem híbrida
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937370"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="5b1c5-103">Migrar para cenários de nuvem híbrida</span><span class="sxs-lookup"><span data-stu-id="5b1c5-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="5b1c5-104">Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas como o Microsoft Azure ou qualquer outra nuvem pública devido a regulamentos ou suas próprias políticas.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="5b1c5-105">No entanto, é provável que qualquer organização possa se beneficiar de ter algumas de suas aplicações na nuvem pública e outras aplicações no local.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="5b1c5-106">Mas um ambiente misto pode levar a uma complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em ambientes públicos versus ambientes locais.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="5b1c5-107">A Microsoft fornece a melhor solução de nuvem híbrida, na qual você pode otimizar seus ativos existentes no local e na nuvem pública, enquanto você garante consistência em uma nuvem híbrida do Azure.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="5b1c5-108">Você pode maximizar as habilidades existentes e obter uma abordagem flexível e unificada para criar aplicativos que possam ser executados na nuvem ou no local, graças ao Azure Stack (no local) e ao Azure (nuvem pública).</span><span class="sxs-lookup"><span data-stu-id="5b1c5-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="5b1c5-109">Quando se trata de segurança, você pode centralizar o gerenciamento e a segurança em toda a sua nuvem híbrida.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="5b1c5-110">Você pode obter controle sobre todos os ativos, desde o seu datacenter até a nuvem, fornecendo o login único no local e aplicativos em nuvem.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="5b1c5-111">Você consegue isso estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="5b1c5-112">Finalmente, você pode distribuir e analisar dados sem problemas, usar as mesmas linguagens de consulta para ativos em nuvem e locais e aplicar análises e aprendizado profundo no Azure para enriquecer seus dados, independentemente de sua fonte.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="5b1c5-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="5b1c5-113">Azure Stack</span></span>

<span data-ttu-id="5b1c5-114">O Azure Stack é uma plataforma de nuvem híbrida que permite que você ofereça serviços do Azure a partir do datacenter da sua organização.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="5b1c5-115">O Azure Stack foi projetado para suportar novas opções para seus aplicativos modernos em cenários-chave, como ambientes de borda e desconectados, ou atender a requisitos específicos de segurança e conformidade.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="5b1c5-116">A Figura 4-13 mostra uma visão geral da verdadeira plataforma de nuvem híbrida que a Microsoft oferece.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagrama da plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="5b1c5-118">**Figura 4-13.**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-118">**Figure 4-13.**</span></span> <span data-ttu-id="5b1c5-119">Plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure</span><span class="sxs-lookup"><span data-stu-id="5b1c5-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="5b1c5-120">O Azure Stack é oferecido em duas opções de implantação, para atender às suas necessidades:</span><span class="sxs-lookup"><span data-stu-id="5b1c5-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="5b1c5-121">Sistemas integrados Azure Stack</span><span class="sxs-lookup"><span data-stu-id="5b1c5-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="5b1c5-122">Kit de desenvolvimento azure Stack</span><span class="sxs-lookup"><span data-stu-id="5b1c5-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="5b1c5-123">Sistemas integrados Azure Stack</span><span class="sxs-lookup"><span data-stu-id="5b1c5-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="5b1c5-124">Os sistemas integrados Azure Stack são oferecidos através de uma parceria da Microsoft e parceiros de hardware.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="5b1c5-125">A parceria cria uma solução que oferece inovação em nuvem que é equilibrada com simplicidade na gestão.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="5b1c5-126">Como o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adota a inovação a partir da nuvem.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="5b1c5-127">Os sistemas integrados Azure Stack variam em tamanho de 4 a 12 nós, e são suportados conjuntamente pelo parceiro de hardware e pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="5b1c5-128">Use sistemas integrados Do Azure Stack para implementar novos cenários para suas cargas de trabalho de produção.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="5b1c5-129">Kit de desenvolvimento azure Stack</span><span class="sxs-lookup"><span data-stu-id="5b1c5-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="5b1c5-130">O Kit de Desenvolvimento do Microsoft Azure Stack é uma implantação de nó único do Azure Stack que você pode usar para avaliar e saber mais sobre essa extensão.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="5b1c5-131">Você também pode usar o Azure Stack Development Kit como um ambiente de desenvolvedor, onde você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="5b1c5-132">O Kit de Desenvolvimento do Azure Stack não foi projetado para ser usado como um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="5b1c5-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5b1c5-133">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="5b1c5-133">Additional resources</span></span>

- <span data-ttu-id="5b1c5-134">**Nuvem híbrida azure**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="5b1c5-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="5b1c5-136">**Contas de serviço do Active Directory para contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="5b1c5-137">**Crie um contêiner com suporte ao Active Directory**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="5b1c5-138">**Licenciamento de benefícios híbridos do Azure**</span><span class="sxs-lookup"><span data-stu-id="5b1c5-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="5b1c5-139">[Próximo](life-cycle-ci-cd-pipelines-devops-tools.md)
>[anterior](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5b1c5-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
