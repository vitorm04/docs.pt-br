---
title: O que é Apache Spark?
description: Saiba mais sobre cenários de Apache Spark e Big Data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458170"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="aa322-103">O que é Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="aa322-103">What is Apache Spark?</span></span>

<span data-ttu-id="aa322-104">[Apache Spark](https://spark.apache.org/) é uma estrutura de processamento paralelo de software livre que dá suporte ao processamento na memória para melhorar o desempenho de aplicativos que analisam Big Data.</span><span class="sxs-lookup"><span data-stu-id="aa322-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="aa322-105">As soluções de Big data são projetadas para lidar com os dados muito grandes ou complexos para os bancos tradicionais de dados.</span><span class="sxs-lookup"><span data-stu-id="aa322-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="aa322-106">O Spark processa grandes quantidades de dados na memória, o que é muito mais rápido do que as alternativas baseadas em disco.</span><span class="sxs-lookup"><span data-stu-id="aa322-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="aa322-107">Cenários comuns de Big Data</span><span class="sxs-lookup"><span data-stu-id="aa322-107">Common big data scenarios</span></span>

<span data-ttu-id="aa322-108">Você pode considerar uma arquitetura de Big Data se precisar armazenar e processar grandes volumes de dados, transformar dados não estruturados ou processar dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="aa322-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="aa322-109">O Spark é um mecanismo de processamento distribuído de finalidade geral que pode ser usado para vários cenários de Big Data.</span><span class="sxs-lookup"><span data-stu-id="aa322-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="aa322-110">ETL (extração, transformação e carregamento)</span><span class="sxs-lookup"><span data-stu-id="aa322-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="aa322-111">[Extração, transformação e carregamento (ETL)](/azure/architecture/data-guide/relational-data/etl) é o processo de coleta de dados de uma ou várias fontes, modificação dos dados e movimentação dos dados para um novo armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="aa322-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="aa322-112">Há várias maneiras de transformar dados, incluindo:</span><span class="sxs-lookup"><span data-stu-id="aa322-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="aa322-113">Filtragem</span><span class="sxs-lookup"><span data-stu-id="aa322-113">Filtering</span></span>
* <span data-ttu-id="aa322-114">Classificação</span><span class="sxs-lookup"><span data-stu-id="aa322-114">Sorting</span></span>
* <span data-ttu-id="aa322-115">Agregar</span><span class="sxs-lookup"><span data-stu-id="aa322-115">Aggregating</span></span>
* <span data-ttu-id="aa322-116">Ingressando</span><span class="sxs-lookup"><span data-stu-id="aa322-116">Joining</span></span>
* <span data-ttu-id="aa322-117">Limpe</span><span class="sxs-lookup"><span data-stu-id="aa322-117">Cleaning</span></span>
* <span data-ttu-id="aa322-118">Eliminação</span><span class="sxs-lookup"><span data-stu-id="aa322-118">Deduplicating</span></span>
* <span data-ttu-id="aa322-119">Verificar</span><span class="sxs-lookup"><span data-stu-id="aa322-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="aa322-120">Processamento de fluxo de dados em tempo real</span><span class="sxs-lookup"><span data-stu-id="aa322-120">Real-time data stream processing</span></span>

<span data-ttu-id="aa322-121">Os dados em tempo real e de streaming são dados em movimento.</span><span class="sxs-lookup"><span data-stu-id="aa322-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="aa322-122">A telemetria de dispositivos IoT, weblogs e cliques são exemplos de dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="aa322-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="aa322-123">Os dados em tempo real podem ser processados para fornecer informações úteis, como análise geoespacial, monitoramento remoto e detecção de anomalias.</span><span class="sxs-lookup"><span data-stu-id="aa322-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="aa322-124">Assim como os dados relacionais, você pode filtrar, agregar e preparar dados de streaming antes de mover os dados para um coletor de saída.</span><span class="sxs-lookup"><span data-stu-id="aa322-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="aa322-125">O Apache Spark dá suporte ao [processamento de fluxo de dados em tempo real](/azure/architecture/data-guide/big-data/real-time-processing) por meio do [streaming do Spark](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="aa322-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="aa322-126">Processamento em lotes</span><span class="sxs-lookup"><span data-stu-id="aa322-126">Batch processing</span></span>

<span data-ttu-id="aa322-127">O [processamento em lotes](/azure/architecture/data-guide/big-data/batch-processing) é o processamento de Big data em repouso.</span><span class="sxs-lookup"><span data-stu-id="aa322-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="aa322-128">Você pode filtrar, agregar e preparar conjuntos de grandes volumes de trabalho usando trabalhos de longa execução em paralelo.</span><span class="sxs-lookup"><span data-stu-id="aa322-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="aa322-129">Aprendizado de máquina por meio do MLlib</span><span class="sxs-lookup"><span data-stu-id="aa322-129">Machine learning through MLlib</span></span>

<span data-ttu-id="aa322-130">O Machine Learning é usado para problemas analíticos avançados.</span><span class="sxs-lookup"><span data-stu-id="aa322-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="aa322-131">Seu computador pode usar dados existentes para prever ou prever comportamentos, resultados e tendências futuros.</span><span class="sxs-lookup"><span data-stu-id="aa322-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="aa322-132">A biblioteca de Machine Learning do Apache Spark, [MLlib](https://spark.apache.org/mllib/), contém vários algoritmos e utilitários de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="aa322-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="aa322-133">Processamento de grafo por meio de GraphX</span><span class="sxs-lookup"><span data-stu-id="aa322-133">Graph processing through GraphX</span></span>

<span data-ttu-id="aa322-134">Um grafo é uma coleção de nós conectados por bordas.</span><span class="sxs-lookup"><span data-stu-id="aa322-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="aa322-135">Você pode usar um banco de dados de grafo se você tiver dado de hierarquia ou dados com relações interconectadas.</span><span class="sxs-lookup"><span data-stu-id="aa322-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="aa322-136">Você pode processar esses dados usando a API [GraphX](https://spark.apache.org/graphx/) do Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa322-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="aa322-137">Processamento de dados estruturado e SQL com Spark SQL</span><span class="sxs-lookup"><span data-stu-id="aa322-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="aa322-138">Se você estiver trabalhando com dados estruturados (formatados), poderá usar consultas SQL em seu aplicativo Spark usando o [Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="aa322-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="aa322-139">Arquitetura de Apache Spark</span><span class="sxs-lookup"><span data-stu-id="aa322-139">Apache Spark architecture</span></span>

<span data-ttu-id="aa322-140">Apache Spark, que usa a arquitetura mestre/de trabalho, tem três componentes principais: o driver, executores e Gerenciador de cluster.</span><span class="sxs-lookup"><span data-stu-id="aa322-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Arquitetura de Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="aa322-142">Driver</span><span class="sxs-lookup"><span data-stu-id="aa322-142">Driver</span></span>

<span data-ttu-id="aa322-143">O driver consiste em seu programa, como um C# aplicativo de console e uma sessão do Spark.</span><span class="sxs-lookup"><span data-stu-id="aa322-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="aa322-144">A sessão do Spark leva seu programa e divide-o em tarefas menores que são manipuladas pelos executores.</span><span class="sxs-lookup"><span data-stu-id="aa322-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="aa322-145">Executores</span><span class="sxs-lookup"><span data-stu-id="aa322-145">Executors</span></span>

<span data-ttu-id="aa322-146">Cada executor, ou nó de trabalho, recebe uma tarefa do driver e executa essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="aa322-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="aa322-147">Os executores residem em uma entidade conhecida como um cluster.</span><span class="sxs-lookup"><span data-stu-id="aa322-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="aa322-148">Gerenciador de cluster</span><span class="sxs-lookup"><span data-stu-id="aa322-148">Cluster manager</span></span>

<span data-ttu-id="aa322-149">O Gerenciador de cluster se comunica com o driver e os executores para:</span><span class="sxs-lookup"><span data-stu-id="aa322-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="aa322-150">Gerenciar alocação de recursos</span><span class="sxs-lookup"><span data-stu-id="aa322-150">Manage resource allocation</span></span>
* <span data-ttu-id="aa322-151">Gerenciar divisão de programa</span><span class="sxs-lookup"><span data-stu-id="aa322-151">Manage program division</span></span>
* <span data-ttu-id="aa322-152">Gerenciar a execução do programa</span><span class="sxs-lookup"><span data-stu-id="aa322-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="aa322-153">Suporte ao idioma</span><span class="sxs-lookup"><span data-stu-id="aa322-153">Language support</span></span>

<span data-ttu-id="aa322-154">O Apache Spark dá suporte às seguintes linguagens de programação:</span><span class="sxs-lookup"><span data-stu-id="aa322-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="aa322-155">Scale</span><span class="sxs-lookup"><span data-stu-id="aa322-155">Scala</span></span>
* <span data-ttu-id="aa322-156">Python</span><span class="sxs-lookup"><span data-stu-id="aa322-156">Python</span></span>
* <span data-ttu-id="aa322-157">Java</span><span class="sxs-lookup"><span data-stu-id="aa322-157">Java</span></span>
* <span data-ttu-id="aa322-158">SQL</span><span class="sxs-lookup"><span data-stu-id="aa322-158">SQL</span></span>
* <span data-ttu-id="aa322-159">R</span><span class="sxs-lookup"><span data-stu-id="aa322-159">R</span></span>
* <span data-ttu-id="aa322-160">.NET</span><span class="sxs-lookup"><span data-stu-id="aa322-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="aa322-161">APIs do Spark</span><span class="sxs-lookup"><span data-stu-id="aa322-161">Spark APIs</span></span>

<span data-ttu-id="aa322-162">O Apache Spark dá suporte às seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="aa322-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="aa322-163">API de escala do Spark</span><span class="sxs-lookup"><span data-stu-id="aa322-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="aa322-164">API do Spark Java</span><span class="sxs-lookup"><span data-stu-id="aa322-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="aa322-165">API do Python do Spark</span><span class="sxs-lookup"><span data-stu-id="aa322-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="aa322-166">API do Spark R</span><span class="sxs-lookup"><span data-stu-id="aa322-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="aa322-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), funções internas</span><span class="sxs-lookup"><span data-stu-id="aa322-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="aa322-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="aa322-168">Next steps</span></span>

<span data-ttu-id="aa322-169">Saiba como você pode usar Apache Spark em seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="aa322-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="aa322-170">Com o .NET para Apache Spark, os desenvolvedores com experiência .NET e lógica de negócios podem escrever C# Big data F#consultas no e no.</span><span class="sxs-lookup"><span data-stu-id="aa322-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="aa322-171">O que é o .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="aa322-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
