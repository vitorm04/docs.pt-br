---
title: Tutorial estruturado com .NET para Apache Spark
description: Neste tutorial, você aprenderá a usar o .NET para Apache Spark para o streaming estruturado do Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: d0fe79ef79125c06be9acd8ba80001a33e150adb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802843"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="74f1e-103">Tutorial: streaming estruturado com .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="74f1e-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span> 

<span data-ttu-id="74f1e-104">Este tutorial ensina como invocar o streaming estruturado do Spark usando o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="74f1e-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="74f1e-105">O streaming estruturado do Spark é o suporte de Apache Spark para o processamento de fluxos de dados em tempo real.</span><span class="sxs-lookup"><span data-stu-id="74f1e-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="74f1e-106">Processamento de fluxo significa analisar dados dinâmicos conforme eles estão sendo produzidos.</span><span class="sxs-lookup"><span data-stu-id="74f1e-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="74f1e-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="74f1e-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="74f1e-108">Criar e executar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="74f1e-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="74f1e-109">Usar netcat para criar um fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="74f1e-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="74f1e-110">Usar funções definidas pelo usuário e SparkSQL para analisar dados de streaming</span><span class="sxs-lookup"><span data-stu-id="74f1e-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74f1e-111">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="74f1e-111">Prerequisites</span></span>

<span data-ttu-id="74f1e-112">Se este for seu primeiro aplicativo .NET para Apache Spark, comece com o [tutorial de introdução](get-started.md) para se familiarizar com os conceitos básicos.</span><span class="sxs-lookup"><span data-stu-id="74f1e-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="74f1e-113">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="74f1e-113">Create a console application</span></span>

1. <span data-ttu-id="74f1e-114">No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="74f1e-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```console
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="74f1e-115">O comando `dotnet` cria um aplicativo `new` do tipo `console` para você.</span><span class="sxs-lookup"><span data-stu-id="74f1e-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="74f1e-116">O parâmetro `-o` cria um diretório chamado *mySparkStreamingApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="74f1e-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="74f1e-117">O comando `cd mySparkStreamingApp` altera o diretório para o diretório de aplicativo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="74f1e-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="74f1e-118">Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="74f1e-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="74f1e-119">No console do, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="74f1e-119">In your console, run the following command:</span></span>

   ```console
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="74f1e-120">Estabelecer e conectar-se a um fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="74f1e-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="74f1e-121">Uma maneira popular de testar o processamento de fluxos é por meio de **netcat**.</span><span class="sxs-lookup"><span data-stu-id="74f1e-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="74f1e-122">Netcat (também conhecido como *NC*) permite que você leia e grave em conexões de rede.</span><span class="sxs-lookup"><span data-stu-id="74f1e-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="74f1e-123">Você estabelece uma conexão de rede com o netcat por meio de uma janela de terminal.</span><span class="sxs-lookup"><span data-stu-id="74f1e-123">You establish a network connection with netcat through a terminal window.</span></span> 

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="74f1e-124">Criar um fluxo de dados com netcat</span><span class="sxs-lookup"><span data-stu-id="74f1e-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="74f1e-125">[Baixe o netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="74f1e-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="74f1e-126">Em seguida, extraia o arquivo do download do zip e acrescente o diretório extraído à variável de ambiente "PATH".</span><span class="sxs-lookup"><span data-stu-id="74f1e-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="74f1e-127">Para iniciar uma nova conexão, abra um novo console e execute o comando a seguir que se conecta ao localhost na porta 9999.</span><span class="sxs-lookup"><span data-stu-id="74f1e-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="74f1e-128">No Windows:</span><span class="sxs-lookup"><span data-stu-id="74f1e-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="74f1e-129">No Linux:</span><span class="sxs-lookup"><span data-stu-id="74f1e-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="74f1e-130">O programa Spark escuta a entrada digitada nesse prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="74f1e-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="74f1e-131">Criar um SparkSession</span><span class="sxs-lookup"><span data-stu-id="74f1e-131">Create a SparkSession</span></span>

1. <span data-ttu-id="74f1e-132">Adicione as seguintes instruções `using` adicionais à parte superior do arquivo *Program.cs* em *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="74f1e-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="74f1e-133">Adicione o código a seguir ao seu método de `Main` para criar um novo `SparkSession`.</span><span class="sxs-lookup"><span data-stu-id="74f1e-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="74f1e-134">A sessão do Spark é o ponto de entrada para programar o Spark com o conjunto de e a API dataframe.</span><span class="sxs-lookup"><span data-stu-id="74f1e-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="74f1e-135">Chamar o objeto *Spark* criado acima permite que você acesse a funcionalidade Spark e dataframe em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="74f1e-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="74f1e-136">Conectar-se a um fluxo com ReadStream ()</span><span class="sxs-lookup"><span data-stu-id="74f1e-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="74f1e-137">O método `ReadStream()` retorna um `DataStreamReader` que pode ser usado para ler dados de streaming no como um `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="74f1e-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="74f1e-138">Inclua as informações de host e porta para informar ao aplicativo Spark onde esperar seus dados de streaming.</span><span class="sxs-lookup"><span data-stu-id="74f1e-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="74f1e-139">Registrar uma função definida pelo usuário</span><span class="sxs-lookup"><span data-stu-id="74f1e-139">Register a user-defined function</span></span>

<span data-ttu-id="74f1e-140">Você pode usar UDFs, *funções definidas pelo usuário*, em aplicativos Spark para executar cálculos e análises em seus dados.</span><span class="sxs-lookup"><span data-stu-id="74f1e-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="74f1e-141">Adicione o código a seguir ao seu método de `Main` para registrar um UDF chamado `udfArray`.</span><span class="sxs-lookup"><span data-stu-id="74f1e-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span> 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="74f1e-142">Esse UDF processa cada cadeia de caracteres que recebe do terminal netcat para produzir uma matriz que inclui a cadeia de caracteres original (contida em *Str*), seguida pela cadeia de caracteres original concatenada com o comprimento da cadeia de caracteres original.</span><span class="sxs-lookup"><span data-stu-id="74f1e-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span> 

<span data-ttu-id="74f1e-143">Por exemplo, a inserção de *Olá, mundo* no terminal netcat produz uma matriz em que:</span><span class="sxs-lookup"><span data-stu-id="74f1e-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="74f1e-144">matriz\[0] = Olá, mundo</span><span class="sxs-lookup"><span data-stu-id="74f1e-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="74f1e-145">matriz\[1] = Olá, mundo 11</span><span class="sxs-lookup"><span data-stu-id="74f1e-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="74f1e-146">Usar SparkSQL</span><span class="sxs-lookup"><span data-stu-id="74f1e-146">Use SparkSQL</span></span>

<span data-ttu-id="74f1e-147">Use SparkSQL para executar várias funções nos dados armazenados em seu dataframe.</span><span class="sxs-lookup"><span data-stu-id="74f1e-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="74f1e-148">É comum combinar UDFs e SparkSQL a aplicar um UDF a cada linha de um dataframe.</span><span class="sxs-lookup"><span data-stu-id="74f1e-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="74f1e-149">Esse trecho de código aplica *udfArray* a cada valor em seu dataframe, que representa cada cadeia de caracteres lida do seu terminal netcat.</span><span class="sxs-lookup"><span data-stu-id="74f1e-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="74f1e-150">Aplique o método SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> para colocar cada entrada da matriz em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="74f1e-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="74f1e-151">Por fim, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> para posicionar as colunas que você produziu no novo dataframe *arrayDF.*</span><span class="sxs-lookup"><span data-stu-id="74f1e-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="74f1e-152">Exibir seu fluxo</span><span class="sxs-lookup"><span data-stu-id="74f1e-152">Display your stream</span></span>

<span data-ttu-id="74f1e-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> para estabelecer características de sua saída, como imprimir resultados no console e exibir apenas a saída mais recente.</span><span class="sxs-lookup"><span data-stu-id="74f1e-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="74f1e-154">Executar o código</span><span class="sxs-lookup"><span data-stu-id="74f1e-154">Run your code</span></span>

<span data-ttu-id="74f1e-155">O streaming estruturado no Spark processa dados por meio de uma série de **lotes**pequenos.</span><span class="sxs-lookup"><span data-stu-id="74f1e-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="74f1e-156">Quando você executa o programa, o prompt de comando no qual você estabelece a conexão netcat permite que você comece a digitar.</span><span class="sxs-lookup"><span data-stu-id="74f1e-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="74f1e-157">Cada vez que você pressiona a tecla ENTER depois de digitar dados nesse prompt de comando, o Spark considera sua entrada em um lote e executa o UDF.</span><span class="sxs-lookup"><span data-stu-id="74f1e-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="74f1e-158">Use o Spark-Submit para executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="74f1e-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="74f1e-159">Depois de iniciar uma nova sessão do netcat, abra um novo terminal e execute o comando `spark-submit`, semelhante ao seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="74f1e-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="74f1e-160">Certifique-se de atualizar o comando acima com o caminho real para o arquivo JAR do Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="74f1e-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="74f1e-161">O comando acima também pressupõe que o servidor netcat está em execução na porta localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="74f1e-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="74f1e-162">Obter o código</span><span class="sxs-lookup"><span data-stu-id="74f1e-162">Get the code</span></span>

<span data-ttu-id="74f1e-163">Este tutorial usa o exemplo [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , mas há três outros exemplos de processamento de fluxo completos no github:</span><span class="sxs-lookup"><span data-stu-id="74f1e-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="74f1e-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): contagem de palavras em dados transmitidos de qualquer fonte</span><span class="sxs-lookup"><span data-stu-id="74f1e-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="74f1e-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): contagem de palavras em dados com lógica de janela</span><span class="sxs-lookup"><span data-stu-id="74f1e-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="74f1e-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): contagem de palavras em dados transmitidos de Kafka</span><span class="sxs-lookup"><span data-stu-id="74f1e-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="74f1e-167">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="74f1e-167">Next steps</span></span>

<span data-ttu-id="74f1e-168">Avance para o próximo artigo para saber como implantar seu .NET para Apache Spark aplicativo no databricks.</span><span class="sxs-lookup"><span data-stu-id="74f1e-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="74f1e-169">Tutorial: implantar um aplicativo .NET para Apache Spark no databricks</span><span class="sxs-lookup"><span data-stu-id="74f1e-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
