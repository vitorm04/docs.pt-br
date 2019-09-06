---
title: Migrar para cenários de nuvem híbrida
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Migrar para cenários de nuvem híbrida
ms.date: 04/30/2018
ms.openlocfilehash: 313608c41427b3833bbc873398595ceb37bd7c7d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373939"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="a662c-103">Migrar para cenários de nuvem híbrida</span><span class="sxs-lookup"><span data-stu-id="a662c-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="a662c-104">Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas como Microsoft Azure ou qualquer outra nuvem pública devido a regulamentos ou suas próprias políticas.</span><span class="sxs-lookup"><span data-stu-id="a662c-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="a662c-105">No entanto, é provável que qualquer organização possa se beneficiar de ter alguns de seus aplicativos na nuvem pública e em outros aplicativos locais.</span><span class="sxs-lookup"><span data-stu-id="a662c-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="a662c-106">Mas um ambiente misto pode levar a uma complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em nuvens públicas versus ambientes locais.</span><span class="sxs-lookup"><span data-stu-id="a662c-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="a662c-107">A Microsoft fornece a melhor solução de nuvem híbrida, uma na qual você pode otimizar seus ativos existentes no local e na nuvem pública, enquanto garante a consistência em uma nuvem híbrida do Azure.</span><span class="sxs-lookup"><span data-stu-id="a662c-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="a662c-108">Você pode maximizar as habilidades existentes e obter uma abordagem flexível e unificada para a criação de aplicativos que podem ser executados na nuvem ou no local, graças a Azure Stack (local) e ao Azure (nuvem pública).</span><span class="sxs-lookup"><span data-stu-id="a662c-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="a662c-109">Quando se trata de segurança, você pode centralizar o gerenciamento e a segurança em sua nuvem híbrida.</span><span class="sxs-lookup"><span data-stu-id="a662c-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="a662c-110">Você pode obter controle sobre todos os ativos, desde seu datacenter até a nuvem, fornecendo logon único para aplicativos locais e na nuvem.</span><span class="sxs-lookup"><span data-stu-id="a662c-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="a662c-111">Você consegue fazer isso estendendo Active Directory para uma nuvem híbrida e usando o gerenciamento de identidades.</span><span class="sxs-lookup"><span data-stu-id="a662c-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="a662c-112">Por fim, você pode distribuir e analisar os dados diretamente, usar as mesmas linguagens de consulta para ativos locais e de nuvem e aplicar análise e aprendizado profundo no Azure para enriquecer seus dados, independentemente de sua origem.</span><span class="sxs-lookup"><span data-stu-id="a662c-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="a662c-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a662c-113">Azure Stack</span></span>

<span data-ttu-id="a662c-114">O Azure Stack é uma plataforma de nuvem híbrida que permite que você forneça serviços do Azure do datacenter da sua organização.</span><span class="sxs-lookup"><span data-stu-id="a662c-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="a662c-115">O Azure Stack foi projetado para dar suporte a novas opções para seus aplicativos modernos em cenários importantes, como ambientes de borda e desconectado, ou atender aos requisitos específicos de segurança e conformidade.</span><span class="sxs-lookup"><span data-stu-id="a662c-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="a662c-116">A Figura 4-13 mostra uma visão geral da verdadeira plataforma de nuvem híbrida que a Microsoft oferece.</span><span class="sxs-lookup"><span data-stu-id="a662c-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure](./media/image13.jpg)

<span data-ttu-id="a662c-118">**Figura 4-13.**</span><span class="sxs-lookup"><span data-stu-id="a662c-118">**Figure 4-13.**</span></span> <span data-ttu-id="a662c-119">Plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure</span><span class="sxs-lookup"><span data-stu-id="a662c-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="a662c-120">O Azure Stack é oferecido em duas opções de implantação para atender às suas necessidades:</span><span class="sxs-lookup"><span data-stu-id="a662c-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="a662c-121">Sistemas integrados do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a662c-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="a662c-122">Kit de Desenvolvimento do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a662c-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="a662c-123">Sistemas integrados do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a662c-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="a662c-124">Azure Stack sistemas integrados são oferecidos por meio de uma parceria de parceiros de hardware e da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a662c-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="a662c-125">A parceria cria uma solução que oferece inovação no ritmo da nuvem que é equilibrada com simplicidade no gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="a662c-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="a662c-126">Como o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, ao mesmo tempo que ainda está adotando a inovação da nuvem.</span><span class="sxs-lookup"><span data-stu-id="a662c-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="a662c-127">Azure Stack intervalo de sistemas integrados de tamanho de 4 a 12 nós e tem suporte em conjunto pelo parceiro de hardware e pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a662c-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="a662c-128">Use Azure Stack sistemas integrados para implementar novos cenários para suas cargas de trabalho de produção.</span><span class="sxs-lookup"><span data-stu-id="a662c-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="a662c-129">Kit de Desenvolvimento do Azure Stack</span><span class="sxs-lookup"><span data-stu-id="a662c-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="a662c-130">O Microsoft Azure Stack Development Kit é uma implantação de nó único do Azure Stack, que você pode usar para avaliar e saber mais sobre o Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="a662c-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="a662c-131">Você também pode usar Kit de Desenvolvimento do Azure Stack como um ambiente de desenvolvedor, no qual você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure.</span><span class="sxs-lookup"><span data-stu-id="a662c-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="a662c-132">O Kit de Desenvolvimento do Azure Stack não se destina a ser usado como um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="a662c-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a662c-133">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="a662c-133">Additional resources</span></span>

- <span data-ttu-id="a662c-134">**Nuvem híbrida do Azure**</span><span class="sxs-lookup"><span data-stu-id="a662c-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="a662c-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="a662c-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="a662c-136">**Active Directory contas de serviço para contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="a662c-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="a662c-137">**Criar um contêiner com suporte a Active Directory**</span><span class="sxs-lookup"><span data-stu-id="a662c-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="a662c-138">**Licenciamento de Benefício Híbrido do Azure**</span><span class="sxs-lookup"><span data-stu-id="a662c-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="a662c-139">[Anterior](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[Próximo](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="a662c-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
