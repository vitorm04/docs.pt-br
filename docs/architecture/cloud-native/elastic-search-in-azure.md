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
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="c85c1-103">Busca elástica em um aplicativo nativo da nuvem</span><span class="sxs-lookup"><span data-stu-id="c85c1-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c85c1-104">O Elasticsearch é um sistema de pesquisa e análise distribuído que permite recursos complexos de pesquisa em diversos tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="c85c1-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="c85c1-105">É de código aberto e amplamente popular.</span><span class="sxs-lookup"><span data-stu-id="c85c1-105">It's open source and widely popular.</span></span> <span data-ttu-id="c85c1-106">Considere como as seguintes empresas integram o Elasticsearch em sua aplicação:</span><span class="sxs-lookup"><span data-stu-id="c85c1-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="c85c1-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) para pesquisa em texto completo e incremental (pesquisa como você digita).</span><span class="sxs-lookup"><span data-stu-id="c85c1-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="c85c1-108">[GitHub](https://www.elastic.co/customers/github) para indexar e expor mais de 8 milhões de repositórios de código.</span><span class="sxs-lookup"><span data-stu-id="c85c1-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="c85c1-109">[Docker](https://www.elastic.co/customers/docker) por tornar sua biblioteca de contêineres descubável.</span><span class="sxs-lookup"><span data-stu-id="c85c1-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="c85c1-110">O Elástico search é construído em cima do motor de busca de texto completo [Apache Lucene.](https://lucene.apache.org/core/)</span><span class="sxs-lookup"><span data-stu-id="c85c1-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="c85c1-111">Lucene fornece indexação e consulta de documentos de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="c85c1-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="c85c1-112">Ele indexa dados com um esquema de indexação invertido – em vez de mapear páginas para palavras-chave, ele mapeia palavras-chave para páginas como um glossário no final de um livro.</span><span class="sxs-lookup"><span data-stu-id="c85c1-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="c85c1-113">Lucene tem poderosos recursos de sintaxe de consulta e pode consultar dados por:</span><span class="sxs-lookup"><span data-stu-id="c85c1-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="c85c1-114">Termo (uma palavra completa)</span><span class="sxs-lookup"><span data-stu-id="c85c1-114">Term (a full word)</span></span>
- <span data-ttu-id="c85c1-115">Prefixo (começa com a palavra)</span><span class="sxs-lookup"><span data-stu-id="c85c1-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="c85c1-116">Curinga (usando filtros "\*" ou "?"</span><span class="sxs-lookup"><span data-stu-id="c85c1-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="c85c1-117">Frase (uma seqüência de texto em um documento)</span><span class="sxs-lookup"><span data-stu-id="c85c1-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="c85c1-118">Valor booleano (pesquisas complexas combinando consultas)</span><span class="sxs-lookup"><span data-stu-id="c85c1-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="c85c1-119">Enquanto Lucene fornece encanamento de baixo nível para pesquisa, o Elasticsearch fornece o servidor que fica em cima de Lucene.</span><span class="sxs-lookup"><span data-stu-id="c85c1-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="c85c1-120">O Elasticsearch adiciona funcionalidade de nível mais alto para simplificar o funcionamento do Lucene, incluindo uma API RESTful para acessar a funcionalidade de indexação e pesquisa da Lucene.</span><span class="sxs-lookup"><span data-stu-id="c85c1-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene’s indexing and searching functionality.</span></span> <span data-ttu-id="c85c1-121">Ele também fornece uma infra-estrutura distribuída capaz de escalabilidade maciça, tolerância a falhas e alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="c85c1-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="c85c1-122">Para aplicativos nativos na nuvem maiores com requisitos complexos de pesquisa, o Elasticsearch está disponível como serviço gerenciado no Azure.</span><span class="sxs-lookup"><span data-stu-id="c85c1-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="c85c1-123">O Microsoft Azure Marketplace possui modelos pré-configurados que os desenvolvedores podem usar para implantar um cluster Elasticsearch no Azure.</span><span class="sxs-lookup"><span data-stu-id="c85c1-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="c85c1-124">A partir do Microsoft Azure Marketplace, os desenvolvedores podem usar modelos pré-configurados construídos para implantar rapidamente um cluster Elasticsearch no Azure.</span><span class="sxs-lookup"><span data-stu-id="c85c1-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="c85c1-125">Usando a oferta gerenciada pelo Azure, você pode implantar até 50 nós de dados, 20 nós de coordenação e três nós mestres dedicados.</span><span class="sxs-lookup"><span data-stu-id="c85c1-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="c85c1-126">Resumo</span><span class="sxs-lookup"><span data-stu-id="c85c1-126">Summary</span></span>

<span data-ttu-id="c85c1-127">Este capítulo apresentou um olhar detalhado sobre os dados em sistemas nativos da nuvem.</span><span class="sxs-lookup"><span data-stu-id="c85c1-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="c85c1-128">Começamos contrastando o armazenamento de dados em aplicativos monolíticos com padrões de armazenamento de dados em sistemas nativos da nuvem.</span><span class="sxs-lookup"><span data-stu-id="c85c1-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="c85c1-129">Analisamos os padrões de dados implementados em sistemas nativos da nuvem, incluindo consultas entre serviços, transações distribuídas e padrões para lidar com sistemas de alto volume.</span><span class="sxs-lookup"><span data-stu-id="c85c1-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="c85c1-130">Contrastamos SQL com dados NoSQL.</span><span class="sxs-lookup"><span data-stu-id="c85c1-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="c85c1-131">Analisamos as opções de armazenamento de dados disponíveis no Azure que incluem opções centradas na Microsoft e de código aberto.</span><span class="sxs-lookup"><span data-stu-id="c85c1-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="c85c1-132">Finalmente, discutimos cache e Elasticsearch em um aplicativo nativo da nuvem.</span><span class="sxs-lookup"><span data-stu-id="c85c1-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="c85c1-133">Referências</span><span class="sxs-lookup"><span data-stu-id="c85c1-133">References</span></span>

- [<span data-ttu-id="c85c1-134">Padrão CQRS (Segregação de Responsabilidade de Consulta e Comando)</span><span class="sxs-lookup"><span data-stu-id="c85c1-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="c85c1-135">Padrão de Sourcing de Eventos</span><span class="sxs-lookup"><span data-stu-id="c85c1-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="c85c1-136">Bancos de dados RDBMSs vs. NoSQL: Visão geral</span><span class="sxs-lookup"><span data-stu-id="c85c1-136">RDBMSs vs. NoSQL Databases: Overview</span></span>](https://maxivak.com/rdbms-vs-nosql-databases/)

- [<span data-ttu-id="c85c1-137">Por que a partição RDBMS não é tolerante no teorema do CAP e por que está disponível?</span><span class="sxs-lookup"><span data-stu-id="c85c1-137">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="c85c1-138">Visualização materializada</span><span class="sxs-lookup"><span data-stu-id="c85c1-138">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="c85c1-139">Tudo o que você realmente precisa saber sobre bancos de dados de código aberto</span><span class="sxs-lookup"><span data-stu-id="c85c1-139">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="c85c1-140">Padrão de transação de compensação</span><span class="sxs-lookup"><span data-stu-id="c85c1-140">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="c85c1-141">Padrão saga</span><span class="sxs-lookup"><span data-stu-id="c85c1-141">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="c85c1-142">Padrões da Saga | Como implementar transações comerciais usando microserviços</span><span class="sxs-lookup"><span data-stu-id="c85c1-142">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="c85c1-143">Padrão de transação de compensação</span><span class="sxs-lookup"><span data-stu-id="c85c1-143">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="c85c1-144">Ficando atrás da bola 9: Cosmos DB Níveis de consistência explicados</span><span class="sxs-lookup"><span data-stu-id="c85c1-144">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="c85c1-145">Explorando os diferentes tipos de bancos de dados NoSQL Parte II</span><span class="sxs-lookup"><span data-stu-id="c85c1-145">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="c85c1-146">Nos bancos de dados RDBMS, NoSQL e NewSQL. Entrevista com John Ryan</span><span class="sxs-lookup"><span data-stu-id="c85c1-146">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="c85c1-147">SQL vs NoSQL vs NewSQL: A comparação completa</span><span class="sxs-lookup"><span data-stu-id="c85c1-147">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="c85c1-148">DASH: Quatro propriedades de bancos de dados nativos do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c85c1-148">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="c85c1-149">BarataDB</span><span class="sxs-lookup"><span data-stu-id="c85c1-149">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="c85c1-150">TiDB</span><span class="sxs-lookup"><span data-stu-id="c85c1-150">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="c85c1-151">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="c85c1-151">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="c85c1-152">Vitess</span><span class="sxs-lookup"><span data-stu-id="c85c1-152">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="c85c1-153">Elasticsearch: o Guia Definitivo</span><span class="sxs-lookup"><span data-stu-id="c85c1-153">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="c85c1-154">Introdução a Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="c85c1-154">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="c85c1-155">[Próximo](azure-caching.md)
>[anterior](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="c85c1-155">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
