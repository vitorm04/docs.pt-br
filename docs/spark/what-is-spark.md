---
title: O que é o Apache Spark?
description: Conheça o Apache Spark e os cenários de big data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458170"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="5a04a-103">O que é o Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="5a04a-103">What is Apache Spark?</span></span>

<span data-ttu-id="5a04a-104">[O Apache Spark](https://spark.apache.org/) é uma estrutura de processamento paralelo de código aberto que suporta processamento na memória para aumentar o desempenho de aplicativos que analisam big data.</span><span class="sxs-lookup"><span data-stu-id="5a04a-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="5a04a-105">As soluções de big data são projetadas para lidar com dados muito grandes ou complexos para bancos de dados tradicionais.</span><span class="sxs-lookup"><span data-stu-id="5a04a-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="5a04a-106">O Spark processa grandes quantidades de dados na memória, o que é muito mais rápido do que as alternativas baseadas em disco.</span><span class="sxs-lookup"><span data-stu-id="5a04a-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="5a04a-107">Cenários comuns de big data</span><span class="sxs-lookup"><span data-stu-id="5a04a-107">Common big data scenarios</span></span>

<span data-ttu-id="5a04a-108">Você pode considerar uma arquitetura de big data se precisar armazenar e processar grandes volumes de dados, transformar dados não estruturados ou processar dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="5a04a-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="5a04a-109">Spark é um mecanismo de processamento distribuído de uso geral que pode ser usado para vários cenários de big data.</span><span class="sxs-lookup"><span data-stu-id="5a04a-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="5a04a-110">ETL (extrair, transformar e carregar)</span><span class="sxs-lookup"><span data-stu-id="5a04a-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="5a04a-111">[Extrair, transformar e carregar (ETL)](/azure/architecture/data-guide/relational-data/etl) é o processo de coleta de dados de uma ou várias fontes, modificando os dados e movendo os dados para um novo armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="5a04a-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="5a04a-112">Existem várias maneiras de transformar dados, incluindo:</span><span class="sxs-lookup"><span data-stu-id="5a04a-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="5a04a-113">Filtragem</span><span class="sxs-lookup"><span data-stu-id="5a04a-113">Filtering</span></span>
* <span data-ttu-id="5a04a-114">Classificação</span><span class="sxs-lookup"><span data-stu-id="5a04a-114">Sorting</span></span>
* <span data-ttu-id="5a04a-115">Agregar</span><span class="sxs-lookup"><span data-stu-id="5a04a-115">Aggregating</span></span>
* <span data-ttu-id="5a04a-116">Adição</span><span class="sxs-lookup"><span data-stu-id="5a04a-116">Joining</span></span>
* <span data-ttu-id="5a04a-117">Limpeza</span><span class="sxs-lookup"><span data-stu-id="5a04a-117">Cleaning</span></span>
* <span data-ttu-id="5a04a-118">Deduplicação</span><span class="sxs-lookup"><span data-stu-id="5a04a-118">Deduplicating</span></span>
* <span data-ttu-id="5a04a-119">Validando</span><span class="sxs-lookup"><span data-stu-id="5a04a-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="5a04a-120">Processamento de fluxo de dados em tempo real</span><span class="sxs-lookup"><span data-stu-id="5a04a-120">Real-time data stream processing</span></span>

<span data-ttu-id="5a04a-121">Streaming, ou em tempo real, dados são dados em movimento.</span><span class="sxs-lookup"><span data-stu-id="5a04a-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="5a04a-122">Telemetria de dispositivos IoT, weblogs e clickstreams são todos exemplos de dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="5a04a-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="5a04a-123">Os dados em tempo real podem ser processados para fornecer informações úteis, como análise geoespacial, monitoramento remoto e detecção de anomalias.</span><span class="sxs-lookup"><span data-stu-id="5a04a-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="5a04a-124">Assim como os dados relacionais, você pode filtrar, agregar e preparar dados de streaming antes de mover os dados para um dissipador de saída.</span><span class="sxs-lookup"><span data-stu-id="5a04a-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="5a04a-125">O Apache Spark suporta [o processamento de fluxo de dados em tempo real](/azure/architecture/data-guide/big-data/real-time-processing) através do Spark [Streaming](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="5a04a-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="5a04a-126">Processamento em lotes</span><span class="sxs-lookup"><span data-stu-id="5a04a-126">Batch processing</span></span>

<span data-ttu-id="5a04a-127">[O processamento em lote](/azure/architecture/data-guide/big-data/batch-processing) é o processamento de big data em repouso.</span><span class="sxs-lookup"><span data-stu-id="5a04a-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="5a04a-128">Você pode filtrar, agregar e preparar conjuntos de dados muito grandes usando trabalhos de longa duração em paralelo.</span><span class="sxs-lookup"><span data-stu-id="5a04a-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="5a04a-129">Aprendizado de máquina através do MLlib</span><span class="sxs-lookup"><span data-stu-id="5a04a-129">Machine learning through MLlib</span></span>

<span data-ttu-id="5a04a-130">O aprendizado de máquina é usado para problemas analíticos avançados.</span><span class="sxs-lookup"><span data-stu-id="5a04a-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="5a04a-131">Seu computador pode usar dados existentes para prever ou prever comportamentos futuros, resultados e tendências.</span><span class="sxs-lookup"><span data-stu-id="5a04a-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="5a04a-132">A biblioteca de aprendizado de máquina da Apache Spark, [MLlib,](https://spark.apache.org/mllib/)contém vários algoritmos e utilitários de aprendizagem de máquina.</span><span class="sxs-lookup"><span data-stu-id="5a04a-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="5a04a-133">Processamento de gráficos através do GraphX</span><span class="sxs-lookup"><span data-stu-id="5a04a-133">Graph processing through GraphX</span></span>

<span data-ttu-id="5a04a-134">Um gráfico é uma coleção de nódulos conectados por bordas.</span><span class="sxs-lookup"><span data-stu-id="5a04a-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="5a04a-135">Você pode usar um banco de dados gráfico se tiver dados hierárquicos ou dados com relacionamentos interconectados.</span><span class="sxs-lookup"><span data-stu-id="5a04a-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="5a04a-136">Você pode processar esses dados usando a API [GraphX](https://spark.apache.org/graphx/) do Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5a04a-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="5a04a-137">SQL e processamento de dados estruturados com Spark SQL</span><span class="sxs-lookup"><span data-stu-id="5a04a-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="5a04a-138">Se você estiver trabalhando com dados estruturados (formatados), você pode usar consultas SQL em seu aplicativo Spark usando [Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="5a04a-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="5a04a-139">Arquitetura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a04a-139">Apache Spark architecture</span></span>

<span data-ttu-id="5a04a-140">O Apache Spark, que usa a arquitetura master/worker, tem três componentes principais: o driver, os executores e o gerenciador de cluster.</span><span class="sxs-lookup"><span data-stu-id="5a04a-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Arquitetura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="5a04a-142">Driver</span><span class="sxs-lookup"><span data-stu-id="5a04a-142">Driver</span></span>

<span data-ttu-id="5a04a-143">O driver consiste em seu programa, como um aplicativo de console C# e uma sessão Spark.</span><span class="sxs-lookup"><span data-stu-id="5a04a-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="5a04a-144">A sessão Spark pega seu programa e o divide em tarefas menores que são tratadas pelos executores.</span><span class="sxs-lookup"><span data-stu-id="5a04a-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="5a04a-145">Executores</span><span class="sxs-lookup"><span data-stu-id="5a04a-145">Executors</span></span>

<span data-ttu-id="5a04a-146">Cada executor, ou nó do trabalhador, recebe uma tarefa do motorista e executa essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="5a04a-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="5a04a-147">Os executores residem em uma entidade conhecida como cluster.</span><span class="sxs-lookup"><span data-stu-id="5a04a-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="5a04a-148">Gerente de cluster</span><span class="sxs-lookup"><span data-stu-id="5a04a-148">Cluster manager</span></span>

<span data-ttu-id="5a04a-149">O gerenciador de cluster comunica-se com o driver e os executores para:</span><span class="sxs-lookup"><span data-stu-id="5a04a-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="5a04a-150">Gerenciar a alocação de recursos</span><span class="sxs-lookup"><span data-stu-id="5a04a-150">Manage resource allocation</span></span>
* <span data-ttu-id="5a04a-151">Gerenciar divisão de programas</span><span class="sxs-lookup"><span data-stu-id="5a04a-151">Manage program division</span></span>
* <span data-ttu-id="5a04a-152">Gerenciar a execução do programa</span><span class="sxs-lookup"><span data-stu-id="5a04a-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="5a04a-153">Suporte ao idioma</span><span class="sxs-lookup"><span data-stu-id="5a04a-153">Language support</span></span>

<span data-ttu-id="5a04a-154">Apache Spark suporta as seguintes linguagens de programação:</span><span class="sxs-lookup"><span data-stu-id="5a04a-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="5a04a-155">Scala</span><span class="sxs-lookup"><span data-stu-id="5a04a-155">Scala</span></span>
* <span data-ttu-id="5a04a-156">Python</span><span class="sxs-lookup"><span data-stu-id="5a04a-156">Python</span></span>
* <span data-ttu-id="5a04a-157">Java</span><span class="sxs-lookup"><span data-stu-id="5a04a-157">Java</span></span>
* <span data-ttu-id="5a04a-158">SQL</span><span class="sxs-lookup"><span data-stu-id="5a04a-158">SQL</span></span>
* <span data-ttu-id="5a04a-159">R</span><span class="sxs-lookup"><span data-stu-id="5a04a-159">R</span></span>
* <span data-ttu-id="5a04a-160">.NET</span><span class="sxs-lookup"><span data-stu-id="5a04a-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="5a04a-161">APIs de faísca</span><span class="sxs-lookup"><span data-stu-id="5a04a-161">Spark APIs</span></span>

<span data-ttu-id="5a04a-162">O Apache Spark suporta as seguintes APIs:</span><span class="sxs-lookup"><span data-stu-id="5a04a-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="5a04a-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="5a04a-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="5a04a-164">Spark Java API</span><span class="sxs-lookup"><span data-stu-id="5a04a-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="5a04a-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="5a04a-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="5a04a-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="5a04a-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="5a04a-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), funções incorporadas</span><span class="sxs-lookup"><span data-stu-id="5a04a-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="5a04a-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5a04a-168">Next steps</span></span>

<span data-ttu-id="5a04a-169">Saiba como usar o Apache Spark no seu aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="5a04a-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="5a04a-170">Com .NET para Apache Spark, desenvolvedores com experiência .NET e lógica de negócios podem escrever consultas de big data em C# e F#.</span><span class="sxs-lookup"><span data-stu-id="5a04a-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5a04a-171">O que é .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a04a-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
