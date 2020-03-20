---
title: Envie um trabalho .NET para Apache Spark para o Azure HDInsight
description: Saiba como enviar um trabalho .NET para Apache Spark para o Azure HDInsight usando spark-submit e Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185794"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Envie um trabalho .NET para Apache Spark para o Azure HDInsight

Existem duas maneiras de implantar seu trabalho .NET para Apache Spark no HDInsight: `spark-submit` e Apache Livy.

## <a name="deploy-using-spark-submit"></a>Implantar usando o envio de faíscas

Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.

1. Navegue até o cluster HDInsight Spark no portal Azure e selecione **o login SSH + Cluster**.

2. Copie as informações de login ssh e cole o login em um terminal. Faça login no cluster usando a senha definida durante a criação do cluster. Você deve ver mensagens de boas-vindas ao Ubuntu e ao Spark.

3. Use o comando **spark-submit** para executar seu aplicativo no cluster HDInsight. Lembre-se de substituir **mycontainer** e **mystorageaccount** no script de exemplo com os nomes reais de sua conta de contêiner e armazenamento blob. Além disso, certifique-se de substituir com `microsoft-spark-2.3.x-0.6.0.jar` o arquivo de jarro apropriado que você está usando para implantação. `2.3.x`representa a versão do Apache `0.6.0` Spark, e representa a versão do [.NET para trabalhador Apache Spark](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Implantar usando Apache Livy

Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos do .NET para Apache Spark a um cluster do Azure HDInsight Spark. Para obter mais informações, consulte [Trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Você pode executar o comando a seguir no Linux usando `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao .NET para Apache Spark](../tutorials/get-started.md)
* [Implantar um aplicativo .NET para Apache Spark no Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Documentação HDInsight](https://docs.microsoft.com/azure/hdinsight/)
