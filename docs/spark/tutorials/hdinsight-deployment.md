---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo do .NET para Apache Spark no HDInsight.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c745231f76142c11002ac6663906c8c44c69cdae
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223359"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="6203b-103">Tutorial: implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="6203b-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="6203b-104">Este tutorial ensina como implantar seu .NET para Apache Spark aplicativo na nuvem por meio de um cluster do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="6203b-105">O HDInsight facilita a criação e a configuração de um cluster Spark no Azure, pois os clusters do Spark no HDInsight são compatíveis com o armazenamento do Azure e Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="6203b-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="6203b-106">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="6203b-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="6203b-107">Acesse suas contas de armazenamento usando Gerenciador de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="6203b-108">Crie um cluster HDInsight do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="6203b-109">Publique seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="6203b-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="6203b-110">Crie e execute uma ação de script do HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="6203b-111">Execute um aplicativo .NET para Apache Spark em um cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6203b-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6203b-112">Prerequisites</span></span>

<span data-ttu-id="6203b-113">Antes de começar, execute as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="6203b-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="6203b-114">Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="6203b-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="6203b-115">Entre no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="6203b-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="6203b-116">Instale o Gerenciador de Armazenamento do Azure em seu computador [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .</span><span class="sxs-lookup"><span data-stu-id="6203b-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="6203b-117">Conclua o [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="6203b-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="6203b-118">Acessar suas contas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="6203b-118">Access your storage accounts</span></span>

1. <span data-ttu-id="6203b-119">Abra o Gerenciador de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="6203b-120">Selecione **adicionar conta** no menu à esquerda e entre em sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Entrar na conta do Azure de Gerenciador de Armazenamento](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="6203b-122">Depois de entrar, você deverá ver todas as contas de armazenamento que você tem e todos os recursos que você carregou em suas contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6203b-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="6203b-123">Crie um cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="6203b-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6203b-124">A cobrança por clusters HDInsight é rateada por minuto, mesmo se você não os estiver usando.</span><span class="sxs-lookup"><span data-stu-id="6203b-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="6203b-125">Exclua seu cluster depois de terminar de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="6203b-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="6203b-126">Para obter mais informações, consulte a seção [limpar recursos](#clean-up-resources) deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6203b-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="6203b-127">Visite o [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="6203b-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="6203b-128">Selecione **+ Criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="6203b-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="6203b-129">Em seguida, selecione **HDInsight** na categoria **análise** .</span><span class="sxs-lookup"><span data-stu-id="6203b-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Criar recurso do HDInsight a partir de portal do Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="6203b-131">Em **Noções básicas**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6203b-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="6203b-132">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6203b-132">Property</span></span>  |<span data-ttu-id="6203b-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="6203b-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="6203b-134">Subscription</span><span class="sxs-lookup"><span data-stu-id="6203b-134">Subscription</span></span>  | <span data-ttu-id="6203b-135">Na lista suspensa, escolha uma das suas assinaturas ativas do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="6203b-136">Grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="6203b-136">Resource group</span></span> | <span data-ttu-id="6203b-137">Especifique se deseja criar um novo grupo de recursos ou usar um existente.</span><span class="sxs-lookup"><span data-stu-id="6203b-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="6203b-138">Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure.</span><span class="sxs-lookup"><span data-stu-id="6203b-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="6203b-139">Nome do cluster</span><span class="sxs-lookup"><span data-stu-id="6203b-139">Cluster name</span></span> | <span data-ttu-id="6203b-140">Dê um nome para seu cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="6203b-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="6203b-141">Location</span><span class="sxs-lookup"><span data-stu-id="6203b-141">Location</span></span>   | <span data-ttu-id="6203b-142">Selecione um local para o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="6203b-142">Select a location for the resource group.</span></span> <span data-ttu-id="6203b-143">O modelo usa esse local para criar o cluster, bem como para o armazenamento de cluster padrão.</span><span class="sxs-lookup"><span data-stu-id="6203b-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="6203b-144">Tipo de cluster</span><span class="sxs-lookup"><span data-stu-id="6203b-144">Cluster type</span></span>| <span data-ttu-id="6203b-145">Selecione **Spark** como o tipo de cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="6203b-146">Versão do cluster</span><span class="sxs-lookup"><span data-stu-id="6203b-146">Cluster version</span></span>|<span data-ttu-id="6203b-147">Este campo será preenchido automaticamente com a versão padrão depois que o tipo de cluster tiver sido selecionado.</span><span class="sxs-lookup"><span data-stu-id="6203b-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="6203b-148">Selecione uma versão 2,3 ou 2,4 do Spark.</span><span class="sxs-lookup"><span data-stu-id="6203b-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="6203b-149">Nome de usuário de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="6203b-149">Cluster login username</span></span>| <span data-ttu-id="6203b-150">Insira o nome de logon do usuário do cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-150">Enter the cluster login username.</span></span>  <span data-ttu-id="6203b-151">O nome padrão é *admin*.</span><span class="sxs-lookup"><span data-stu-id="6203b-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="6203b-152">Senha de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="6203b-152">Cluster login password</span></span>| <span data-ttu-id="6203b-153">Insira qualquer senha de logon.</span><span class="sxs-lookup"><span data-stu-id="6203b-153">Enter any login password.</span></span> |
    |<span data-ttu-id="6203b-154">Nome de usuário do Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="6203b-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="6203b-155">Insira um Nome de Usuário SSH.</span><span class="sxs-lookup"><span data-stu-id="6203b-155">Enter the SSH username.</span></span> <span data-ttu-id="6203b-156">Por padrão, essa conta tem a mesma senha que a conta de*nome de usuário de logon do cluster*.</span><span class="sxs-lookup"><span data-stu-id="6203b-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="6203b-157">Selecione **Avançar: Armazenamento >>** para continuar para a página **Armazenamento**.</span><span class="sxs-lookup"><span data-stu-id="6203b-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="6203b-158">Em **Armazenamento**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6203b-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="6203b-159">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6203b-159">Property</span></span>  |<span data-ttu-id="6203b-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="6203b-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="6203b-161">Tipo de armazenamento primário</span><span class="sxs-lookup"><span data-stu-id="6203b-161">Primary storage type</span></span>|<span data-ttu-id="6203b-162">Use o valor padrão **Armazenamento do Azure**.</span><span class="sxs-lookup"><span data-stu-id="6203b-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="6203b-163">Método de seleção</span><span class="sxs-lookup"><span data-stu-id="6203b-163">Selection method</span></span>|<span data-ttu-id="6203b-164">Use o valor padrão **Selecione na lista**.</span><span class="sxs-lookup"><span data-stu-id="6203b-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="6203b-165">Conta de armazenamento primária</span><span class="sxs-lookup"><span data-stu-id="6203b-165">Primary storage account</span></span>|<span data-ttu-id="6203b-166">Escolha sua assinatura e uma de suas contas de armazenamento ativas nessa assinatura.</span><span class="sxs-lookup"><span data-stu-id="6203b-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="6203b-167">Contêiner</span><span class="sxs-lookup"><span data-stu-id="6203b-167">Container</span></span>|<span data-ttu-id="6203b-168">Esse contêiner é o contêiner de blob específico em sua conta de armazenamento em que o cluster procura arquivos para executar seu aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="6203b-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="6203b-169">Você pode dar a ele qualquer nome disponível.</span><span class="sxs-lookup"><span data-stu-id="6203b-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="6203b-170">Em **Examinar + criar**, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="6203b-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="6203b-171">Demora cerca de 20 minutos para criar o cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="6203b-172">O cluster deve ser criado para que você possa continuar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="6203b-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="6203b-173">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6203b-173">Publish your app</span></span>

<span data-ttu-id="6203b-174">Em seguida, você publica o *mySparkApp* criado no [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) , que dá acesso ao cluster Spark a todos os arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6203b-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="6203b-175">Execute os seguintes comandos para publicar o *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="6203b-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="6203b-176">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="6203b-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="6203b-177">**No Linux:**</span><span class="sxs-lookup"><span data-stu-id="6203b-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="6203b-178">Execute as seguintes tarefas para compactar seus arquivos de aplicativo publicados para que você possa carregá-los facilmente em seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span> <span data-ttu-id="6203b-179">Zip o conteúdo da pasta de publicação, *publish.zip* por exemplo, que foi criado como resultado da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="6203b-179">Zip the contents of the publish folder, *publish.zip* for example, that was created as a result of Step 1.</span></span> <span data-ttu-id="6203b-180">Todos os assemblies devem estar na primeira camada do arquivo ZIP e não deve haver nenhuma camada de pasta intermediária.</span><span class="sxs-lookup"><span data-stu-id="6203b-180">All the assemblies should be in the first layer of the ZIP file and there should be no intermediate folder layer.</span></span> <span data-ttu-id="6203b-181">Isso significa que, quando você descompactar *publish.zip*, todos os assemblies são extraídos em seu diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="6203b-181">This means when you unzip *publish.zip*, all assemblies are extracted into your current working directory.</span></span>

   <span data-ttu-id="6203b-182">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="6203b-182">**On Windows:**</span></span>

   <span data-ttu-id="6203b-183">Use um programa de extração, como 7-zip ou WinZip, para extrair o arquivo para o diretório bin com todos os binários publicados.</span><span class="sxs-lookup"><span data-stu-id="6203b-183">Use an extraction program, like 7-Zip or WinZip, to extract the file into the bin directory with all the published binaries.</span></span>

   <span data-ttu-id="6203b-184">**No Linux, execute o seguinte comando:**</span><span class="sxs-lookup"><span data-stu-id="6203b-184">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="6203b-185">Carregar arquivos no Azure</span><span class="sxs-lookup"><span data-stu-id="6203b-185">Upload files to Azure</span></span>

<span data-ttu-id="6203b-186">Em seguida, use o Gerenciador de Armazenamento do Azure para carregar os cinco arquivos a seguir no contêiner de BLOBs que você escolheu para o armazenamento do cluster:</span><span class="sxs-lookup"><span data-stu-id="6203b-186">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="6203b-187">Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="6203b-187">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="6203b-188">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="6203b-188">install-worker.sh</span></span>
* <span data-ttu-id="6203b-189">publish.zip</span><span class="sxs-lookup"><span data-stu-id="6203b-189">publish.zip</span></span>
* <span data-ttu-id="6203b-190">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="6203b-190">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="6203b-191">input.txt.</span><span class="sxs-lookup"><span data-stu-id="6203b-191">input.txt.</span></span>

1. <span data-ttu-id="6203b-192">Abra Gerenciador de Armazenamento do Azure e navegue até sua conta de armazenamento no menu à esquerda.</span><span class="sxs-lookup"><span data-stu-id="6203b-192">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="6203b-193">Faça uma busca detalhada no contêiner de BLOBs do cluster em **contêineres de blob** em sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6203b-193">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="6203b-194">O *Microsoft. Spark. Worker* ajuda a Apache Spark executar seu aplicativo, como qualquer UDFs (funções definidas pelo usuário) que você possa ter escrito.</span><span class="sxs-lookup"><span data-stu-id="6203b-194">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="6203b-195">Baixe [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="6203b-195">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="6203b-196">Em seguida, selecione **carregar** em Gerenciador de armazenamento do Azure para carregar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="6203b-196">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Carregar arquivos para Gerenciador de Armazenamento do Azure](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="6203b-198">O *install-Worker.sh* é um script que permite que você copie o .net para Apache Spark arquivos dependentes nos nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-198">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="6203b-199">Crie um novo arquivo chamado **install-Worker.sh** seu computador local e cole o [conteúdo do install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no github.</span><span class="sxs-lookup"><span data-stu-id="6203b-199">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="6203b-200">Em seguida, carregue *install-Worker.sh* em seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="6203b-200">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="6203b-201">O cluster precisa do arquivo de publish.zip que contém os arquivos publicados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6203b-201">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="6203b-202">Navegue até a pasta publicada, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, e localize **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="6203b-202">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="6203b-203">Em seguida, carregue *publish.zip* em seu contêiner de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="6203b-203">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="6203b-204">O cluster precisa do código do aplicativo que foi empacotado em um arquivo jar.</span><span class="sxs-lookup"><span data-stu-id="6203b-204">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="6203b-205">Navegue até a pasta publicada, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**, e localize **Microsoft-Spark-2.3. x-0.3.0. jar**.</span><span class="sxs-lookup"><span data-stu-id="6203b-205">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="6203b-206">Em seguida, carregue o arquivo jar em seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="6203b-206">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="6203b-207">Pode haver vários arquivos. jar (para as versões 2.3. x e 2.4. x do Spark).</span><span class="sxs-lookup"><span data-stu-id="6203b-207">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="6203b-208">Você precisa escolher o arquivo. jar que corresponde à versão do Spark escolhida durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-208">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="6203b-209">Por exemplo, escolha *Microsoft-Spark-2.3. x-0.3.0. jar* se você escolheu Spark 2.3.2 durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-209">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="6203b-210">O cluster precisa da entrada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6203b-210">Your cluster needs the input to your app.</span></span> <span data-ttu-id="6203b-211">Navegue até o diretório **mySparkApp** e localize **input.txt**.</span><span class="sxs-lookup"><span data-stu-id="6203b-211">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="6203b-212">Carregue o arquivo de entrada no diretório **User/sshuser** no seu contêiner de BLOB.</span><span class="sxs-lookup"><span data-stu-id="6203b-212">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="6203b-213">Você se conectará ao cluster por meio de SSH e essa pasta será onde o cluster procurará sua entrada.</span><span class="sxs-lookup"><span data-stu-id="6203b-213">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="6203b-214">O arquivo de *input.txt* é o único arquivo carregado em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="6203b-214">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="6203b-215">Executar a ação de script do HDInsight</span><span class="sxs-lookup"><span data-stu-id="6203b-215">Run the HDInsight script action</span></span>

<span data-ttu-id="6203b-216">Depois que o cluster estiver em execução e você carregou seus arquivos no Azure, execute o script **install-Worker.sh** no cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-216">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="6203b-217">Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **ações de script**.</span><span class="sxs-lookup"><span data-stu-id="6203b-217">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="6203b-218">Selecione **+ Enviar novo** e forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6203b-218">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="6203b-219">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6203b-219">Property</span></span>  |<span data-ttu-id="6203b-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="6203b-220">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="6203b-221">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="6203b-221">Script type</span></span> |<span data-ttu-id="6203b-222">Personalizado</span><span class="sxs-lookup"><span data-stu-id="6203b-222">Custom</span></span>|
   | <span data-ttu-id="6203b-223">Nome</span><span class="sxs-lookup"><span data-stu-id="6203b-223">Name</span></span> | <span data-ttu-id="6203b-224">Instalar trabalho</span><span class="sxs-lookup"><span data-stu-id="6203b-224">Install Worker</span></span>|
   | <span data-ttu-id="6203b-225">URI do script Bash</span><span class="sxs-lookup"><span data-stu-id="6203b-225">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="6203b-226">Para confirmar esse URI, clique com o botão direito do mouse em install-worker.sh em Gerenciador de Armazenamento do Azure e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="6203b-226">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="6203b-227">Tipo(s) de nó</span><span class="sxs-lookup"><span data-stu-id="6203b-227">Node type(s)</span></span>| <span data-ttu-id="6203b-228">Trabalho</span><span class="sxs-lookup"><span data-stu-id="6203b-228">Worker</span></span>|
   | <span data-ttu-id="6203b-229">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6203b-229">Parameters</span></span> | <span data-ttu-id="6203b-230">azure</span><span class="sxs-lookup"><span data-stu-id="6203b-230">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="6203b-231">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="6203b-231">/usr/local/bin</span></span>

3. <span data-ttu-id="6203b-232">Selecione **criar** para enviar o script.</span><span class="sxs-lookup"><span data-stu-id="6203b-232">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="6203b-233">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="6203b-233">Run your app</span></span>

1. <span data-ttu-id="6203b-234">Navegue até o cluster HDInsight Spark no portal do Azure e, em seguida, selecione **SSH + logon do cluster**.</span><span class="sxs-lookup"><span data-stu-id="6203b-234">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="6203b-235">Copie as informações de logon SSH e cole o logon em um terminal.</span><span class="sxs-lookup"><span data-stu-id="6203b-235">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="6203b-236">Entre no cluster usando a senha que você definiu durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="6203b-236">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="6203b-237">Você deve ver as mensagens com boas-vindas ao Ubuntu e ao Spark.</span><span class="sxs-lookup"><span data-stu-id="6203b-237">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="6203b-238">Use o comando **Spark-Submit** para executar seu aplicativo em seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-238">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="6203b-239">Lembre-se de substituir **MyContainer** e **mystorageaccount** no script de exemplo pelos nomes reais do contêiner de BLOB e da conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6203b-239">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="6203b-240">Quando seu aplicativo for executado, você verá a mesma tabela de contagem de palavras da execução local de introdução gravada no console.</span><span class="sxs-lookup"><span data-stu-id="6203b-240">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="6203b-241">Parabéns, você executou seu primeiro .NET para Apache Spark aplicativo na nuvem!</span><span class="sxs-lookup"><span data-stu-id="6203b-241">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="6203b-242">Limpar os recursos</span><span class="sxs-lookup"><span data-stu-id="6203b-242">Clean up resources</span></span>

<span data-ttu-id="6203b-243">O HDInsight salva seus dados no armazenamento do Azure, para que você possa excluir um cluster com segurança quando ele não estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="6203b-243">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="6203b-244">Você também é cobrado por um cluster HDInsight, mesmo quando ele não está em uso.</span><span class="sxs-lookup"><span data-stu-id="6203b-244">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="6203b-245">Como os encargos para o cluster são muitas vezes maiores do que os encargos para armazenamento, faz sentido, do ponto de vista econômico, excluir os clusters quando não estiverem em uso.</span><span class="sxs-lookup"><span data-stu-id="6203b-245">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="6203b-246">Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="6203b-246">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="6203b-247">Ao excluir o grupo de recursos, você exclui o cluster Spark do HDInsight e a conta de armazenamento padrão.</span><span class="sxs-lookup"><span data-stu-id="6203b-247">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6203b-248">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6203b-248">Next steps</span></span>

<span data-ttu-id="6203b-249">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-249">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="6203b-250">Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="6203b-250">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6203b-251">Documentação do HDInsight do Azure</span><span class="sxs-lookup"><span data-stu-id="6203b-251">Azure HDInsight Documentation</span></span>](/azure/hdinsight/)
