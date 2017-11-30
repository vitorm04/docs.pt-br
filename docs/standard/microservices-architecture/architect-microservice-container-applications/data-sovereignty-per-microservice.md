---
title: "Soberania dados por microsserviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Soberania dados por microsserviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c51daae04215cfa6f5b5b8d2158a8ed1a8949652
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="data-sovereignty-per-microservice"></a>Soberania dados por microsserviço

Uma regra importante para arquitetura microservices é que cada microsserviço deve ter seus dados de domínio e lógica. Assim como um aplicativo completo possui sua lógica e os dados, portanto deve cada microsserviço possui sua lógica e os dados em um ciclo de vida autônomo, com a implantação independente por microsserviço.

Isso significa que o modelo conceitual do domínio será diferente entre subsistemas ou microservices. Considere a possibilidade de aplicativos da empresa, onde os aplicativos de CRM (gerenciamento) relação cliente, transacionais comprarem subsistemas e subsistemas de suporte ao cliente cada chamada em atributos de entidade exclusivo do cliente e dados, e cada emprega um diferente Contexto limitado (BC).

Esse princípio é semelhante em [design orientado a domínio (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), onde cada [limitada contexto](https://martinfowler.com/bliki/BoundedContext.html) ou subsistema autônomo ou serviço deve possuir o seu modelo de domínio (dados mais lógica e comportamento). Cada DDD limitada contexto se correlaciona com uma microsserviço de negócios (um ou vários serviços). (É expandir nesse ponto sobre o padrão do contexto associado na próxima seção).

Por outro lado, a abordagem tradicional (dados monolítico) usada em muitos aplicativos é ter um único banco de dados centralizado ou apenas alguns bancos de dados. Isso geralmente é um banco de dados SQL normalizado que é usado para o aplicativo inteiro e todos os seus subsistemas internos, conforme mostrado na Figura 4-7.

![](./media/image7.png)

**Figura 4-7**. Comparação de Soberania de dados: banco de dados monolítico versus microservices

Inicialmente, a abordagem de banco de dados centralizado é mais simples e parece habilitar a reutilização de entidades em subsistemas diferentes para fazer tudo o que é consistente. Mas a realidade é que você acabará com grandes tabelas que servem vários subsistemas diferentes e que incluem atributos e colunas que não são necessários na maioria dos casos. é como tentar usar o mesmo mapa físico para caminhada uma trilha de curta, fazer uma viagem de carro de dia inteiro e aprendizado Geografia.

Um aplicativo monolítico com normalmente um único banco de dados relacional tem dois benefícios importantes: [transações ACID](https://en.wikipedia.org/wiki/ACID) e a linguagem SQL, ambos os funcionando em todas as tabelas e os dados relacionados a seu aplicativo. Essa abordagem fornece uma maneira fácil escrever uma consulta que combina dados de várias tabelas.

No entanto, acesso a dados se torna muito mais complexo quando você move para uma arquitetura de microservices. Mas, mesmo quando as transações ACID podem ou devem ser usadas dentro de um microsserviço ou contexto limitado, os dados de cada microsserviço é privados que microsserviço e só podem ser acessados por meio de sua API microsserviço. Encapsula os dados garante que o microservices são acoplados de forma flexível e pode evoluir independentemente uma da outra. Se vários serviços estavam acessando os mesmos dados, as atualizações de esquema exigiria coordenadas atualizações para todos os serviços. Isso interrompe a autonomia de ciclo de vida de microsserviço. Mas as estruturas de dados distribuído significam que você não pode fazer uma única transação ACID em microservices. Por sua vez, isso significa que você deve usar consistência eventual quando um processo de negócios abrange vários microservices. Isso é muito mais difícil de implementar do que as junções SQL simples; da mesma forma, muitos outros recursos de banco de dados relacional não estão disponíveis em vários microservices.

Indo mais além, microservices diferentes geralmente usam diferentes *tipos* de bancos de dados. Repositório de aplicativos modernos e processo diferentes tipos de dados e um banco de dados relacional não é sempre a melhor escolha. Em alguns casos de uso, um banco de dados NoSQL, como documentos do Azure ou MongoDB pode ter um modelo de dados mais conveniente e oferecer melhor desempenho e escalabilidade do que um banco de dados SQL como o SQL Server ou banco de dados do SQL Azure. Em outros casos, um banco de dados relacional ainda é a melhor abordagem. Portanto, a aplicativos baseados em microservices geralmente usam uma mistura de bancos de dados SQL e NoSQL, que às vezes é chamada de [polyglot persistência](http://martinfowler.com/bliki/PolyglotPersistence.html) abordagem.

Uma arquitetura particionada polyglot persistente para armazenamento de dados tem muitos benefícios. Isso inclui serviços acoplados de forma flexível e melhor desempenho, escalabilidade, custos e capacidade de gerenciamento. No entanto, ela pode apresentar alguns desafios de gerenciamento de dados distribuídos, como explicaremos em "[identificar limites de modelo de domínio](#identifying-domain-model-boundaries-for-each-microservice)" mais adiante neste capítulo.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>A relação entre microservices e o padrão de contexto limitado

O conceito de microsserviço deriva o [padrão do contexto associado (BC)](http://martinfowler.com/bliki/BoundedContext.html) na [design orientado a domínio (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD lida com modelos grandes, dividindo-los em vários BCs e sendo explícito sobre seus limites. Cada BC deve ter seu próprio modelo e o banco de dados. da mesma forma, cada microsserviço possui seus dados relacionados. Além disso, cada BC geralmente tem seu próprio [idioma onipresente](http://martinfowler.com/bliki/UbiquitousLanguage.html) para ajudar a comunicação entre os desenvolvedores de software e especialistas de domínio.

Esses termos (principalmente entidades de domínio) no idioma onipresente podem ter nomes diferentes em diferentes contextos limitada, mesmo quando outro domínio entidades compartilham a mesma identidade (ou seja, a ID exclusiva que é usada para ler a entidade de armazenamento). Por exemplo, em um perfil de usuário limitado contexto, a entidade de domínio do usuário pode compartilhar identidade com a entidade de domínio do comprador no contexto de ordenação limitada.

Um microsserviço, portanto, é como um contexto limitado, mas ela também especifica que se trata de um serviço distribuído. Ele é criado como um processo separado para cada contexto associado e deve usar os protocolos distribuídos observados anteriormente, como HTTP/HTTPS, o WebSocket, ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). O padrão de contexto limitado, no entanto, não especifica se o contexto associado é um serviço distribuído ou se ele é simplesmente um limite lógico (por exemplo, um subsistema genérico) dentro de um aplicativo de implantação monolítico.

É importante destacar que a definição de um serviço para cada contexto associado é um bom lugar para começar. Mas você não precisa restringir o design para ele. Às vezes, você deve criar um contexto associado ou business microsserviço composto por vários serviços físicos. Mas, por fim, ambos os padrões — contexto limitado e microsserviço — estão intimamente relacionados.

DDD beneficia microservices obtendo os limites reais na forma de microservices distribuída. Mas ideias, como o modelo entre microservices de compartilhamento não são o que você deseja em um contexto associado.

### <a name="additional-resources"></a>Recursos adicionais

-   **Carlos Richardson. Padrão: Banco de dados por serviço**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler. BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler. PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini. Domínio estratégico controlada por Design com o mapeamento de contexto**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Anterior] (microservices-architecture.md) [Avançar] (lógico-versus-físico-architecture.md)
