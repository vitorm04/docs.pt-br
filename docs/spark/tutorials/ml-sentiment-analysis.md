---
title: Análise de sentimento com .NET para Apache Spark e tutorial de ML.NET
description: Neste tutorial, você aprende a usar ML.NET com .NET para Apache Spark para análise de sentimentos.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391254"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="838f4-103">Tutorial: Análise de sentimento com .NET para Apache Spark e ML.NET</span><span class="sxs-lookup"><span data-stu-id="838f4-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="838f4-104">Este tutorial ensina como fazer análise de sentimentos de avaliações online usando ML.NET e .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="838f4-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="838f4-105">[ML.NET](http://dot.net/ml) é uma estrutura gratuita de aprendizado de máquina de código aberto e multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="838f4-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="838f4-106">Você pode usar ML.NET com .NET para Apache Spark para dimensionar o treinamento e a previsão de algoritmos de aprendizagem de máquina.</span><span class="sxs-lookup"><span data-stu-id="838f4-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="838f4-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="838f4-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="838f4-108">Crie um modelo de análise de sentimento usando ML.NET Model Builder no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="838f4-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="838f4-109">Crie um aplicativo de console .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="838f4-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="838f4-110">Escreva e implemente uma função definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="838f4-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="838f4-111">Execute um aplicativo de console .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="838f4-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="838f4-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="838f4-112">Prerequisites</span></span>

* <span data-ttu-id="838f4-113">Se você ainda não desenvolveu um aplicativo .NET para Apache Spark antes, comece com o [tutorial Getting Started](get-started.md) para se familiarizar com o básico.</span><span class="sxs-lookup"><span data-stu-id="838f4-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="838f4-114">Complete todos os pré-requisitos para o tutorial De Começar antes de continuar com este tutorial.</span><span class="sxs-lookup"><span data-stu-id="838f4-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="838f4-115">Este tutorial usa o ML.NET Model Builder (preview), uma interface visual disponível no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="838f4-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="838f4-116">Se você ainda não tem o Visual Studio, você pode baixar a [versão comunitária do Visual Studio](https://visualstudio.microsoft.com/downloads/) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="838f4-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="838f4-117">[Baixar e instalar](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (visualização).</span><span class="sxs-lookup"><span data-stu-id="838f4-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="838f4-118">Baixe os conjuntos de dados de revisão [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) e [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.</span><span class="sxs-lookup"><span data-stu-id="838f4-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="838f4-119">Examinar os dados</span><span class="sxs-lookup"><span data-stu-id="838f4-119">Review the data</span></span>

<span data-ttu-id="838f4-120">O conjunto de avaliações do Yelp contém avaliações online do Yelp sobre vários serviços.</span><span class="sxs-lookup"><span data-stu-id="838f4-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="838f4-121">Abra [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) e observe a estrutura dos dados.</span><span class="sxs-lookup"><span data-stu-id="838f4-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="838f4-122">A primeira coluna contém texto de revisão, e a segunda coluna contém pontuações de sentimento.</span><span class="sxs-lookup"><span data-stu-id="838f4-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="838f4-123">Se o placar é 1, a revisão é positiva, e se o placar do sentimento é 0, a revisão é negativa.</span><span class="sxs-lookup"><span data-stu-id="838f4-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="838f4-124">A tabela a seguir contém dados de amostra:</span><span class="sxs-lookup"><span data-stu-id="838f4-124">The following table contains sample data:</span></span>

|<span data-ttu-id="838f4-125">ComentárioTexto</span><span class="sxs-lookup"><span data-stu-id="838f4-125">ReviewText</span></span>|<span data-ttu-id="838f4-126">Sentimento</span><span class="sxs-lookup"><span data-stu-id="838f4-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="838f4-127">Wow... Adorei esse lugar.</span><span class="sxs-lookup"><span data-stu-id="838f4-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="838f4-128">1</span><span class="sxs-lookup"><span data-stu-id="838f4-128">1</span></span>|
|<span data-ttu-id="838f4-129">A torrada não é boa.</span><span class="sxs-lookup"><span data-stu-id="838f4-129">Crust is not good.</span></span>|    <span data-ttu-id="838f4-130">0</span><span class="sxs-lookup"><span data-stu-id="838f4-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="838f4-131">Construa seu modelo de aprendizado de máquina</span><span class="sxs-lookup"><span data-stu-id="838f4-131">Build your machine learning model</span></span>

1. <span data-ttu-id="838f4-132">Abra o Visual Studio e crie um novo c# console App (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="838f4-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="838f4-133">Nomeie o projeto *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="838f4-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="838f4-134">No **Solution Explorer,** clique com o botão direito do mouse no projeto *MLSparkModel.*</span><span class="sxs-lookup"><span data-stu-id="838f4-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="838f4-135">Em seguida, **selecione Adicionar > Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="838f4-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="838f4-136">No ML.NET Model Builder, selecione o cenário de Análise de **Sentimento.**</span><span class="sxs-lookup"><span data-stu-id="838f4-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="838f4-137">Na página **Adicionar dados,** faça upload do conjunto de dados *yelptrain.csv.*</span><span class="sxs-lookup"><span data-stu-id="838f4-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="838f4-138">Escolha *Sentimento* nas **Colunas para prever a** queda.</span><span class="sxs-lookup"><span data-stu-id="838f4-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="838f4-139">Na página **Trem,** defina o tempo para treinar para *60 segundos* e selecione **Iniciar o treinamento**.</span><span class="sxs-lookup"><span data-stu-id="838f4-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="838f4-140">Observe o status do seu treinamento em **Andamento.**</span><span class="sxs-lookup"><span data-stu-id="838f4-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="838f4-141">Uma vez que o Model Builder termine o treinamento, **avalie** os resultados do treinamento.</span><span class="sxs-lookup"><span data-stu-id="838f4-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="838f4-142">Você pode digitar frases na caixa de texto abaixo **Tente seu modelo** e selecione **Prever** para ver a saída.</span><span class="sxs-lookup"><span data-stu-id="838f4-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="838f4-143">Selecione **Código** e **selecione Adicionar projetos** para adicionar o modelo ML à solução.</span><span class="sxs-lookup"><span data-stu-id="838f4-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="838f4-144">Observe que dois projetos são adicionados às suas soluções: **MLSparkModelML.ConsoleApp** e **MLSparkModelML.Model .**</span><span class="sxs-lookup"><span data-stu-id="838f4-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="838f4-145">Clique duas vezes no projeto *MLSpark* C# e observe que a seguinte referência ao projeto foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="838f4-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="838f4-146">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="838f4-146">Create a console app</span></span>

<span data-ttu-id="838f4-147">Model Builder cria um aplicativo de console para você.</span><span class="sxs-lookup"><span data-stu-id="838f4-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="838f4-148">Clique com o botão direito do mouse no **MLSparkModelML.Console** no Solution Explorer e selecione **Gerenciar pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="838f4-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="838f4-149">Procure o **Microsoft.Spark** e instale o pacote.</span><span class="sxs-lookup"><span data-stu-id="838f4-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="838f4-150">**Microsoft.ML** é automaticamente instalado para você pelo Model Builder.</span><span class="sxs-lookup"><span data-stu-id="838f4-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="838f4-151">Criar uma SparkSession</span><span class="sxs-lookup"><span data-stu-id="838f4-151">Create a SparkSession</span></span>

1. <span data-ttu-id="838f4-152">Abra o arquivo *Program.cs* para **MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="838f4-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="838f4-153">Este arquivo foi gerado automaticamente pelo Model Builder.</span><span class="sxs-lookup"><span data-stu-id="838f4-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="838f4-154">Exclua `using` as declarações, o conteúdo do `CreateSingleDataSample` método Principal e a região.</span><span class="sxs-lookup"><span data-stu-id="838f4-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="838f4-155">Adicione as `using` seguintes instruções adicionais à parte superior do *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="838f4-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="838f4-156">Mude `DATA_FILEPATH` o caminho do seu *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="838f4-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="838f4-157">Adicione o seguinte `Main` código ao seu `SparkSession`método para criar um novo .</span><span class="sxs-lookup"><span data-stu-id="838f4-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="838f4-158">A Sessão spark é o ponto de entrada para programar o Spark com a API Dataset e DataFrame.</span><span class="sxs-lookup"><span data-stu-id="838f4-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="838f4-159">Chamar o objeto *de faísca* criado acima permite que você acesse a funcionalidade do Spark e do DataFrame durante todo o seu programa.</span><span class="sxs-lookup"><span data-stu-id="838f4-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="838f4-160">Crie um DataFrame e imprima para console</span><span class="sxs-lookup"><span data-stu-id="838f4-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="838f4-161">Leia nos dados de revisão do Yelp do arquivo `DataFrame` *yelptest.csv* como a .</span><span class="sxs-lookup"><span data-stu-id="838f4-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="838f4-162">Inclua `header` `inferSchema` e opções.</span><span class="sxs-lookup"><span data-stu-id="838f4-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="838f4-163">A `header` opção lê a primeira linha de *yelptest.csv* como nomes de coluna em vez de dados.</span><span class="sxs-lookup"><span data-stu-id="838f4-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="838f4-164">A `inferSchema` opção infere tipos de coluna com base nos dados.</span><span class="sxs-lookup"><span data-stu-id="838f4-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="838f4-165">Registre uma função definida pelo usuário</span><span class="sxs-lookup"><span data-stu-id="838f4-165">Register a user-defined function</span></span>

<span data-ttu-id="838f4-166">Você pode usar UDFs, *funções definidas pelo usuário,* em aplicativos Spark para fazer cálculos e análises em seus dados.</span><span class="sxs-lookup"><span data-stu-id="838f4-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="838f4-167">Neste tutorial, você usa ML.NET com um UDF para avaliar cada revisão do Yelp.</span><span class="sxs-lookup"><span data-stu-id="838f4-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="838f4-168">Adicione o seguinte `Main` código ao seu método `MLudf`para registrar um UDF chamado .</span><span class="sxs-lookup"><span data-stu-id="838f4-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="838f4-169">Este UDF toma uma seqüência de revisão do Yelp como entrada, e produz verdadeiro ou falso para sentimentos positivos ou negativos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="838f4-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="838f4-170">Ele usa o método *predict()* que você define em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="838f4-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="838f4-171">Use o Spark SQL para chamar o UDF</span><span class="sxs-lookup"><span data-stu-id="838f4-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="838f4-172">Agora que você leu em seus dados e incorporou ml, use Spark SQL para chamar o UDF que executará a análise de sentimento em cada linha do seu DataFrame.</span><span class="sxs-lookup"><span data-stu-id="838f4-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="838f4-173">Adicione o código a seguir ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="838f4-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="838f4-174">Criar método de previsão()</span><span class="sxs-lookup"><span data-stu-id="838f4-174">Create predict() method</span></span>

<span data-ttu-id="838f4-175">Adicione o seguinte `Main()` código antes do seu método.</span><span class="sxs-lookup"><span data-stu-id="838f4-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="838f4-176">Este código é semelhante ao que é produzido pelo Model Builder em *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="838f4-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="838f4-177">Mover este método para o seu console carrega o modelo carregando cada vez que você executa seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="838f4-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="838f4-178">Adicione o modelo ao seu aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="838f4-178">Add the model to your console app</span></span>

<span data-ttu-id="838f4-179">No Solution Explorer, copie o arquivo *MLModel.zip* do projeto **MLSparkModelML.Model** e cole-o no projeto **MLSparkModelML.ConsoleApp.**</span><span class="sxs-lookup"><span data-stu-id="838f4-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="838f4-180">Uma referência é adicionada automaticamente em *MLSparkModelML.ConsoleApp.csproj*.</span><span class="sxs-lookup"><span data-stu-id="838f4-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="838f4-181">Execute seu código</span><span class="sxs-lookup"><span data-stu-id="838f4-181">Run your code</span></span>

<span data-ttu-id="838f4-182">Use `spark-submit` para executar o seu código.</span><span class="sxs-lookup"><span data-stu-id="838f4-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="838f4-183">Navegue até a pasta raiz do aplicativo do console usando o prompt de comando e execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="838f4-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="838f4-184">Primeiro, limpe e publique seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="838f4-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="838f4-185">Em seguida, navegue até a pasta `spark-submit` de publicação do aplicativo de console e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="838f4-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="838f4-186">Lembre-se de atualizar o comando com o caminho real do seu arquivo de jarro Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="838f4-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="838f4-187">Obter o código</span><span class="sxs-lookup"><span data-stu-id="838f4-187">Get the code</span></span>

<span data-ttu-id="838f4-188">Este tutorial é semelhante ao código da Análise de Sentimento com o exemplo [de Big Data.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)</span><span class="sxs-lookup"><span data-stu-id="838f4-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="838f4-189">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="838f4-189">Next steps</span></span>

<span data-ttu-id="838f4-190">Avance para o próximo artigo para saber como fazer Streaming Estruturado com .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="838f4-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="838f4-191">Tutorial: Streaming estruturado com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="838f4-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
