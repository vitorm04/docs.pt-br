---
title: Soberania de dados por microsserviço
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Soberania de dados por microsserviço
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d739cc33dec372f6bd9569c05d034dcd25be8395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577287"
---
# <a name="data-sovereignty-per-microservice"></a>Soberania de dados por microsserviço

Uma regra importante para a arquitetura de microsserviços é que cada um deles precisa ter dados e lógica de domínio. Assim como um aplicativo completo tem sua própria lógica e dados, cada microsserviço precisa tê-los em um ciclo de vida autônomo, com implantação independente por microsserviço.

Isso significa que o modelo conceitual do domínio será diferente entre subsistemas ou microsserviços. Imagine aplicativos empresariais, em que os aplicativos de gerenciamento de relacionamento com o cliente (CRM), subsistemas de compras transacionais e subsistemas de suporte ao cliente exigem atributos e dados únicos de entidade do cliente e aplicam um contexto delimitado diferente.

Esse princípio é semelhante no [DDD (design controlado por domínio)](https://en.wikipedia.org/wiki/Domain-driven_design), em que cada [Contexto Delimitado](https://martinfowler.com/bliki/BoundedContext.html) ou subsistema autônomo ou serviço precisa ter seu próprio modelo de domínio (dados, lógica e comportamento). Cada Contexto Delimitado por DDD se correlaciona a um microsserviço de negócios (um ou vários serviços). O padrão do Contexto Delimitado é aprofundado na próxima seção.

Por outro lado, a abordagem tradicional (dados monolíticos) usada em diversos aplicativos é ter um banco de dados único centralizado ou poucos bancos de dados. Geralmente, trata-se de um Banco de Dados SQL normalizado utilizado para o aplicativo inteiro e todos seus subsistemas internos, conforme mostrado na Figura 4-7.

![](./media/image7.png)

**Figura 4-7**. Comparação de soberania de dados: banco de dados monolítico x microsserviços

A abordagem de banco de dados centralizado aparenta ser mais simples inicialmente e parece permitir a reutilização de entidades em subsistemas diferentes para tornar tudo consistente. Mas a realidade é que você acaba com uma quantidade enorme de tabelas que servem para muitos subsistemas diferentes e incluem atributos e colunas que não são necessárias na maioria dos casos. É como tentar usar o mesmo mapa físico para uma caminhada em uma trilha pequena, uma viagem de carro de um dia e para aprender geografia.

Um aplicativo monolítico com um banco de dados relacional único conta com duas vantagens: [transações ACID](https://en.wikipedia.org/wiki/ACID) e a linguagem SQL, ambas em funcionamento em todas as tabelas e dados relacionados ao aplicativo. Essa abordagem é uma maneira fácil de gravar consultas que combinam dados de diversas tabelas.

No entanto, o acesso a dados se torna muito mais complexo ao migrar para uma arquitetura de microsserviços. Porém, mesmo quando as transações ACID podem ou devem ser usadas no âmbito de um microsserviço ou Contexto Delimitado, os dados de propriedade de cada microsserviço são privados e só podem ser acessados por meio de suas APIs. Encapsular os dados garante que os microsserviços sejam acoplados de forma flexível e evoluam de modo independente. Se vários serviços acessarem os mesmos dados, as atualizações de esquema exigirão atualizações coordenadas de todos os serviços. Isso interrompe a autonomia do ciclo de vida do microsserviço. Entretanto, as estruturas de dados distribuídos impedem você de realizar transações ACID nos microsserviços. Por sua vez, isso significa que é necessário utilizar consistência eventual quando um processo de negócios abrange vários microsserviços. Isso é muito mais difícil de implementar do que uma simples união SQL. Da mesma forma, vários outros recursos de banco de dados relacional não estão disponíveis em diversos microsserviços.

Além disso, microsserviços diferentes geralmente usam *tipos* diferentes de bancos de dados. Aplicativos modernos armazenam e processam tipos de dados diversificados, e um banco de dados relacional nem sempre é a melhor opção. Em alguns casos de uso, um banco de dados NoSQL como o Azure DocumentDB ou o MongoDB podem ter um modelo de dados mais conveniente e oferecer desempenho e escalabilidade melhores que um banco de dados SQL como o SQL Server ou o Banco de Dados SQL do Azure. Em outros casos, um banco de dados relacional ainda é a melhor abordagem. Portanto, aplicativos baseados em microsserviço geralmente usam uma combinação de bancos de dados SQL e NoSQL, chamada às vezes de abordagem de [persistência poliglota](https://martinfowler.com/bliki/PolyglotPersistence.html).

Uma arquitetura particionada e de persistência poliglota para armazenamento de dados traz muitos benefícios. Entre eles, serviços acoplados de forma flexível, desempenho e escalabilidade melhores e capacidade de gerenciamento. No entanto, essa arquitetura pode apresentar alguns desafios relacionados com o gerenciamento de dados distribuídos. Isso será explicado mais adiante neste capítulo, em "[Identificar os limites do modelo de domínio](#identifying-domain-model-boundaries-for-each-microservice)".

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>A relação entre os microsserviços e o padrão do Contexto Delimitado

O conceito de microsserviço tem origem no [padrão de BC (Contexto Delimitado)](https://martinfowler.com/bliki/BoundedContext.html) na [DDD (design controlado por domínio)](https://en.wikipedia.org/wiki/Domain-driven_design). A DDD aborda modelos grandes dividindo-os em vários BCs e explicitando seus limites. Cada BC precisa ter um modelo e banco de dados próprios. Da mesma forma, cada microsserviço tem seus próprios dados relacionados. Além disso, cada BC geralmente tem uma [linguagem ubíqua](https://martinfowler.com/bliki/UbiquitousLanguage.html) própria para ajudar na comunicação entre desenvolvedores de software e especialistas em domínio.

Esses termos (principalmente entidades de domínio) na linguagem ubíqua podem ter nomes diferentes em Contextos Delimitados distintos, mesmo quando entidades de domínio diferentes compartilham a mesma identidade (ou seja, a ID exclusiva utilizada para ler a entidade do armazenamento). Por exemplo, em um Contexto Delimitado de perfil de usuário, a entidade de domínio Usuário pode compartilhar a identidade com a entidade de domínio Comprador no Contexto Delimitado de pedido.

Desse modo, um microsserviço é como um Contexto Delimitado, mas também especifica seu caráter de serviço distribuído. Ele é criado como um processo separado para cada Contexto Delimitado e precisa utilizar os protocolos distribuídos mencionados anteriormente, como HTTP/HTTPS, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Entretanto, o padrão Contexto Delimitado não especifica se é um serviço distribuído ou simplesmente um limite lógico (como um subsistema genérico) em um aplicativo de implantação monolítica.

É importante salientar que definir um serviço para cada Contexto Delimitado é uma boa maneira de começar. Porém, não é preciso restringir seu design a ele. Às vezes, é necessário criar um Contexto Delimitado ou microsserviço de negócios composto de vários serviços físicos. Mas, por fim, ambos os padrões — Contexto Delimitado e microsserviço — estão intimamente relacionados.

A DDD se beneficia dos microsserviços ao obter limites reais na forma de microsserviços distribuídos. Contudo, ideias como o não compartilhamento do modelo entre os microsserviços também são desejáveis em um Contexto Delimitado.

### <a name="additional-resources"></a>Recursos adicionais

-   **Chris Richardson. Padrão: banco de dados por serviço**
    [*https://microservices.io/patterns/data/database-per-service.html*](https://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler. BoundedContext**
    [*https://martinfowler.com/bliki/BoundedContext.html*](https://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler. PolyglotPersistence**
    [*https://martinfowler.com/bliki/PolyglotPersistence.html*](https://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini. Design controlado por domínio estratégico com mapeamento de contexto**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Anterior] (microservices-architecture.md) [Próximo] (logical-versus-physical-architecture.md)
