---
title: Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark
description: Descubra como implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5414bc20de3bb90a5d2144bd006d1b859e184a39
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "69576923"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="df0f5-103">Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="df0f5-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="df0f5-104">Este tutorial ensina como implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="df0f5-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="df0f5-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="df0f5-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="df0f5-106">Preparar o Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="df0f5-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="df0f5-107">Publicar seu aplicativo Spark .NET</span><span class="sxs-lookup"><span data-stu-id="df0f5-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="df0f5-108">Implantar seu aplicativo no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="df0f5-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="df0f5-109">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="df0f5-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df0f5-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="df0f5-110">Prerequisites</span></span>

<span data-ttu-id="df0f5-111">Antes de começar, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="df0f5-111">Before you start, do the following:</span></span>

* <span data-ttu-id="df0f5-112">Baixe a [CLI do AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="df0f5-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="df0f5-113">Baixe o [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) no computador local.</span><span class="sxs-lookup"><span data-stu-id="df0f5-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="df0f5-114">Esse é um script auxiliar que você usa posteriormente para copiar o .NET para Apache Spark arquivos dependentes nos nós de trabalho do seu cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="df0f5-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="df0f5-115">Preparar dependências de trabalhador</span><span class="sxs-lookup"><span data-stu-id="df0f5-115">Prepare worker dependencies</span></span>

<span data-ttu-id="df0f5-116">**Microsoft. Spark. Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="df0f5-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="df0f5-117">Quando você deseja executar uma C# UDF (função definida pelo usuário), o Spark precisa entender como iniciar o .NET CLR para executar o UDF.</span><span class="sxs-lookup"><span data-stu-id="df0f5-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="df0f5-118">**O Microsoft. Spark. Worker** fornece uma coleção de classes para Spark que habilitam essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="df0f5-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="df0f5-119">Selecione uma versão do [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) netcoreapp do Linux para ser implantada em seu cluster.</span><span class="sxs-lookup"><span data-stu-id="df0f5-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="df0f5-120">Por exemplo, se você quiser `.NET for Apache Spark v0.1.0` usar `netcoreapp2.1`o, você baixará [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="df0f5-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="df0f5-121">Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, S3) ao qual seu cluster tem acesso.</span><span class="sxs-lookup"><span data-stu-id="df0f5-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="df0f5-122">Preparar o aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="df0f5-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="df0f5-123">Siga o tutorial de [introdução](get-started.md) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df0f5-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="df0f5-124">Publique seu aplicativo .NET Spark como independente.</span><span class="sxs-lookup"><span data-stu-id="df0f5-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="df0f5-125">Execute o seguinte comando no Linux.</span><span class="sxs-lookup"><span data-stu-id="df0f5-125">Run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="df0f5-126">Produzir `<your app>.zip` para os arquivos publicados.</span><span class="sxs-lookup"><span data-stu-id="df0f5-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="df0f5-127">Execute o comando a seguir no Linux `zip`usando.</span><span class="sxs-lookup"><span data-stu-id="df0f5-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="df0f5-128">Carregue os seguintes itens em um sistema de arquivos distribuído (por exemplo, S3) ao qual seu cluster tem acesso:</span><span class="sxs-lookup"><span data-stu-id="df0f5-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="df0f5-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote NuGet do [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída da compilação do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df0f5-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="df0f5-130">Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu aplicativo depende) serão colocados no diretório de trabalho de cada executor.</span><span class="sxs-lookup"><span data-stu-id="df0f5-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="df0f5-131">Implantar no Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="df0f5-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="df0f5-132">O [Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) é uma plataforma de cluster gerenciada que simplifica a execução de estruturas Big data no AWS.</span><span class="sxs-lookup"><span data-stu-id="df0f5-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE] 
> <span data-ttu-id="df0f5-133">O Amazon EMR Spark é baseado em Linux.</span><span class="sxs-lookup"><span data-stu-id="df0f5-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="df0f5-134">Portanto, se você estiver interessado em implantar seu aplicativo no Amazon EMR Spark, verifique se seu aplicativo é .NET Standard compatível e se você usa o [compilador .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df0f5-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="df0f5-135">Implantar Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="df0f5-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="df0f5-136">Esta etapa só é necessária na criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="df0f5-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="df0f5-137">Executar `install-worker.sh` durante a criação do cluster usando [ações de inicialização](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="df0f5-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="df0f5-138">Execute o seguinte comando no Linux usando a CLI do AWS.</span><span class="sxs-lookup"><span data-stu-id="df0f5-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="df0f5-139">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="df0f5-139">Run your app</span></span>

<span data-ttu-id="df0f5-140">Há duas maneiras de executar seu aplicativo no Amazon EMR Spark: Spark-Submit e nas etapas do Amazon EMR.</span><span class="sxs-lookup"><span data-stu-id="df0f5-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="df0f5-141">Usar Spark-enviar</span><span class="sxs-lookup"><span data-stu-id="df0f5-141">Use spark-submit</span></span>

<span data-ttu-id="df0f5-142">Você pode usar o comando [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar Apache Spark trabalhos do .net para o Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="df0f5-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="df0f5-143">`ssh`em um dos nós no cluster.</span><span class="sxs-lookup"><span data-stu-id="df0f5-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="df0f5-144">Execute `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="df0f5-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="df0f5-145">Usar as etapas do Amazon EMR</span><span class="sxs-lookup"><span data-stu-id="df0f5-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="df0f5-146">[As etapas do Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) podem ser usadas para enviar trabalhos para a estrutura do Spark instalada no cluster EMR.</span><span class="sxs-lookup"><span data-stu-id="df0f5-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="df0f5-147">Execute o seguinte comando no Linux usando a CLI do AWS.</span><span class="sxs-lookup"><span data-stu-id="df0f5-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="df0f5-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="df0f5-148">Next steps</span></span>

<span data-ttu-id="df0f5-149">Neste tutorial, você implantou seu .NET para Apache Spark aplicativo para o Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="df0f5-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="df0f5-150">Para .NET para Apache Spark projetos de exemplo, continue no GitHub.</span><span class="sxs-lookup"><span data-stu-id="df0f5-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df0f5-151">.NET para exemplos de Apache Spark</span><span class="sxs-lookup"><span data-stu-id="df0f5-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
