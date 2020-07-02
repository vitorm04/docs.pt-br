---
title: Enviar um trabalho .NET para Apache Spark para o Azure HDInsight
description: Saiba como enviar um trabalho .NET para Apache Spark para o Azure HDInsight usando Spark-Submit e Apache Livy.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50611b1f62934a446e5b80a8c53698efe23cd1fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617685"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="d9572-103">Enviar um trabalho .NET para Apache Spark para o Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="d9572-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="d9572-104">Há duas maneiras de implantar seu .NET para Apache Spark trabalho para o HDInsight: `spark-submit` e o Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="d9572-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="d9572-105">Implantar usando Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="d9572-105">Deploy using spark-submit</span></span>

<span data-ttu-id="d9572-106">Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="d9572-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="d9572-107">Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **SSH + logon do cluster**.</span><span class="sxs-lookup"><span data-stu-id="d9572-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="d9572-108">Copie as informações de logon SSH e cole o logon em um terminal.</span><span class="sxs-lookup"><span data-stu-id="d9572-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="d9572-109">Entre no cluster usando a senha que você definiu durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="d9572-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="d9572-110">Você deve ver as mensagens com boas-vindas ao Ubuntu e ao Spark.</span><span class="sxs-lookup"><span data-stu-id="d9572-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="d9572-111">Use o comando **Spark-Submit** para executar seu aplicativo em seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="d9572-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="d9572-112">Lembre-se de substituir **MyContainer** e **mystorageaccount** no script de exemplo pelos nomes reais do contêiner de BLOB e da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d9572-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="d9572-113">Além disso, certifique-se de substituir `microsoft-spark-2.3.x-0.6.0.jar` pelo arquivo JAR apropriado que você está usando para a implantação.</span><span class="sxs-lookup"><span data-stu-id="d9572-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="d9572-114">`2.3.x`representa a versão do Apache Spark e `0.6.0` representa a versão do [.net para o trabalho do Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="d9572-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="d9572-115">Implantar usando o Apache Livy</span><span class="sxs-lookup"><span data-stu-id="d9572-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="d9572-116">Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos do .NET para Apache Spark a um cluster do Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="d9572-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="d9572-117">Para obter mais informações, consulte [Trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="d9572-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="d9572-118">Você pode executar o comando a seguir no Linux usando `curl`:</span><span class="sxs-lookup"><span data-stu-id="d9572-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="d9572-119">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d9572-119">Next steps</span></span>

* [<span data-ttu-id="d9572-120">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d9572-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="d9572-121">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="d9572-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="d9572-122">Documentação do HDInsight</span><span class="sxs-lookup"><span data-stu-id="d9572-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
