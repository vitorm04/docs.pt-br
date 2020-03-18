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
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrar para cenários de nuvem híbrida

Algumas organizações e empresas não podem migrar alguns de seus aplicativos para nuvens públicas como o Microsoft Azure ou qualquer outra nuvem pública devido a regulamentos ou suas próprias políticas. No entanto, é provável que qualquer organização possa se beneficiar de ter algumas de suas aplicações na nuvem pública e outras aplicações no local. Mas um ambiente misto pode levar a uma complexidade excessiva em ambientes devido a diferentes plataformas e tecnologias usadas em ambientes públicos versus ambientes locais.

A Microsoft fornece a melhor solução de nuvem híbrida, na qual você pode otimizar seus ativos existentes no local e na nuvem pública, enquanto você garante consistência em uma nuvem híbrida do Azure. Você pode maximizar as habilidades existentes e obter uma abordagem flexível e unificada para criar aplicativos que possam ser executados na nuvem ou no local, graças ao Azure Stack (no local) e ao Azure (nuvem pública).

Quando se trata de segurança, você pode centralizar o gerenciamento e a segurança em toda a sua nuvem híbrida. Você pode obter controle sobre todos os ativos, desde o seu datacenter até a nuvem, fornecendo o login único no local e aplicativos em nuvem. Você consegue isso estendendo o Active Directory para uma nuvem híbrida e usando o gerenciamento de identidade.

Finalmente, você pode distribuir e analisar dados sem problemas, usar as mesmas linguagens de consulta para ativos em nuvem e locais e aplicar análises e aprendizado profundo no Azure para enriquecer seus dados, independentemente de sua fonte.

## <a name="azure-stack"></a>Azure Stack

O Azure Stack é uma plataforma de nuvem híbrida que permite que você ofereça serviços do Azure a partir do datacenter da sua organização. O Azure Stack foi projetado para suportar novas opções para seus aplicativos modernos em cenários-chave, como ambientes de borda e desconectados, ou atender a requisitos específicos de segurança e conformidade.

A Figura 4-13 mostra uma visão geral da verdadeira plataforma de nuvem híbrida que a Microsoft oferece.

![Diagrama da plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Figura 4-13.** Plataforma de nuvem híbrida da Microsoft com Azure Stack e Azure

O Azure Stack é oferecido em duas opções de implantação, para atender às suas necessidades:

- Sistemas integrados Azure Stack

- Kit de desenvolvimento azure Stack

### <a name="azure-stack-integrated-systems"></a>Sistemas integrados Azure Stack

Os sistemas integrados Azure Stack são oferecidos através de uma parceria da Microsoft e parceiros de hardware. A parceria cria uma solução que oferece inovação em nuvem que é equilibrada com simplicidade na gestão. Como o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém a quantidade certa de flexibilidade e controle, enquanto ainda adota a inovação a partir da nuvem. Os sistemas integrados Azure Stack variam em tamanho de 4 a 12 nós, e são suportados conjuntamente pelo parceiro de hardware e pela Microsoft. Use sistemas integrados Do Azure Stack para implementar novos cenários para suas cargas de trabalho de produção.

### <a name="azure-stack-development-kit"></a>Kit de desenvolvimento azure Stack

O Kit de Desenvolvimento do Microsoft Azure Stack é uma implantação de nó único do Azure Stack que você pode usar para avaliar e saber mais sobre essa extensão. Você também pode usar o Azure Stack Development Kit como um ambiente de desenvolvedor, onde você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure. O Kit de Desenvolvimento do Azure Stack não foi projetado para ser usado como um ambiente de produção.

### <a name="additional-resources"></a>Recursos adicionais

- **Nuvem híbrida azure**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Contas de serviço do Active Directory para contêineres do Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Crie um contêiner com suporte ao Active Directory**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Licenciamento de benefícios híbridos do Azure**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Próximo](life-cycle-ci-cd-pipelines-devops-tools.md)
>[anterior](../walkthroughs-technical-get-started-overview.md)
