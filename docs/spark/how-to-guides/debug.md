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
# <a name="debug-a-net-for-apache-spark-application"></a>Depurar um aplicativo .NET para Apache Spark

Este como fazer fornece as etapas para depurar seu aplicativo .NET para Apache Spark no Windows.

## <a name="debug-your-application"></a>Depurar seu aplicativo

Abra uma nova janela de solicitação de comando e execute o seguinte comando:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Quando você executa o comando, você vê a seguinte saída:

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

No modo de depuração, o DotnetRunner não inicia o aplicativo .NET, mas espera que você inicie o aplicativo .NET. Deixe esta janela de solicitação de comando aberta e inicie seu aplicativo .NET através do depurador C# para depurar seu aplicativo. Inicie seu aplicativo .NET com um depurador C#[(Visual Studio Debugger para Windows/macOS](https://visualstudio.microsoft.com/vs/) ou [C# Debugger Extension in Visual Studio Code)](https://code.visualstudio.com/Docs/editor/debugging)para depurar seu aplicativo.

## <a name="debug-a-user-defined-function-udf"></a>Depurar uma função definida pelo usuário (UDF)

> [!NOTE]
> As funções definidas pelo usuário são suportadas apenas no Windows com o Visual Studio Debugger.

Antes `spark-submit`de executar, defina a seguinte variável de ambiente:

```bat
set DOTNET_WORKER_DEBUG=1
```

Quando você executar o `Choose Just-In-Time Debugger` aplicativo Spark, uma janela aparecerá. Escolha um depurador do Visual Studio.

O depurador quebrará no seguinte local em [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

Navegue até o arquivo *.cs* que contém o UDF que você planeja depurar e [defina um ponto de ruptura](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019). O ponto de `The breakpoint will not currently be hit` partida dirá porque o trabalhador ainda não carregou a montagem que contém UDF.

Aperte `F5` para continuar sua aplicação e o ponto de ruptura será eventualmente atingido.

> [!NOTE]
> A janela Escolher depurador just-in-time aparece para cada tarefa. Para evitar pop-ups excessivos, defina o número de executores para um número baixo. Por exemplo, você pode usar a opção **--master local[1]** para enviar faíscas para definir o número de tarefas como 1, que inicia uma única instância de depurador.

## <a name="debug-scala-code"></a>Depurar código Scala

Se você precisar depurar o código`DotnetRunner` `DotnetBackendHandler`do lado do Scala (, etc.), você pode usar o seguinte comando e anexar um depurador ao processo de execução usando [o IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Após executar o comando, anexe um depurador ao processo em execução usando o [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao .NET para Apache Spark](../tutorials/get-started.md)
* [Implantar um aplicativo .NET para Apache Spark no Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Implantar um aplicativo .NET para Apache Spark no Databricks](../tutorials/databricks-deployment.md)
* [Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
