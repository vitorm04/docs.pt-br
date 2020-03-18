---
title: E quanto aos aplicativos nativos na nuvem?
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | E os aplicativos cloud-native?
ms.date: 04/28/2018
ms.openlocfilehash: d2a7f89e347d75ddbdae84c8eb57e32447b83297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543541"
---
# <a name="what-about-cloud-native-applications"></a>E quanto aos aplicativos nativos na nuvem?

Embora os aplicativos [cloud-native](https://azure.microsoft.com/overview/cloudnative/) não sejam o foco principal deste guia, é útil ter uma compreensão desse nível de maturidade de modernização e distingui-lo de aplicativos otimizados para nuvem.

A Figura 4-3 posiciona aplicativos nativos da Nuvem nos níveis de maturidade de modernização do aplicativo:

![Diagrama mostrando como posicionar aplicativos nativos da nuvem.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Figura 4-3.** Posicionamento de aplicativos nativos da nuvem

O nível de maturidade de modernização cloud-native geralmente requer novos investimentos em desenvolvimento. A mudança para o nível nativo da nuvem normalmente é impulsionada pela necessidade dos negócios de modernizar os aplicativos o máximo possível para melhorar drasticamente a escala em grandes aplicações, criando subsistemas autônomos (microsserviços) que podem ser implantados e dimensionados independentemente de outras áreas do aplicativo, ao mesmo tempo em que reduz custos a longo prazo e aumenta a agilidade de evolução das peças do aplicativo autônomo que oferecem vantagens significativas de concorrência.

Os principais pilares das aplicações cloud-native são baseados em abordagens de arquitetura de microsserviços, que podem evoluir com agilidade e escala para limites que seriam difíceis de alcançar em uma arquitetura monolítica, implantada em locais ou em nuvem Ambiente.

A Figura 4-4 mostra as principais características do modelo Cloud-Native.

![Diagrama listando as principais características nativas da nuvem.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Figura 4-4.** Características nativas da nuvem

Além disso, você pode estender aplicativos web modernos básicos e aplicativos nativos da nuvem adicionando outros serviços, como inteligência artificial (IA), machine learning (ML) e IoT. Você pode usar qualquer um desses serviços para estender qualquer uma das possíveis abordagens otimizadas para a nuvem.

A diferença fundamental nos aplicativos no nível Cloud-Native está na arquitetura do aplicativo. Aplicativos nativos da nuvem são, por definição, aplicativos baseados em microsserviços. Aplicativos nativos da nuvem exigem arquiteturas, tecnologias e plataformas especiais, em comparação com um aplicativo web monolítico ou um aplicativo Tradicional N-Tier.

## <a name="cloud-native-applications-details"></a>Detalhes de aplicativos nativos da nuvem

Cloud-Native é um estado mais avançado ou maduro para aplicações grandes e essenciais. Os aplicativos nativos da nuvem geralmente exigem arquitetura e design que são criados do zero em vez de modernizar os aplicativos existentes. A principal diferença entre um aplicativo nativo da nuvem e um aplicativo web otimizado para nuvem mais simples é a recomendação de usar arquiteturas de microsserviços em uma abordagem nativa da nuvem. Aplicativos otimizados para a nuvem também podem ser aplicativos web monolíticos ou n-tier.

O [Aplicativo De Doze Fatores](https://12factor.net/) (uma coleção de padrões que estão intimamente relacionados com abordagens de microsserviços) também é considerado um requisito para arquiteturas de aplicativos nativas da nuvem.

A [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) é uma das principais promotoras de princípios nativos da nuvem. A Microsoft é [membro do CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Para obter orientações detalhadas sobre como projetar e desenvolver aplicativos nativos da nuvem, leia os seguintes e-books gratuitos:

* [Arquitetando aplicações nativas da nuvem .NET para o Azure](../../cloud-native/introduction.md)
* [.NET Microservices: Arquitetura para aplicativos .NET contêiner](../../microservices/index.md). NET .

O fator mais importante a considerar se você migrar um aplicativo completo para o modelo nativo da nuvem é que você deve reprojetar para uma arquitetura baseada em microsserviços. Isso requer claramente um investimento significativo no desenvolvimento devido ao grande processo de refatoração envolvido. Essa opção geralmente é escolhida para aplicações de missão crítica que precisam de novos níveis de escalabilidade e agilidade a longo prazo. Mas, você pode começar a se mover em direção à nuvem nativa adicionando microsserviços para apenas alguns novos cenários, e eventualmente refatorar o aplicativo totalmente como microsserviços. Esta é uma abordagem incremental que é a melhor opção para alguns cenários.

## <a name="what-about-microservices"></a>E quanto aos microsserviços?

Entender microsserviços e como eles funcionam é importante quando você está considerando aplicativos nativos da nuvem para sua organização.

A arquitetura de microsserviços é uma abordagem avançada que você pode usar para aplicativos que são criados a partir do zero ou quando você evolui aplicativos existentes para aplicativos nativos da nuvem. Você pode começar adicionando alguns microsserviços aos aplicativos existentes para aprender sobre os novos paradigmas de microsserviços. Mas claramente, você precisa arquitetar e codificar, especialmente para este tipo de abordagem arquitetônica.

No entanto, os microserviços não são obrigatórios para qualquer aplicação nova ou moderna. Microsserviços não são uma "bala mágica", e eles não são a única e melhor maneira de criar cada aplicativo. Como e quando você usa microsserviços depende do tipo de aplicação que você precisa construir.

A arquitetura de microsserviços está se tornando a abordagem preferida para aplicativos distribuídos e grandes ou complexos de missão crítica que são baseados em subsistemas múltiplos e independentes na forma de serviços autônomos. Em uma arquitetura baseada em microsserviços, um aplicativo é construído como uma coleção de serviços que podem ser desenvolvidos, testados, versionados, implantados e dimensionados de forma independente. Isso pode incluir qualquer banco de dados autônomo relacionado por microserviço.

Para obter uma olhada detalhada em uma arquitetura de microsserviços que você pode implementar usando o .NET Core, consulte o e-book PDF para download [.NET microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook). O guia também está disponível [online.](../../microservices/index.md)

Mas mesmo em cenários em que os microsserviços oferecem poderosas capacidades de implantação independente, fortes limites de subsistema e diversidade tecnológica, eles também levantam muitos novos desafios. Os desafios estão relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independentes; alcançar comunicação resiliente entre microserviços; a necessidade de eventual consistência; e complexidade operacional. Os microserviços introduzem um nível mais elevado de complexidade em comparação com as aplicações monolíticas tradicionais.

Devido à complexidade de uma arquitetura de microserviços, apenas cenários específicos e certos tipos de aplicativos são adequados para aplicativos baseados em microsserviços. Estes incluem aplicações grandes e complexas que têm subsistemas múltiplos e em evolução. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para maior agilidade a longo prazo e manutenção de aplicativos mais eficiente. Mas para cenários menos complexos, talvez seja melhor continuar com uma abordagem de aplicação monolítica ou abordagens N-Tier mais simples.

Como nota final, mesmo com o risco de ser repetitivo sobre esse conceito, você não deve olhar para o uso de microsserviços em seus aplicativos como "tudo ou nada". Você pode estender e evoluir aplicações monolíticas existentes adicionando novos cenários pequenos baseados em microsserviços. Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura de microsserviços. Na verdade, recomendamos que você evolua de usar um aplicativo monolítico ou N-Tier existente adicionando novos cenários. Eventualmente, você pode dividir o aplicativo em componentes autônomos ou microsserviços. Você pode começar a evoluir suas aplicações monolíticas em uma direção de microsserviços, passo a passo.

De qualquer forma, o resto desta orientação atual se concentra principalmente em "aplicativos baseados em microsserviços" porque essa orientação visa principalmente a modernização de aplicativos existentes que geralmente têm arquiteturas monolíticas ou N-Tier.

> [!div class="step-by-step"]
> [Próximo](microsoft-technologies-in-cloud-optimized-applications.md)
> [anterior](deploy-existing-net-apps-as-windows-containers.md)
