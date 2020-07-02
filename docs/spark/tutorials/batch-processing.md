---
title: Tutorial de processamento em lote com .NET para Apache Spark
description: Saiba como fazer o processamento em lotes usando o .NET para Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: dbc3ab5cc4bd7f438e9f3f8e5d36c764d785ce4b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618279"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="b9b0c-103">Tutorial: fazer processamento em lote com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b9b0c-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="b9b0c-104">Neste tutorial, você aprenderá a fazer o processamento em lotes usando o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="b9b0c-105">O processamento em lotes é a transformação de dados em repouso, o que significa que os dados de origem já foram carregados no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="b9b0c-106">Em geral, o processamento em lotes é executado em conjuntos de grandes volumes de valores simples, que precisam ser preparados para análise posterior.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="b9b0c-107">O processamento de log e o data warehousing são cenários comuns de processamento em lote.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="b9b0c-108">Nesse cenário, você analisa informações sobre projetos do GitHub, como o número de vezes que projetos diferentes foram bifurcados ou como os projetos foram atualizados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="b9b0c-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="b9b0c-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b9b0c-110">Criar e executar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b9b0c-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="b9b0c-111">Ler dados em um dataframe e prepará-los para análise</span><span class="sxs-lookup"><span data-stu-id="b9b0c-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="b9b0c-112">Processar os dados usando o Spark SQL</span><span class="sxs-lookup"><span data-stu-id="b9b0c-112">Process the data using Spark SQL</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="b9b0c-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b9b0c-113">Prerequisites</span></span>

<span data-ttu-id="b9b0c-114">Se esta for a primeira vez que você usa o .NET para Apache Spark, confira o tutorial introdução ao [.net para Apache Spark](get-started.md) para saber como preparar seu ambiente e executar seu primeiro aplicativo .net para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="b9b0c-115">Baixe os dados de exemplo</span><span class="sxs-lookup"><span data-stu-id="b9b0c-115">Download the sample data</span></span>

<span data-ttu-id="b9b0c-116">O [GHTorrent](http://ghtorrent.org/) monitora todos os eventos públicos do GitHub, como informações sobre projetos, confirmações e inspetores, e armazena os eventos e sua estrutura em bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="b9b0c-117">Os dados coletados em períodos de tempo diferentes estão disponíveis como arquivos mortos para download.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="b9b0c-118">Como os arquivos de despejo são muito grandes, este guia usa uma [versão truncada do arquivo de despejo](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) que pode ser baixada do github.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="b9b0c-119">O conjunto de GHTorrent é distribuído sob um esquema de licenciamento duplo ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="b9b0c-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="b9b0c-120">Para usos não comerciais (incluindo, mas não se limitando a, os usos educativos, de pesquisa ou pessoais), o conjunto de pontos é distribuído na [licença CC por SA](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="b9b0c-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b9b0c-121">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="b9b0c-121">Create a console application</span></span>

1. <span data-ttu-id="b9b0c-122">No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="b9b0c-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="b9b0c-123">O `dotnet` comando cria um `new` aplicativo do tipo `console` para você.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="b9b0c-124">O `-o` parâmetro cria um diretório chamado *mySparkBatchApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="b9b0c-125">O `cd mySparkBatchApp` comando altera o diretório para o diretório de aplicativo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="b9b0c-126">Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="b9b0c-127">No console do, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b9b0c-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="b9b0c-128">Criar um SparkSession</span><span class="sxs-lookup"><span data-stu-id="b9b0c-128">Create a SparkSession</span></span>

1. <span data-ttu-id="b9b0c-129">Adicione as instruções adicionais a seguir `using` à parte superior do arquivo *Program.cs* no *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="b9b0c-130">Adicione o código a seguir ao namespace do projeto.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="b9b0c-131">*s_referenceData* é usado posteriormente no programa para filtrar com base na data.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="b9b0c-132">Adicione o código a seguir dentro do método Main para estabelecer um novo SparkSession.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="b9b0c-133">O SparkSession é o ponto de entrada para programação do Spark com a API do conjunto de e do DataSet.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="b9b0c-134">Ao chamar o `spark` objeto, você pode acessar a funcionalidade Spark e dataframe em todo o seu programa.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="b9b0c-135">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="b9b0c-135">Prepare the data</span></span>

1. <span data-ttu-id="b9b0c-136">Leia o arquivo de entrada em um `DataFrame` , que é uma coleção distribuída de dados organizados em colunas nomeadas.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="b9b0c-137">Você pode definir as colunas para os dados por meio de <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> .</span><span class="sxs-lookup"><span data-stu-id="b9b0c-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="b9b0c-138">Use o <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> método para exibir os dados em seu dataframe.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="b9b0c-139">Certifique-se de atualizar o caminho do arquivo CSV para o local dos dados do GitHub que você baixou.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="b9b0c-140">Use o <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> método para descartar linhas com valores de na (NULL) e o <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> método para remover determinadas colunas de seus dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="b9b0c-141">Isso ajuda a evitar erros se você tentar analisar dados nulos ou colunas que não são relevantes para sua análise final.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="b9b0c-142">Analisar os dados</span><span class="sxs-lookup"><span data-stu-id="b9b0c-142">Analyze the data</span></span>

<span data-ttu-id="b9b0c-143">O Spark SQL permite fazer chamadas SQL em seus dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="b9b0c-144">É comum combinar funções definidas pelo usuário e o Spark SQL para aplicar uma função definida pelo usuário a todas as linhas do dataframe.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="b9b0c-145">Você pode chamar especificamente `spark.Sql` para imitar chamadas SQL padrão vistas em outros tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="b9b0c-146">Você também pode chamar métodos como <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> e <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> para combinar, filtrar e executar cálculos em seus dados especificamente.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="b9b0c-147">O objetivo deste aplicativo é obter algumas informações sobre os dados de projetos do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="b9b0c-148">Adicione os trechos de código a seguir ao seu programa para analisar os dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="b9b0c-149">Adicionar o seguinte bloco de código localiza o número de vezes que cada idioma foi bifurcado.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="b9b0c-150">Primeiro, os dados são agrupados por linguagem.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-150">First, the data is grouped by language.</span></span> <span data-ttu-id="b9b0c-151">Em seguida, o número médio de bifurcações de cada idioma é tirado.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="b9b0c-152">Adicione o seguinte bloco de código para ordenar o número médio de bifurcações em ordem decrescente para ver quais idiomas são os mais bifurcados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="b9b0c-153">Ou seja, o maior número de bifurcações será exibido primeiro.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="b9b0c-154">O próximo bloco de código mostra como os projetos recentemente foram atualizados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="b9b0c-155">Você registra uma nova função definida pelo usuário chamada *MyUDF* e a compara com uma data, *s_referenceDate*, que foi declarado no início do tutorial.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="b9b0c-156">A data de cada projeto é comparada com a data de referência.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="b9b0c-157">Em seguida, o Spark SQL é usado para chamar o UDF em cada linha dos dados para analisar cada projeto no conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="b9b0c-158">Chame `spark.Stop()` para terminar o SparkSession.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="b9b0c-159">Use o Spark-Submit para executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b9b0c-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="b9b0c-160">Use o seguinte comando para compilar seu aplicativo .NET:</span><span class="sxs-lookup"><span data-stu-id="b9b0c-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="b9b0c-161">Execute seu aplicativo com `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="b9b0c-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="b9b0c-162">Certifique-se de atualizar o comando a seguir com os caminhos reais para o arquivo JAR do Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="b9b0c-163">Obter o código</span><span class="sxs-lookup"><span data-stu-id="b9b0c-163">Get the code</span></span>

<span data-ttu-id="b9b0c-164">Você pode ver a [solução completa](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) no github.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b9b0c-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b9b0c-165">Next steps</span></span>

<span data-ttu-id="b9b0c-166">Avance para o próximo artigo para saber como processar dados de streaming com o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b9b0c-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b9b0c-167">Tutorial: streaming estruturado com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b9b0c-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
