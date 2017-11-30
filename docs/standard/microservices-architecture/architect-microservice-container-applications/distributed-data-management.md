---
title: "Desafios e soluções de gerenciamento de dados distribuído"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Desafios e soluções de gerenciamento de dados distribuído"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f961475b40c74bf448cff1aeae04ae4866360e52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Desafios e soluções de gerenciamento de dados distribuído

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Desafio \#1: como definir os limites de cada microsserviço

Definir limites de microsserviço provavelmente é o primeiro desafio que qualquer pessoa que se encontra. Cada microsserviço deve ser uma parte do seu aplicativo, e cada microsserviço deve ser autônomo com todos os benefícios e desafios que transmite. Mas como identificar esses limites?

Primeiro, você precisa se concentrar em modelos de domínio lógica do aplicativo e dados relacionados. Você deve tentar identificar desacopladas ilhas de dados e contextos diferentes dentro do mesmo aplicativo. Cada contexto pode ter um idioma diferente de negócios (termos de negócios diferente). Os contextos devem ser definidos e gerenciados de forma independente. Os termos e as entidades usadas nesses contextos diferentes, podem parecer semelhantes, mas você pode descobrir que, em um contexto específico, um conceito de negócios com um é usado para uma finalidade diferente em outro contexto e pode ter um nome diferente. Por exemplo, um usuário pode ser referido como um usuário no contexto de identidade ou de associação, como um cliente em um contexto CRM, como um cliente em um contexto de ordenação e assim por diante.

A maneira como você identificar os limites entre vários contextos de aplicativo com um domínio diferente para cada contexto é exatamente como você pode identificar os limites para cada microsserviço de negócios e seu relacionados modelo de domínio e os dados. Você sempre tentar reduzir o acoplamento entre esses microservices. Este guia apresenta mais detalhes sobre esse design de modelo de domínio e a identificação na seção [identificar limites de modelo de domínio para cada microsserviço](#identifying-domain-model-boundaries-for-each-microservice) mais tarde.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Desafio \#2: como criar consultas que recuperam dados de vários microservices

Um segundo desafio é a implementação de consultas que recuperam dados de vários microservices, evitando a comunicação verborrágica para o microservices de aplicativos de cliente remoto. Um exemplo pode ser uma única tela de um aplicativo móvel que precisa para mostrar informações do usuário que pertencem o carrinho, catálogo e microservices de identidade do usuário. Outro exemplo seria um relatório complexo que envolve muitas tabelas localizadas em vários microservices. A solução certa depende da complexidade das consultas. Mas em qualquer caso, será necessário um método de agregação informações para melhorar a eficiência na comunicação do sistema. As soluções mais comuns são as seguintes.

**API de Gateway**. Para a agregação de dados simples de vários microservices que possui bancos de dados diferentes, a abordagem recomendada é um microsserviço de agregação, conhecido como um Gateway de API. No entanto, você precisa ter cuidado ao implementar esse padrão, porque ele pode ser um ponto de restrição no seu sistema e ele pode violar o princípio de microsserviço autonomia. Para atenuar essa possibilidade, você pode ter vários Gateways de API granular cada um focalizando um vertical "fatia" ou a área de negócios do sistema. O padrão de Gateway de API é explicado mais detalhadamente na seção de usando um Gateway de API mais tarde.

**CQRS com tabelas de consulta/leituras**. Outra solução para agregar dados de vários microservices é o [padrão da exibição materializada](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Nessa abordagem, gerar, com antecedência (preparar dados desnormalizados antes das consultas reais ocorrem), uma tabela somente leitura com os dados que pertencem a vários microservices. A tabela tem um formato adequado às necessidades do aplicativo cliente.

Considere a possibilidade de algo como tela de um aplicativo móvel. Se você tiver um único banco de dados, você pode reunir dados para essa tela usando uma consulta SQL que executa uma junção complexa que envolve várias tabelas. No entanto, quando você tiver vários bancos de dados, e cada banco de dados pertence a um microsserviço diferente, você não pode consultar esses bancos de dados e criar uma junção SQL. Sua consulta complexa se torna um desafio. Você pode lidar com o requisito usando uma abordagem CQRS — criar uma tabela não normalizada em outro banco de dados que é usado apenas para consultas. A tabela pode ser desenvolvida especificamente para os dados que necessários para a consulta complexa, com uma relação um para um entre campos necessários a tela do aplicativo e as colunas na tabela de consulta. Ele também pode funcionar para fins de relatório.

Essa abordagem não apenas resolve o problema original (como a consulta e junção em microservices); Isso também melhora o desempenho consideravelmente em comparação com uma junção complexa, porque você já tem os dados que o aplicativo precisa na tabela de consulta. É claro que, usando o comando e consulta responsabilidade CQRS (segregação) com tabelas de consulta/leituras significa o trabalho de desenvolvimento adicional e você precisará adotar consistência eventual. No entanto, requisitos de desempenho e alta escalabilidade em [cenários de colaboração](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (ou cenários de concorrência, dependendo do ponto de Vista) é onde você deve aplicar CQRS com vários bancos de dados.

**"Dados frios" em bancos de dados centrais**. Para relatórios complexos e consultas que podem não exigir dados em tempo real, uma abordagem comum é exportar o "hot dados" (dados transacionais do microservices) como "dados frios" para grandes bancos de dados que são usados somente para relatórios. Esse sistema de banco de dados central pode ser um sistema baseado em Big Data, como Hadoop, um data warehouse como com base no Azure SQL Data Warehouse, ou até mesmo um único banco de dados SQL usados apenas para relatórios (se o tamanho não será um problema).

Tenha em mente que este banco de dados centralizado deve ser usado somente para consultas e relatórios que não precisam de dados em tempo real. As atualizações de original e transações, como a fonte de verdade, precisam ser em seus dados microservices. A maneira como você sincronizarão os dados seriam usando comunicação controlada por evento (abordada nas próximas seções) ou usando outras ferramentas de importação/exportação de infraestrutura de banco de dados. Se você usar a comunicação controlada por evento, esse processo de integração seria semelhante à forma como você propagar os dados conforme descrito anteriormente para consultar tabelas de CQRS.

No entanto, se o design do aplicativo envolve constantemente agregar informações de vários microservices para consultas complexas, pode ser um sintoma de um design ruim — um microsserviço deve ser isolado como possível de outros microservices. (Isso exclui relatórios/analytics que sempre devem usar bancos de dados centrais de dados a frio). Com esse problema geralmente pode ser um motivo para mesclar microservices. Você precisa equilibrar a autonomia de evolução e a implantação de cada microsserviço com dependências fortes, coesão e agregação de dados.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Desafio \#3: como obter consistência em vários microservices

Como mencionado anteriormente, os dados de cada microsserviço é privados que microsserviço e só podem ser acessados usando o API microsserviço. Portanto, um desafio apresentado é como implementar processos de negócios de ponta a ponta, mantendo a consistência entre várias microservices.

Para analisar o problema, vamos examinar um exemplo da [eShopOnContainers Referência aplicativo](http://aka.ms/eshoponcontainers). O catálogo microsserviço mantém informações sobre todos os produtos, inclusive o nível de estoque. O ordenação microsserviço gerencia pedidos e deve verificar que um novo pedido não exceda o estoque de produtos disponíveis do catálogo. (Ou o cenário pode envolver a lógica que trata os produtos pendente). Em uma versão monolítica hipotética deste aplicativo, o subsistema de ordenação pode simplesmente usar uma transação ACID para verificar o estoque disponível, criar a ordem na tabela Orders e atualizar o estoque disponível na tabela de produtos.

No entanto, em um aplicativo baseados em microservices, tabelas Order e produto pertencem a seus respectivos microservices. Nenhum microsserviço já deve incluir bancos de dados pertencentes a outro microsserviço em suas próprias transações ou consultas, conforme mostrado na Figura 4-9.

![](./media/image9.PNG)

**Figura 4-9**. Um microsserviço não pode acessar diretamente uma tabela em outro microsserviço

O ordenação de microsserviço não deve atualizar a tabela de produtos diretamente, porque a tabela de produtos é de propriedade de microsserviço o catálogo. Para fazer uma atualização para o catálogo de microsserviço, microsserviço a ordenação só deve usar a comunicação assíncrona, como eventos de integração (mensagem e comunicação baseada em evento). Isso é como o [eShopOnContainers](http://aka.ms/eshoponcontainers) referência aplicativo executa esse tipo de atualização.

Conforme indicado pelo [Teorema de CAP](https://en.wikipedia.org/wiki/CAP_theorem), é necessário escolher entre disponibilidade e ACID consistência forte. Maioria dos cenários de microsserviço exigem alta escalabilidade em vez de consistência forte e disponibilidade. Aplicativos de missão crítica devem permanecer para cima e em execução e os desenvolvedores podem contornar consistência forte usando técnicas para trabalhar com consistência eventual ou fraca. Essa é a abordagem usada pela maioria das arquiteturas de microsserviço.

Além disso, o estilo ACID ou transações de confirmação de duas fases não são apenas em relação a princípios microservices; a maioria dos bancos de dados SQL (como o banco de dados do Azure Cosmos, MongoDB, etc.) não dão suporte a transações de confirmação de duas fases. No entanto, manter dados de consistência em serviços e bancos de dados é essencial. Esse desafio também está relacionado à pergunta de como propagar alterações em várias microservices quando determinados dados precisam ser redundante — por exemplo, quando você precisa ter o nome ou a descrição em microsserviço o catálogo e o carrinho do produto microsserviço.

Uma boa solução para esse problema é usar consistência eventual entre microservices articulados por meio de comunicação orientada a eventos e um sistema de publicação e assinatura. Esses tópicos são abordados na seção [comunicação assíncrona controlada por evento](#async_event_driven_communication) posteriormente neste guia.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Desafio \#4: como criar a comunicação entre os limites de microsserviço

Limites de se comunicar pela microsserviço é um desafio real. Nesse contexto, comunicação não se refere ao protocolo ao qual você deve usar (HTTP e REST, AMQP, mensagens e assim por diante). Em vez disso, aborda o estilo de comunicação, você deve usar, e especialmente o microservices como acopladas deve ser. Dependendo do nível de acoplamento, quando ocorre falha, o impacto dessa falha em seu sistema variam significativamente.

Em um sistema distribuído como um aplicativo baseado em microservices, com muitos artefatos de movimentação e serviços distribuídos em vários servidores ou hosts, componentes eventualmente falhará. Falha parcial e falhas ainda maiores ocorrerá, portanto você precisa para projetar seu microservices e a comunicação entre eles levando em conta os riscos comum nesse tipo de sistema distribuído.

É um método popular implementar o HTTP (REST)-com base em microservices, devido à sua simplicidade. Uma abordagem baseada em HTTP é perfeitamente aceitável; aqui, o problema está relacionado à maneira como você usa. Se você usar solicitações e respostas HTTP para interagir com seu microservices de aplicativos cliente ou de Gateways de API, que é bom. Mas, se você criar longas cadeias de chamadas HTTP síncronas em microservices, comunicação seus limites, como se o microservices foram objetos em um aplicativo monolítico, seu aplicativo serão eventualmente tiver problemas.

Por exemplo, imagine que o aplicativo cliente faz uma chamada de API HTTP para um microsserviço individual como o ordenação de microsserviço. Se o microsserviço de ordenação por sua vez chama adicional microservices usando HTTP na mesma solicitação/resposta ciclo, você está criando uma cadeia de chamadas HTTP. Parece razoável inicialmente. No entanto, existem pontos importantes a considerar quando este caminho:

-   Bloqueio e baixo desempenho. Devido à natureza síncrona de HTTP, a solicitação original não obterá uma resposta até que todas as chamadas HTTP internas sejam concluídas. Imagine se o número dessas chamadas aumenta significativamente e ao mesmo tempo um intermediário HTTP chamadas para um microsserviço está bloqueado. O resultado é que o desempenho é afetado, e a escalabilidade geral será afetada exponencialmente como um aumento adicional de solicitações HTTP.

-   Acoplamento microservices com HTTP. Business microservices não deve ser combinado com outros microservices de negócios. Idealmente, eles devem "conhece" a existência de outros microservices. Se seu aplicativo depende de acoplamento microservices como no exemplo, para alcançar a autonomia por microsserviço será praticamente impossível.

-   Falha em qualquer um microsserviço. Se você implementou uma cadeia de microservices vinculadas por chamadas HTTP, quando qualquer uma da microservices falha (e, eventualmente, eles falharão) toda a cadeia de microservices falhará. Um sistema baseado em microsserviço deve ser criado para continuar a trabalhar, bem como possíveis durante falhas parciais. Mesmo se você implementar a lógica do cliente que usa novas tentativas com retirada exponencial ou mecanismos de Disjuntor, as cadeias de chamada mais complexos HTTP são, mais complexo, ele é implementar uma estratégia de falha com base em HTTP.

Na verdade, se seu microservices internos estão se comunicando por meio da criação de cadeias de solicitações HTTP conforme descrito, poderíamos argumentar que você tenha um aplicativo monolítico, mas um com base em HTTP entre processos em vez de mecanismos de comunicação intraprocess.

Portanto, para impor a autonomia de microsserviço e ter melhor resiliência, você deve minimizar o uso de cadeias de comunicação de solicitação/resposta em microservices. É recomendável que você usar interação assíncrona apenas para comunicação de microsserviço inter usando a comunicação assíncrona baseado em evento e à mensagem ou consulta de HTTP, independentemente do ciclo de solicitação/resposta HTTP original.

O uso de comunicação assíncrona é explicado com mais detalhes posteriormente neste guia nas seções a [microsserviço assíncrona integração impõe a autonomia do microsserviço](#asynchronous-microservice-integration-enforce-microservices-autonomy) e [assíncrona comunicação baseada em mensagem](#asynchronous-message-based-communication).

## <a name="additional-resources"></a>Recursos adicionais

-   **Teorema de CAP**
    [*https://en.wikipedia.org/wiki/CAP\_Teorema*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Consistência eventual**
    [*https://en.wikipedia.org/wiki/Eventual\_consistência*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Primer de consistência de dados**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Martin Fowler. CQRS (comando e segregação de responsabilidade de consulta)**
    [*http://martinfowler.com/bliki/CQRS.html*](http://martinfowler.com/bliki/CQRS.html)

-   **Materializada exibição**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Charles linha. ACID vs. BASE: O Shifting pH de processamento de transações do banco de dados**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **Transações de compensação**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **Udi Dahan. Composição orientada a serviços**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[Anterior] (lógico-versus-físico-architecture.md) [Avançar] (identificar-microsserviço-domínio-modelo-boundaries.md)
