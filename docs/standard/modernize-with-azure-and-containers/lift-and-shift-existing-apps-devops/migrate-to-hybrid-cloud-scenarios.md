---
title: "Migrar para cenários de nuvem híbrida"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Migrar para cenários de nuvem híbrida"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6216068786745ac4ebc00263a14b4afe247193f5
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrar para cenários de nuvem híbrida

Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas, como o Microsoft Azure ou qualquer nuvem pública devido a normas ou suas próprias políticas. No entanto, é provável que qualquer organização pode se beneficiar de ter alguns de seus aplicativos na nuvem pública e outros aplicativos no local. Mas um ambiente misto pode levar a complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em nuvens públicas versus ambientes locais.

A Microsoft fornece a melhor solução de nuvem híbrida, um em que você pode otimizar seus ativos locais e na nuvem pública, enquanto você garante a consistência em uma nuvem híbrida do Azure. Você pode maximizar os recursos existentes e obter uma abordagem flexível e unificada para a criação de aplicativos que podem ser executados na nuvem ou no local, graças a pilha do Azure (local) e o Azure (nuvem pública).

Quando se trata de segurança, você pode centralizar o gerenciamento e segurança em sua nuvem híbrida. Você pode obter controle sobre todos os ativos, do Data Center na nuvem, fornecendo logon único no local e aplicativos de nuvem. Fazer isso, estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.

Por fim, você pode distribuir e analisar dados diretamente, usar as mesmas linguagens de consulta para ativos de nuvem e local e aplicar análises e profundo de aprendizagem no Azure para enriquecer seus dados, independentemente de sua origem.

## <a name="azure-stack"></a>Azure Stack

A pilha do Azure é uma plataforma de nuvem híbrida que lhe permite oferecer serviços do Azure do datacenter de sua organização. A pilha do Azure foi projetada para dar suporte a novas opções para seus aplicativos modernos em cenários mais importantes, como borda e desconectado de ambientes ou requisitos específicos de segurança e conformidade reunião.

Figura 4-13 mostra uma visão geral da plataforma de nuvem híbrida true oferecidas pela Microsoft.

![Plataforma de nuvem híbrida Microsoft com a pilha do Azure e o Azure](./media/image13.jpg)

> **Figura 4-13.** Plataforma de nuvem híbrida Microsoft com a pilha do Azure e o Azure

A pilha do Azure é oferecida em duas opções de implantação para atender às suas necessidades:

-   Sistemas de pilha integrado do Azure

-   Kit de desenvolvimento de pilha do Azure

### <a name="azure-stack-integrated-systems"></a>Sistemas de pilha integrado do Azure

Sistemas de pilha integrado do Azure são oferecidos por meio de uma parceria de parceiros da Microsoft e de hardware. A parceria cria uma solução que oferece inovação individual de nuvem que é equilibrada com simplicidade no gerenciamento. Como pilha do Azure é oferecida como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adotando inovação da nuvem. Sistemas de pilha integrado do Azure variam em tamanho de 4 a 12 nós e têm suporte em conjunto de parceiros de hardware e da Microsoft. Use sistemas de pilha do Azure integradas para implementar novos cenários para suas cargas de trabalho de produção.

### <a name="azure-stack-development-kit"></a>Kit de desenvolvimento de pilha do Azure

Kit de desenvolvimento de pilha do Microsoft Azure é uma implantação de nó único da pilha do Azure, que você pode usar para avaliar e saber mais sobre a pilha do Azure. Você também pode usar o Kit de desenvolvimento de pilha do Azure como um ambiente de desenvolvedor, onde você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure. Kit de desenvolvimento de pilha do Azure não se destina a ser usado como um ambiente de produção.

### <a name="additional-resources"></a>Recursos adicionais

-   **Nuvem híbrida do Azure**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Contas de serviço do Active Directory para contêineres do Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Criar um contêiner com o suporte do Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Licenciamento de benefício híbrido do Azure**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[Anterior](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Próximo](../walkthroughs-technical-get-started-overview.md)
