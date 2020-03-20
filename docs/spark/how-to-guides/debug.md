---
title: Depurar um aplicativo .NET para Apache Spark no Windows
description: Saiba como depurar seu aplicativo .NET para Apache Spark no Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185802"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="ba0ab-103">Depurar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ba0ab-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="ba0ab-104">Este como fazer fornece as etapas para depurar seu aplicativo .NET para Apache Spark no Windows.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="ba0ab-105">Depurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ba0ab-105">Debug your application</span></span>

<span data-ttu-id="ba0ab-106">Abra uma nova janela de solicitação de comando e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ba0ab-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="ba0ab-107">Quando você executa o comando, você vê a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ba0ab-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="ba0ab-108">No modo de depuração, o DotnetRunner não inicia o aplicativo .NET, mas espera que você inicie o aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="ba0ab-109">Deixe esta janela de solicitação de comando aberta e inicie seu aplicativo .NET através do depurador C# para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="ba0ab-110">Inicie seu aplicativo .NET com um depurador C#[(Visual Studio Debugger para Windows/macOS](https://visualstudio.microsoft.com/vs/) ou [C# Debugger Extension in Visual Studio Code)](https://code.visualstudio.com/Docs/editor/debugging)para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="ba0ab-111">Depurar uma função definida pelo usuário (UDF)</span><span class="sxs-lookup"><span data-stu-id="ba0ab-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="ba0ab-112">As funções definidas pelo usuário são suportadas apenas no Windows com o Visual Studio Debugger.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="ba0ab-113">Antes `spark-submit`de executar, defina a seguinte variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="ba0ab-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="ba0ab-114">Quando você executar o `Choose Just-In-Time Debugger` aplicativo Spark, uma janela aparecerá.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="ba0ab-115">Escolha um depurador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="ba0ab-116">O depurador quebrará no seguinte local em [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span><span class="sxs-lookup"><span data-stu-id="ba0ab-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="ba0ab-117">Navegue até o arquivo *.cs* que contém o UDF que você planeja depurar e [defina um ponto de ruptura](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="ba0ab-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="ba0ab-118">O ponto de `The breakpoint will not currently be hit` partida dirá porque o trabalhador ainda não carregou a montagem que contém UDF.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="ba0ab-119">Aperte `F5` para continuar sua aplicação e o ponto de ruptura será eventualmente atingido.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="ba0ab-120">A janela Escolher depurador just-in-time aparece para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="ba0ab-121">Para evitar pop-ups excessivos, defina o número de executores para um número baixo.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="ba0ab-122">Por exemplo, você pode usar a opção **--master local[1]** para enviar faíscas para definir o número de tarefas como 1, que inicia uma única instância de depurador.</span><span class="sxs-lookup"><span data-stu-id="ba0ab-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="ba0ab-123">Depurar código Scala</span><span class="sxs-lookup"><span data-stu-id="ba0ab-123">Debug Scala code</span></span>

<span data-ttu-id="ba0ab-124">Se você precisar depurar o código`DotnetRunner` `DotnetBackendHandler`do lado do Scala (, etc.), você pode usar o seguinte comando e anexar um depurador ao processo de execução usando [o IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span><span class="sxs-lookup"><span data-stu-id="ba0ab-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="ba0ab-125">Após executar o comando, anexe um depurador ao processo em execução usando o [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="ba0ab-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ba0ab-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ba0ab-126">Next steps</span></span>

* [<span data-ttu-id="ba0ab-127">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ba0ab-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="ba0ab-128">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ba0ab-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ba0ab-129">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="ba0ab-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="ba0ab-130">Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="ba0ab-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
