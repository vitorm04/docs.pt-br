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
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Tutorial: Análise de sentimento com .NET para Apache Spark e ML.NET

Este tutorial ensina como fazer análise de sentimentos de avaliações online usando ML.NET e .NET para Apache Spark. [ML.NET](http://dot.net/ml) é uma estrutura gratuita de aprendizado de máquina de código aberto e multiplataforma. Você pode usar ML.NET com .NET para Apache Spark para dimensionar o treinamento e a previsão de algoritmos de aprendizagem de máquina.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Crie um modelo de análise de sentimento usando ML.NET Model Builder no Visual Studio.
> * Crie um aplicativo de console .NET para Apache Spark.
> * Escreva e implemente uma função definida pelo usuário.
> * Execute um aplicativo de console .NET para Apache Spark.

## <a name="prerequisites"></a>Pré-requisitos

* Se você ainda não desenvolveu um aplicativo .NET para Apache Spark antes, comece com o [tutorial Getting Started](get-started.md) para se familiarizar com o básico. Complete todos os pré-requisitos para o tutorial De Começar antes de continuar com este tutorial.

* Este tutorial usa o ML.NET Model Builder (preview), uma interface visual disponível no Visual Studio. Se você ainda não tem o Visual Studio, você pode baixar a [versão comunitária do Visual Studio](https://visualstudio.microsoft.com/downloads/) gratuitamente.

* [Baixar e instalar](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (visualização).

* Baixe os conjuntos de dados de revisão [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) e [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.

## <a name="review-the-data"></a>Examinar os dados

O conjunto de avaliações do Yelp contém avaliações online do Yelp sobre vários serviços. Abra [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) e observe a estrutura dos dados. A primeira coluna contém texto de revisão, e a segunda coluna contém pontuações de sentimento. Se o placar é 1, a revisão é positiva, e se o placar do sentimento é 0, a revisão é negativa.

A tabela a seguir contém dados de amostra:

|ComentárioTexto|Sentimento|
|-|-|
|Wow... Adorei esse lugar.|    1|
|A torrada não é boa.|    0|

## <a name="build-your-machine-learning-model"></a>Construa seu modelo de aprendizado de máquina

1. Abra o Visual Studio e crie um novo c# console App (.NET Core). Nomeie o projeto *MLSparkModel*.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto *MLSparkModel.* Em seguida, **selecione Adicionar > Machine Learning**.

1. No ML.NET Model Builder, selecione o cenário de Análise de **Sentimento.**

1. Na página **Adicionar dados,** faça upload do conjunto de dados *yelptrain.csv.*

1. Escolha *Sentimento* nas **Colunas para prever a** queda.

1. Na página **Trem,** defina o tempo para treinar para *60 segundos* e selecione **Iniciar o treinamento**. Observe o status do seu treinamento em **Andamento.**

1. Uma vez que o Model Builder termine o treinamento, **avalie** os resultados do treinamento. Você pode digitar frases na caixa de texto abaixo **Tente seu modelo** e selecione **Prever** para ver a saída.

1. Selecione **Código** e **selecione Adicionar projetos** para adicionar o modelo ML à solução.

1. Observe que dois projetos são adicionados às suas soluções: **MLSparkModelML.ConsoleApp** e **MLSparkModelML.Model .**

1. Clique duas vezes no projeto *MLSpark* C# e observe que a seguinte referência ao projeto foi adicionada.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Criar um aplicativo de console

Model Builder cria um aplicativo de console para você.

1. Clique com o botão direito do mouse no **MLSparkModelML.Console** no Solution Explorer e selecione **Gerenciar pacotes NuGet**.

1. Procure o **Microsoft.Spark** e instale o pacote. **Microsoft.ML** é automaticamente instalado para você pelo Model Builder.

### <a name="create-a-sparksession"></a>Criar uma SparkSession

1. Abra o arquivo *Program.cs* para **MLSparkModelML.ConsoleApp**. Este arquivo foi gerado automaticamente pelo Model Builder. Exclua `using` as declarações, o conteúdo do `CreateSingleDataSample` método Principal e a região.

1. Adicione as `using` seguintes instruções adicionais à parte superior do *Program.cs*:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Mude `DATA_FILEPATH` o caminho do seu *yelptest.csv*.

1. Adicione o seguinte `Main` código ao seu `SparkSession`método para criar um novo . A Sessão spark é o ponto de entrada para programar o Spark com a API Dataset e DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Chamar o objeto *de faísca* criado acima permite que você acesse a funcionalidade do Spark e do DataFrame durante todo o seu programa.

### <a name="create-a-dataframe-and-print-to-console"></a>Crie um DataFrame e imprima para console

Leia nos dados de revisão do Yelp do arquivo `DataFrame` *yelptest.csv* como a . Inclua `header` `inferSchema` e opções. A `header` opção lê a primeira linha de *yelptest.csv* como nomes de coluna em vez de dados. A `inferSchema` opção infere tipos de coluna com base nos dados.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Registre uma função definida pelo usuário

Você pode usar UDFs, *funções definidas pelo usuário,* em aplicativos Spark para fazer cálculos e análises em seus dados. Neste tutorial, você usa ML.NET com um UDF para avaliar cada revisão do Yelp.

Adicione o seguinte `Main` código ao seu método `MLudf`para registrar um UDF chamado .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Este UDF toma uma seqüência de revisão do Yelp como entrada, e produz verdadeiro ou falso para sentimentos positivos ou negativos, respectivamente. Ele usa o método *predict()* que você define em uma etapa posterior.

### <a name="use-spark-sql-to-call-the-udf"></a>Use o Spark SQL para chamar o UDF

Agora que você leu em seus dados e incorporou ml, use Spark SQL para chamar o UDF que executará a análise de sentimento em cada linha do seu DataFrame. Adicione o código a seguir ao método `Main`:

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

### <a name="create-predict-method"></a>Criar método de previsão()

Adicione o seguinte `Main()` código antes do seu método. Este código é semelhante ao que é produzido pelo Model Builder em *ConsumeModel.cs*. Mover este método para o seu console carrega o modelo carregando cada vez que você executa seu aplicativo.

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

## <a name="add-the-model-to-your-console-app"></a>Adicione o modelo ao seu aplicativo de console

No Solution Explorer, copie o arquivo *MLModel.zip* do projeto **MLSparkModelML.Model** e cole-o no projeto **MLSparkModelML.ConsoleApp.** Uma referência é adicionada automaticamente em *MLSparkModelML.ConsoleApp.csproj*.

## <a name="run-your-code"></a>Execute seu código

Use `spark-submit` para executar o seu código. Navegue até a pasta raiz do aplicativo do console usando o prompt de comando e execute os seguintes comandos.

Primeiro, limpe e publique seu aplicativo.

```dotnetcli
dotnet clean
dotnet publish
```

Em seguida, navegue até a pasta `spark-submit` de publicação do aplicativo de console e execute o seguinte comando. Lembre-se de atualizar o comando com o caminho real do seu arquivo de jarro Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Obter o código

Este tutorial é semelhante ao código da Análise de Sentimento com o exemplo [de Big Data.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)

## <a name="next-steps"></a>Próximas etapas

Avance para o próximo artigo para saber como fazer Streaming Estruturado com .NET para Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Streaming estruturado com .NET para Apache Spark](streaming.md)
