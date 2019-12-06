---
title: Enviar um trabalho .NET para Apache Spark para o databricks
description: Saiba como enviar um .NET para Apache Spark trabalho para o databricks usando Spark-Submit e Set jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9cd3d40871d4600660957ec268f192ef3e045845
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838347"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="64f24-103">Enviar um trabalho .NET para Apache Spark para o databricks</span><span class="sxs-lookup"><span data-stu-id="64f24-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="64f24-104">Há duas maneiras de implantar seu .NET para Apache Spark trabalho no databricks: `spark-submit` e definir jar.</span><span class="sxs-lookup"><span data-stu-id="64f24-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span> 

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="64f24-105">Implantar usando Spark-Submit</span><span class="sxs-lookup"><span data-stu-id="64f24-105">Deploy using spark-submit</span></span>

<span data-ttu-id="64f24-106">Você pode usar o comando [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar o .net para trabalhos do Apache Spark para o databricks.</span><span class="sxs-lookup"><span data-stu-id="64f24-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="64f24-107">`spark-submit` permite enviar somente para um cluster que é criado sob demanda.</span><span class="sxs-lookup"><span data-stu-id="64f24-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="64f24-108">Navegue até o espaço de trabalho do databricks e crie um trabalho.</span><span class="sxs-lookup"><span data-stu-id="64f24-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="64f24-109">Escolha um título para seu trabalho e, em seguida, selecione **Configurar Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="64f24-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="64f24-110">Cole os seguintes parâmetros na configuração do trabalho e, em seguida, selecione **confirmar**.</span><span class="sxs-lookup"><span data-stu-id="64f24-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="64f24-111">Atualize o conteúdo do parâmetro acima com base em seus arquivos e configurações específicos.</span><span class="sxs-lookup"><span data-stu-id="64f24-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="64f24-112">Por exemplo, referencie a versão do arquivo JAR do Microsoft. Spark que você carregou em DBFS e use o nome apropriado do seu aplicativo e o arquivo zip do aplicativo publicado.</span><span class="sxs-lookup"><span data-stu-id="64f24-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="64f24-113">Navegue até seu trabalho e selecione **Editar** para configurar o cluster do trabalho.</span><span class="sxs-lookup"><span data-stu-id="64f24-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="64f24-114">Defina a versão Databricks Runtime com base na versão do Apache Spark que você deseja usar em sua implantação.</span><span class="sxs-lookup"><span data-stu-id="64f24-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="64f24-115">Em seguida, selecione **Opções avançadas > scripts de inicialização**e defina caminho do script de inicialização como `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="64f24-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="64f24-116">Selecione **confirmar** para confirmar as configurações de cluster.</span><span class="sxs-lookup"><span data-stu-id="64f24-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="64f24-117">Navegue até seu trabalho e selecione **executar agora** para executar seu trabalho em seu cluster Spark recém configurado.</span><span class="sxs-lookup"><span data-stu-id="64f24-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="64f24-118">Leva alguns minutos para que o cluster do trabalho seja criado.</span><span class="sxs-lookup"><span data-stu-id="64f24-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="64f24-119">Depois que ele for criado, seu trabalho será enviado.</span><span class="sxs-lookup"><span data-stu-id="64f24-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="64f24-120">Você pode exibir a saída selecionando **clusters** no menu à esquerda do seu espaço de trabalho do databricks e, em seguida, selecionar **logs de driver**.</span><span class="sxs-lookup"><span data-stu-id="64f24-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="64f24-121">Implantar usando Set jar</span><span class="sxs-lookup"><span data-stu-id="64f24-121">Deploy using Set Jar</span></span>

<span data-ttu-id="64f24-122">Como alternativa, você pode usar [set jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) em seu espaço de trabalho do databricks para enviar Apache Spark trabalhos do .net para o databricks.</span><span class="sxs-lookup"><span data-stu-id="64f24-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="64f24-123">*Set jar* permite o envio de trabalhos para um cluster ativo existente.</span><span class="sxs-lookup"><span data-stu-id="64f24-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="64f24-124">Configuração única</span><span class="sxs-lookup"><span data-stu-id="64f24-124">One-time setup</span></span>

1. <span data-ttu-id="64f24-125">Navegue até o cluster do databricks e selecione **trabalhos** no menu do lado esquerdo, seguido por **set jar**.</span><span class="sxs-lookup"><span data-stu-id="64f24-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="64f24-126">Carregue o `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`apropriado.</span><span class="sxs-lookup"><span data-stu-id="64f24-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="64f24-127">Modifique os seguintes parâmetros para incluir o nome correto para o executável que você publicou no lugar do `<your-app-name>`:</span><span class="sxs-lookup"><span data-stu-id="64f24-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="64f24-128">Configure o cluster para apontar para um cluster existente para o qual você já definiu o script de inicialização.</span><span class="sxs-lookup"><span data-stu-id="64f24-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="64f24-129">Publicar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="64f24-129">Publish and run your app</span></span>

1. <span data-ttu-id="64f24-130">Verifique se você publicou seu aplicativo e se o código do aplicativo não usa `SparkSession.Stop()`.</span><span class="sxs-lookup"><span data-stu-id="64f24-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="64f24-131">Use a [CLI do databricks](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) para carregar seu aplicativo em seu cluster do databricks.</span><span class="sxs-lookup"><span data-stu-id="64f24-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="64f24-132">Por exemplo, use o seguinte comando para carregar seu aplicativo publicado em seu cluster:</span><span class="sxs-lookup"><span data-stu-id="64f24-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="64f24-133">Se você tiver funções definidas pelo usuário em seu aplicativo, os assemblies de aplicativo, como DLLs que contêm funções definidas pelo usuário, juntamente com suas dependências, precisam ser colocados no diretório de trabalho de cada *Microsoft. Spark. Worker*.</span><span class="sxs-lookup"><span data-stu-id="64f24-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="64f24-134">Carregue seus assemblies de aplicativo em seu cluster do databricks:</span><span class="sxs-lookup"><span data-stu-id="64f24-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="64f24-135">Remova a marca de comentário e modifique a seção de dependências do aplicativo em [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) para apontar para o caminho de dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64f24-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="64f24-136">Em seguida, carregue o *DB-init.sh* atualizado em seu cluster:</span><span class="sxs-lookup"><span data-stu-id="64f24-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="64f24-137">Navegue até **cluster do databricks > trabalhos > [nome-do-trabalho] > executar agora** para executar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="64f24-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="64f24-138">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="64f24-138">Next steps</span></span>

* [<span data-ttu-id="64f24-139">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="64f24-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="64f24-140">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="64f24-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="64f24-141">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="64f24-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
