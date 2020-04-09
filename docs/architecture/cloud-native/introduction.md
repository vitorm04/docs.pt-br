---
title: Introdução aos aplicativos nativos de nuvem
description: Saiba mais sobre computação nativa em nuvem
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989045"
---
# <a name="introduction-to-cloud-native-applications"></a>Introdução aos aplicativos nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Outro dia, no escritório, trabalhando em "a próxima grande coisa".

Seu celular toca. É o seu recrutador amigável, aquele que te liga duas vezes por dia sobre novos empregos.

Mas desta vez é diferente: Start-up, equidade e muito financiamento.

A menção da nuvem e da tecnologia de ponta empurra você para o limite.

Avance algumas semanas e agora você é um novo funcionário em uma sessão de design arquitetando um grande aplicativo de comércio eletrônico. Você vai completar com outros sites de comércio eletrônico líderes.

Como você vai construí-lo?

Se você seguir a orientação dos últimos 15 anos, provavelmente construirá o sistema mostrado na Figura 1.1.

![Design monolítico tradicional](./media/monolithic-design.png)

**Figura 1-1**. Design monolítico tradicional

Você constrói uma grande aplicação central contendo toda a sua lógica de domínio. Inclui módulos como Identidade, Catálogo, Pedidos e muito mais. O aplicativo principal se comunica com um grande banco de dados relacional. O núcleo expõe a funcionalidade através de uma interface HTML.

Parabéns!  Você acabou de criar uma aplicação monolítica.

Nem tudo é ruim. Os monólitos oferecem algumas vantagens distintas. Por exemplo, eles são diretos para...

- compilar
- test
- deploy
- Solucionar problemas
- scale

Muitos aplicativos de sucesso que existem hoje foram criados como monólitos. O aplicativo é um sucesso e continua a evoluir, iteração após iteração, adicionando cada vez mais funcionalidade.

Em algum momento, no entanto, você começa a se sentir desconfortável. Você se vê perdendo o controle da aplicação. Com o passar do tempo, o sentimento se torna mais intenso e você eventualmente entra em um estado conhecido como Ciclo do **Medo.**

- O aplicativo tornou-se tão esmagadoramente complicado que nenhuma pessoa o entende.
- Você temmedo de fazer mudanças - cada mudança tem efeitos colaterais não intencionais e caros.
- Novos recursos/correções tornam-se complicados, demorados e caros para implementar.
- Cada versão tão pequena quanto pode ser requer uma implantação completa de todo o aplicativo.
- Um componente instável pode travar todo o sistema.
- Novas tecnologias e frameworks não são uma opção.
- É difícil implementar metodologias de entrega ágeis.
- A erosão arquitetônica se instala à medida que a base de código se deteriora com "casos especiais" intermináveis.
- Os consultores lhe dizem para reescrevê-lo.

Muitas organizações têm abordado o ciclo do medo monolítico, adotando uma abordagem nativa da nuvem para sistemas de construção. A Figura 1-2 mostra o mesmo sistema construído aplicando técnicas e práticas nativas da nuvem.

![Design nativo da nuvem](./media/cloud-native-design.png)

**Figura 1-2**. Design nativo da nuvem

Observe como o aplicativo é decomposto em um conjunto de pequenos microserviços isolados. Cada serviço é independente e encapsula seu próprio código, dados e dependências. Cada um é implantado em um contêiner de software e gerenciado por um orquestrador de contêineres. Em vez de um grande banco de dados relacional, cada serviço possui seu próprio datastore, o tipo que varia de acordo com as necessidades de dados. Observe como alguns serviços dependem de um banco de dados relacional, mas outros em bancos de dados NoSQL. Um serviço armazena seu estado em um cache distribuído. Observe como todas as rotas de tráfego através de um serviço API Gateway que é responsável por direcionar o tráfego para os principais serviços de back-end e impor muitas preocupações transversais. Mais importante, o aplicativo aproveita ao máximo os recursos de escalabilidade e resiliência encontrados em plataformas modernas em nuvem.

### <a name="cloud-native-computing"></a>Computação nativa da nuvem

Hum... Nós apenas usamos o termo , "*Cloud Native*". Você primeiro pensou, "O que exatamente isso significa?" Outra palavra de ordem da indústria inventada por fornecedores de software para comercializar mais coisas?"

Felizmente é muito diferente e espero que este livro ajude a convencê-lo.

Em pouco tempo, o nativo da nuvem tornou-se uma tendência de condução na indústria de software. É uma nova maneira de pensar sobre a construção de sistemas grandes e complexos, uma abordagem que aproveita ao máximo as práticas modernas de desenvolvimento de software, tecnologias e infraestrutura em nuvem. A abordagem muda a maneira como você projeta, implementa, implanta e operacionaliza sistemas.

Ao contrário do hype contínuo que impulsiona nossa indústria, o nativo da nuvem é "*para real*". Considere a [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), um consórcio de mais de 300 grandes corporações com uma carta para tornar a computação nativa em nuvem onipresente entre tecnologia e pilhas de nuvem. Como um dos grupos de código aberto mais influentes, ele hospeda muitos dos projetos de código aberto que mais crescem no GitHub. Eles incluem projetos como [Kubernetes,](https://kubernetes.io/) [Prometheus,](https://prometheus.io/) [Helm,](https://helm.sh/) [Envoy](https://www.envoyproxy.io/)e [gRPC.](https://grpc.io/)

O CNCF promove um ecossistema de código aberto e neutralidade de fornecedores. Seguindo esse exemplo, apresentamos princípios, padrões e práticas recomendadas nativas da nuvem que são agnósticos tecnológicos. Ao mesmo tempo, discutimos os serviços e a infra-estrutura disponíveis na nuvem do Microsoft Azure para a construção de sistemas nativos em nuvem.

Então, o que exatamente é Cloud Native? Sente-se, relaxe, e deixe-nos ajudá-lo a explorar este novo mundo.

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](definition.md)
