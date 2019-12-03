---
title: Apêndice-gRPC para desenvolvedores do WCF
description: Discussão sobre transações distribuídas e sua implementação em arquiteturas de microserviços modernas.
ms.date: 09/02/2019
ms.openlocfilehash: 9931681727f921e007c2f80852ad0e69cd7288de
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711465"
---
# <a name="appendix-a---transactions"></a>Apêndice A – transações

O Windows Communication Foundation (WCF) dá suporte a transações distribuídas, permitindo que você execute operações atômicas em vários serviços. Essa funcionalidade é baseada no [Microsoft coordenador de transações distribuídas](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

Na nova paisagem de microserviços, esse tipo de processamento automatizado de transações distribuídas não é possível. Há muitas tecnologias diferentes envolvidas, incluindo bancos de dados relacionais, armazenamentos de dado NoSQL e sistemas de mensagens. Também pode haver uma combinação de sistemas operacionais, linguagens de programação e estruturas em uso em um único ambiente.

A transação distribuída do WCF é uma implementação do que é conhecido como uma [confirmação de duas fases (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Você pode implementar transações 2PC manualmente coordenando mensagens entre serviços, criando transações abertas dentro de cada serviço e enviando mensagens de confirmação ou reversão, dependendo do êxito ou da falha. No entanto, a complexidade envolvida no gerenciamento de 2PC pode aumentar exponencialmente conforme os sistemas evoluem. Transações abertas mantêm bloqueios de banco de dados que podem afetar negativamente o desempenho ou, pior, causam deadlocks entre serviços.

Se possível, é melhor evitar totalmente as transações distribuídas. Se dois itens de dados estiverem tão vinculados quanto exigirem atualizações atômicas, considere tratá-los com o mesmo serviço. Aplique essas alterações atômicas usando uma única solicitação ou mensagem para esse serviço.

Se isso não for possível, então uma alternativa é usar o [padrão saga](https://microservices.io/patterns/data/saga.html). Em um saga, as atualizações são processadas sequencialmente; à medida que cada atualização é realizada com sucesso, a próxima é disparada. Esses gatilhos podem ser propagados do serviço para o serviço ou gerenciados por um coordenador ou orquestrador do Saga. Se uma atualização falhar em qualquer ponto durante o processo, os serviços que já concluíram suas atualizações aplicarão uma lógica específica para invertê-las.

Outra opção é usar o DDD (design controlado por domínio) e o CQRS (segregação de responsabilidade de comando/consulta), conforme descrito no [livro eletrônico de microservices do .net](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). Em particular, o uso de eventos de domínio ou [fornecimento de eventos](https://martinfowler.com/eaaDev/EventSourcing.html) pode ajudar a garantir que as atualizações sejam consistentemente, caso não sejam aplicadas imediatamente.

>[!div class="step-by-step"]
>[Anterior](application-performance-management.md)
