---
title: E aplicativos de nuvem nativo?
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | E aplicativos de nuvem nativo?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0e880689001ece2b770811cfbe3fea43aa425b32
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="what-about-cloud-native-applications"></a>E aplicativos de nuvem nativo?

Embora [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos não são o principal foco deste guia, é útil para compreender desse nível de maturidade modernização e distingui-lo de aplicativos otimizada para a nuvem.

Figura 4-3 posiciona aplicativos de nuvem nativo nos níveis de maturidade modernização de aplicativo:

![Aplicativos de nuvem nativo de posicionamento](./media/image3.png)

> **Figura 4-3.** Aplicativos de nuvem nativo de posicionamento

O nível de maturidade modernização nativo nuvem normalmente requer investimentos de desenvolvimento de novo. Mover para o nível de nuvem nativo normalmente é orientada por empresas que precisam modernizar aplicativos tanto quanto possíveis melhorar drasticamente escalas em aplicativos grandes criando subsistemas autônomos (microservices) que podem ser implantados e independentemente de outras áreas do aplicativo enquanto reduz os custos em agilidade longo prazo e aumento de evolução das partes do aplicativo esses autônomos que fornecem significativa competir vantagens. 

Principais pilares de [nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplicativos são baseados em abordagens de arquitetura microservices, que podem evoluir com agilidade e dimensionar aos limites que seriam difíceis de uma arquitetura monolítica implantada para um ambiente de nuvem ou local.

Figura 4-4 mostra as principais características do modelo de nuvem nativo.  

> ![Características de nuvem nativo são Microservices, contêineres, nuvem resilientes, orchestrators e serverles](./media/image4.png)
>
> **Figura 4-4.** Características de nuvem nativo

Além disso, você pode estender aplicativos web modernos básico e nativo de nuvem adicionando outros serviços, como inteligência artificial (AI), o aprendizado de máquina (ML) e IoT. Você pode usar qualquer um desses serviços para estender uma das abordagens possíveis otimizada para a nuvem.

A diferença fundamental em aplicativos no nível de nuvem nativo está na arquitetura do aplicativo. [Nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos são, por definição, os aplicativos que se baseiam no microservices. Aplicativos de nuvem nativo exigem arquiteturas especiais, tecnologias e plataformas, em comparação comparadas um aplicativo web monolítico ou tradicionais de aplicativos de N camadas.

## <a name="cloud-native-applications-details"></a>Detalhes de aplicativos de nuvem nativo

[Nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) é um estado mais avançado ou mais maduro para aplicativos grandes e de missão crítica. Aplicativos de nuvem nativo geralmente requerem a arquitetura e design criado do zero, em vez de por modernizar aplicativos existentes. A principal diferença entre um aplicativo nativo de nuvem e um aplicativo web com otimização de nuvem mais simples é a recomendação para usar microservices arquiteturas em uma abordagem de nuvem nativo. Otimização de nuvem aplicativos também podem ser aplicativos web monolítico ou aplicativos de N camadas.

O [aplicativo doze Factor](https://12factor.net/) (uma coleção de padrões que estão intimamente relacionados abordagens microservices) também é considerada um requisito para [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) arquiteturas de aplicativo.

O [Foundation de computação nativo de nuvem (CNCF)](https://www.cncf.io/) é um Promotores primário dos princípios de nuvem nativo. A Microsoft tem um [membro o CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Para um exemplo de definição e para obter mais informações sobre as características dos aplicativos de nuvem nativo, consulte o artigo Gartner [como projetar e criar aplicativos de nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Para obter orientações específicas da Microsoft sobre como implementar um aplicativo nativo de nuvem, consulte [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook).

O fator mais importante a considerar se você migrar um aplicativo completo para o [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modelo é que você deve Refaça a arquitetura para uma arquitetura baseada em microservices. Isso exige um investimento significativo em desenvolvimento devido o grande refatoração processo envolvido. Essa opção geralmente é escolhida para aplicativos de missão crítica que precisam de novos níveis de escalabilidade e agilidade de longo prazo. Mas, você pode começar a mover em direção à nuvem nativo adicionando microservices para apenas alguns novos cenários e eventualmente refatorar o aplicativo totalmente como microservices. Esta é uma abordagem incremental que é a melhor opção para alguns cenários.

## <a name="what-about-microservices"></a>E microservices? 

Noções básicas sobre microservices e como eles funcionam é importante quando você estiver pensando em aplicativos de nuvem nativo para sua organização.

A arquitetura de microservices é uma abordagem avançada que você pode usar para aplicativos que são criados do zero ou quando você desenvolve aplicativos existentes para aplicativos de nuvem nativo. Você pode iniciar adicionando microservices alguns aplicativos existentes para saber mais sobre os novos paradigmas de microservices. Mas, obviamente, você precisa arquiteto e código, especialmente para esse tipo de abordagem de arquitetura.

No entanto, microservices não são obrigatórios para qualquer aplicativo novo ou moderno. Microservices não são um marcador"magic", e não são a maneira recomendada único de criar todos os aplicativos. Como e quando você usar microservices depende do tipo de aplicativo que você precisa criar.

A arquitetura microservices está se tornando a abordagem preferencial para aplicativos de missão crítica distribuídos e grandes ou complexas com base em vários subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microservices, um aplicativo é criado como uma coleção de serviços que podem ser desenvolvidos de forma independente, testada e com controle de versão, implantado e expandida. Isso pode incluir qualquer banco de dados relacionado, autônomo por microsserviço.

Para obter uma visão detalhada de uma arquitetura de microservices que você pode implementar usando .NET Core, consulte para download PDF livro eletrônico [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook). O guia também está disponível [online](../../microservices-architecture/index.md).

Mas, mesmo em cenários em que microservices oferecem implantação de independente de recursos avançada, limites de subsistema de alta segurança e diversidade de tecnologia-elas também geram muitos novos desafios. Os desafios relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independente. Obtendo resiliente comunicação entre microservices; a necessidade de consistência eventual. e a complexidade operacional. Microservices introduzir um nível mais alto de complexidade em comparação comparada aplicativos monolíticos tradicionais.

Devido à complexidade de uma arquitetura de microservices, somente determinados tipos de aplicativos e cenários específicos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos que têm várias surgimento de subsistemas. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para maior agilidade de longo prazo e manutenção de aplicativos mais eficiente. Mas para cenários menos complexos, talvez seja melhor continuar com uma abordagem de aplicativo monolítico ou abordagens mais simples de N camadas.

Como uma observação final, mesmo com o risco de ser repetitiva sobre esse conceito, você não deve examinar usando microservices em seus aplicativos como "completo ou nada." Você pode estender e desenvolver aplicativos monolíticos existentes adicionando novos e cenários pequenos com base em microservices. Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura microservices. Na verdade, é recomendável que você evoluir do uso de um aplicativo monolítico ou de N camadas existente adicionando novos cenários. Por fim, você pode dividir o aplicativo em componentes autônomos ou microservices. Você pode iniciar o surgimento de seus aplicativos monolíticos em direção microservices, passo a passo.

Em qualquer caso, o restante deste guia presente concentra-se de tudo em "nenhum aplicativo baseado em microservices" porque este guia se destina principalmente modernização dos aplicativos existentes que normalmente têm arquiteturas monolíticos ou de N camadas.


>[!div class="step-by-step"]
[Anterior](microsoft-technologies-in-cloud-optimized-applications.md)
[Próximo](deploy-existing-net-apps-as-windows-containers.md)
