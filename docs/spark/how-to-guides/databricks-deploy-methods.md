---
title: Envie um trabalho .NET para Apache Spark para Databricks
description: Saiba como enviar um trabalho .NET para Apache Spark para Databricks usando spark-submit e Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187602"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="19952-103">Envie um trabalho .NET para Apache Spark para Databricks</span><span class="sxs-lookup"><span data-stu-id="19952-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="19952-104">Existem duas maneiras de implantar seu trabalho .NET `spark-submit` para Apache Spark no Databricks: e Definir Jar.</span><span class="sxs-lookup"><span data-stu-id="19952-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="19952-105">Implantar usando o envio de faíscas</span><span class="sxs-lookup"><span data-stu-id="19952-105">Deploy using spark-submit</span></span>

<span data-ttu-id="19952-106">Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar .NET para trabalhos do Apache Spark para Databricks.</span><span class="sxs-lookup"><span data-stu-id="19952-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="19952-107">`spark-submit`permite a submissão apenas a um cluster que é criado demanda.</span><span class="sxs-lookup"><span data-stu-id="19952-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="19952-108">Navegue até o seu Databricks Workspace e crie um trabalho.</span><span class="sxs-lookup"><span data-stu-id="19952-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="19952-109">Escolha um título para o seu trabalho e, em seguida, selecione **Configurar envio de faíscas**.</span><span class="sxs-lookup"><span data-stu-id="19952-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="19952-110">Cole os seguintes parâmetros na configuração do trabalho e **selecione Confirmar**.</span><span class="sxs-lookup"><span data-stu-id="19952-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="19952-111">Atualize o conteúdo do parâmetro acima com base em seus arquivos e configuração específicos.</span><span class="sxs-lookup"><span data-stu-id="19952-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="19952-112">Por exemplo, faça referência à versão do arquivo de jaro Microsoft.Spark que você carregou para o DBFS e use o nome apropriado do seu aplicativo e publicado arquivo zip do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19952-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="19952-113">Navegue até o seu trabalho e selecione **Editar** para configurar o cluster do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="19952-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="19952-114">Defina a versão de tempo de execução de databricks com base na versão do Apache Spark que deseja usar em sua implantação.</span><span class="sxs-lookup"><span data-stu-id="19952-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="19952-115">Em seguida, selecione **Opções Avançadas > Scripts Init**e defina Init Script Path como `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="19952-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="19952-116">Selecione **Confirmar** para confirmar as configurações do cluster.</span><span class="sxs-lookup"><span data-stu-id="19952-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="19952-117">Navegue até o seu trabalho e selecione **Executar agora** para executar seu trabalho no cluster Spark recém-configurado.</span><span class="sxs-lookup"><span data-stu-id="19952-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="19952-118">Leva alguns minutos para o cluster do trabalho ser criado.</span><span class="sxs-lookup"><span data-stu-id="19952-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="19952-119">Uma vez criado, seu trabalho será submetido.</span><span class="sxs-lookup"><span data-stu-id="19952-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="19952-120">Você pode exibir a saída selecionando **Clusters** no menu esquerdo do espaço de trabalho databricks e, em seguida, selecione **Registros de driver**.</span><span class="sxs-lookup"><span data-stu-id="19952-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="19952-121">Implantar usando set jar</span><span class="sxs-lookup"><span data-stu-id="19952-121">Deploy using Set Jar</span></span>

<span data-ttu-id="19952-122">Alternativamente, você pode usar [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) em seu espaço de trabalho Databricks para enviar .NET para trabalhos Apache Spark para Databricks.</span><span class="sxs-lookup"><span data-stu-id="19952-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="19952-123">*Set Jar* permite a submissão de trabalho a um cluster ativo existente.</span><span class="sxs-lookup"><span data-stu-id="19952-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="19952-124">Configuração única</span><span class="sxs-lookup"><span data-stu-id="19952-124">One-time setup</span></span>

1. <span data-ttu-id="19952-125">Navegue até o cluster Databricks e selecione **Trabalhos** no menu do lado esquerdo, seguido por **Set JAR**.</span><span class="sxs-lookup"><span data-stu-id="19952-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="19952-126">Faça o `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`upload do apropriado .</span><span class="sxs-lookup"><span data-stu-id="19952-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="19952-127">Modifique os seguintes parâmetros para incluir o nome `<your-app-name>`correto para o executável que você publicou no lugar de :</span><span class="sxs-lookup"><span data-stu-id="19952-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="19952-128">Configure o cluster para apontar para um cluster existente para o qual você já definiu o script init.</span><span class="sxs-lookup"><span data-stu-id="19952-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="19952-129">Publicar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="19952-129">Publish and run your app</span></span>

1. <span data-ttu-id="19952-130">Certifique-se de que você publicou seu aplicativo `SparkSession.Stop()`e que seu código de aplicativo não use .</span><span class="sxs-lookup"><span data-stu-id="19952-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="19952-131">Use [o Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) para carregar seu aplicativo no cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="19952-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="19952-132">Por exemplo, use o seguinte comando para carregar seu aplicativo publicado no cluster:</span><span class="sxs-lookup"><span data-stu-id="19952-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="19952-133">Se você tiver alguma função definida pelo usuário em seu aplicativo, os conjuntos de aplicativos, como DLLs que contêm funções definidas pelo usuário, juntamente com suas dependências, precisam ser colocados no diretório de trabalho de cada *Microsoft.Spark.Worker*.</span><span class="sxs-lookup"><span data-stu-id="19952-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="19952-134">Carregue seus conjuntos de aplicativos para o cluster Databricks:</span><span class="sxs-lookup"><span data-stu-id="19952-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="19952-135">Descomentar e modificar a seção dependências do aplicativo em [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) apontar para o caminho das dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19952-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="19952-136">Em seguida, carregue o *db-init.sh* atualizado para o seu cluster:</span><span class="sxs-lookup"><span data-stu-id="19952-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="19952-137">Navegue até **o cluster Databricks > Jobs > [Nome do trabalho] > Execute agora** para executar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="19952-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19952-138">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="19952-138">Next steps</span></span>

* [<span data-ttu-id="19952-139">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="19952-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="19952-140">Implantar um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="19952-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="19952-141">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="19952-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
