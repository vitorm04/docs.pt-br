---
title: Depurar um aplicativo .NET para Apache Spark no Windows
description: Saiba como depurar seu aplicativo .NET para Apache Spark no Windows.
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 098c7519fe99ef04773c5e4b81685ca0f06f1272
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281525"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Depurar um aplicativo .NET para Apache Spark

Este guia de instruções fornece os comandos de que você precisa executar para depurar o aplicativo .NET para Apache Spark e código Scala no Windows.

## <a name="debug-your-application"></a>Depurar seu aplicativo

Abra uma nova janela do prompt de comando e execute o seguinte:

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

Nesse modo de depuração, o `DotnetRunner` não inicia o aplicativo .NET, mas aguarda até que ele se conecte. Deixe essa janela do prompt de comando aberta.

Agora você pode executar o aplicativo .NET com qualquer depurador para depurar seu aplicativo.

## <a name="debug-scala-code"></a>Depurar código Scala

Se você precisar depurar o código do lado do Scala, como `DotnetRunner` ou `DotnetBackendHandler`, execute o seguinte comando:

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
