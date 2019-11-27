---
title: Enviar um trabalho .NET para Apache Spark para o Azure HDInsight
description: Saiba como enviar um trabalho .NET para Apache Spark para o Azure HDInsight usando Spark-Submit e Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cdd5e15ffde78ccb8b3156ee047b8ca98f7320b8
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74553007"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Enviar um trabalho .NET para Apache Spark para o Azure HDInsight

Há duas maneiras de implantar seu .NET para Apache Spark trabalho para HDInsight: `spark-submit` e Apache Livy.

## <a name="deploy-using-spark-submit"></a>Implantar usando Spark-Submit

Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.
 
1. Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **SSH + logon do cluster**.

2. Copie as informações de logon SSH e cole o logon em um terminal. Entre no cluster usando a senha que você definiu durante a criação do cluster. Você deve ver as mensagens com boas-vindas ao Ubuntu e ao Spark.

3. Use o comando **Spark-Submit** para executar seu aplicativo em seu cluster HDInsight. Lembre-se de substituir **MyContainer** e **mystorageaccount** no script de exemplo pelos nomes reais do contêiner de BLOB e da conta de armazenamento. Além disso, certifique-se de substituir `microsoft-spark-2.3.x-0.6.0.jar` pelo arquivo JAR apropriado que você está usando para implantação. `2.3.x` representa a versão do Apache Spark e `0.6.0` representa a versão do [.net para Apache Spark Worker](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Implantar usando o Apache Livy

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
* [Documentação do HDInsight](https://docs.microsoft.com/azure/hdinsight/)
