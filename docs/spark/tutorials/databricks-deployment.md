---
title: Implantar um aplicativo .NET para Apache Spark no Databricks
description: Descubra como implantar um aplicativo do .NET para Apache Spark no Databricks.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503967"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="206c6-103">Tutorial: Implante um aplicativo .NET para Apache Spark no Databricks</span><span class="sxs-lookup"><span data-stu-id="206c6-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="206c6-104">Este tutorial ensina como implantar seu aplicativo na nuvem através do Azure Databricks, uma plataforma de análise baseada no Apache Spark com configuração de um clique, fluxos de trabalho simplificados e espaço de trabalho interativo que permite a colaboração.</span><span class="sxs-lookup"><span data-stu-id="206c6-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="206c6-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="206c6-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="206c6-106">Criar um workspace do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="206c6-107">Publique seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="206c6-108">Crie um cluster Spark e Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="206c6-109">Execute seu aplicativo no cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="206c6-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="206c6-110">Prerequisites</span></span>

<span data-ttu-id="206c6-111">Antes de começar, faça as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="206c6-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="206c6-112">Se você não tiver uma conta no Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="206c6-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="206c6-113">Faça login no [portal Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="206c6-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="206c6-114">Complete o .NET para Apache Spark - Comece no tutorial [de 10 minutos.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)</span><span class="sxs-lookup"><span data-stu-id="206c6-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="206c6-115">Criar um workspace do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="206c6-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="206c6-116">Este tutorial não pode ser realizado usando a **Assinatura de avaliação gratuita do Azure**.</span><span class="sxs-lookup"><span data-stu-id="206c6-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="206c6-117">Se você tiver uma conta gratuita, acesse seu perfil e altere para uma assinatura **pré-paga**.</span><span class="sxs-lookup"><span data-stu-id="206c6-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="206c6-118">Para saber mais, confira [Conta gratuita do Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="206c6-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="206c6-119">Em seguida, [remova o limite de gastos](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit) e [solicite um aumento de cota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) para as vCPUs da sua região.</span><span class="sxs-lookup"><span data-stu-id="206c6-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="206c6-120">Quando você cria seu espaço de trabalho do Azure Databricks, pode selecionar o tipo de preço **Versão de avaliação (Premium - DBUs gratuitas por 14 dias)** para conceder ao espaço de trabalho acesso gratuito aos DBUs do Premium Azure Databricks por 14 dias.</span><span class="sxs-lookup"><span data-stu-id="206c6-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="206c6-121">Nesta seção, você deve cria um workspace do Azure Databricks usando o Portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="206c6-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="206c6-122">No portal Azure, selecione **Criar um recurso** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="206c6-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Crie um recurso do Azure Databricks no portal Azure](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="206c6-124">Em **Serviço do Azure Databricks**, forneça os valores para criar um workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="206c6-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="206c6-125">Property</span></span>  |<span data-ttu-id="206c6-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="206c6-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="206c6-127">**Nome do workspace**</span><span class="sxs-lookup"><span data-stu-id="206c6-127">**Workspace name**</span></span>     | <span data-ttu-id="206c6-128">Forneça um nome para o seu workspace do Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="206c6-129">**Assinatura**</span><span class="sxs-lookup"><span data-stu-id="206c6-129">**Subscription**</span></span>     | <span data-ttu-id="206c6-130">Na lista suspensa, selecione sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="206c6-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="206c6-131">**Grupo de recursos**</span><span class="sxs-lookup"><span data-stu-id="206c6-131">**Resource group**</span></span>     | <span data-ttu-id="206c6-132">Especifique se deseja criar um novo grupo de recursos ou usar um existente.</span><span class="sxs-lookup"><span data-stu-id="206c6-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="206c6-133">Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure.</span><span class="sxs-lookup"><span data-stu-id="206c6-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="206c6-134">Para obter mais informações, consulte [Visão geral do Grupo de Recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="206c6-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="206c6-135">**Local**</span><span class="sxs-lookup"><span data-stu-id="206c6-135">**Location**</span></span>     | <span data-ttu-id="206c6-136">Selecione sua região preferida.</span><span class="sxs-lookup"><span data-stu-id="206c6-136">Select your preferred region.</span></span> <span data-ttu-id="206c6-137">Para obter informações sobre as regiões disponíveis, consulte [os serviços do Azure disponíveis por região](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="206c6-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="206c6-138">**Nível de preços**</span><span class="sxs-lookup"><span data-stu-id="206c6-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="206c6-139">Escolha entre o cluster **Standard**, **Premium** ou **Avaliação**.</span><span class="sxs-lookup"><span data-stu-id="206c6-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="206c6-140">Para saber mais sobre essas camadas, confira [Página de preços do Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="206c6-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="206c6-141">**Rede Virtual**</span><span class="sxs-lookup"><span data-stu-id="206c6-141">**Virtual Network**</span></span>     |   <span data-ttu-id="206c6-142">Não</span><span class="sxs-lookup"><span data-stu-id="206c6-142">No</span></span>       |

3. <span data-ttu-id="206c6-143">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="206c6-143">Select **Create**.</span></span> <span data-ttu-id="206c6-144">A criação do workspace leva alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="206c6-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="206c6-145">Durante a criação do workspace, você pode exibir o status da implantação em **Notificações**.</span><span class="sxs-lookup"><span data-stu-id="206c6-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="206c6-146">Instale ferramentas do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="206c6-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="206c6-147">Você pode usar o **Databricks CLI** para conectar-se aos clusters do Azure Databricks e enviar arquivos para eles a partir de sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="206c6-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="206c6-148">Databricks clusters arquivos de acesso através do DBFS (Databricks File System).</span><span class="sxs-lookup"><span data-stu-id="206c6-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="206c6-149">O Databricks CLI requer Python 3.6 ou superior.</span><span class="sxs-lookup"><span data-stu-id="206c6-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="206c6-150">Se você já tiver o Python instalado, você pode pular este passo.</span><span class="sxs-lookup"><span data-stu-id="206c6-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="206c6-151">**Para windows:**</span><span class="sxs-lookup"><span data-stu-id="206c6-151">**For Windows:**</span></span>

   [<span data-ttu-id="206c6-152">Baixar Python para Windows</span><span class="sxs-lookup"><span data-stu-id="206c6-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="206c6-153">**Para Linux:** Python vem pré-instalado na maioria das distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="206c6-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="206c6-154">Execute o seguinte comando para ver qual versão você instalou:</span><span class="sxs-lookup"><span data-stu-id="206c6-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="206c6-155">Use pip para instalar o Databricks CLI.</span><span class="sxs-lookup"><span data-stu-id="206c6-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="206c6-156">Python 3.4 e posteriormente incluir pip por padrão.</span><span class="sxs-lookup"><span data-stu-id="206c6-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="206c6-157">Use pip3 para Python 3.</span><span class="sxs-lookup"><span data-stu-id="206c6-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="206c6-158">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="206c6-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="206c6-159">Depois de instalar o Databricks CLI, abra um novo `databricks`prompt de comando e execute o comando .</span><span class="sxs-lookup"><span data-stu-id="206c6-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="206c6-160">Se você receber um **'databricks' não for reconhecido como um erro de comando interno ou externo,** certifique-se de abrir um novo prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="206c6-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="206c6-161">Configure os Databricks do Azure</span><span class="sxs-lookup"><span data-stu-id="206c6-161">Set up Azure Databricks</span></span>

<span data-ttu-id="206c6-162">Agora que você tem o Databricks CLI instalado, você precisa configurar detalhes de autenticação.</span><span class="sxs-lookup"><span data-stu-id="206c6-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="206c6-163">Execute o comando `databricks configure --token`Databricks CLI .</span><span class="sxs-lookup"><span data-stu-id="206c6-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="206c6-164">Depois de executar o comando configurar, você é solicitado a inserir um host.</span><span class="sxs-lookup"><span data-stu-id="206c6-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="206c6-165">O URL do host usa o formato: **https://<\Location>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="206c6-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="206c6-166">Por exemplo, se você selecionou **eastus2** durante a criação do **https://eastus2.azuredatabricks.net**Azure Databricks Service, o host seria .</span><span class="sxs-lookup"><span data-stu-id="206c6-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="206c6-167">Depois de inserir seu host, você é solicitado a inserir um token.</span><span class="sxs-lookup"><span data-stu-id="206c6-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="206c6-168">No portal Azure, selecione **Iniciar espaço de trabalho** para iniciar seu espaço de trabalho do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Inicie o Azure Databricks Workspace](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="206c6-170">Na página inicial do seu espaço de trabalho, selecione **Configurações do usuário**.</span><span class="sxs-lookup"><span data-stu-id="206c6-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Configurações do usuário no espaço de trabalho do Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="206c6-172">Na página Configurações do usuário, você pode gerar um novo token.</span><span class="sxs-lookup"><span data-stu-id="206c6-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="206c6-173">Copie o token gerado e cole-o de volta no seu prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="206c6-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Gerar novo token de acesso no espaço de trabalho do Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="206c6-175">Agora você deve ser capaz de acessar quaisquer clusters do Azure Databricks que você criar e carregar arquivos para o DBFS.</span><span class="sxs-lookup"><span data-stu-id="206c6-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="206c6-176">Baixar dependências de trabalhadores</span><span class="sxs-lookup"><span data-stu-id="206c6-176">Download worker dependencies</span></span>

1. <span data-ttu-id="206c6-177">O Microsoft.Spark.Worker ajuda o Apache Spark a executar seu aplicativo, como quaisquer funções definidas pelo usuário (UDFs) que você possa ter escrito.</span><span class="sxs-lookup"><span data-stu-id="206c6-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="206c6-178">Baixe [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="206c6-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="206c6-179">O *install-worker.sh* é um script que permite copiar .NET para arquivos dependentes apache spark nos nós do seu cluster.</span><span class="sxs-lookup"><span data-stu-id="206c6-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="206c6-180">Crie um novo arquivo chamado **install-worker.sh** em seu computador local e cole o [conteúdo install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no GitHub.</span><span class="sxs-lookup"><span data-stu-id="206c6-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="206c6-181">O *db-init.sh* é um script que instala dependências no cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="206c6-182">Crie um novo arquivo chamado **db-init.sh** em seu computador local e cole o [conteúdo db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) localizado no GitHub.</span><span class="sxs-lookup"><span data-stu-id="206c6-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="206c6-183">No arquivo que você acabou `DOTNET_SPARK_RELEASE` de `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`criar, defina a variável para .</span><span class="sxs-lookup"><span data-stu-id="206c6-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="206c6-184">Deixe o resto do *arquivo db-init.sh* como está.</span><span class="sxs-lookup"><span data-stu-id="206c6-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="206c6-185">Se você estiver usando o Windows, verifique se as terminações de linha em seus *scripts install-worker.sh* e *db-init.sh* são no estilo Unix (LF).</span><span class="sxs-lookup"><span data-stu-id="206c6-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="206c6-186">Você pode alterar finais de linha através de editores de texto como Notepad++ e Átomo.</span><span class="sxs-lookup"><span data-stu-id="206c6-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="206c6-187">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="206c6-187">Publish your app</span></span>

<span data-ttu-id="206c6-188">Em seguida, você publica o *mySparkApp* criado no .NET para Apache Spark - Comece no tutorial [de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) para garantir que seu cluster Spark tenha acesso a todos os arquivos necessários para executar o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="206c6-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="206c6-189">Execute os seguintes comandos para publicar o *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="206c6-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="206c6-190">Faça as seguintes tarefas para fechar os arquivos do aplicativo publicados para que você possa facilmente carregá-los para o seu cluster Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="206c6-191">**No Windows:**</span><span class="sxs-lookup"><span data-stu-id="206c6-191">**On Windows:**</span></span>

   <span data-ttu-id="206c6-192">Navegue até o mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="206c6-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="206c6-193">Em seguida, clique com o botão direito do mouse na pasta **Publicar** e **selecione Enviar para > pasta Compactada (fechada).**</span><span class="sxs-lookup"><span data-stu-id="206c6-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="206c6-194">Nomeie a nova pasta **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="206c6-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="206c6-195">**No Linux, execute o seguinte comando:**</span><span class="sxs-lookup"><span data-stu-id="206c6-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="206c6-196">Carregar arquivos</span><span class="sxs-lookup"><span data-stu-id="206c6-196">Upload files</span></span>

<span data-ttu-id="206c6-197">Nesta seção, você carrega vários arquivos para o DBFS para que seu cluster tenha tudo o que precisa para executar seu aplicativo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="206c6-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="206c6-198">Cada vez que você carregar um arquivo para o DBFS, certifique-se de que você está no diretório onde esse arquivo está localizado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="206c6-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="206c6-199">Execute os seguintes comandos para carregar os *db-init.sh,* *install-worker.sh*e *Microsoft.Spark.Worker* para DBFS:</span><span class="sxs-lookup"><span data-stu-id="206c6-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="206c6-200">Execute os seguintes comandos para carregar os arquivos restantes que seu cluster precisará para executar seu aplicativo: a pasta de publicação com zíper, *input.txt*e *microsoft-spark-2.4.x-0.3.0.jar*.</span><span class="sxs-lookup"><span data-stu-id="206c6-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="206c6-201">Criar um trabalho</span><span class="sxs-lookup"><span data-stu-id="206c6-201">Create a job</span></span>

<span data-ttu-id="206c6-202">Seu aplicativo é executado no Azure Databricks através de um trabalho que executa **o spark-submit**, que é o comando que você usa para executar .NET para trabalhos Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="206c6-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="206c6-203">Em seu Espaço de Trabalho do Azure Databricks, selecione o ícone **Empregos** **e, em seguida, + Criar trabalho**.</span><span class="sxs-lookup"><span data-stu-id="206c6-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Crie um trabalho no Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="206c6-205">Escolha um título para o seu trabalho e, em seguida, selecione **Configurar envio de faíscas**.</span><span class="sxs-lookup"><span data-stu-id="206c6-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Configure o envio de faíscas para o trabalho databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="206c6-207">Cole os seguintes parâmetros na configuração do trabalho.</span><span class="sxs-lookup"><span data-stu-id="206c6-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="206c6-208">Em seguida, **selecione Confirmar**.</span><span class="sxs-lookup"><span data-stu-id="206c6-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="206c6-209">Criar um cluster</span><span class="sxs-lookup"><span data-stu-id="206c6-209">Create a cluster</span></span>

1. <span data-ttu-id="206c6-210">Navegue até o seu trabalho e selecione **Editar** para configurar o cluster do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="206c6-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="206c6-211">Defina seu cluster como **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="206c6-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="206c6-212">Em seguida, selecione **Scripts init de opções** > **avançadas**.</span><span class="sxs-lookup"><span data-stu-id="206c6-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="206c6-213">Definir init script `dbfs:/spark-dotnet/db-init.sh`path como .</span><span class="sxs-lookup"><span data-stu-id="206c6-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Configure cluster de faíscas no Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="206c6-215">Selecione **Confirmar** para confirmar as configurações do cluster.</span><span class="sxs-lookup"><span data-stu-id="206c6-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="206c6-216">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="206c6-216">Run your app</span></span>

1. <span data-ttu-id="206c6-217">Navegue até o seu trabalho e selecione **Executar agora** para executar seu trabalho no cluster Spark recém-configurado.</span><span class="sxs-lookup"><span data-stu-id="206c6-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="206c6-218">Leva alguns minutos para o cluster do trabalho criar.</span><span class="sxs-lookup"><span data-stu-id="206c6-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="206c6-219">Uma vez criado, seu trabalho será enviado, e você poderá visualizar a saída.</span><span class="sxs-lookup"><span data-stu-id="206c6-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="206c6-220">Selecione **Clusters** no menu esquerdo e, em seguida, o nome e execução do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="206c6-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="206c6-221">Selecione **Registros de driver** para exibir a saída do seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="206c6-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="206c6-222">Quando o aplicativo termina de executar, você vê a mesma tabela de contagem de palavras desde a execução local iniciada escrita até o console de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="206c6-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Tabela de saída de trabalho do Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="206c6-224">Parabéns, você executou seu primeiro aplicativo .NET para Apache Spark na nuvem!</span><span class="sxs-lookup"><span data-stu-id="206c6-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="206c6-225">Limpar recursos</span><span class="sxs-lookup"><span data-stu-id="206c6-225">Clean up resources</span></span>

<span data-ttu-id="206c6-226">Se você não precisar mais do espaço de trabalho Databricks, você pode excluir o recurso Azure Databricks no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="206c6-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="206c6-227">Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.</span><span class="sxs-lookup"><span data-stu-id="206c6-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="206c6-228">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="206c6-228">Next steps</span></span>

<span data-ttu-id="206c6-229">Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="206c6-230">Para saber mais sobre o Databricks, leia a documentação do Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="206c6-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="206c6-231">Documentação do Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="206c6-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
