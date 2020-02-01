---
title: Depurar um aplicativo .NET para Apache Spark no Windows
description: Saiba como depurar seu aplicativo .NET para Apache Spark no Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 25f5291c47dc1cdf2668cb077fae7439e330cc1c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919932"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="e4ded-103">Depurar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e4ded-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="e4ded-104">Este "como" fornece as etapas para depurar o aplicativo .NET para Apache Spark no Windows.</span><span class="sxs-lookup"><span data-stu-id="e4ded-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="e4ded-105">Depurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e4ded-105">Debug your application</span></span>

<span data-ttu-id="e4ded-106">Abra uma nova janela de prompt de comando e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e4ded-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="e4ded-107">Quando você executa o comando, você vê a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e4ded-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="e4ded-108">No modo de depuração, o DotnetRunner não inicia o aplicativo .NET, mas, em vez disso, espera que você inicie o aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="e4ded-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="e4ded-109">Deixe essa janela de prompt de comando aberta e inicie o aplicativo C# .net por meio do depurador para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4ded-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="e4ded-110">Inicie seu aplicativo .NET com um C# depurador ([depurador do Visual Studio para Windows/MacOS](https://visualstudio.microsoft.com/vs/) ou [ C# extensão do depurador no Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4ded-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="e4ded-111">Depurar uma UDF (função definida pelo usuário)</span><span class="sxs-lookup"><span data-stu-id="e4ded-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="e4ded-112">As funções definidas pelo usuário têm suporte apenas no Windows com o depurador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4ded-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="e4ded-113">Antes de executar `spark-submit`, defina a seguinte variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="e4ded-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="e4ded-114">Quando você executar o aplicativo Spark, uma janela `Choose Just-In-Time Debugger` será exibida.</span><span class="sxs-lookup"><span data-stu-id="e4ded-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="e4ded-115">Escolha um depurador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4ded-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="e4ded-116">O depurador será interrompido no seguinte local em [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="e4ded-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="e4ded-117">Navegue até o arquivo *. cs* que contém o UDF que você planeja depurar e [defina um ponto de interrupção](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="e4ded-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="e4ded-118">O ponto de interrupção dirá `The breakpoint will not currently be hit` porque o trabalho ainda não carregou o assembly que contém o UDF.</span><span class="sxs-lookup"><span data-stu-id="e4ded-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="e4ded-119">Pressione `F5` para continuar seu aplicativo e o ponto de interrupção eventualmente será atingido.</span><span class="sxs-lookup"><span data-stu-id="e4ded-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE] 
> <span data-ttu-id="e4ded-120">A janela escolher depurador just-in-time é exibida para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="e4ded-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="e4ded-121">Para evitar pop-ups em excesso, defina o número de executores como um número baixo.</span><span class="sxs-lookup"><span data-stu-id="e4ded-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="e4ded-122">Por exemplo, você pode usar a opção **--Master local [1]** para o Spark-Submit para definir o número de tarefas como 1, que inicia uma única instância do depurador.</span><span class="sxs-lookup"><span data-stu-id="e4ded-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="e4ded-123">Depurar código Scala</span><span class="sxs-lookup"><span data-stu-id="e4ded-123">Debug Scala code</span></span>

<span data-ttu-id="e4ded-124">Se você precisar depurar o código do lado do escala (`DotnetRunner`, `DotnetBackendHandler`, etc.), poderá usar o comando a seguir e anexar um depurador ao processo em execução usando [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="e4ded-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="e4ded-125">Após executar o comando, anexe um depurador ao processo em execução usando o [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="e4ded-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4ded-126">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4ded-126">Next steps</span></span>

* [<span data-ttu-id="e4ded-127">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e4ded-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="e4ded-128">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="e4ded-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="e4ded-129">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="e4ded-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="e4ded-130">Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="e4ded-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
