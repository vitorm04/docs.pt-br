---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo do .NET para Apache Spark no HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 81d1af1fd4e3329c4a289eea388edf8af57d7c4e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243943"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="13e41-103">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="13e41-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="13e41-104">Este tutorial ensina a implantar um aplicativo do .NET para Apache Spark no Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="13e41-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="13e41-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="13e41-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="13e41-106">Preparar o Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="13e41-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="13e41-107">Publicar seu aplicativo Spark .NET</span><span class="sxs-lookup"><span data-stu-id="13e41-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="13e41-108">Implantar seu aplicativo no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="13e41-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="13e41-109">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="13e41-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13e41-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="13e41-110">Prerequisites</span></span>

<span data-ttu-id="13e41-111">Antes de começar, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="13e41-111">Before you start, do the following:</span></span>

* <span data-ttu-id="13e41-112">Baixe o [Gerenciador de Armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="13e41-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="13e41-113">Baixe o [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="13e41-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="13e41-114">Esse é um script auxiliar que você usa posteriormente para copiar arquivos dependentes do .NET para Apache Spark para os nós de trabalho do cluster do Spark.</span><span class="sxs-lookup"><span data-stu-id="13e41-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="13e41-115">Preparar dependências de trabalho</span><span class="sxs-lookup"><span data-stu-id="13e41-115">Prepare worker dependencies</span></span>

<span data-ttu-id="13e41-116">O **Microsoft.Spark.Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster do Spark.</span><span class="sxs-lookup"><span data-stu-id="13e41-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="13e41-117">Quando você deseja executar uma UDF (função definida pelo usuário) em C#, o Spark precisa entender como iniciar o CLR .NET para executar a UDF.</span><span class="sxs-lookup"><span data-stu-id="13e41-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="13e41-118">O **Microsoft.Spark.Worker** fornece uma coleção de classes para o Spark que habilitam essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="13e41-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="13e41-119">Selecione uma versão do netcoreapp do Linux do [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) para ser implantada em seu cluster.</span><span class="sxs-lookup"><span data-stu-id="13e41-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="13e41-120">Por exemplo, se quiser `.NET for Apache Spark v0.1.0` usando o `netcoreapp2.1`, você baixará o [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="13e41-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="13e41-121">Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso.</span><span class="sxs-lookup"><span data-stu-id="13e41-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="13e41-122">Preparar seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="13e41-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="13e41-123">Siga o tutorial de [Introdução](get-started.md) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13e41-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="13e41-124">Publique seu aplicativo .NET do Spark como independente.</span><span class="sxs-lookup"><span data-stu-id="13e41-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="13e41-125">Você pode executar o comando a seguir no Linux.</span><span class="sxs-lookup"><span data-stu-id="13e41-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="13e41-126">Produza `<your app>.zip` para os arquivos publicados.</span><span class="sxs-lookup"><span data-stu-id="13e41-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="13e41-127">Você pode executar o comando a seguir no Linux usando `zip`.</span><span class="sxs-lookup"><span data-stu-id="13e41-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="13e41-128">Carregue o seguinte para um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso:</span><span class="sxs-lookup"><span data-stu-id="13e41-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="13e41-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote do NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída do build do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13e41-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="13e41-130">Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou Assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu `app` depende) serão colocados no diretório de trabalho de cada executor.</span><span class="sxs-lookup"><span data-stu-id="13e41-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="13e41-131">Implantar no Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="13e41-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="13e41-132">O [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) é a implementação da Microsoft do Apache Spark na nuvem que permite que os usuários iniciem e configurem clusters do Spark no Azure.</span><span class="sxs-lookup"><span data-stu-id="13e41-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="13e41-133">Você pode usar clusters do Spark do HDInsight para processar seus dados armazenados no [Armazenamento do Azure](https://azure.microsoft.com/services/storage/) ou no [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span><span class="sxs-lookup"><span data-stu-id="13e41-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="13e41-134">O Azure HDInsight Spark é baseado em Linux.</span><span class="sxs-lookup"><span data-stu-id="13e41-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="13e41-135">Se você estiver interessado em implantar seu aplicativo no Azure HDInsight Spark, verifique se seu aplicativo é compatível com o .Net Standard e se você usa o [compilador do .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13e41-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="13e41-136">Implantar o Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="13e41-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="13e41-137">Esta etapa é necessária apenas uma vez para seu cluster.</span><span class="sxs-lookup"><span data-stu-id="13e41-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="13e41-138">Execute `install-worker.sh` no cluster usando as [Ações de Script do HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="13e41-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="13e41-139">Configuração</span><span class="sxs-lookup"><span data-stu-id="13e41-139">Setting</span></span>|<span data-ttu-id="13e41-140">Valor</span><span class="sxs-lookup"><span data-stu-id="13e41-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="13e41-141">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="13e41-141">Script type</span></span>|<span data-ttu-id="13e41-142">Personalizado</span><span class="sxs-lookup"><span data-stu-id="13e41-142">Custom</span></span>|
|<span data-ttu-id="13e41-143">Nome</span><span class="sxs-lookup"><span data-stu-id="13e41-143">Name</span></span>|<span data-ttu-id="13e41-144">Instalar o Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="13e41-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="13e41-145">URI do script bash</span><span class="sxs-lookup"><span data-stu-id="13e41-145">Bash script URI</span></span>|<span data-ttu-id="13e41-146">O URI para o qual você carregou `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="13e41-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="13e41-147">Por exemplo, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span><span class="sxs-lookup"><span data-stu-id="13e41-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="13e41-148">Tipo (s) de nó</span><span class="sxs-lookup"><span data-stu-id="13e41-148">Node type(s)</span></span>|<span data-ttu-id="13e41-149">Funcionários</span><span class="sxs-lookup"><span data-stu-id="13e41-149">Worker</span></span>|
|<span data-ttu-id="13e41-150">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13e41-150">Parameters</span></span>|<span data-ttu-id="13e41-151">Parâmetros para `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="13e41-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="13e41-152">Por exemplo, se você carregasse o `install-worker.sh` para o Azure Data Lake Gen 2, ele seria `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span><span class="sxs-lookup"><span data-stu-id="13e41-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Imagem de Ação do Script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="13e41-154">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="13e41-154">Run your app</span></span>

<span data-ttu-id="13e41-155">Você pode enviar seu trabalho para o Azure HDInsight usando `spark-submit` o ou o Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="13e41-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="13e41-156">Usar spark-submit</span><span class="sxs-lookup"><span data-stu-id="13e41-156">Use spark-submit</span></span>

<span data-ttu-id="13e41-157">Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="13e41-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="13e41-158">`ssh` em um dos nós de cabeçalho no cluster.</span><span class="sxs-lookup"><span data-stu-id="13e41-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="13e41-159">Executar `spark-submit`:</span><span class="sxs-lookup"><span data-stu-id="13e41-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="13e41-160">Usar o Apache Livy</span><span class="sxs-lookup"><span data-stu-id="13e41-160">Use Apache Livy</span></span>

<span data-ttu-id="13e41-161">Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos do .NET para Apache Spark a um cluster do Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="13e41-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="13e41-162">Para obter mais informações, consulte [Trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="13e41-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="13e41-163">Você pode executar o comando a seguir no Linux usando `curl`:</span><span class="sxs-lookup"><span data-stu-id="13e41-163">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="13e41-164">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="13e41-164">Next steps</span></span>

<span data-ttu-id="13e41-165">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="13e41-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="13e41-166">Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="13e41-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13e41-167">Documentação do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="13e41-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
