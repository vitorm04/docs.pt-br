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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="e7c26-103">Envie um trabalho .NET para Apache Spark para o Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="e7c26-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="e7c26-104">Existem duas maneiras de implantar seu trabalho .NET para Apache Spark no HDInsight: `spark-submit` e Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="e7c26-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="e7c26-105">Implantar usando o envio de faíscas</span><span class="sxs-lookup"><span data-stu-id="e7c26-105">Deploy using spark-submit</span></span>

<span data-ttu-id="e7c26-106">Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e7c26-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="e7c26-107">Navegue até o cluster HDInsight Spark no portal Azure e selecione **o login SSH + Cluster**.</span><span class="sxs-lookup"><span data-stu-id="e7c26-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="e7c26-108">Copie as informações de login ssh e cole o login em um terminal.</span><span class="sxs-lookup"><span data-stu-id="e7c26-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="e7c26-109">Faça login no cluster usando a senha definida durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="e7c26-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="e7c26-110">Você deve ver mensagens de boas-vindas ao Ubuntu e ao Spark.</span><span class="sxs-lookup"><span data-stu-id="e7c26-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="e7c26-111">Use o comando **spark-submit** para executar seu aplicativo no cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e7c26-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="e7c26-112">Lembre-se de substituir **mycontainer** e **mystorageaccount** no script de exemplo com os nomes reais de sua conta de contêiner e armazenamento blob.</span><span class="sxs-lookup"><span data-stu-id="e7c26-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="e7c26-113">Além disso, certifique-se de substituir com `microsoft-spark-2.3.x-0.6.0.jar` o arquivo de jarro apropriado que você está usando para implantação.</span><span class="sxs-lookup"><span data-stu-id="e7c26-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="e7c26-114">`2.3.x`representa a versão do Apache `0.6.0` Spark, e representa a versão do [.NET para trabalhador Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="e7c26-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="e7c26-115">Implantar usando Apache Livy</span><span class="sxs-lookup"><span data-stu-id="e7c26-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="e7c26-116">Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos do .NET para Apache Spark a um cluster do Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="e7c26-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="e7c26-117">Para obter mais informações, consulte [Trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="e7c26-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="e7c26-118">Você pode executar o comando a seguir no Linux usando `curl`:</span><span class="sxs-lookup"><span data-stu-id="e7c26-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="e7c26-119">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e7c26-119">Next steps</span></span>

* [<span data-ttu-id="e7c26-120">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e7c26-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="e7c26-121">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="e7c26-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="e7c26-122">Documentação HDInsight</span><span class="sxs-lookup"><span data-stu-id="e7c26-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
