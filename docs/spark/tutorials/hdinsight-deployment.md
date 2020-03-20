---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo do .NET para Apache Spark no HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504170"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="0b558-103">Tutorial: Implante um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="0b558-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="0b558-104">Este tutorial ensina como implantar seu aplicativo .NET para Apache Spark na nuvem através de um cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="0b558-105">O HDInsight facilita a criação e a configuração de um cluster Spark no Azure, uma vez que os clusters Spark no HDInsight são compatíveis com o Azure Storage e o Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="0b558-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="0b558-106">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="0b558-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0b558-107">Acesse suas contas de armazenamento usando o Azure Storage Explorer.</span><span class="sxs-lookup"><span data-stu-id="0b558-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="0b558-108">Crie um cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="0b558-109">Publique seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0b558-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="0b558-110">Crie e execute uma ação de script HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="0b558-111">Execute um aplicativo .NET para Apache Spark em um cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b558-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0b558-112">Prerequisites</span></span>

<span data-ttu-id="0b558-113">Antes de começar, faça as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="0b558-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="0b558-114">Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="0b558-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="0b558-115">Faça login no [portal Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="0b558-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="0b558-116">Instale o Azure Storage Explorer no seu computador [Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="0b558-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="0b558-117">Complete o .NET para Apache Spark - Comece no tutorial [de 10 minutos.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)</span><span class="sxs-lookup"><span data-stu-id="0b558-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="0b558-118">Acesse suas contas de armazenamento</span><span class="sxs-lookup"><span data-stu-id="0b558-118">Access your storage accounts</span></span>

1. <span data-ttu-id="0b558-119">Abra o Gerenciador de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="0b558-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="0b558-120">Selecione **Adicionar conta** no menu esquerdo e faça login na sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="0b558-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Faça login na conta do Azure no Storage Explorer](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="0b558-122">Depois de fazer login, você deve ver todas as contas de armazenamento que você tem e quaisquer recursos que você tenha carregado em suas contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0b558-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="0b558-123">Crie um cluster HDInsight</span><span class="sxs-lookup"><span data-stu-id="0b558-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b558-124">O faturamento dos clusters HDInsight é rateado por minuto, mesmo que você não esteja usando-os.</span><span class="sxs-lookup"><span data-stu-id="0b558-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="0b558-125">Exclua seu cluster depois de terminar de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0b558-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="0b558-126">Para obter mais informações, consulte a seção [Limpar recursos](#clean-up-resources) deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="0b558-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="0b558-127">Visite o [Portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0b558-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="0b558-128">Selecione **+ Crie um recurso**.</span><span class="sxs-lookup"><span data-stu-id="0b558-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="0b558-129">Em seguida, selecione **HDInsight** na categoria **Analytics.**</span><span class="sxs-lookup"><span data-stu-id="0b558-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Crie recurso HDInsight a partir do portal Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="0b558-131">Em **Noções básicas**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0b558-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="0b558-132">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0b558-132">Property</span></span>  |<span data-ttu-id="0b558-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b558-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="0b558-134">Subscription</span><span class="sxs-lookup"><span data-stu-id="0b558-134">Subscription</span></span>  | <span data-ttu-id="0b558-135">A partir do drop-down, escolha uma de suas assinaturas ativas do Azure.</span><span class="sxs-lookup"><span data-stu-id="0b558-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="0b558-136">Resource group</span><span class="sxs-lookup"><span data-stu-id="0b558-136">Resource group</span></span> | <span data-ttu-id="0b558-137">Especifique se deseja criar um novo grupo de recursos ou usar um existente.</span><span class="sxs-lookup"><span data-stu-id="0b558-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="0b558-138">Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure.</span><span class="sxs-lookup"><span data-stu-id="0b558-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="0b558-139">Nome do cluster</span><span class="sxs-lookup"><span data-stu-id="0b558-139">Cluster name</span></span> | <span data-ttu-id="0b558-140">Dê um nome para seu cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="0b558-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="0b558-141">Location</span><span class="sxs-lookup"><span data-stu-id="0b558-141">Location</span></span>   | <span data-ttu-id="0b558-142">Selecione um local para o grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="0b558-142">Select a location for the resource group.</span></span> <span data-ttu-id="0b558-143">O modelo usa esse local para criar o cluster, bem como para o armazenamento de cluster padrão.</span><span class="sxs-lookup"><span data-stu-id="0b558-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="0b558-144">Tipo de cluster</span><span class="sxs-lookup"><span data-stu-id="0b558-144">Cluster type</span></span>| <span data-ttu-id="0b558-145">Selecione **Spark** como o tipo de cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="0b558-146">Versão do cluster</span><span class="sxs-lookup"><span data-stu-id="0b558-146">Cluster version</span></span>|<span data-ttu-id="0b558-147">Este campo será preenchido automaticamente com a versão padrão uma vez que o tipo de cluster tenha sido selecionado.</span><span class="sxs-lookup"><span data-stu-id="0b558-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="0b558-148">Selecione uma versão 2.3 ou 2.4 do Spark.</span><span class="sxs-lookup"><span data-stu-id="0b558-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="0b558-149">Nome de usuário de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="0b558-149">Cluster login username</span></span>| <span data-ttu-id="0b558-150">Insira o nome de logon do usuário do cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-150">Enter the cluster login username.</span></span>  <span data-ttu-id="0b558-151">O nome padrão é *admin*.</span><span class="sxs-lookup"><span data-stu-id="0b558-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="0b558-152">Senha de logon do cluster</span><span class="sxs-lookup"><span data-stu-id="0b558-152">Cluster login password</span></span>| <span data-ttu-id="0b558-153">Digite qualquer senha de login.</span><span class="sxs-lookup"><span data-stu-id="0b558-153">Enter any login password.</span></span> |
    |<span data-ttu-id="0b558-154">Nome de usuário do Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="0b558-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="0b558-155">Insira um Nome de Usuário SSH.</span><span class="sxs-lookup"><span data-stu-id="0b558-155">Enter the SSH username.</span></span> <span data-ttu-id="0b558-156">Por padrão, essa conta tem a mesma senha que a conta de*nome de usuário de logon do cluster*.</span><span class="sxs-lookup"><span data-stu-id="0b558-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="0b558-157">Selecione **A seguir: O >>de armazenamento** para continuar na página **Armazenamento.**</span><span class="sxs-lookup"><span data-stu-id="0b558-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="0b558-158">Em **Armazenamento**, forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0b558-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="0b558-159">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0b558-159">Property</span></span>  |<span data-ttu-id="0b558-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b558-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="0b558-161">Tipo de armazenamento primário</span><span class="sxs-lookup"><span data-stu-id="0b558-161">Primary storage type</span></span>|<span data-ttu-id="0b558-162">Use o valor padrão **Armazenamento do Azure**.</span><span class="sxs-lookup"><span data-stu-id="0b558-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="0b558-163">Método de seleção</span><span class="sxs-lookup"><span data-stu-id="0b558-163">Selection method</span></span>|<span data-ttu-id="0b558-164">Use o valor padrão **Selecione na lista**.</span><span class="sxs-lookup"><span data-stu-id="0b558-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="0b558-165">Conta de armazenamento primária</span><span class="sxs-lookup"><span data-stu-id="0b558-165">Primary storage account</span></span>|<span data-ttu-id="0b558-166">Escolha sua assinatura e uma de suas contas de armazenamento ativas dentro dessa assinatura.</span><span class="sxs-lookup"><span data-stu-id="0b558-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="0b558-167">Contêiner</span><span class="sxs-lookup"><span data-stu-id="0b558-167">Container</span></span>|<span data-ttu-id="0b558-168">Este contêiner é o recipiente blob específico em sua conta de armazenamento onde seu cluster procura arquivos para executar seu aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="0b558-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="0b558-169">Você pode dar-lhe qualquer nome disponível.</span><span class="sxs-lookup"><span data-stu-id="0b558-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="0b558-170">Em **Examinar + criar**, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0b558-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="0b558-171">Demora cerca de 20 minutos para criar o cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="0b558-172">O cluster deve ser criado antes que você possa continuar até o próximo passo.</span><span class="sxs-lookup"><span data-stu-id="0b558-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="0b558-173">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b558-173">Publish your app</span></span>

<span data-ttu-id="0b558-174">Em seguida, você publica o *mySparkApp* criado no .NET para Apache Spark - Comece no tutorial [de 10 minutos,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) que dá ao seu cluster Spark acesso a todos os arquivos necessários para executar o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b558-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="0b558-175">Execute os seguintes comandos para publicar o *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="0b558-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="0b558-176">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="0b558-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="0b558-177">**No Linux:**</span><span class="sxs-lookup"><span data-stu-id="0b558-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="0b558-178">Faça as seguintes tarefas para fechar os arquivos do aplicativo publicados para que você possa facilmente carregá-los para o seu cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="0b558-179">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="0b558-179">**On Windows:**</span></span>

   <span data-ttu-id="0b558-180">Navegue até *o mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="0b558-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="0b558-181">Em seguida, clique com o botão direito do mouse na pasta **Publicar** e **selecione Enviar para > pasta Compactada (fechada).**</span><span class="sxs-lookup"><span data-stu-id="0b558-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="0b558-182">Nomeie a nova pasta **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="0b558-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="0b558-183">**No Linux, execute o seguinte comando:**</span><span class="sxs-lookup"><span data-stu-id="0b558-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="0b558-184">Enviar arquivos para o Azure</span><span class="sxs-lookup"><span data-stu-id="0b558-184">Upload files to Azure</span></span>

<span data-ttu-id="0b558-185">Em seguida, você usa o Azure Storage Explorer para carregar os cinco arquivos a seguir para o contêiner blob que você escolheu para o armazenamento do seu cluster:</span><span class="sxs-lookup"><span data-stu-id="0b558-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="0b558-186">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="0b558-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="0b558-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="0b558-187">install-worker.sh</span></span>
* <span data-ttu-id="0b558-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="0b558-188">publish.zip</span></span>
* <span data-ttu-id="0b558-189">microsoft-spark-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="0b558-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="0b558-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="0b558-190">input.txt.</span></span>

1. <span data-ttu-id="0b558-191">Abra o Azure Storage Explorer e navegue até sua conta de armazenamento no menu esquerdo.</span><span class="sxs-lookup"><span data-stu-id="0b558-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="0b558-192">Aprofunde-se no recipiente blob para o cluster em **Blob Containers** em sua conta de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0b558-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="0b558-193">*O Microsoft.Spark.Worker* ajuda o Apache Spark a executar seu aplicativo, como quaisquer funções definidas pelo usuário (UDFs) que você possa ter escrito.</span><span class="sxs-lookup"><span data-stu-id="0b558-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="0b558-194">Baixe [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="0b558-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="0b558-195">Em seguida, **selecione Upload** no Azure Storage Explorer para carregar o trabalhador.</span><span class="sxs-lookup"><span data-stu-id="0b558-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Carregar arquivos para o Azure Storage Explorer](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="0b558-197">O *install-worker.sh* é um script que permite copiar .NET para arquivos dependentes apache spark nos nós do seu cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="0b558-198">Crie um novo arquivo chamado **install-worker.sh** seu computador local e cole o [conteúdo install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no GitHub.</span><span class="sxs-lookup"><span data-stu-id="0b558-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="0b558-199">Em seguida, carregue *install-worker.sh* para o seu recipiente de bolha.</span><span class="sxs-lookup"><span data-stu-id="0b558-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="0b558-200">Seu cluster precisa do arquivo publish.zip que contém os arquivos publicados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b558-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="0b558-201">Navegue até sua pasta publicada, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, e **localize publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="0b558-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="0b558-202">Em seguida, carregue *publish.zip* para o seu recipiente blob.</span><span class="sxs-lookup"><span data-stu-id="0b558-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="0b558-203">Seu cluster precisa do código de aplicativo que foi embalado em um arquivo de frasco.</span><span class="sxs-lookup"><span data-stu-id="0b558-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="0b558-204">Navegue até sua pasta publicada, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, e localize **microsoft-spark-2.3.x-0.3.0.jar**.</span><span class="sxs-lookup"><span data-stu-id="0b558-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="0b558-205">Em seguida, carregue o arquivo do frasco para o recipiente blob.</span><span class="sxs-lookup"><span data-stu-id="0b558-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="0b558-206">Pode haver vários arquivos .jar (para versões 2.3.x e 2.4.x de Spark).</span><span class="sxs-lookup"><span data-stu-id="0b558-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="0b558-207">Você precisa escolher o arquivo .jar que corresponde à versão do Spark que você escolheu durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="0b558-208">Por exemplo, escolha *o microsoft-spark-2.3.x-0.3.0.jar* se você escolheu o Spark 2.3.2 durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="0b558-209">Seu cluster precisa da entrada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b558-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="0b558-210">Navegue até o diretório **mySparkApp** e localize **input.txt**.</span><span class="sxs-lookup"><span data-stu-id="0b558-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="0b558-211">Carregue seu arquivo de entrada para o diretório **usuário/sshuser** no recipiente blob.</span><span class="sxs-lookup"><span data-stu-id="0b558-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="0b558-212">Você estará se conectando ao seu cluster através de ssh, e esta pasta é onde seu cluster procura sua entrada.</span><span class="sxs-lookup"><span data-stu-id="0b558-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="0b558-213">O arquivo *input.txt* é o único arquivo carregado para um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="0b558-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="0b558-214">Execute a ação de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="0b558-214">Run the HDInsight script action</span></span>

<span data-ttu-id="0b558-215">Uma vez que seu cluster está sendo executado e você carregou seus arquivos para o Azure, você executa o **script install-worker.sh** no cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="0b558-216">Navegue até o cluster HDInsight Spark no portal Azure e selecione **ações de script**.</span><span class="sxs-lookup"><span data-stu-id="0b558-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="0b558-217">Selecione **+ Envie novos** e forneça os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0b558-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="0b558-218">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0b558-218">Property</span></span>  |<span data-ttu-id="0b558-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b558-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="0b558-220">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="0b558-220">Script type</span></span> |<span data-ttu-id="0b558-221">Personalizado</span><span class="sxs-lookup"><span data-stu-id="0b558-221">Custom</span></span>|
   | <span data-ttu-id="0b558-222">Nome</span><span class="sxs-lookup"><span data-stu-id="0b558-222">Name</span></span> | <span data-ttu-id="0b558-223">Instalar o Worker</span><span class="sxs-lookup"><span data-stu-id="0b558-223">Install Worker</span></span>|
   | <span data-ttu-id="0b558-224">URI do script Bash</span><span class="sxs-lookup"><span data-stu-id="0b558-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="0b558-225">Para confirmar este URI, clique com o botão direito do mouse em install-worker.sh no Azure Storage Explorer e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="0b558-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="0b558-226">Tipo(s) de nó</span><span class="sxs-lookup"><span data-stu-id="0b558-226">Node type(s)</span></span>| <span data-ttu-id="0b558-227">Trabalho</span><span class="sxs-lookup"><span data-stu-id="0b558-227">Worker</span></span>|
   | <span data-ttu-id="0b558-228">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b558-228">Parameters</span></span> | <span data-ttu-id="0b558-229">azure</span><span class="sxs-lookup"><span data-stu-id="0b558-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="0b558-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="0b558-230">/usr/local/bin</span></span>

3. <span data-ttu-id="0b558-231">Selecione **Criar** para enviar seu script.</span><span class="sxs-lookup"><span data-stu-id="0b558-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="0b558-232">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b558-232">Run your app</span></span>

1. <span data-ttu-id="0b558-233">Navegue até o cluster HDInsight Spark no portal Azure e selecione **o login SSH + Cluster**.</span><span class="sxs-lookup"><span data-stu-id="0b558-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="0b558-234">Copie as informações de login ssh e cole o login em um terminal.</span><span class="sxs-lookup"><span data-stu-id="0b558-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="0b558-235">Faça login no cluster usando a senha definida durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="0b558-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="0b558-236">Você deve ver mensagens de boas-vindas ao Ubuntu e ao Spark.</span><span class="sxs-lookup"><span data-stu-id="0b558-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="0b558-237">Use o comando **spark-submit** para executar seu aplicativo no cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="0b558-238">Lembre-se de substituir **mycontainer** e **mystorageaccount** no script de exemplo com os nomes reais de sua conta de contêiner e armazenamento blob.</span><span class="sxs-lookup"><span data-stu-id="0b558-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="0b558-239">Quando o aplicativo é executado, você vê a mesma tabela de contagem de palavras desde o início da execução local escrita para o console.</span><span class="sxs-lookup"><span data-stu-id="0b558-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="0b558-240">Parabéns, você executou seu primeiro aplicativo .NET para Apache Spark na nuvem!</span><span class="sxs-lookup"><span data-stu-id="0b558-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="0b558-241">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="0b558-241">Clean up resources</span></span>

<span data-ttu-id="0b558-242">O HDInsight salva seus dados no Azure Storage, para que você possa excluir com segurança um cluster quando ele não estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="0b558-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="0b558-243">Você também é cobrado por um cluster HDInsight, mesmo quando ele não está em uso.</span><span class="sxs-lookup"><span data-stu-id="0b558-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="0b558-244">Como os encargos para o cluster são muitas vezes maiores do que os encargos para armazenamento, faz sentido, do ponto de vista econômico, excluir os clusters quando não estiverem em uso.</span><span class="sxs-lookup"><span data-stu-id="0b558-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="0b558-245">Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="0b558-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="0b558-246">Ao excluir o grupo de recursos, você exclui o cluster Spark do HDInsight e a conta de armazenamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0b558-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0b558-247">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0b558-247">Next steps</span></span>

<span data-ttu-id="0b558-248">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="0b558-249">Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="0b558-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b558-250">Documentação do Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="0b558-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
