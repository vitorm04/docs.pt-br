---
title: Elasticsearch em aplicativos nativos de nuvem
description: Saiba mais sobre como adicionar recursos de pesquisa elástica a aplicativos nativos de nuvem.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 70d1925d6b8c7bbe515ee4f178513dc61212ebce
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271796"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="6454a-103">Elasticsearch em um aplicativo nativo de nuvem</span><span class="sxs-lookup"><span data-stu-id="6454a-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="6454a-104">O Elasticsearch é um sistema de pesquisa e análise distribuído que permite recursos de pesquisa complexos em diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="6454a-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="6454a-105">É de código-fonte aberto e amplamente popular.</span><span class="sxs-lookup"><span data-stu-id="6454a-105">It's open source and widely popular.</span></span> <span data-ttu-id="6454a-106">Considere como as seguintes empresas integram o Elasticsearch em seus aplicativos:</span><span class="sxs-lookup"><span data-stu-id="6454a-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="6454a-107">[Wikipédia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) para pesquisa de texto completo e incremental (Pesquisar ao digitar).</span><span class="sxs-lookup"><span data-stu-id="6454a-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="6454a-108">[GitHub](https://www.elastic.co/customers/github) para indexar e expor mais de 8 milhões repositórios de código.</span><span class="sxs-lookup"><span data-stu-id="6454a-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="6454a-109">[Docker](https://www.elastic.co/customers/docker) para tornar sua biblioteca de contêineres detectável.</span><span class="sxs-lookup"><span data-stu-id="6454a-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="6454a-110">O Elasticsearch é criado sobre o mecanismo de pesquisa de texto completo do [Apache Lucene](https://lucene.apache.org/core/) .</span><span class="sxs-lookup"><span data-stu-id="6454a-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="6454a-111">O Lucene fornece indexação e consulta de documentos de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="6454a-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="6454a-112">Ele indexa dados com um esquema de indexação invertido – em vez de mapear páginas para palavras-chave, ele mapeia palavras-chave para páginas assim como um glossário no final de um livro.</span><span class="sxs-lookup"><span data-stu-id="6454a-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="6454a-113">O Lucene tem recursos de sintaxe de consulta avançados e pode consultar dados por:</span><span class="sxs-lookup"><span data-stu-id="6454a-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="6454a-114">Termo (uma palavra completa)</span><span class="sxs-lookup"><span data-stu-id="6454a-114">Term (a full word)</span></span>
- <span data-ttu-id="6454a-115">Prefixo (começa com o Word)</span><span class="sxs-lookup"><span data-stu-id="6454a-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="6454a-116">Curinga (usando os \* filtros "" ou "?")</span><span class="sxs-lookup"><span data-stu-id="6454a-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="6454a-117">Frase (uma sequência de texto em um documento)</span><span class="sxs-lookup"><span data-stu-id="6454a-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="6454a-118">Valor booliano (pesquisas complexas combinando consultas)</span><span class="sxs-lookup"><span data-stu-id="6454a-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="6454a-119">Embora o Lucene forneça um direcionamento de baixo nível para pesquisa, o Elasticsearch fornece o servidor que se encontra na parte superior do Lucene.</span><span class="sxs-lookup"><span data-stu-id="6454a-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="6454a-120">O Elasticsearch adiciona funcionalidade de nível superior para simplificar o funcionamento do Lucene, incluindo uma API RESTful para acessar a funcionalidade de indexação e pesquisa do Lucene.</span><span class="sxs-lookup"><span data-stu-id="6454a-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="6454a-121">Ele também fornece uma infraestrutura distribuída capaz de grande escalabilidade, tolerância a falhas e alta disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="6454a-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="6454a-122">Para aplicativos nativos de nuvem maiores com requisitos de pesquisa complexos, o Elasticsearch está disponível como serviço gerenciado no Azure.</span><span class="sxs-lookup"><span data-stu-id="6454a-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="6454a-123">O Microsoft Azure Marketplace apresenta modelos pré-configurados que os desenvolvedores podem usar para implantar um cluster Elasticsearch no Azure.</span><span class="sxs-lookup"><span data-stu-id="6454a-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="6454a-124">No Microsoft Azure Marketplace, os desenvolvedores podem usar modelos pré-configurados criados para implantar rapidamente um cluster Elasticsearch no Azure.</span><span class="sxs-lookup"><span data-stu-id="6454a-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="6454a-125">Usando a oferta gerenciada pelo Azure, você pode implantar até 50 nós de dados, 20 nós coordenados e três nós mestres dedicados.</span><span class="sxs-lookup"><span data-stu-id="6454a-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="6454a-126">Resumo</span><span class="sxs-lookup"><span data-stu-id="6454a-126">Summary</span></span>

<span data-ttu-id="6454a-127">Este capítulo apresentou uma visão detalhada dos dados em sistemas nativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="6454a-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="6454a-128">Começamos por contrastar o armazenamento de dados em aplicativos monolíticos com padrões de armazenamento de dados em sistemas nativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="6454a-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="6454a-129">Examinamos os padrões de dados implementados em sistemas nativos de nuvem, incluindo consultas entre serviços, transações distribuídas e padrões para lidar com sistemas de alto volume.</span><span class="sxs-lookup"><span data-stu-id="6454a-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="6454a-130">Nós contrastamos o SQL com dados NoSQL.</span><span class="sxs-lookup"><span data-stu-id="6454a-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="6454a-131">Examinamos as opções de armazenamento de dados disponíveis no Azure que incluem opções centradas na Microsoft e em código aberto.</span><span class="sxs-lookup"><span data-stu-id="6454a-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="6454a-132">Por fim, discutimos Caching e Elasticsearch em um aplicativo nativo de nuvem.</span><span class="sxs-lookup"><span data-stu-id="6454a-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="6454a-133">Referências</span><span class="sxs-lookup"><span data-stu-id="6454a-133">References</span></span>

- [<span data-ttu-id="6454a-134">Padrão CQRS (Segregação de Responsabilidade de Consulta e Comando)</span><span class="sxs-lookup"><span data-stu-id="6454a-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="6454a-135">Padrão de fornecimento do evento</span><span class="sxs-lookup"><span data-stu-id="6454a-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="6454a-136">Por que a partição RDBMS não é tolerante a teorema em CAP e por que ela está disponível?</span><span class="sxs-lookup"><span data-stu-id="6454a-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="6454a-137">Exibição Materializada</span><span class="sxs-lookup"><span data-stu-id="6454a-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="6454a-138">Tudo o que você realmente precisa saber sobre bancos de dados de código-fonte aberto</span><span class="sxs-lookup"><span data-stu-id="6454a-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="6454a-139">Padrão de transação de compensação</span><span class="sxs-lookup"><span data-stu-id="6454a-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="6454a-140">Padrão saga</span><span class="sxs-lookup"><span data-stu-id="6454a-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="6454a-141">Padrões de Saga | Como implementar transações de negócios usando microserviços</span><span class="sxs-lookup"><span data-stu-id="6454a-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="6454a-142">Padrão de transação de compensação</span><span class="sxs-lookup"><span data-stu-id="6454a-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="6454a-143">Voltando para o 9-Ball: níveis de consistência de Cosmos DB explicados</span><span class="sxs-lookup"><span data-stu-id="6454a-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="6454a-144">Explorando os diferentes tipos de bancos de dados NoSQL parte II</span><span class="sxs-lookup"><span data-stu-id="6454a-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="6454a-145">Nos bancos de dados RDBMS, NoSQL e NewSQL. Entrevista com John Ryan</span><span class="sxs-lookup"><span data-stu-id="6454a-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="6454a-146">SQL vs NoSQL vs NewSQL: a comparação completa</span><span class="sxs-lookup"><span data-stu-id="6454a-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="6454a-147">DASH: quatro propriedades de bancos de dados kubernetes-Native</span><span class="sxs-lookup"><span data-stu-id="6454a-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="6454a-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="6454a-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="6454a-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="6454a-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="6454a-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="6454a-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="6454a-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="6454a-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="6454a-152">Elasticsearch: o Guia Definitivo</span><span class="sxs-lookup"><span data-stu-id="6454a-152">Elasticsearch: The Definitive Guide</span></span>](https://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="6454a-153">Introdução ao Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="6454a-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="6454a-154">[Anterior](azure-caching.md) 
> [Avançar](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="6454a-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
