---
title: Instalar o .NET para Apache Spark em blocos de anotações do Jupyter em clusters Azure HDInsight Spark
description: Saiba como instalar o .NET para Apache Spark nos notebooks Jupyter do Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 8110b87991e2f0253257faf19f383dec6cbd3853
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557197"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="33b40-103">Instalar o .NET para Apache Spark em blocos de anotações do Jupyter em clusters Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="33b40-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="33b40-104">Este artigo ensina como instalar o .NET para Apache Spark em blocos de anotações do Jupyter em clusters Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="33b40-105">Você pode implantar o .NET para Apache Spark em clusters do Azure HDInsight por meio de uma combinação da linha de comando e do portal do Azure (para obter mais informações, consulte [como implantar um aplicativo .net para Apache Spark no Azure HDInsight](../tutorials/hdinsight-deployment.md)), mas os notebooks fornecem uma experiência mais interativa e iterativa.</span><span class="sxs-lookup"><span data-stu-id="33b40-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="33b40-106">Os clusters do Azure HDInsight já vêm com notebooks Jupyter, portanto, tudo o que você precisa fazer é configurar os notebooks Jupyter para executar o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="33b40-107">Para usar o .NET para Apache Spark em seus notebooks Jupyter, é necessário um REPL em C# para executar o código em C# linha por linha e para preservar o estado de execução quando necessário.</span><span class="sxs-lookup"><span data-stu-id="33b40-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="33b40-108">[Experimente o .net](https://github.com/dotnet/try) seja integrado como o .net repl oficial.</span><span class="sxs-lookup"><span data-stu-id="33b40-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="33b40-109">Para habilitar o .NET para Apache Spark por meio da experiência do Jupyter notebooks, você precisa seguir algumas etapas manuais por meio de [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) e enviar [ações de script](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) no cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="33b40-110">Esse recurso é *experimental* e não tem suporte da equipe do HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="33b40-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="33b40-111">Prerequisites</span></span>

<span data-ttu-id="33b40-112">Se você ainda não tiver uma, crie um cluster [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .</span><span class="sxs-lookup"><span data-stu-id="33b40-112">If you don't already have one, create an [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="33b40-113">Visite a [portal do Azure](https://portal.azure.com) e selecione **+ criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="33b40-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="33b40-114">Crie um novo recurso de cluster do Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="33b40-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="33b40-115">Selecione **Spark 2,4** e **HDI 4,0** durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="33b40-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="33b40-116">Instalar .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="33b40-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="33b40-117">No portal do Azure, selecione o **cluster HDInsight Spark** criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="33b40-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="33b40-118">Parar o servidor Livy</span><span class="sxs-lookup"><span data-stu-id="33b40-118">Stop the Livy server</span></span>

1. <span data-ttu-id="33b40-119">No portal, selecione **visão geral**e, em seguida, selecione **Ambari página inicial**.</span><span class="sxs-lookup"><span data-stu-id="33b40-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="33b40-120">Se solicitado, insira as credenciais de logon para o cluster.</span><span class="sxs-lookup"><span data-stu-id="33b40-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Parar o servidor Livy](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="33b40-122">Selecione **Spark2** no menu de navegação à esquerda e selecione **LIVY para o servidor Spark2**.</span><span class="sxs-lookup"><span data-stu-id="33b40-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Parar o servidor Livy](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="33b40-124">Selecione **hn0... host**.</span><span class="sxs-lookup"><span data-stu-id="33b40-124">Select **hn0... host**.</span></span>

   ![Parar o servidor Livy](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="33b40-126">Selecione as reticências ao lado de **Livy para servidor Spark2** e selecione **parar**.</span><span class="sxs-lookup"><span data-stu-id="33b40-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="33b40-127">Quando solicitado, selecione **OK** para continuar.</span><span class="sxs-lookup"><span data-stu-id="33b40-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="33b40-128">Pare o Livy para o servidor Spark2.</span><span class="sxs-lookup"><span data-stu-id="33b40-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="33b40-129">![Parar o servidor Livy](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="33b40-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="33b40-130">Repita as etapas anteriores para **hn1... host**.</span><span class="sxs-lookup"><span data-stu-id="33b40-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="33b40-131">Enviar uma ação de script do HDInsight</span><span class="sxs-lookup"><span data-stu-id="33b40-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="33b40-132">O `install-interactive-notebook.sh` é um script que instala o .net para Apache Spark e faz alterações no Apache Livy e sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="33b40-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="33b40-133">Antes de enviar uma ação de script para o HDInsight, você precisa criar e carregar `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="33b40-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="33b40-134">Crie um novo arquivo chamado **install-Interactive-notebook.sh** no computador local e cole o conteúdo do [conteúdo do install-Interactive-notebook.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="33b40-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="33b40-135">Carregue o script em um [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) acessível do cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="33b40-135">Upload the script to a [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="33b40-136">Por exemplo, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="33b40-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="33b40-137">Execute `install-interactive-notebook.sh` no cluster usando as [Ações de Script do HDInsight](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="33b40-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="33b40-138">Volte para o cluster HDI no portal do Azure e selecione ações de **script** nas opções à esquerda.</span><span class="sxs-lookup"><span data-stu-id="33b40-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="33b40-139">Você envia uma ação de script para implantar o .NET para Apache Spark REPL em seu cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="33b40-140">Use as configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="33b40-140">Use the following settings:</span></span>

   |<span data-ttu-id="33b40-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="33b40-141">Property</span></span>  |<span data-ttu-id="33b40-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="33b40-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="33b40-143">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="33b40-143">Script type</span></span> | <span data-ttu-id="33b40-144">Personalizado</span><span class="sxs-lookup"><span data-stu-id="33b40-144">Custom</span></span> |
   | <span data-ttu-id="33b40-145">Name</span><span class="sxs-lookup"><span data-stu-id="33b40-145">Name</span></span> | <span data-ttu-id="33b40-146">*Instalar o .NET para Apache Spark experiência de notebook interativa*</span><span class="sxs-lookup"><span data-stu-id="33b40-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="33b40-147">URI do script Bash</span><span class="sxs-lookup"><span data-stu-id="33b40-147">Bash script URI</span></span> | <span data-ttu-id="33b40-148">O URI para o qual você carregou `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="33b40-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="33b40-149">Tipo(s) de nó</span><span class="sxs-lookup"><span data-stu-id="33b40-149">Node type(s)</span></span>| <span data-ttu-id="33b40-150">Cabeçalho e trabalho</span><span class="sxs-lookup"><span data-stu-id="33b40-150">Head and Worker</span></span> |
   | <span data-ttu-id="33b40-151">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33b40-151">Parameters</span></span> | <span data-ttu-id="33b40-152">.NET para Apache Spark versão.</span><span class="sxs-lookup"><span data-stu-id="33b40-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="33b40-153">Você pode verificar o [.net em busca de Apache Spark versões](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="33b40-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="33b40-154">Por exemplo, se você quiser instalar o Sparkdotnet versão 0.6.0, ele seria `0.6.0` .</span><span class="sxs-lookup"><span data-stu-id="33b40-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="33b40-155">Vá para a próxima etapa quando as marcas de seleção verdes aparecerem ao lado do status da ação de script.</span><span class="sxs-lookup"><span data-stu-id="33b40-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="33b40-156">Iniciar o servidor Livy</span><span class="sxs-lookup"><span data-stu-id="33b40-156">Start the Livy server</span></span>

<span data-ttu-id="33b40-157">Siga as instruções na seção [parar servidor Livy](#stop-the-livy-server) para **Iniciar** (em vez de **parar**) o Livy do Spark2 Server para hosts **hn0** e **hn1**.</span><span class="sxs-lookup"><span data-stu-id="33b40-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="33b40-158">Configurar as configurações padrão do Spark</span><span class="sxs-lookup"><span data-stu-id="33b40-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="33b40-159">No portal, selecione **visão geral**e, em seguida, selecione **Ambari página inicial**.</span><span class="sxs-lookup"><span data-stu-id="33b40-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="33b40-160">Em caso de solicitação, insira as credenciais de logon do cluster.</span><span class="sxs-lookup"><span data-stu-id="33b40-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="33b40-161">Selecione **Spark2** e **configurações**.</span><span class="sxs-lookup"><span data-stu-id="33b40-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="33b40-162">Em seguida, selecione **Spark2 personalizados-padrões**.</span><span class="sxs-lookup"><span data-stu-id="33b40-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="33b40-164">Selecione **Adicionar Propriedade...** para adicionar as configurações padrão do Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Adicionar propriedade](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="33b40-166">Há três propriedades individuais.</span><span class="sxs-lookup"><span data-stu-id="33b40-166">There are three individual properties.</span></span> <span data-ttu-id="33b40-167">Adicione um de cada vez usando o tipo de propriedade **texto** no modo de adição de propriedade única.</span><span class="sxs-lookup"><span data-stu-id="33b40-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="33b40-168">Verifique se você não tem espaços extras antes ou depois de qualquer uma das chaves/valores.</span><span class="sxs-lookup"><span data-stu-id="33b40-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="33b40-169">**Propriedade 1**</span><span class="sxs-lookup"><span data-stu-id="33b40-169">**Property 1**</span></span>
       * <span data-ttu-id="33b40-170">Chaves&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="33b40-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="33b40-171">Valor: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="33b40-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="33b40-172">**Propriedade 2** Use a versão do .NET para Apache Spark que você incluiu na ação de script anterior.</span><span class="sxs-lookup"><span data-stu-id="33b40-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="33b40-173">Chaves&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="33b40-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="33b40-174">Valor: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="33b40-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="33b40-175">**Propriedade 3**</span><span class="sxs-lookup"><span data-stu-id="33b40-175">**Property 3**</span></span>
       * <span data-ttu-id="33b40-176">Chaves&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="33b40-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="33b40-177">Valor: `try`</span><span class="sxs-lookup"><span data-stu-id="33b40-177">Value: `try`</span></span>

   <span data-ttu-id="33b40-178">Por exemplo, a imagem a seguir captura a configuração para adicionar a propriedade 1:</span><span class="sxs-lookup"><span data-stu-id="33b40-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="33b40-180">Depois de adicionar as três propriedades, selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="33b40-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="33b40-181">Se você vir uma tela de aviso de recomendações de configuração, selecione **continuar mesmo assim**.</span><span class="sxs-lookup"><span data-stu-id="33b40-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="33b40-182">Reinicie os componentes afetados.</span><span class="sxs-lookup"><span data-stu-id="33b40-182">Restart affected components.</span></span>

   <span data-ttu-id="33b40-183">Depois de adicionar as novas propriedades, você precisa reiniciar os componentes que foram afetados pelas alterações.</span><span class="sxs-lookup"><span data-stu-id="33b40-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="33b40-184">Na parte superior, selecione **reiniciar**e **reinicie todos os afetados** da lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="33b40-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="33b40-186">Quando solicitado, selecione **confirmar reiniciar tudo** para continuar e clique em **OK** para concluir.</span><span class="sxs-lookup"><span data-stu-id="33b40-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="33b40-187">Enviar trabalhos por meio de um notebook Jupyter</span><span class="sxs-lookup"><span data-stu-id="33b40-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="33b40-188">Depois de concluir as etapas anteriores, agora você pode enviar seu .NET para trabalhos de Apache Spark por meio de notebooks Jupyter.</span><span class="sxs-lookup"><span data-stu-id="33b40-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="33b40-189">Crie um novo .NET para Apache Spark notebook.</span><span class="sxs-lookup"><span data-stu-id="33b40-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="33b40-190">Inicie um notebook Jupyter do seu cluster do HDI no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="33b40-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Iniciar Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="33b40-192">Em seguida, selecione **novo**  >  **.net Spark (C#)** para criar um bloco de anotações.</span><span class="sxs-lookup"><span data-stu-id="33b40-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="33b40-194">Envie trabalhos usando o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="33b40-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="33b40-195">Use o seguinte trecho de código para criar um dataframe:</span><span class="sxs-lookup"><span data-stu-id="33b40-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Enviar trabalho do Spark](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="33b40-197">Use o trecho de código a seguir para registrar uma UDF (função definida pelo usuário) e usar o UDF com quadros de itens:</span><span class="sxs-lookup"><span data-stu-id="33b40-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Enviar trabalho do Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="33b40-199">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="33b40-199">Next steps</span></span>

* [<span data-ttu-id="33b40-200">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="33b40-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="33b40-201">Documentação do HDInsight</span><span class="sxs-lookup"><span data-stu-id="33b40-201">HDInsight Documentation</span></span>](/azure/hdinsight/)
