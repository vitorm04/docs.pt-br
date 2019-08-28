---
title: Implantar um aplicativo .NET para Apache Spark no Databricks
description: Descubra como implantar um aplicativo do .NET para Apache Spark no Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "69576963"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="2ebb7-103">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="2ebb7-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="2ebb7-104">Este tutorial ensina a implantar um aplicativo do .NET para Apache Spark para o Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="2ebb7-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="2ebb7-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="2ebb7-106">Preparar o Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="2ebb7-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="2ebb7-107">Publicar seu aplicativo Spark .NET</span><span class="sxs-lookup"><span data-stu-id="2ebb7-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="2ebb7-108">Implantar seu aplicativo no Databricks</span><span class="sxs-lookup"><span data-stu-id="2ebb7-108">Deploy your app to Databricks</span></span>
> * <span data-ttu-id="2ebb7-109">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ebb7-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ebb7-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2ebb7-110">Prerequisites</span></span>

<span data-ttu-id="2ebb7-111">Antes de começar, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ebb7-111">Before you start, do the following:</span></span>

* <span data-ttu-id="2ebb7-112">Baixe a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="2ebb7-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
* <span data-ttu-id="2ebb7-113">Baixe o [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="2ebb7-114">Esse é um script auxiliar que você usa posteriormente para copiar arquivos dependentes do .NET para Apache Spark para os nós de trabalho do cluster do Spark.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="2ebb7-115">Preparar dependências de trabalho</span><span class="sxs-lookup"><span data-stu-id="2ebb7-115">Prepare worker dependencies</span></span>

<span data-ttu-id="2ebb7-116">O **Microsoft.Spark.Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster do Spark.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="2ebb7-117">Quando você deseja executar uma UDF (função definida pelo usuário) em C#, o Spark precisa entender como iniciar o CLR .NET para executar a UDF.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="2ebb7-118">O **Microsoft.Spark.Worker** fornece uma coleção de classes para o Spark que habilitam essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="2ebb7-119">Selecione uma versão do netcoreapp do Linux do [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) para ser implantada em seu cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="2ebb7-120">Por exemplo, se quiser `.NET for Apache Spark v0.1.0` usando o `netcoreapp2.1`, você baixará o [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="2ebb7-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="2ebb7-121">Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, DBFS) ao qual seu cluster tem acesso.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="2ebb7-122">Preparar seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="2ebb7-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="2ebb7-123">Siga o tutorial de [Introdução](get-started.md) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="2ebb7-124">Publique seu aplicativo .NET do Spark como independente.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="2ebb7-125">Você pode executar o comando a seguir no Linux.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="2ebb7-126">Produza `<your app>.zip` para os arquivos publicados.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="2ebb7-127">Você pode executar o comando a seguir no Linux usando `zip`.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="2ebb7-128">Carregue o seguinte para um sistema de arquivos distribuído (por exemplo, DBFS) ao qual seu cluster tem acesso:</span><span class="sxs-lookup"><span data-stu-id="2ebb7-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   * <span data-ttu-id="2ebb7-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote do NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída do build do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="2ebb7-130">Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu aplicativo depende) serão colocados no diretório de trabalho de cada executor.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="2ebb7-131">Implantar no Databricks</span><span class="sxs-lookup"><span data-stu-id="2ebb7-131">Deploy to Databricks</span></span>

<span data-ttu-id="2ebb7-132">O [Databricks](https://databricks.com) é uma plataforma que fornece processamento de Big Data baseado em nuvem usando o Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="2ebb7-133">O [Azure Databricks](https://azure.microsoft.com/services/databricks/) e o [AWS Databricks](https://databricks.com/aws) são baseados em Linux.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="2ebb7-134">Portanto, se você estiver interessado em implantar seu aplicativo no Databricks, verifique se ele é compatível com o .Net Standard e se você usa o [compilador do .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="2ebb7-135">O Databricks permite que você envie aplicativos .NET para Apache Spark a um cluster ativo existente ou crie um novo cluster sempre que iniciar um trabalho.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="2ebb7-136">Isso exige que o **Microsoft.Spark.Worker** seja instalado antes de você enviar um aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="2ebb7-137">Implantar o Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="2ebb7-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="2ebb7-138">Esta etapa é necessária apenas uma vez para um cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="2ebb7-139">Baixe [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="2ebb7-140">Modifique **db-init.sh** para apontar para a versão do **Microsoft.Spark.Worker** que você deseja baixar e instalar em seu cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="2ebb7-141">Instale a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="2ebb7-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="2ebb7-142">Detalhes de [Configurar autenticação](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) para a CLI do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="2ebb7-143">Carregue os arquivos para o cluster do Databricks usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2ebb7-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="2ebb7-144">Vá para seu espaço de trabalho do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="2ebb7-145">Selecione **Clusters** no menu do lado esquerdo e, em seguida, selecione **Criar Cluster**.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="2ebb7-146">Depois de configurar o cluster adequadamente, defina o **Script Init** e crie o cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Imagem de Ação do Script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="2ebb7-148">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ebb7-148">Run your app</span></span> 

<span data-ttu-id="2ebb7-149">Você pode usar `set JAR` ou `spark-submit` para enviar o trabalho para o Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="2ebb7-150">Usar o Set JAR</span><span class="sxs-lookup"><span data-stu-id="2ebb7-150">Use Set JAR</span></span>

<span data-ttu-id="2ebb7-151">O [Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) permite que você envie um trabalho para um cluster ativo existente.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="2ebb7-152">Configuração única</span><span class="sxs-lookup"><span data-stu-id="2ebb7-152">One-time setup</span></span>

1. <span data-ttu-id="2ebb7-153">Acesse seu cluster do Databricks e selecione **Trabalhos** no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="2ebb7-154">Em seguida, selecione **Set JAR**.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="2ebb7-155">Carregue o arquivo `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` apropriado.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="2ebb7-156">Defina os parâmetros adequadamente.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="2ebb7-157">Configure o **Cluster** para apontar para o cluster existente criado no **Init Script** na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="2ebb7-158">Publicar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ebb7-158">Publish and run your app</span></span>

1. <span data-ttu-id="2ebb7-159">Use a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) para carregar seu aplicativo para o cluster do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="2ebb7-160">Esta etapa será necessária apenas se os assemblies do aplicativo (por exemplo, DLLs que contêm funções definidas pelo usuário junto com as respectivas dependências) precisarem ser colocados no diretório de trabalho de cada **Microsoft.Spark.Worker**.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="2ebb7-161">Carregar os assemblies do aplicativo para o cluster do Databricks</span><span class="sxs-lookup"><span data-stu-id="2ebb7-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="2ebb7-162">Remova a marca de comentário e modifique a seção de dependências do aplicativo em [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) para apontar para o caminho de dependências do aplicativo e carregar para o cluster do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="2ebb7-163">Reinicie seu cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-163">Restart your cluster.</span></span>

3. <span data-ttu-id="2ebb7-164">Vá para o cluster do Databricks em seu workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="2ebb7-165">Em **Trabalhos**, selecione seu trabalho e, em seguida, selecione **Executar Agora** para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="2ebb7-166">Usar spark-submit</span><span class="sxs-lookup"><span data-stu-id="2ebb7-166">Use spark-submit</span></span>

<span data-ttu-id="2ebb7-167">O comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) permite que você envie um trabalho para um novo cluster.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="2ebb7-168">[Crie um trabalho](https://docs.databricks.com/user-guide/jobs.html) e selecione **configurar spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="2ebb7-169">Configure `spark-submit` com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="2ebb7-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="2ebb7-170">Vá para o cluster do Databricks em seu workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="2ebb7-171">Em **Trabalhos**, selecione seu trabalho e, em seguida, selecione **Executar Agora** para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ebb7-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2ebb7-172">Next steps</span></span>

<span data-ttu-id="2ebb7-173">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="2ebb7-174">Para saber mais sobre o Databricks, leia a documentação do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="2ebb7-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ebb7-175">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="2ebb7-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
