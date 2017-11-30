---
title: "Aplicando padrões CQRS e DDD simplificados em um microsserviço."
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Aplicando padrões CQRS e DDD simplificados em um microsserviço."
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 99fd7ce32039742e23f8e01aa4c33cddd7a9f698
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Aplicando padrões CQRS e DDD simplificados em um microsserviço.

CQRS é um padrão de arquitetura que separa os modelos para ler e gravar dados. O termo relacionado [separação de consulta de comando (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) foi originalmente definido por Bertrand Meyer em seu livro *construção de Software orientada a objeto*. A ideia básica é que você pode dividir operações do sistema em duas categorias nitidamente separadas:

-   Consultas. Esses retornam um resultado e não altera o estado do sistema e são livres de efeitos colaterais.

-   Os comandos. Esses alterar o estado de um sistema.

CQS é um conceito simple — é sobre métodos de dentro do mesmo objeto sendo consultas ou comandos. Cada método retorna o estado ou muda de estado, mas não ambos. Até mesmo um objeto de padrão único repositório pode estar em conformidade com CQS. CQS pode ser considerado um princípio fundamental para CQRS.

[Comando e consulta responsabilidade CQRS (segregação)](https://martinfowler.com/bliki/CQRS.html) foi introduzido por Greg Young e altamente promovido pelos Udi Dahan e outros. Ele se baseia no princípio CQS, embora mais detalhada. Ele pode ser considerado um padrão com base em comandos e eventos mais opcionalmente nas mensagens assíncronas. Em muitos casos, a CQRS está relacionado a cenários mais avançados, como ter um banco de dados diferente para leituras (consultas) que, para gravações (atualizações). Além disso, um sistema CQRS mais evoluído pode implementar [(ES) de fornecimento do evento](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) para seu banco de dados de atualizações, assim você deve apenas armazenar eventos no modelo de domínio em vez de armazenar os dados de estado atual. No entanto, isso não é a abordagem usada neste guia; Estamos usando a abordagem mais simples de CQRS, que consiste em separar apenas as consultas dos comandos.

O aspecto de separação de CQRS é obtido com o agrupamento de operações de consulta em uma camada e comandos em outra camada. Cada camada tem seu próprio modelo de dados (Observe que dizemos que o modelo, não necessariamente um banco de dados diferente) e é criada usando seu próprio combinação de padrões e tecnologias. Além disso, as duas camadas podem ser dentro do mesmo nível ou microsserviço, como no exemplo (ordem microsserviço) usado para este guia. Ou eles podem ser implementados em microservices diferente ou processos para que possa ser otimizados e expandidos separadamente sem afetar uma da outra.

CQRS significa ter dois objetos para uma operação de leitura/gravação em que em outros contextos houver. Há motivos para ter um banco de dados desnormalizados leituras, que você pode aprender sobre na literatura CQRS mais avançada. Mas não estamos usando essa abordagem aqui, onde o objetivo é ter mais flexibilidade em consultas, em vez de limitar as consultas com restrições de padrões DDD como agregações.

Um exemplo desse tipo de serviço é o ordenação microsserviço do aplicativo eShopOnContainers referência. Este serviço implementa um microsserviço com base em uma abordagem CQRS simplificada. Ele usa uma fonte de dados ou banco de dados, mas dois modelos lógicos mais padrões DDD para o domínio transacional, conforme mostrado na Figura 9-2.

![](./media/image2.png)

**Figura 9-2**. Simplificado CQRS DDD baseada e microsserviço

A camada de aplicativo pode ser a própria API da Web. O aspecto de design importante aqui é que o microsserviço dividiu as consultas e ViewModels (modelos de dados criados especialmente para os aplicativos cliente) do modelo de domínio, comandos e transações após o padrão CQRS. Essa abordagem mantém as consultas independentes de restrições e restrições provenientes de padrões DDD que só fazem sentido para transações e atualizações, conforme explicado nas seções posteriores.


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (eshoponcontainers-cqrs-ddd-microservice.md)
