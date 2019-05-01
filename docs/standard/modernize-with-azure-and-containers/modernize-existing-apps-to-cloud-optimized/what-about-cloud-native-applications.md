---
title: E quanto aos aplicativos nativos na nuvem?
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | E quanto aos aplicativos nativos de nuvem?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 10f7761b7c0d2ddd8cb9247b1a02aa49cdc4e5d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012063"
---
# <a name="what-about-cloud-native-applications"></a>E quanto aos aplicativos nativos na nuvem?

Embora [nativos de nuvem](https://azure.microsoft.com/overview/cloudnative/) aplicativos não são o foco principal deste guia, é útil ter uma compreensão desse nível de maturidade de modernização e distingui-lo de aplicativos otimizados para a nuvem.

Figura 4-3 posiciona aplicativos nativos de nuvem em que os níveis de maturidade de modernização do aplicativo:

![Posicionamento de aplicativos nativos de nuvem](./media/image3.png)

> **Figura 4-3.** Posicionamento de aplicativos nativos de nuvem

O nível de maturidade de modernização nativos de nuvem normalmente exige novos investimentos de desenvolvimento. Mover para o nível de nuvem nativa normalmente é orientada pela necessidade de negócios para modernizar aplicativos tanto quanto possíveis melhorar drasticamente a escala em aplicativos grandes, criando subsistemas autônomos (microsserviços) que podem ser implantados e escala independentemente de outras áreas do aplicativo enquanto reduz os custos em agilidade longo prazo e aumento de evolução das partes do aplicativo esses autônomos que fornecem significativa competir vantagens.

Dos principais pilares de aplicativos nativos de nuvem se baseiam em abordagens de arquitetura de microsserviços, que podem evoluir com agilidade e dimensionar aos limites que seriam difícil de atingir em uma arquitetura monolítica, implantada no local ou de nuvem ambiente.

Figura 4-4 mostra as principais características do modelo nativos da nuvem.

> ![Características de nativos de nuvem são Microsserviços, orquestradores de nuvem resilientes, contêineres e sem servidor](./media/image4.png)
>
> **Figura 4-4.** Características de nativos da nuvem

Além disso, você pode estender aplicativos web modernos básico e aplicativos nativos de nuvem com a adição de outros serviços, como IoT, aprendizado de máquina (ML) e a inteligência artificial (AI). Você pode usar qualquer um desses serviços para estender qualquer uma das abordagens possíveis otimizada para a nuvem.

A diferença fundamental em aplicativos no nível nativo de nuvem é a arquitetura de aplicativo. Aplicativos nativos de nuvem são, por definição, os aplicativos baseados em microsserviços. Aplicativos nativos de nuvem exigem arquiteturas especiais, tecnologias e plataformas, em comparação comparadas um aplicativo web monolítico ou aplicativo de N camadas tradicional.

## <a name="cloud-native-applications-details"></a>Detalhes de aplicativos nativos de nuvem

Nativo de nuvem é um estado mais avançado ou maduro para aplicativos grandes e de missão crítica. Aplicativos nativos de nuvem geralmente exigem a arquitetura e design que são criados do zero, em vez de ao modernizar aplicativos existentes. A principal diferença entre um aplicativo nativo de nuvem e um aplicativo web otimizada para a nuvem mais simples é a recomendação de uso de arquiteturas de microsserviços em uma abordagem nativos da nuvem. Otimização para nuvem aplicativos também podem ser aplicativos web monolíticos ou aplicativos de N camadas.

O [aplicativo de doze fatores](https://12factor.net/) (uma coleção de padrões que estão intimamente relacionadas às abordagens de microsserviços) também é considerada um requisito para arquiteturas de aplicativos nativos de nuvem.

O [Foundation de computação nativa de nuvem (CNCF)](https://www.cncf.io/) é um promotor primário dos princípios nativos da nuvem. A Microsoft é uma [membro o CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Para um exemplo de definição e para obter mais informações sobre as características de aplicativos nativos de nuvem, consulte o artigo da Gartner [como arquitetar e desenvolver aplicativos nativos de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Para obter orientações específicas da Microsoft sobre como implementar um aplicativo nativo de nuvem, consulte [microsserviços do .NET: Arquitetura para aplicativos .NET em contêineres](https://aka.ms/microservicesebook).

O fator mais importante a considerar se você migrar um aplicativo completo para o modelo nativos de nuvem é que você deve refazer a arquitetura para uma arquitetura baseada em microsserviços. Claramente, isso exige um investimento significativo em desenvolvimento devido à grande processo de refatoração envolvido. Geralmente, essa opção é escolhida para aplicativos de missão crítica que precisam de novos níveis de escalabilidade e agilidade de longo prazo. Mas, você pode começar a mover na direção nativos de nuvem adicionando microsserviços para apenas alguns novos cenários e, eventualmente, refatorar o aplicativo totalmente como microsserviços. Essa é uma abordagem incremental que é a melhor opção para alguns cenários.

## <a name="what-about-microservices"></a>E sobre os microsserviços?

Noções básicas sobre microsserviços e como eles funcionam é importante quando você estiver pensando em aplicativos nativos de nuvem para sua organização.

A arquitetura de microsserviços é uma abordagem avançada que você pode usar para aplicativos que são criados a partir do zero ou quando você desenvolve aplicativos existentes em direção a aplicativos nativos de nuvem. Você pode começar adicionando alguns microsserviços para aplicativos existentes para saber mais sobre os novos paradigmas de microsserviços. Mas, sem dúvida, você precisará arquiteto e código, especialmente para esse tipo de abordagem de arquitetura.

No entanto, os microsserviços não são obrigatórios para qualquer aplicativo novo ou moderno. Microsserviços não são "receita mágica", e eles não são a maneira única e é melhor criar todos os aplicativos. Como e quando você usa microsserviços depende do tipo de aplicativo que você precisa para criar.

A arquitetura de microsserviços está se tornando a abordagem preferencial para aplicativos críticos distribuídos grandes ou complexos e com base em vários subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microsserviços, um aplicativo é compilado como uma coleção de serviços que podem ser desenvolvidos de forma independente, testada e com controle de versão, implantar e dimensionar. Isso pode incluir qualquer banco de dados relacionado, autônomo por microsserviço.

Para obter uma visão detalhada de uma arquitetura de microsserviços que você pode implementar usando .NET Core, consulte o PDF e-book para download [microsserviços do .NET: Arquitetura para aplicativos .NET em contêineres](https://aka.ms/microservicesebook). O guia também está disponível [online](../../microservices-architecture/index.md).

Mas mesmo em cenários em que os microsserviços oferecem implantação de recursos independentes poderosa, fortes limites de subsistema e diversidade tecnológica-eles também apresentam vários novos desafios. Os desafios relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independentes; obter a comunicação resiliente entre microsserviços; a necessidade de consistência eventual. e a complexidade operacional. Microsserviços introduzem um nível mais alto de complexidade em comparação comparada os aplicativos monolíticos tradicionais.

Devido à complexidade de uma arquitetura de microsserviços, apenas cenários específicos e determinados tipos de aplicativos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos que têm várias evoluindo subsistemas. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para maior agilidade de longo prazo e manutenção de aplicativos mais eficiente. Mas para cenários menos complexos, talvez seja melhor continuar com uma abordagem de aplicativo monolítico ou abordagens mais simples de N camadas.

Como uma observação final, mesmo com o risco de serem repetitiva sobre esse conceito, você não deve examinar o uso de microsserviços em seus aplicativos como "totalmente em ou nada mesmo." Você pode estender e desenvolver aplicativos monolíticos existentes adicionando novos e pequenos cenários com base em microsserviços. Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura de microsserviços. Na verdade, é recomendável que você evoluir do uso de um aplicativo monolítico ou de N camadas existente com a adição de novos cenários. Por fim, você pode dividir o aplicativo em componentes autônomos ou microsserviços. Você pode iniciar a evolução de seus aplicativos monolíticos em uma direção de microsserviços, passo a passo.

Em qualquer caso, o restante deste guia presente se concentra acima de tudo em "não há aplicativos baseados em microsserviços" porque este guia destina principalmente a modernização de aplicativos existentes que normalmente têm arquiteturas monolíticas ou de N camadas.

> [!div class="step-by-step"]
> [Anterior](microsoft-technologies-in-cloud-optimized-applications.md)
> [Próximo](deploy-existing-net-apps-as-windows-containers.md)
