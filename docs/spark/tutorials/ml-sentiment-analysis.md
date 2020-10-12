---
title: Tutorial de análise de sentimentos com .NET para Apache Spark e ML.NET
description: Neste tutorial, você aprenderá a usar o ML.NET com .NET para Apache Spark para análise de sentimentos.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 16b4d34e4c581da2cd0ba798d87e53ccfc49f0e9
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954887"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="2d77b-103">Tutorial: análise de sentimentos com .NET para Apache Spark e ML.NET</span><span class="sxs-lookup"><span data-stu-id="2d77b-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="2d77b-104">Este tutorial ensina como fazer uma análise de sentimentos das revisões online usando o ML.NET e o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="2d77b-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="2d77b-105">O [ml.net](http://dot.net/ml) é uma estrutura de aprendizado de máquina livre, de plataforma cruzada e gratuita.</span><span class="sxs-lookup"><span data-stu-id="2d77b-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="2d77b-106">Você pode usar o ML.NET com .NET para Apache Spark para dimensionar o treinamento e a previsão de algoritmos de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="2d77b-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="2d77b-107">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="2d77b-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="2d77b-108">Criar um modelo de análise de sentimentos usando o ML.NET Model Builder no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d77b-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="2d77b-109">Crie um .NET para Apache Spark aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="2d77b-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="2d77b-110">Escreva e implemente uma função definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2d77b-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="2d77b-111">Execute um .NET para Apache Spark aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="2d77b-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d77b-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2d77b-112">Prerequisites</span></span>

* <span data-ttu-id="2d77b-113">Se você ainda não desenvolveu um aplicativo .NET para Apache Spark antes, comece com o [tutorial de introdução](get-started.md) para se familiarizar com os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="2d77b-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="2d77b-114">Conclua todos os pré-requisitos para o tutorial de Introdução antes de continuar com este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2d77b-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="2d77b-115">Este tutorial usa o ML.NET Model Builder (versão prévia), uma interface visual disponível no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d77b-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="2d77b-116">Se você ainda não tiver o Visual Studio, poderá [baixar a versão da Comunidade do Visual Studio](https://visualstudio.microsoft.com/downloads/) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="2d77b-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="2d77b-117">[Baixar e instalar](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (versão prévia).</span><span class="sxs-lookup"><span data-stu-id="2d77b-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="2d77b-118">Baixe o [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) e [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) os conjuntos de Yelp de revisão.</span><span class="sxs-lookup"><span data-stu-id="2d77b-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="2d77b-119">Examinar os dados</span><span class="sxs-lookup"><span data-stu-id="2d77b-119">Review the data</span></span>

<span data-ttu-id="2d77b-120">O conjunto de informações de revisões do Yelp contém revisões online do Yelp sobre vários serviços.</span><span class="sxs-lookup"><span data-stu-id="2d77b-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="2d77b-121">Abra [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) e observe a estrutura dos dados.</span><span class="sxs-lookup"><span data-stu-id="2d77b-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="2d77b-122">A primeira coluna contém o texto de revisão e a segunda coluna contém pontuações de sentimentos.</span><span class="sxs-lookup"><span data-stu-id="2d77b-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="2d77b-123">Se a pontuação de sentimentos for 1, a revisão será positiva e, se a pontuação de sentimentos for 0, a revisão será negativa.</span><span class="sxs-lookup"><span data-stu-id="2d77b-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="2d77b-124">A tabela a seguir contém dados de exemplo:</span><span class="sxs-lookup"><span data-stu-id="2d77b-124">The following table contains sample data:</span></span>

|<span data-ttu-id="2d77b-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="2d77b-125">ReviewText</span></span>|<span data-ttu-id="2d77b-126">Sentimento</span><span class="sxs-lookup"><span data-stu-id="2d77b-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="2d77b-127">Wow... Adorei este lugar.</span><span class="sxs-lookup"><span data-stu-id="2d77b-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="2d77b-128">1</span><span class="sxs-lookup"><span data-stu-id="2d77b-128">1</span></span>|
|<span data-ttu-id="2d77b-129">A torrada não é boa.</span><span class="sxs-lookup"><span data-stu-id="2d77b-129">Crust is not good.</span></span>|    <span data-ttu-id="2d77b-130">0</span><span class="sxs-lookup"><span data-stu-id="2d77b-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="2d77b-131">Crie seu modelo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="2d77b-131">Build your machine learning model</span></span>

1. <span data-ttu-id="2d77b-132">Abra o Visual Studio e crie um novo aplicativo de console em C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="2d77b-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="2d77b-133">Nomeie o projeto *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="2d77b-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="2d77b-134">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto *MLSparkModel* .</span><span class="sxs-lookup"><span data-stu-id="2d77b-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="2d77b-135">Em seguida, selecione **adicionar > Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="2d77b-136">No construtor de modelos de ML.NET, selecione o bloco **análise de sentimento** cenário.</span><span class="sxs-lookup"><span data-stu-id="2d77b-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="2d77b-137">Na página **Adicionar dados** , carregue o conjunto de dados *yelptrain.csv* .</span><span class="sxs-lookup"><span data-stu-id="2d77b-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="2d77b-138">Escolha *sentimentos* das **colunas para prever a** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="2d77b-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="2d77b-139">Na página **treinar** , defina o tempo de treinamento para *60 segundos* e selecione **Iniciar treinamento**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="2d77b-140">Observe o status do treinamento em **andamento**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="2d77b-141">Depois de concluir o treinamento do construtor de modelos, **avalie** os resultados do treinamento.</span><span class="sxs-lookup"><span data-stu-id="2d77b-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="2d77b-142">Você pode digitar frases na caixa de texto abaixo, **testar o modelo** e selecionar **prever** para ver a saída.</span><span class="sxs-lookup"><span data-stu-id="2d77b-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="2d77b-143">Selecione **código** e, em seguida, selecione **adicionar projetos** para adicionar o modelo ml à solução.</span><span class="sxs-lookup"><span data-stu-id="2d77b-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="2d77b-144">Observe que dois projetos são adicionados às suas soluções: **MLSparkModelML. ConsoleApp** e **MLSparkModelML. Model**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="2d77b-145">Clique duas vezes em seu projeto *MLSpark* C# e observe que a referência de projeto a seguir foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="2d77b-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="2d77b-146">Criar um aplicativo do console</span><span class="sxs-lookup"><span data-stu-id="2d77b-146">Create a console app</span></span>

<span data-ttu-id="2d77b-147">O construtor de modelos cria um aplicativo de console para você.</span><span class="sxs-lookup"><span data-stu-id="2d77b-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="2d77b-148">Clique com o botão direito do mouse em **MLSparkModelML. console** em Gerenciador de soluções e selecione **gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="2d77b-149">Procure **Microsoft. Spark** e instale o pacote.</span><span class="sxs-lookup"><span data-stu-id="2d77b-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="2d77b-150">O **Microsoft.ml** é instalado automaticamente para você pelo construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="2d77b-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="2d77b-151">Criar um SparkSession</span><span class="sxs-lookup"><span data-stu-id="2d77b-151">Create a SparkSession</span></span>

1. <span data-ttu-id="2d77b-152">Abra o arquivo *Program.cs* para **MLSparkModelML. ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="2d77b-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="2d77b-153">Este arquivo foi gerado automaticamente pelo construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="2d77b-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="2d77b-154">Exclua as `using` instruções, o conteúdo do método Main () e a `CreateSingleDataSample` região.</span><span class="sxs-lookup"><span data-stu-id="2d77b-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="2d77b-155">Adicione as seguintes `using` instruções adicionais à parte superior do *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="2d77b-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="2d77b-156">Altere o `DATA_FILEPATH` para o caminho do seu *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="2d77b-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="2d77b-157">Adicione o código a seguir ao `Main` método para criar um novo `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="2d77b-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="2d77b-158">A sessão do Spark é o ponto de entrada para programar o Spark com o conjunto de e a API dataframe.</span><span class="sxs-lookup"><span data-stu-id="2d77b-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="2d77b-159">Chamar o objeto *Spark* criado acima permite que você acesse a funcionalidade Spark e dataframe em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="2d77b-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="2d77b-160">Criar um dataframe e imprimir no console</span><span class="sxs-lookup"><span data-stu-id="2d77b-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="2d77b-161">Leia em Yelp dados de revisão do arquivo de *yelptest.csv* como um `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="2d77b-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="2d77b-162">Incluir `header` e `inferSchema` opções.</span><span class="sxs-lookup"><span data-stu-id="2d77b-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="2d77b-163">A `header` opção lê a primeira linha de *yelptest.csv* como nomes de coluna em vez de dados.</span><span class="sxs-lookup"><span data-stu-id="2d77b-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="2d77b-164">A `inferSchema` opção infere os tipos de coluna com base nos dados.</span><span class="sxs-lookup"><span data-stu-id="2d77b-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="2d77b-165">Registrar uma função definida pelo usuário</span><span class="sxs-lookup"><span data-stu-id="2d77b-165">Register a user-defined function</span></span>

<span data-ttu-id="2d77b-166">Você pode usar UDFs, *funções definidas pelo usuário*, em aplicativos Spark para fazer cálculos e análises em seus dados.</span><span class="sxs-lookup"><span data-stu-id="2d77b-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="2d77b-167">Neste tutorial, você usará o ML.NET com um UDF para avaliar cada revisão de Yelp.</span><span class="sxs-lookup"><span data-stu-id="2d77b-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="2d77b-168">Adicione o código a seguir ao `Main` método para registrar um UDF chamado `MLudf` .</span><span class="sxs-lookup"><span data-stu-id="2d77b-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="2d77b-169">Esse UDF usa uma cadeia de caracteres de revisão Yelp como entrada e produz verdadeiro ou falso para sentimentos positivos ou negativos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2d77b-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="2d77b-170">Ele usa o método *Predict ()* que você define em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="2d77b-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="2d77b-171">Usar o Spark SQL para chamar o UDF</span><span class="sxs-lookup"><span data-stu-id="2d77b-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="2d77b-172">Agora que você leu os dados e incorporou o ML, use o Spark SQL para chamar o UDF que executará a análise de sentimentos em cada linha do dataframe.</span><span class="sxs-lookup"><span data-stu-id="2d77b-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="2d77b-173">Adicione o código a seguir ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="2d77b-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="2d77b-174">Criar método Predict ()</span><span class="sxs-lookup"><span data-stu-id="2d77b-174">Create predict() method</span></span>

<span data-ttu-id="2d77b-175">Adicione o código a seguir antes do seu `Main()` método.</span><span class="sxs-lookup"><span data-stu-id="2d77b-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="2d77b-176">Esse código é semelhante ao que é produzido pelo construtor de modelos no *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="2d77b-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="2d77b-177">Mover esse método para o console carrega o carregamento do modelo cada vez que você executa seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d77b-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="2d77b-178">Adicionar o modelo ao seu aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="2d77b-178">Add the model to your console app</span></span>

<span data-ttu-id="2d77b-179">Em Gerenciador de Soluções, copie o arquivo de *MLModel.zip* do projeto **MLSparkModelML. Model** e cole-o no projeto **MLSparkModelML. ConsoleApp** .</span><span class="sxs-lookup"><span data-stu-id="2d77b-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="2d77b-180">Uma referência é adicionada automaticamente em *MLSparkModelML. ConsoleApp. csproj*.</span><span class="sxs-lookup"><span data-stu-id="2d77b-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="2d77b-181">Executar seu código</span><span class="sxs-lookup"><span data-stu-id="2d77b-181">Run your code</span></span>

<span data-ttu-id="2d77b-182">Use `spark-submit` para executar seu código.</span><span class="sxs-lookup"><span data-stu-id="2d77b-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="2d77b-183">Navegue até a pasta raiz do aplicativo de console usando o prompt de comando e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d77b-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="2d77b-184">Primeiro, limpe e publique seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d77b-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="2d77b-185">Em seguida, navegue até a pasta de publicação do aplicativo de console e execute o comando a seguir `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="2d77b-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="2d77b-186">Lembre-se de atualizar o comando com o caminho real do arquivo JAR do Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="2d77b-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="2d77b-187">Obter o código</span><span class="sxs-lookup"><span data-stu-id="2d77b-187">Get the code</span></span>

<span data-ttu-id="2d77b-188">Este tutorial é semelhante ao código do exemplo [análise de sentimento com Big data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) .</span><span class="sxs-lookup"><span data-stu-id="2d77b-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2d77b-189">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2d77b-189">Next steps</span></span>

<span data-ttu-id="2d77b-190">Avance para o próximo artigo para saber como fazer streaming estruturado com o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="2d77b-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2d77b-191">Tutorial: streaming estruturado com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2d77b-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
