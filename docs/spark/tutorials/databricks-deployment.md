---
title: Implantar um aplicativo .NET para Apache Spark no Databricks
description: Descubra como implantar um aplicativo do .NET para Apache Spark no Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dfd33e83c04428b7a6a72e4992c40f00982b1958
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960468"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="e74cd-103">Tutorial: implantar um aplicativo .NET para Apache Spark no databricks</span><span class="sxs-lookup"><span data-stu-id="e74cd-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="e74cd-104">Este tutorial ensina como implantar seu aplicativo na nuvem por meio de Azure Databricks, uma plataforma de análise baseada em Apache Spark com instalação com um clique, fluxos de trabalho simplificados e espaço de trabalho interativo que permite a colaboração.</span><span class="sxs-lookup"><span data-stu-id="e74cd-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="e74cd-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="e74cd-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e74cd-106">Criar um workspace do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="e74cd-107">Publique seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="e74cd-108">Crie um trabalho do Spark e um cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="e74cd-109">Execute seu aplicativo no cluster do Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e74cd-110">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e74cd-110">Prerequisites</span></span>

<span data-ttu-id="e74cd-111">Antes de começar, execute as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="e74cd-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="e74cd-112">Se você não tiver uma conta do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e74cd-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="e74cd-113">Entre no [Portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="e74cd-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="e74cd-114">Conclua o [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="e74cd-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="e74cd-115">Criar um workspace do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e74cd-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="e74cd-116">Este tutorial não pode ser realizado usando a **Assinatura de avaliação gratuita do Azure**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="e74cd-117">Se você tiver uma conta gratuita, acesse seu perfil e altere para uma assinatura **pré-paga**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="e74cd-118">Para saber mais, confira [Conta gratuita do Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e74cd-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="e74cd-119">Em seguida, [remova o limite de gastos](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit) e [solicite um aumento de cota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) para as vCPUs da sua região.</span><span class="sxs-lookup"><span data-stu-id="e74cd-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="e74cd-120">Quando você cria seu espaço de trabalho do Azure Databricks, pode selecionar o tipo de preço **Versão de avaliação (Premium - DBUs gratuitas por 14 dias)** para conceder ao espaço de trabalho acesso gratuito aos DBUs do Premium Azure Databricks por 14 dias.</span><span class="sxs-lookup"><span data-stu-id="e74cd-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="e74cd-121">Nesta seção, você deve cria um workspace do Azure Databricks usando o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="e74cd-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="e74cd-122">No Portal do Azure, selecione **Criar um recurso** > **Análise** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Criar um recurso de Azure Databricks no portal do Azure](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="e74cd-124">Em **Serviço do Azure Databricks**, forneça os valores para criar um workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="e74cd-125">propriedade</span><span class="sxs-lookup"><span data-stu-id="e74cd-125">Property</span></span>  |<span data-ttu-id="e74cd-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e74cd-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="e74cd-127">**Nome do workspace**</span><span class="sxs-lookup"><span data-stu-id="e74cd-127">**Workspace name**</span></span>     | <span data-ttu-id="e74cd-128">Forneça um nome para o seu workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="e74cd-129">**Assinatura**</span><span class="sxs-lookup"><span data-stu-id="e74cd-129">**Subscription**</span></span>     | <span data-ttu-id="e74cd-130">Na lista suspensa, selecione sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="e74cd-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="e74cd-131">**Grupo de recursos**</span><span class="sxs-lookup"><span data-stu-id="e74cd-131">**Resource group**</span></span>     | <span data-ttu-id="e74cd-132">Especifique se deseja criar um novo grupo de recursos ou usar um existente.</span><span class="sxs-lookup"><span data-stu-id="e74cd-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="e74cd-133">Um grupo de recursos é um contêiner que armazena os recursos relacionados de uma solução do Azure.</span><span class="sxs-lookup"><span data-stu-id="e74cd-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="e74cd-134">Para obter mais informações, consulte [Visão geral do Grupo de Recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="e74cd-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="e74cd-135">**Local**</span><span class="sxs-lookup"><span data-stu-id="e74cd-135">**Location**</span></span>     | <span data-ttu-id="e74cd-136">Selecione sua região preferida.</span><span class="sxs-lookup"><span data-stu-id="e74cd-136">Select your preferred region.</span></span> <span data-ttu-id="e74cd-137">Para obter informações sobre regiões disponíveis, consulte [Serviços do Azure disponíveis por região](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="e74cd-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="e74cd-138">**Tipo de Preço**</span><span class="sxs-lookup"><span data-stu-id="e74cd-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="e74cd-139">Escolha entre o cluster **Standard**, **Premium** ou **Avaliação**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="e74cd-140">Para saber mais sobre essas camadas, confira [Página de preços do Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="e74cd-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="e74cd-141">**Rede Virtual**</span><span class="sxs-lookup"><span data-stu-id="e74cd-141">**Virtual Network**</span></span>     |   <span data-ttu-id="e74cd-142">Não</span><span class="sxs-lookup"><span data-stu-id="e74cd-142">No</span></span>       |

3. <span data-ttu-id="e74cd-143">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-143">Select **Create**.</span></span> <span data-ttu-id="e74cd-144">A criação do workspace leva alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="e74cd-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="e74cd-145">Durante a criação do workspace, você pode exibir o status da implantação em **Notificações**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="e74cd-146">Instalar ferramentas de Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e74cd-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="e74cd-147">Você pode usar a **CLI do databricks** para se conectar a Azure Databricks clusters e carregar arquivos para eles no computador local.</span><span class="sxs-lookup"><span data-stu-id="e74cd-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="e74cd-148">Os clusters do databricks acessam arquivos por meio do DBFS (sistema de arquivos do databricks).</span><span class="sxs-lookup"><span data-stu-id="e74cd-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="e74cd-149">A CLI do databricks requer o Python 3,6 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e74cd-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="e74cd-150">Se você já tiver o Python instalado, poderá ignorar esta etapa.</span><span class="sxs-lookup"><span data-stu-id="e74cd-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="e74cd-151">**Para Windows:**</span><span class="sxs-lookup"><span data-stu-id="e74cd-151">**For Windows:**</span></span>

   [<span data-ttu-id="e74cd-152">Baixar o Python para Windows</span><span class="sxs-lookup"><span data-stu-id="e74cd-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="e74cd-153">**Para Linux:** O Python vem pré-instalado na maioria das distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="e74cd-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="e74cd-154">Execute o seguinte comando para ver qual versão você instalou:</span><span class="sxs-lookup"><span data-stu-id="e74cd-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="e74cd-155">Use o Pip para instalar a CLI do databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="e74cd-156">Python 3,4 e posterior incluem Pip por padrão.</span><span class="sxs-lookup"><span data-stu-id="e74cd-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="e74cd-157">Use pip3 para Python 3.</span><span class="sxs-lookup"><span data-stu-id="e74cd-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="e74cd-158">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e74cd-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="e74cd-159">Depois de instalar a CLI do databricks, abra um novo prompt de comando e execute o comando `databricks`.</span><span class="sxs-lookup"><span data-stu-id="e74cd-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="e74cd-160">Se você receber um **"databricks" não é reconhecido como um erro de comando interno ou externo**, certifique-se de que você abriu um novo prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e74cd-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="e74cd-161">Configurar Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e74cd-161">Set up Azure Databricks</span></span>

<span data-ttu-id="e74cd-162">Agora que a CLI do databricks está instalada, você precisa configurar os detalhes de autenticação.</span><span class="sxs-lookup"><span data-stu-id="e74cd-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="e74cd-163">Execute o `databricks configure --token`de comando da CLI do databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="e74cd-164">Depois de executar o comando configurar, você será solicitado a inserir um host.</span><span class="sxs-lookup"><span data-stu-id="e74cd-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="e74cd-165">A URL do host usa o formato: **https://< \Location >. azuredatabricks. net**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="e74cd-166">Por exemplo, se você selecionou **eastus2** durante a criação Azure Databricks serviço, o host seria **https://eastus2.azuredatabricks.net** .</span><span class="sxs-lookup"><span data-stu-id="e74cd-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="e74cd-167">Depois de inserir o host, você será solicitado a inserir um token.</span><span class="sxs-lookup"><span data-stu-id="e74cd-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="e74cd-168">Na portal do Azure, selecione **Iniciar espaço de trabalho** para iniciar o espaço de trabalho do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Iniciar Azure Databricks espaço de trabalho](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="e74cd-170">Na home page do espaço de trabalho, selecione **configurações do usuário**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Configurações do usuário no espaço de trabalho Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="e74cd-172">Na página Configurações do usuário, você pode gerar um novo token.</span><span class="sxs-lookup"><span data-stu-id="e74cd-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="e74cd-173">Copie o token gerado e cole-o de volta no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e74cd-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Gerar novo token de acesso no espaço de trabalho Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="e74cd-175">Agora você deve ser capaz de acessar quaisquer Azure Databricks clusters que você criar e carregar arquivos para o DBFS.</span><span class="sxs-lookup"><span data-stu-id="e74cd-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="e74cd-176">Baixar dependências de trabalhador</span><span class="sxs-lookup"><span data-stu-id="e74cd-176">Download worker dependencies</span></span>

1. <span data-ttu-id="e74cd-177">O Microsoft. Spark. Worker ajuda a Apache Spark executar seu aplicativo, como qualquer UDFs (funções definidas pelo usuário) que você possa ter escrito.</span><span class="sxs-lookup"><span data-stu-id="e74cd-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="e74cd-178">Baixe [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="e74cd-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="e74cd-179">O *install-Worker.sh* é um script que permite que você copie o .net para Apache Spark arquivos dependentes nos nós do cluster.</span><span class="sxs-lookup"><span data-stu-id="e74cd-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="e74cd-180">Crie um novo arquivo chamado **install-Worker.sh** no computador local e cole o conteúdo do [install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no github.</span><span class="sxs-lookup"><span data-stu-id="e74cd-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="e74cd-181">O *DB-init.sh* é um script que instala dependências em seu cluster do databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e74cd-182">Crie um novo arquivo chamado **DB-init.sh** no computador local e cole o conteúdo do [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) localizado no github.</span><span class="sxs-lookup"><span data-stu-id="e74cd-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="e74cd-183">No arquivo que você acabou de criar, defina a variável `DOTNET_SPARK_RELEASE` como `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="e74cd-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="e74cd-184">Deixe o restante do arquivo *DB-init.sh* como está.</span><span class="sxs-lookup"><span data-stu-id="e74cd-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="e74cd-185">Se você estiver usando o Windows, verifique se as terminações de linha nos scripts *install-Worker.sh* e *DB-init.sh* são de estilo UNIX (LF).</span><span class="sxs-lookup"><span data-stu-id="e74cd-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="e74cd-186">Você pode alterar as terminações de linha por meio de editores de texto como o notepad + + e Atom.</span><span class="sxs-lookup"><span data-stu-id="e74cd-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="e74cd-187">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e74cd-187">Publish your app</span></span>

<span data-ttu-id="e74cd-188">Em seguida, você publica o *mySparkApp* criado no [.net para Apache Spark-introdução no tutorial de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) para garantir que o cluster Spark tenha acesso a todos os arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e74cd-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="e74cd-189">Execute os seguintes comandos para publicar o *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="e74cd-189">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="e74cd-190">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="e74cd-190">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="e74cd-191">**No Linux:**</span><span class="sxs-lookup"><span data-stu-id="e74cd-191">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="e74cd-192">Execute as seguintes tarefas para compactar seus arquivos de aplicativo publicados para que você possa carregá-los facilmente em seu cluster do databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e74cd-193">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="e74cd-193">**On Windows:**</span></span>

   <span data-ttu-id="e74cd-194">Navegue até mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="e74cd-194">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="e74cd-195">Em seguida, clique com o botão direito do mouse em **publicar** pasta e selecione **Enviar para > pasta compactada (zipada)** .</span><span class="sxs-lookup"><span data-stu-id="e74cd-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="e74cd-196">Nomeie a nova pasta **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="e74cd-197">**No Linux, execute o seguinte comando:**</span><span class="sxs-lookup"><span data-stu-id="e74cd-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="e74cd-198">Carregar arquivos</span><span class="sxs-lookup"><span data-stu-id="e74cd-198">Upload files</span></span>

<span data-ttu-id="e74cd-199">Nesta seção, você carrega vários arquivos em DBFS para que o cluster tenha tudo o que precisa para executar seu aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="e74cd-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="e74cd-200">Sempre que você carregar um arquivo para o DBFS, verifique se você está no diretório em que o arquivo está localizado no computador.</span><span class="sxs-lookup"><span data-stu-id="e74cd-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="e74cd-201">Execute os comandos a seguir para carregar o *DB-init.sh*, o *install-Worker.sh*e o *Microsoft. Spark. Worker* para o DBFS:</span><span class="sxs-lookup"><span data-stu-id="e74cd-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="e74cd-202">Execute os seguintes comandos para carregar os arquivos restantes que o cluster precisará para executar seu aplicativo: a pasta de publicação compactada, *Input. txt*e *Microsoft-Spark-2.4. x-0.3.0. jar*.</span><span class="sxs-lookup"><span data-stu-id="e74cd-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="e74cd-203">Criar um trabalho</span><span class="sxs-lookup"><span data-stu-id="e74cd-203">Create a job</span></span>

<span data-ttu-id="e74cd-204">Seu aplicativo é executado em Azure Databricks por meio de um trabalho que executa o **Spark-Submit**, que é o comando usado para executar o .net para trabalhos do Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e74cd-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="e74cd-205">No espaço de trabalho Azure Databricks, selecione o ícone **trabalhos** e **+ criar trabalho**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Criar um trabalho de Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="e74cd-207">Escolha um título para seu trabalho e, em seguida, selecione **Configurar Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Configurar o Spark-enviar para o trabalho do databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="e74cd-209">Cole os seguintes parâmetros na configuração do trabalho.</span><span class="sxs-lookup"><span data-stu-id="e74cd-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="e74cd-210">Em seguida, selecione **confirmar**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="e74cd-211">Criar um cluster</span><span class="sxs-lookup"><span data-stu-id="e74cd-211">Create a cluster</span></span>

1. <span data-ttu-id="e74cd-212">Navegue até seu trabalho e selecione **Editar** para configurar o cluster do trabalho.</span><span class="sxs-lookup"><span data-stu-id="e74cd-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="e74cd-213">Defina o cluster para o **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="e74cd-214">Em seguida, selecione **Opções avançadas** > **scripts de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="e74cd-215">Defina caminho do script de inicialização como `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="e74cd-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Configurar o cluster Spark no Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="e74cd-217">Selecione **confirmar** para confirmar as configurações de cluster.</span><span class="sxs-lookup"><span data-stu-id="e74cd-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="e74cd-218">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e74cd-218">Run your app</span></span>

1. <span data-ttu-id="e74cd-219">Navegue até seu trabalho e selecione **executar agora** para executar seu trabalho em seu cluster Spark recém configurado.</span><span class="sxs-lookup"><span data-stu-id="e74cd-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="e74cd-220">Leva alguns minutos para que o cluster do trabalho seja criado.</span><span class="sxs-lookup"><span data-stu-id="e74cd-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="e74cd-221">Depois que ele for criado, seu trabalho será enviado e você poderá exibir a saída.</span><span class="sxs-lookup"><span data-stu-id="e74cd-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="e74cd-222">Selecione **clusters** no menu à esquerda e, em seguida, o nome e a execução do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="e74cd-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="e74cd-223">Selecione **logs de driver** para exibir a saída do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="e74cd-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="e74cd-224">Quando seu aplicativo concluir a execução, você verá a mesma tabela de contagem de palavras da execução local de introdução gravada no console de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="e74cd-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks tabela de saída de trabalho](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="e74cd-226">Parabéns, você executou seu primeiro .NET para Apache Spark aplicativo na nuvem!</span><span class="sxs-lookup"><span data-stu-id="e74cd-226">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="e74cd-227">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="e74cd-227">Clean up resources</span></span>

<span data-ttu-id="e74cd-228">Se você não precisar mais do espaço de trabalho do databricks, poderá excluir seu recurso de Azure Databricks no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="e74cd-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="e74cd-229">Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="e74cd-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e74cd-230">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e74cd-230">Next steps</span></span>

<span data-ttu-id="e74cd-231">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="e74cd-232">Para saber mais sobre o Databricks, leia a documentação do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="e74cd-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e74cd-233">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="e74cd-233">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
