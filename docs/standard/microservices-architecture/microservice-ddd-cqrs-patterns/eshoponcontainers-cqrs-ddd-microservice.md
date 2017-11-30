---
title: "Aplicando CQRS e CQS abordagens um microsserviço DDD em eShopOnContainers"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Aplicando CQRS e CQS abordagens um microsserviço DDD em eShopOnContainers"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Aplicando CQRS e CQS abordagens um microsserviço DDD em eShopOnContainers

O design do ordenação microsserviço no aplicativo eShopOnContainers referência se baseia em princípios CQRS. No entanto, ele usa a abordagem mais simples, que apenas as consultas a separação dos comandos e usando o mesmo banco de dados para ambas as ações.

A essência desses padrões e o ponto importante aqui é que as consultas são idempotentes: não importa quantas vezes você consultar um sistema, o estado do sistema não serão alterado, você pode até usar um modelo de dados diferente de "leitura" que a lógica transacional "gravação" modelo de domínio, embora a ordenação microservices está usando o mesmo banco de dados. Portanto, essa é uma abordagem CQRS simplificada.

Por outro lado, comandos que iniciam transações e as atualizações de dados, alteram o estado do sistema. Com os comandos, você precisa ter cuidado quando relacionadas com complexidade e constantes de regras de negócio. Isso é onde você deseja aplicar as técnicas DDD para ter um sistema modelado melhor.

Os padrões DDD apresentados neste guia não devem ser aplicados universalmente. Eles apresentam restrições em seu design. Essas restrições fornecem benefícios como alta qualidade ao longo do tempo, especialmente em comandos e outro código que modifica o estado do sistema. No entanto, essas restrições adicionam complexidade com menos benefícios para ler e consultar dados.

Um esse padrão é o agregação padrão, o que mais são examinadas em seções posteriores. Resumidamente, a agregação padrão, tratar vários objetos de domínio como uma única unidade como resultado de sua relação no domínio. Você não pode obter vantagens deste padrão em consultas; sempre ele pode aumentar a complexidade da lógica de consulta. Para consultas somente leitura, você não obtiver as vantagens de tratamento de vários objetos como uma única agregação. Você somente obtém a complexidade.

Conforme mostrado na Figura 9-2, este guia sugere usando padrões DDD apenas na área de transacional/atualizações do seu microsserviço (ou seja, como disparado por comandos). Consultas podem seguir uma abordagem mais simples e devem ser separadas dos comandos, seguindo uma abordagem CQRS.

Para implementar o lado"consultas", você pode escolher entre várias abordagens de seu ORM completo como EF Core, AutoMapper projeções, procedimentos armazenados, exibições, Exibições materializadas ou um ORM micro.

Neste guia e eShopOnContainers (especificamente o microsserviço ordenação) que escolhemos para implementar retas consultas usando um micro ORM como [Dapper](https://github.com/StackExchange/dapper-dot-net). Isso permite ao usuário implementar qualquer consulta com base nas instruções SQL para obter o melhor desempenho, graças uma estrutura leve com muito pouca sobrecarga.

Observe que, quando você usar essa abordagem, as atualizações para seu modelo que afetam como entidades são persistentes em um banco de dados SQL também necessário atualizações separadas em consultas SQL usadas por Dapper ou quaisquer outras abordagens (não EF) separadas para consultar.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Padrões de CQRS e DDD não são as arquiteturas de nível superior

É importante entender que CQRS e a maioria dos padrões DDD (como camadas DDD ou um modelo de domínio com agregações) não são estilos de arquitetura, mas apenas os padrões de arquitetura. Microservices, SOA e arquitetura orientada a eventos (EDA) são exemplos de estilos de arquitetura. Eles descrevem um sistema de vários componentes, como muitos microservices. Padrões de CQRS e DDD descrevem algo dentro de um único sistema ou um componente. Nesse caso, algo dentro de um microsserviço.

Diferentes contextos limitada (BCs) empregará padrões diferentes. Eles têm responsabilidades diferentes e que leva a diferentes soluções. Vale enfatizar que forçar o mesmo padrão em todos os lugares leva a uma falha. Não use CQRS e DDD padrões em todos os lugares. Vários subsistemas, BCs ou microservices são mais simples e pode ser implementado mais facilmente usando serviços CRUD simples ou outra abordagem.

Arquitetura de apenas um aplicativo: a arquitetura do aplicativo de sistema ou de ponta a ponta que você está criando (por exemplo, a arquitetura de microservices). No entanto, o design de cada contexto limitado ou microsserviço que reflete o seu próprio compensações e decisões de design interno em um nível de padrões de arquitetura. Não tente aplicar os mesmos padrões de arquitetura como CQRS ou DDD em qualquer lugar.

####  <a name="additional-resources"></a>Recursos adicionais

-   **Martin Fowler. CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Greg Young. CQS vs. CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Greg Young. Documentos CQRS**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Greg Young. CQRS, tarefa baseado em interfaces de usuário e o fornecimento de evento**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **Udi Dahan. Esclareceu CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **(ES) de fornecimento de evento**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[Anterior] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Avançar] (cqrs-microsserviço-reads.md)
