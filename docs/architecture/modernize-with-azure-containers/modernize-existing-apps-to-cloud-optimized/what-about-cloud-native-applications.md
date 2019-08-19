---
title: E quanto aos aplicativos nativos na nuvem?
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | E quanto aos aplicativos nativos de nuvem?
ms.date: 04/28/2018
ms.openlocfilehash: 26adb87c426442ebf0e88165e521819e3a49d175
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578009"
---
# <a name="what-about-cloud-native-applications"></a>E quanto aos aplicativos nativos na nuvem?

Embora os aplicativos [nativos de nuvem](https://azure.microsoft.com/overview/cloudnative/) não sejam o foco principal deste guia, é útil ter uma compreensão desse nível de maturidade de modernização e distingui-lo de aplicativos otimizados para a nuvem.

A Figura 4-3 posiciona os aplicativos nativos de nuvem nos níveis de maturidade de modernização do aplicativo:

![Posicionando aplicativos nativos de nuvem](./media/image3.png)

> **Figura 4-3.** Posicionando aplicativos nativos de nuvem

O nível de maturidade de modernização nativa da nuvem geralmente requer novos investimentos em desenvolvimento. A mudança para o nível nativo de nuvem normalmente é orientada pela necessidade comercial de modernizar os aplicativos o máximo possível para melhorar drasticamente a escala em aplicativos grandes criando subsistemas autônomos (superserviços) que podem ser implantados e dimensionados de forma independente de outras áreas do aplicativo, enquanto reduz os custos a longo prazo e aumenta a agilidade da evolução das partes do aplicativo autônomo que fornecem vantagens de concorrência significativas.

Os principais pilares de aplicativos nativos de nuvem baseiam-se em abordagens de arquitetura de microserviços, que podem evoluir com agilidade e escalabilidade para limites que seriam difíceis de alcançar em uma arquitetura monolítica, implantada no local ou na nuvem ambiente.

A Figura 4-4 mostra as principais características do modelo nativo de nuvem.

> ![As características nativas de nuvem são microserviços, contêineres, resilientes de nuvem, orquestradores e sem servidor](./media/image4.png)
>
> **Figura 4-4.** Características nativas de nuvem

Além disso, você pode estender aplicativos Web modernos básicos e aplicativos nativos de nuvem adicionando outros serviços, como ia (inteligência artificial), ML (aprendizado de máquina) e IoT. Você pode usar qualquer um desses serviços para estender qualquer uma das abordagens possíveis otimizadas para nuvem.

A diferença fundamental nos aplicativos no nível de nuvem nativa está na arquitetura do aplicativo. Os aplicativos nativos de nuvem são, por definição, aplicativos baseados em microserviços. Os aplicativos nativos de nuvem exigem arquiteturas, tecnologias e plataformas especiais, em comparação com um aplicativo Web monolítico ou um aplicativo de N camadas tradicional.

## <a name="cloud-native-applications-details"></a>Detalhes de aplicativos nativos de nuvem

A nuvem nativa é um estado mais avançado ou maduro para aplicativos grandes e de missão crítica. Os aplicativos nativos de nuvem geralmente exigem arquitetura e design criados a partir do zero, em vez de modernizar os aplicativos existentes. A principal diferença entre um aplicativo nativo de nuvem e um aplicativo Web com otimização de nuvem mais simples é a recomendação para usar arquiteturas de microserviços em uma abordagem nativa de nuvem. Os aplicativos otimizados para a nuvem também podem ser aplicativos Web monolíticos ou aplicativos de N camadas.

O [aplicativo de doze fatores](https://12factor.net/) (uma coleção de padrões que estão fortemente relacionados a abordagens de microserviço) também é considerado um requisito para arquiteturas de aplicativo nativas de nuvem.

A [CNCF (nuvem Native Computing Foundation)](https://www.cncf.io/) é uma promoção principal de princípios nativos de nuvem. A Microsoft é [membro do CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Para obter uma definição de exemplo e para obter mais informações sobre as características de aplicativos nativos de nuvem, consulte o artigo da Gartner [como arquitetar e projetar aplicativos nativos de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Para obter diretrizes específicas da Microsoft sobre como implementar um aplicativo nativo de nuvem, consulte [microservices do .net: Arquitetura para aplicativos](https://aka.ms/microservicesebook).net em contêineres.

O fator mais importante a ser considerado ao migrar um aplicativo completo para o modelo nativo de nuvem é que você deve rearquitetar para uma arquitetura baseada em microserviços. Isso exige claramente um investimento significativo em desenvolvimento devido ao grande processo de refatoração envolvido. Essa opção geralmente é escolhida para aplicativos críticos que precisam de novos níveis de escalabilidade e agilidade a longo prazo. Mas, você pode começar a mudar para a nuvem nativa adicionando microservices para apenas alguns cenários novos e eventualmente refatorar o aplicativo completamente como microservices. Essa é uma abordagem incremental que é a melhor opção para alguns cenários.

## <a name="what-about-microservices"></a>E quanto aos microserviços?

Compreender os microserviços e como eles funcionam é importante quando você está considerando aplicativos nativos de nuvem para sua organização.

A arquitetura de microserviços é uma abordagem avançada que você pode usar para aplicativos criados a partir do zero ou quando você desenvolve aplicativos existentes para aplicativos nativos de nuvem. Você pode começar adicionando alguns microserviços a aplicativos existentes para saber mais sobre os novos paradigmas de microserviços. Mas, claramente, você precisa arquitetar e codificar, especialmente para esse tipo de abordagem arquitetônica.

No entanto, os microserviços não são obrigatórios para nenhum aplicativo novo ou moderno. Os microserviços não são um "marcador mágico", e eles não são a melhor maneira de criar cada aplicativo. Como e quando você usa os microserviços depende do tipo de aplicativo que você precisa criar.

A arquitetura de microserviços está se tornando a abordagem preferida para aplicativos de missão crítica distribuídos e grandes ou complexos que se baseiam em vários subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microserviços, um aplicativo é criado como uma coleção de serviços que podem ser desenvolvidos de forma independente, testados, com controle de versão, implantados e dimensionados. Isso pode incluir qualquer banco de dados autônomo, por microserviço, relacionado.

Para obter uma visão detalhada de uma arquitetura de microserviços que você pode implementar usando o .NET Core, consulte os microserviços PDF [para download do .net: Arquitetura para aplicativos](https://aka.ms/microservicesebook).net em contêineres. O guia também está disponível [online](../../microservices/index.md).

Mas, mesmo em cenários em que os microserviços oferecem uma implantação independente de recursos, limites fortes de subsistema e diversidade de tecnologia, eles também geram muitos desafios novos. Os desafios estão relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independentes; obtendo comunicação resiliente entre os microserviços; a necessidade de consistência eventual; e a complexidade operacional. Os microserviços apresentam um nível mais alto de complexidade em comparação com os aplicativos monolíticos tradicionais.

Devido à complexidade de uma arquitetura de microserviços, apenas cenários específicos e determinados tipos de aplicativos são adequados para aplicativos baseados em microserviço. Isso inclui aplicativos grandes e complexos que têm vários subsistemas em evolução. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para aumentar a agilidade de longo prazo e a manutenção de aplicativos mais eficiente. Mas, para cenários menos complexos, pode ser melhor continuar com uma abordagem de aplicativo monolítico ou abordagens de N camadas mais simples.

Como uma observação final, mesmo no risco de ser repetitivo sobre esse conceito, você não deve examinar o uso de microserviços em seus aplicativos como "tudo ou nada." Você pode estender e desenvolver aplicativos monolíticos existentes adicionando novos cenários pequenos com base em microservices. Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura de microserviços. Na verdade, é recomendável que você evolua do uso de um aplicativo monolítico ou de N camadas existente adicionando novos cenários. Eventualmente, você pode dividir o aplicativo em componentes autônomos ou em microservices. Você pode começar a evoluir seus aplicativos monolíticos em uma direção de microserviços, passo a passo.

De qualquer forma, o restante desta orientação presente enfoca a maioria de todos os "aplicativos baseados em microserviçors", pois essas diretrizes se destinam principalmente à modernização de aplicativos existentes que geralmente têm arquiteturas monolíticos ou de N camadas.

> [!div class="step-by-step"]
> [Anterior](microsoft-technologies-in-cloud-optimized-applications.md)
> [Próximo](deploy-existing-net-apps-as-windows-containers.md)
