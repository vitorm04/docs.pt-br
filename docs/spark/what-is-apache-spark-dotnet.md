---
title: O que é o .NET para o Apache Spark?
description: Saiba mais sobre o .NET para Apache Spark, uma estrutura de análise de Big Data gratuita de software livre e multiplataforma que usa o Spark em qualquer lugar em que você escreva o código .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458195"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="678ad-103">O que é o .NET para o Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="678ad-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="678ad-104">[Apache Spark](what-is-spark.md) é um mecanismo de processamento distribuído de uso geral para análise sobre grandes conjuntos de dados - tipicamente terabytes ou petabytes de dados.</span><span class="sxs-lookup"><span data-stu-id="678ad-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="678ad-105">Com o .NET para Apache Spark, o suporte gratuito, de código aberto e multiplataforma .NET para a popular estrutura de análise de big data de código aberto, agora você pode adicionar o poder do Apache Spark aos seus aplicativos de big data usando idiomas que você já conhece.</span><span class="sxs-lookup"><span data-stu-id="678ad-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="678ad-106">Por que escolher .NET para Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="678ad-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="678ad-107">.NET para Apache Spark capacita desenvolvedores com experiência .NET ou bases de código para participar no mundo da análise de big data.</span><span class="sxs-lookup"><span data-stu-id="678ad-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="678ad-108">.NET para Apache Spark fornece APIs de alto desempenho para usar Spark de C# e F#.</span><span class="sxs-lookup"><span data-stu-id="678ad-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="678ad-109">Com C# e F#, você pode acessar:</span><span class="sxs-lookup"><span data-stu-id="678ad-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="678ad-110">DataFrame e SparkSQL para trabalhar com dados estruturados.</span><span class="sxs-lookup"><span data-stu-id="678ad-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="678ad-111">Streaming estruturado do Spark para trabalhar usando dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="678ad-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="678ad-112">Spark SQL para escrever consultas com sintaxe SQL.</span><span class="sxs-lookup"><span data-stu-id="678ad-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="678ad-113">Integração de aprendizado de máquina para treinamento e previsão mais rápidos (ou seja, use .NET para Apache Spark ao lado [de ML.NET](https://dot.net/ml)).</span><span class="sxs-lookup"><span data-stu-id="678ad-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="678ad-114">O .NET para Apache Spark está em conformidade com o .NET Standard, uma especificação formal das APIs do .NET comuns em implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="678ad-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="678ad-115">Isso significa que você pode usar o .NET para Apache Spark em qualquer lugar em que você escreva código .NET, permitindo que você reutilize todo o conhecimento, as habilidades, o código e as bibliotecas que você já tem como um desenvolvedor do .NET.</span><span class="sxs-lookup"><span data-stu-id="678ad-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="678ad-116">O .NET para Apache Spark é executado no Windows, no Linux e no macOS usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="678ad-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="678ad-117">Ele também é executado no Windows usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="678ad-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="678ad-118">Você pode implantar seus aplicativos em todos os principais provedores de nuvem, incluindo Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks e Databricks na AWS.</span><span class="sxs-lookup"><span data-stu-id="678ad-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="678ad-119">.NET para arquitetura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="678ad-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="678ad-120">A vinculação da língua C#/ F# ao Spark está escrita em uma nova camada de interop Spark que oferece extensibilidade mais fácil.</span><span class="sxs-lookup"><span data-stu-id="678ad-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="678ad-121">Esta nova camada de Interop Spark foi escrita usando as melhores práticas para extensão de linguagem e otimiza para interop e desempenho.</span><span class="sxs-lookup"><span data-stu-id="678ad-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="678ad-122">A longo prazo, essa extensibilidade pode ser usada para adicionar suporte para outras línguas em Spark.</span><span class="sxs-lookup"><span data-stu-id="678ad-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="678ad-123">![.NET para arquitetura Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="678ad-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="678ad-124">Você pode aprender sobre o suporte interop para extensões de linguagem Spark a partir da [proposta](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="678ad-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="678ad-125">.NET para o desempenho do Apache Spark</span><span class="sxs-lookup"><span data-stu-id="678ad-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="678ad-126">Quando comparado com Python e Scala usando o [benchmark TPC-H,](http://www.tpc.org/tpch/)o .NET para Apache Spark tem um bom desempenho na maioria dos casos e é 2x mais rápido que o Python quando o desempenho da função definido pelo usuário é crítico.</span><span class="sxs-lookup"><span data-stu-id="678ad-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="678ad-127">Há um esforço contínuo para melhorar e avaliar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="678ad-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="678ad-128">Para fazer seu próprio benchmarking, consulte os benchmarks disponíveis no [.NET para Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="678ad-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="678ad-129">.NET para Apache Spark roadmap</span><span class="sxs-lookup"><span data-stu-id="678ad-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="678ad-130">Conheça os planos de curto e longo prazo do .NET oficial [para o roteiro do Apache Spark.](https://github.com/dotnet/spark/blob/master/ROADMAP.md)</span><span class="sxs-lookup"><span data-stu-id="678ad-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="678ad-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="678ad-131">.NET Foundation</span></span>

<span data-ttu-id="678ad-132">O projeto .NET para Apache Spark faz parte do [.NET Foundation.](https://www.dotnetfoundation.org/)</span><span class="sxs-lookup"><span data-stu-id="678ad-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="678ad-133">Contribuições</span><span class="sxs-lookup"><span data-stu-id="678ad-133">Contributions</span></span>

<span data-ttu-id="678ad-134">A equipe do .NET para Apache Spark incentiva contribuições, tanto em problemas do GitHub quanto em solicitações de pull.</span><span class="sxs-lookup"><span data-stu-id="678ad-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="678ad-135">Primeiro, procure um [problema existente](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="678ad-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="678ad-136">Se você não conseguir encontrar um problema existente, [abra um novo problema](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="678ad-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="678ad-137">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="678ad-137">Next steps</span></span>

<span data-ttu-id="678ad-138">Experimente .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="678ad-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="678ad-139">Tutorial: Comece com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="678ad-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
