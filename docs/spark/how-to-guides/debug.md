---
title: Depurar um aplicativo .NET para Apache Spark no Windows
description: Saiba como depurar seu aplicativo .NET para Apache Spark no Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206150"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="e1c54-103">Depurar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e1c54-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="e1c54-104">Este guia de instruções fornece os comandos de que você precisa executar para depurar o aplicativo .NET para Apache Spark e código Scala no Windows.</span><span class="sxs-lookup"><span data-stu-id="e1c54-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="e1c54-105">Depurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1c54-105">Debug your application</span></span>

<span data-ttu-id="e1c54-106">Abra uma nova janela do prompt de comando e execute o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e1c54-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="e1c54-107">Quando você executa o comando, você vê a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="e1c54-107">When you run the command, you see the following output:</span></span>

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="e1c54-108">Nesse modo de depuração, o `DotnetRunner` não inicia o aplicativo .NET, mas aguarda até que ele se conecte.</span><span class="sxs-lookup"><span data-stu-id="e1c54-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="e1c54-109">Deixe essa janela do prompt de comando aberta.</span><span class="sxs-lookup"><span data-stu-id="e1c54-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="e1c54-110">Agora você pode executar o aplicativo .NET com qualquer depurador para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1c54-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="e1c54-111">Depurar código Scala</span><span class="sxs-lookup"><span data-stu-id="e1c54-111">Debug Scala code</span></span>

<span data-ttu-id="e1c54-112">Se você precisar depurar o código do lado do Scala, como `DotnetRunner` ou `DotnetBackendHandler`, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e1c54-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="e1c54-113">Após executar o comando, anexe um depurador ao processo em execução usando o [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span><span class="sxs-lookup"><span data-stu-id="e1c54-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e1c54-114">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e1c54-114">Next steps</span></span>

* [<span data-ttu-id="e1c54-115">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e1c54-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="e1c54-116">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="e1c54-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="e1c54-117">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="e1c54-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="e1c54-118">Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="e1c54-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
