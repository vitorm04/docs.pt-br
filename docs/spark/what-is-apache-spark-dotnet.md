---
title: O que é o .NET para o Apache Spark?
description: Saiba mais sobre o .NET para Apache Spark, uma estrutura de análise de Big Data gratuita de software livre e multiplataforma que usa o Spark em qualquer lugar em que você escreva o código .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: c31b50a20ac08bcde077e1e85ee915435a99fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395866"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="9fd95-103">O que é o .NET para o Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="9fd95-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="9fd95-104">[Apache Spark](what-is-spark.md) é um mecanismo de processamento distribuído de finalidade geral para análise em conjuntos de dados grandes – normalmente terabytes ou petabytes de dados.</span><span class="sxs-lookup"><span data-stu-id="9fd95-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="9fd95-105">Com o .NET para Apache Spark, o suporte .NET gratuito, de software livre e multiplataforma para a estrutura de análise de Big Data de código aberto popular, agora você pode adicionar o poder de Apache Spark aos seus aplicativos de Big Data usando as linguagens que você já conhece.</span><span class="sxs-lookup"><span data-stu-id="9fd95-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="9fd95-106">Por que escolher o .NET para Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="9fd95-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="9fd95-107">O .NET para Apache Spark capacita os desenvolvedores com a experiência .NET ou com bases de código para participar do mundo da análise de Big Data.</span><span class="sxs-lookup"><span data-stu-id="9fd95-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="9fd95-108">O .NET para Apache Spark fornece APIs de alto desempenho para usar C# o F#Spark de e.</span><span class="sxs-lookup"><span data-stu-id="9fd95-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="9fd95-109">Com C# e F#, você pode acessar:</span><span class="sxs-lookup"><span data-stu-id="9fd95-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="9fd95-110">Dataframe e SparkSQL para trabalhar com dados estruturados</span><span class="sxs-lookup"><span data-stu-id="9fd95-110">DataFrame and SparkSQL for working with structured data</span></span>
* <span data-ttu-id="9fd95-111">Streaming estruturado do Spark para trabalhar com dados de streaming</span><span class="sxs-lookup"><span data-stu-id="9fd95-111">Spark Structured Streaming for working with streaming data</span></span>
* <span data-ttu-id="9fd95-112">Spark SQL para gravar consultas com sintaxe SQL</span><span class="sxs-lookup"><span data-stu-id="9fd95-112">Spark SQL for writing queries with SQL syntax</span></span>
* <span data-ttu-id="9fd95-113">Integração do Machine Learning para treinamento e previsão mais rápidos (ou seja, use o .NET para Apache Spark junto com [ml.net](http://dot.net/ml))</span><span class="sxs-lookup"><span data-stu-id="9fd95-113">Machine learning integration for faster training and prediction (i.e. use .NET for Apache Spark alongside [ML.NET](http://dot.net/ml))</span></span>

<span data-ttu-id="9fd95-114">O .NET para Apache Spark está em conformidade com o .NET Standard, uma especificação formal das APIs do .NET comuns em implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="9fd95-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="9fd95-115">Isso significa que você pode usar o .NET para Apache Spark em qualquer lugar em que você escreva código .NET, permitindo que você reutilize todo o conhecimento, as habilidades, o código e as bibliotecas que você já tem como um desenvolvedor do .NET.</span><span class="sxs-lookup"><span data-stu-id="9fd95-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="9fd95-116">O .NET para Apache Spark é executado no Windows, no Linux e no macOS usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9fd95-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="9fd95-117">Ele também é executado no Windows usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9fd95-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="9fd95-118">Você pode implantar seus aplicativos em todos os principais provedores de nuvem, incluindo Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks e Databricks na AWS.</span><span class="sxs-lookup"><span data-stu-id="9fd95-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="9fd95-119">.NET para arquitetura de Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9fd95-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="9fd95-120">A C#Associação F# de idioma/para Spark é escrita em uma nova camada de interoperabilidade do Spark, que oferece extensibilidade mais fácil.</span><span class="sxs-lookup"><span data-stu-id="9fd95-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="9fd95-121">Essa nova camada de interoperabilidade do Spark foi escrita usando as práticas recomendadas para extensão de linguagem e otimiza a interoperabilidade e o desempenho.</span><span class="sxs-lookup"><span data-stu-id="9fd95-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="9fd95-122">A longo prazo, essa extensibilidade pode ser usada para adicionar suporte a outros idiomas no Spark.</span><span class="sxs-lookup"><span data-stu-id="9fd95-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="9fd95-123">![.NET para a arquitetura de Apache Spark @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="9fd95-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="9fd95-124">Você pode aprender sobre o suporte de interoperabilidade para extensões de linguagem do Spark da [proposta](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="9fd95-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="9fd95-125">Desempenho do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9fd95-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="9fd95-126">Quando comparado com o Python e escalabilidade usando o parâmetro de [comparação de TPC-H](http://www.tpc.org/tpch/), o .net para Apache Spark funciona bem na maioria dos casos e é 2x mais rápido do que o Python quando o desempenho da função definida pelo usuário é crítico.</span><span class="sxs-lookup"><span data-stu-id="9fd95-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="9fd95-127">Há um esforço contínuo para melhorar o desempenho do benchmark.</span><span class="sxs-lookup"><span data-stu-id="9fd95-127">There is an ongoing effort to improve and benchmark performance.</span></span> 

<span data-ttu-id="9fd95-128">Para fazer seu próprio benchmark, consulte os parâmetros de comparação disponíveis no [.net para Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="9fd95-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="9fd95-129">Mapa do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9fd95-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="9fd95-130">Saiba mais sobre os planos de curto e longo prazo do [.net oficial para o roteiro de Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="9fd95-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="9fd95-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="9fd95-131">.NET Foundation</span></span>

<span data-ttu-id="9fd95-132">O projeto .NET para Apache Spark faz parte do [.NET Foundation.](https://www.dotnetfoundation.org/)</span><span class="sxs-lookup"><span data-stu-id="9fd95-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="9fd95-133">Contribuições</span><span class="sxs-lookup"><span data-stu-id="9fd95-133">Contributions</span></span>

<span data-ttu-id="9fd95-134">A equipe do .NET para Apache Spark incentiva contribuições, tanto em problemas do GitHub quanto em solicitações de pull.</span><span class="sxs-lookup"><span data-stu-id="9fd95-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="9fd95-135">Primeiro, procure um [problema existente](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="9fd95-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="9fd95-136">Se você não conseguir encontrar um problema existente, [abra um novo problema](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="9fd95-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9fd95-137">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9fd95-137">Next steps</span></span>

<span data-ttu-id="9fd95-138">Experimente o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="9fd95-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9fd95-139">Tutorial: introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="9fd95-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
