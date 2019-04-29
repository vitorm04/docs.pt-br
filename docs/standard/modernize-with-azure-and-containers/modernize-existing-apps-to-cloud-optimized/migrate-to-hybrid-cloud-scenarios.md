---
title: Migrar para cenários de nuvem híbrida
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Migrar para cenários de nuvem híbrida
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b04c6edecf5b63f191cb2e0f808fb1d0f801d0a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936716"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrar para cenários de nuvem híbrida

Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas, como o Microsoft Azure ou qualquer outra nuvem pública devido a normas ou suas próprias políticas. No entanto, é provável que qualquer organização pode se beneficiar de alguns de seus aplicativos na nuvem pública e outros aplicativos no local. Mas um ambiente misto pode levar a complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em nuvens públicas versus ambientes locais.

A Microsoft fornece a melhor solução de nuvem híbrida, uma na qual você pode otimizar os ativos existentes no local e na nuvem pública, enquanto você garante a consistência em uma nuvem híbrida do Azure. Você pode maximizar as habilidades existentes e obtenha uma abordagem flexível e unificada para compilar aplicativos que podem ser executados na nuvem ou no local, graças ao Azure Stack (local) e o Azure (nuvem pública).

Quando se trata de segurança, você pode centralizar o gerenciamento e segurança em sua nuvem híbrida. Você pode obter controle sobre todos os ativos, do seu datacenter para a nuvem, fornecendo logon único para o local e aplicativos de nuvem. Fazer isso, estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.

Por fim, você pode distribuir e analise dados perfeitamente, usa as mesmas linguagens de consulta para ativos locais e de nuvem e aplique análise e aprendizagem aprofundada no Azure para enriquecer seus dados, independentemente de sua fonte.

## <a name="azure-stack"></a>Azure Stack

O Azure Stack é uma plataforma de nuvem híbrida que possibilita entregar serviços do Azure do datacenter da sua organização. O Azure Stack foi projetado para dar suporte a novas opções para seus aplicativos modernos em cenários-chave, como borda e desconectadas ambientes ou requisitos específicos de segurança e conformidade reunião.

Figura 4-13 mostra uma visão geral da plataforma em nuvem híbrida real oferecidas pela Microsoft.

![Plataforma de nuvem híbrida Microsoft com o Azure Stack e o Azure](./media/image13.jpg)

> **Figura 4-13.** Plataforma de nuvem híbrida Microsoft com o Azure Stack e o Azure

O Azure Stack é oferecido em duas opções de implantação para atender às suas necessidades:

- Sistemas integrados do Azure Stack

- Kit de Desenvolvimento do Azure Stack

### <a name="azure-stack-integrated-systems"></a>Sistemas integrados do Azure Stack

Sistemas de pilha integrado do Azure são oferecidos por meio de uma parceria de parceiros da Microsoft e de hardware. A parceria cria uma solução que oferece inovação conduzida a nuvem que é equilibrada com simplicidade no gerenciamento. Porque o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adotando a inovação da nuvem. Sistemas de pilha integrado do Azure variam de tamanho de 4 a 12 nós e têm suporte em conjunto pela Microsoft e parceiros de hardware. Use sistemas integrados do Azure Stack para implementação de novos cenários para suas cargas de trabalho de produção.

### <a name="azure-stack-development-kit"></a>Kit de Desenvolvimento do Azure Stack

Kit de desenvolvimento do Microsoft Azure Stack é uma implantação de nó único do Azure Stack, que você pode usar para avaliar e saber mais sobre o Azure Stack. Você também pode usar o Kit de desenvolvimento do Azure Stack como um ambiente de desenvolvedor, onde você pode desenvolver usando as APIs e ferramentas que são consistentes com o Azure. Kit de desenvolvimento do Azure Stack não se destina a ser usado como um ambiente de produção.

### <a name="additional-resources"></a>Recursos adicionais

- **Nuvem híbrida do Azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Contas de serviço do Active Directory para contêineres do Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Criar um contêiner com suporte do Active Directory**

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- **Licenciamento do benefício híbrido do Azure**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Anterior](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[Próximo](../walkthroughs-technical-get-started-overview.md)
