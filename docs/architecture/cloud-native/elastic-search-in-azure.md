---
title: Busca elástica em aplicativos nativos da nuvem
description: Aprenda a adicionar recursos de Pesquisa Elástica a aplicativos nativos da nuvem.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141283"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Busca elástica em um aplicativo nativo da nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O Elasticsearch é um sistema de pesquisa e análise distribuído que permite recursos complexos de pesquisa em diversos tipos de dados. É de código aberto e amplamente popular. Considere como as seguintes empresas integram o Elasticsearch em sua aplicação:

- [Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) para pesquisa em texto completo e incremental (pesquisa como você digita).
- [GitHub](https://www.elastic.co/customers/github) para indexar e expor mais de 8 milhões de repositórios de código.  
- [Docker](https://www.elastic.co/customers/docker) por tornar sua biblioteca de contêineres descubável.

O Elástico search é construído em cima do motor de busca de texto completo [Apache Lucene.](https://lucene.apache.org/core/) Lucene fornece indexação e consulta de documentos de alto desempenho. Ele indexa dados com um esquema de indexação invertido – em vez de mapear páginas para palavras-chave, ele mapeia palavras-chave para páginas como um glossário no final de um livro. Lucene tem poderosos recursos de sintaxe de consulta e pode consultar dados por:

- Termo (uma palavra completa)
- Prefixo (começa com a palavra)
- Curinga (usando filtros "\*" ou "?"
- Frase (uma seqüência de texto em um documento)
- Valor booleano (pesquisas complexas combinando consultas)

Enquanto Lucene fornece encanamento de baixo nível para pesquisa, o Elasticsearch fornece o servidor que fica em cima de Lucene. O Elasticsearch adiciona funcionalidade de nível mais alto para simplificar o funcionamento do Lucene, incluindo uma API RESTful para acessar a funcionalidade de indexação e pesquisa da Lucene. Ele também fornece uma infra-estrutura distribuída capaz de escalabilidade maciça, tolerância a falhas e alta disponibilidade.

Para aplicativos nativos na nuvem maiores com requisitos complexos de pesquisa, o Elasticsearch está disponível como serviço gerenciado no Azure. O Microsoft Azure Marketplace possui modelos pré-configurados que os desenvolvedores podem usar para implantar um cluster Elasticsearch no Azure.

A partir do Microsoft Azure Marketplace, os desenvolvedores podem usar modelos pré-configurados construídos para implantar rapidamente um cluster Elasticsearch no Azure. Usando a oferta gerenciada pelo Azure, você pode implantar até 50 nós de dados, 20 nós de coordenação e três nós mestres dedicados.

## <a name="summary"></a>Resumo

Este capítulo apresentou um olhar detalhado sobre os dados em sistemas nativos da nuvem. Começamos contrastando o armazenamento de dados em aplicativos monolíticos com padrões de armazenamento de dados em sistemas nativos da nuvem. Analisamos os padrões de dados implementados em sistemas nativos da nuvem, incluindo consultas entre serviços, transações distribuídas e padrões para lidar com sistemas de alto volume. Contrastamos SQL com dados NoSQL. Analisamos as opções de armazenamento de dados disponíveis no Azure que incluem opções centradas na Microsoft e de código aberto. Finalmente, discutimos cache e Elasticsearch em um aplicativo nativo da nuvem.

### <a name="references"></a>Referências

- [Padrão CQRS (Segregação de Responsabilidade de Consulta e Comando)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Padrão de Sourcing de Eventos](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Bancos de dados RDBMSs vs. NoSQL: Visão geral](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Por que a partição RDBMS não é tolerante no teorema do CAP e por que está disponível?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Visualização materializada](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Tudo o que você realmente precisa saber sobre bancos de dados de código aberto](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Padrão de transação de compensação](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Padrão saga](https://microservices.io/patterns/data/saga.html)

- [Padrões da Saga | Como implementar transações comerciais usando microserviços](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Padrão de transação de compensação](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Ficando atrás da bola 9: Cosmos DB Níveis de consistência explicados](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Explorando os diferentes tipos de bancos de dados NoSQL Parte II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [Nos bancos de dados RDBMS, NoSQL e NewSQL. Entrevista com John Ryan](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: A comparação completa](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Quatro propriedades de bancos de dados nativos do Kubernetes](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [BarataDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch: o Guia Definitivo](http://shop.oreilly.com/product/0636920028505.do)
  
- [Introdução a Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Próximo](azure-caching.md)
>[anterior](resiliency.md) <!-- Next Chapter -->
