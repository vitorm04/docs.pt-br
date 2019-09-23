---
title: Resiliência nativa de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Resiliência nativa na nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184837"
---
# <a name="cloud-native-resiliency"></a>Resiliência nativa de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A resiliência é a capacidade do seu sistema de reagir à falha e ainda continuar funcionando. Não está prestes a evitar falhas. Mas trata-se de aceitar que a falha seja inevitável em sistemas baseados em nuvem e criando seu aplicativo para responder a ele. O objetivo final da resiliência é retornar o aplicativo para um estado totalmente funcional após uma falha.

Ao contrário dos aplicativos monolíticos tradicionais, onde tudo é executado juntos em um único processo, os sistemas nativos de nuvem adotam a arquitetura distribuída, conforme mostrado na Figura 6-1:

![Ambiente nativo de nuvem distribuída](./media/distributed-cloud-native-environment.png)

**Figura 6-1.** Ambiente nativo de nuvem distribuída

Na figura anterior, observe como cada cliente, microserviço e [serviço de backup](https://12factor.net/backing-services) baseado em nuvem é executado como um processo separado, em execução em diferentes servidores, todas comunicando-se por meio de chamadas baseadas em rede.

Então, o que poderia dar errado?

- [Latência de rede](https://www.techopedia.com/definition/8553/network-latency)inesperada.
- [Falhas transitórias](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (erros de conectividade de rede temporários).
- Bloqueio por uma operação síncrona de execução longa.
- Um processo de host que falhou e está sendo reiniciado ou movido.
- Um microserviço sobrecarregado que não pode responder por um curto período de tempo.
- Uma operação DevOps em andamento, como uma operação de atualização ou de dimensionamento.
- Uma operação de orquestrador, como mover um serviço de um nó para outro.
- Falhas de hardware do hardware de mercadoria.

Ao implantar serviços distribuídos em infraestrutura baseada em nuvem, os fatores da lista anterior se tornam muito reais e você deve arquitetar e desenvolver de maneira defensiva para lidar com eles.

Em um sistema distribuído de pequena escala, a falha será menos frequente, mas, à medida que o sistema for expandido e reduzido, você poderá esperar mais desses problemas até um ponto em que a falha parcial se tornará uma operação normal.

Portanto, seu aplicativo e sua infraestrutura devem ser resilientes. Nas seções a seguir, exploraremos técnicas defensivas que você pode adicionar ao seu aplicativo e recursos de nuvem internos que você pode aproveitar para ajudar a verificar a experiência do usuário na prova de marcadores.

>[!div class="step-by-step"]
>[Anterior](azure-data-storage.md)
>[Próximo](application-resiliency-patterns.md)
