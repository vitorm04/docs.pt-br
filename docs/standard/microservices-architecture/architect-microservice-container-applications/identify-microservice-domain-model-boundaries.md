---
title: "Identificando os limites de modelo de domínio para cada microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Identificando os limites de modelo de domínio para cada microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6fef11e5718706701abb29149c4c4a23ba39bde0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identificar limites de modelo de domínio para cada microsserviço

O objetivo de identificar os limites do modelo e o tamanho de cada microsserviço é não get para a separação mais granular possíveis, embora deve tendem para microservices pequeno se possível. Em vez disso, sua meta deve ser para obter a separação mais significativa orientada por seu conhecimento do domínio. A ênfase não é o tamanho, mas em recursos de negócios. Além disso, se houver limpar coesão necessários para uma determinada área do aplicativo com base em um grande número de dependências, que indica a necessidade de um único microsserviço, muito. Coesão é uma maneira de identificar como separar ou microservices juntos de grupo. Por fim, enquanto você obtém mais dados de Conhecimento sobre o domínio, você deve adaptar o tamanho do seu microsserviço iterativamente. Localizar o tamanho correto não é um processo única.

[SAM Newman](http://samnewman.io/), um promotor reconhecida de microservices e autor do livro [Microservices de construção](http://samnewman.io/books/building_microservices/), realça o que você deve projetar seu microservices baseado no padrão de contexto limitado (BC) (parte do controlado por domínio design), conforme apresentado anteriormente. Às vezes, uma continuidade de negócios pode ser composta de vários serviços físicos, mas não vice-versa.

Aplica um modelo de domínio com entidades de domínio específico dentro de um BC concreto ou microsserviço. Um BC delimita a aplicabilidade de um modelo de domínio e os membros da equipe do desenvolvedor dá uma compreensão clara e compartilhada dos quais devem ser consistente e que podem ser desenvolvido de modo independente. Esses são os mesmos objetivos de microservices.

Outra ferramenta que informa a sua escolha de design é [lei de Conway](https://en.wikipedia.org/wiki/Conway%27s_law), indicando que um aplicativo irão refletir os limites sociais da organização que produziu. Mas, às vezes, o oposto é verdadeiro, a organização da empresa é formada pelo software. Você precisará reverter lei de Conway e os limites de compilação a maneira como deseja que a empresa sejam organizados, inclinada em direção de consultoria do processo de negócios.

Para identificar os contextos limitados, um padrão DDD que pode ser usado para isso é o [contexto mapeamento padrão](https://www.infoq.com/articles/ddd-contextmapping). Mapeamento de contexto, você identificar os vários contextos no aplicativo e seus limites. É comum que haja um contexto diferente e limites para cada subsistema pequeno, por exemplo. O mapa de contexto é uma maneira de definir e tornar explícita esses limites entre domínios. Um BC autônomo e inclui os detalhes de um único domínio — detalhes como as entidades de domínio — e define os contratos de integração com outros BCs. Isso é semelhante à definição de um microsserviço: é autônomo, ele implementa determinados recursos de domínio e ele deve fornecer interfaces. Isso é porque o mapeamento de contexto e o padrão de contexto limitado bom abordagens para identificar os limites de modelo de domínio do seu microservices.

Ao criar um aplicativo grande, você verá como seu modelo de domínio pode ser fragmentado — um especialista de domínio do domínio de catálogo nomeará entidades de maneira diferente nos domínios de catálogo e inventário de um domínio de envio especializado, para a instância. Ou a entidade de usuário de domínio pode ser diferente em tamanho e número de atributos ao lidar com um especialista do CRM que deseja armazenar todos os detalhes sobre o cliente do que para especialista ordenação do domínio que precisa apenas parcial de dados sobre o cliente. É muito difícil de resolver a ambiguidade de todos os termos do domínio em todos os domínios relacionados a um aplicativo grande. Mas o mais importante é que você não deve tentar unificar os termos; em vez disso, aceite as diferenças e riqueza fornecidas por cada domínio. Se você tentar se tiver um banco de dados unificado para o aplicativo inteiro, tentativas de um vocabulário unificada serão inadequadas e não tocará direita a qualquer um dos vários especialistas de domínio. Portanto, BCs (implementados como microservices) ajudará a esclarecer onde você pode usar determinados termos do domínio e onde você precisará dividir o sistema e criar BCs adicionais com domínios diferentes.

Você saberá que você obteve os limites à direita e os tamanhos de cada BC e modelo de domínio se você tem algumas relações fortes entre modelos de domínio e normalmente não faria necessário mesclar as informações de vários modelos de domínio ao executar um aplicativo típico operações.

Talvez a melhor resposta à pergunta de grande como um modelo de domínio para cada microsserviço deve ser é o seguinte: ele deve ter um BC autônomo, como isolado possível, o que permite que você trabalhe sem precisar alternar constantemente a outros contextos (outros modelos do microsserviço). Figura 4-10, você pode ver como várias microservices (várias BCs) cada têm seus próprios modelos e como suas entidades podem ser definidas, dependendo dos requisitos específicos para cada um dos domínios identificados em seu aplicativo.

![](./media/image10.png)

**Figura 4-10**. Identificação de entidades e limites de modelo de microsserviço

Figura 4-10 ilustra um cenário de exemplo relacionado a um sistema de gerenciamento de conferência on-line. Você identificou várias BCs que podem ser implementados como microservices, com base em domínios que especialistas de domínio definidos para você. Como você pode ver, há entidades que estão presentes apenas em um modelo de microsserviço único, como pagamentos em microsserviço de pagamento. Esses serão fáceis de implementar.

No entanto, você também pode ter entidades que têm uma forma diferente, mas compartilham a mesma identidade em vários modelos de domínio de microservices a vários. Por exemplo, a entidade de usuário é identificada no microsserviço gerenciamento de conferências. Esse mesmo usuário, com a mesma identidade, é o chamado compradores em microsserviço a ordenação ou a chamada contribuinte no microsserviço o pagamento e até mesmo o um cliente nomeado no microsserviço atendimento ao cliente. Isso ocorre porque, dependendo do [idioma onipresente](https://martinfowler.com/bliki/UbiquitousLanguage.html) que está usando o especialista em cada domínio, um usuário pode ter uma perspectiva diferente, mesmo com atributos diferentes. A entidade de usuário no modelo de microsserviço denominado conferências Management pode ter mais de seus atributos de dados pessoais. No entanto, esse mesmo usuário na forma de cliente em que o pagamento de microsserviço ou na forma de cliente de microsserviço atendimento ao cliente talvez não seja necessário a mesma lista de atributos.

Uma abordagem semelhante é ilustrada na Figura 4-11.

![](./media/image11.png)

**Figura 4-11**. A decomposição de modelos de dados tradicional em vários modelos de domínio

Você pode ver como o usuário está presente no modelo de microsserviço de gerenciamento de conferências como entidade de usuário e também está presente no formulário da entidade comprador microsserviço a preços, com detalhes sobre o usuário quando ele é realmente um comprador ou de atributos alternativos. Cada microsserviço ou BC talvez não seja necessário todos os dados relacionados a uma entidade de usuário, apenas parte dele, dependendo de resolver o problema ou o contexto. Por exemplo, no modelo de preços de microsserviço, não é necessário o endereço ou a ID do usuário, apenas o ID (como identidade) e o Status, que terá um impacto em descontos quando preços estações por comprador.

A entidade de estação tem o mesmo nome mas diferentes atributos em cada modelo de domínio. No entanto, os compartilhamentos de estação identidade com base na ID da mesma, como acontece com o comprador e o usuário.

Basicamente, há um conceito compartilhado de um usuário que existe em vários serviços (domínios), que compartilham a identidade do usuário. Mas, em cada modelo de domínio pode ser adicionais ou diferentes detalhes sobre a entidade de usuário. Portanto, precisa ser uma maneira de mapear uma entidade de usuário de um domínio (microsserviço) para outro.

Há vários benefícios para não compartilhar a mesma entidade de usuário com o mesmo número de atributos entre domínios. Um benefício é reduzir a duplicação, para que os modelos de microsserviço não tem todos os dados que não seja necessário. Outro benefício está tendo um microsserviço mestre que possui um determinado tipo de dados por entidade para que as atualizações e consultas para esse tipo de dados são controladas por apenas por esse microsserviço.


>[!div class="step-by-step"]
[Anterior] (distributed-data-management.md) [Avançar] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
