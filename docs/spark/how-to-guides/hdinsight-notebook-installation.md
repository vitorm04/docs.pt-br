---
title: Instale .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark
description: Saiba como instalar o .NET para Apache Spark nos notebooks Jupyter do Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546744"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="65439-103">Instale .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="65439-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="65439-104">Este artigo ensina como instalar .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="65439-105">Você pode implantar .NET para Apache Spark em clusters Azure HDInsight através de uma combinação da linha de comando e do portal Azure (para obter mais informações, veja [como implantar um aplicativo .NET para Apache Spark no Azure HDInsight),](../tutorials/hdinsight-deployment.md)mas os notebooks fornecem uma experiência mais interativa e iterativa.</span><span class="sxs-lookup"><span data-stu-id="65439-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="65439-106">Os clusters Azure HDInsight já vêm com notebooks Jupyter, então tudo o que você precisa fazer é configurar os notebooks Jupyter para executar o .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="65439-107">Para usar o .NET para Apache Spark em seus notebooks Jupyter, um C# REPL é necessário para executar o seu código C# linha por linha e para preservar o estado de execução quando necessário.</span><span class="sxs-lookup"><span data-stu-id="65439-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="65439-108">[Try .NET](https://github.com/dotnet/try) foi integrado como o .NET REPL oficial.</span><span class="sxs-lookup"><span data-stu-id="65439-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="65439-109">Para habilitar o .NET para Apache Spark através da experiência jupyter Notebooks, você precisa seguir alguns passos manuais através [do Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) e enviar [ações de script](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) no cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="65439-110">Este recurso é *experimental* e não é suportado pela equipe do HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65439-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="65439-111">Prerequisites</span></span>

<span data-ttu-id="65439-112">Se você ainda não tiver um, crie um cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster)</span><span class="sxs-lookup"><span data-stu-id="65439-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) cluster.</span></span>

1. <span data-ttu-id="65439-113">Visite o [portal Dozure](https://portal.azure.com) e selecione **+ Criar um Recurso**.</span><span class="sxs-lookup"><span data-stu-id="65439-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="65439-114">Crie um novo recurso de cluster Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="65439-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="65439-115">Selecione **Spark 2.4** e **HDI 4.0** durante a criação do cluster.</span><span class="sxs-lookup"><span data-stu-id="65439-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="65439-116">Instale .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="65439-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="65439-117">No portal Azure, selecione o **cluster HDInsight Spark** que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="65439-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="65439-118">Pare o servidor Da Livy</span><span class="sxs-lookup"><span data-stu-id="65439-118">Stop the Livy server</span></span>

1. <span data-ttu-id="65439-119">No portal, selecione **Visão Geral**e selecione **ambari home**.</span><span class="sxs-lookup"><span data-stu-id="65439-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="65439-120">Se solicitado, digite as credenciais de login para o cluster.</span><span class="sxs-lookup"><span data-stu-id="65439-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="65439-122">Selecione **Spark2** no menu de navegação à esquerda e selecione **LIVY FOR SPARK2 SERVER**.</span><span class="sxs-lookup"><span data-stu-id="65439-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="65439-124">Selecione **hn0... host**.</span><span class="sxs-lookup"><span data-stu-id="65439-124">Select **hn0... host**.</span></span>

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="65439-126">Selecione a elipse ao lado **de Livy para Spark2 Server** e selecione **Stop**.</span><span class="sxs-lookup"><span data-stu-id="65439-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="65439-127">Quando solicitado, selecione **OK** para prosseguir.</span><span class="sxs-lookup"><span data-stu-id="65439-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="65439-128">Pare a Livy para o Servidor Spark2.</span><span class="sxs-lookup"><span data-stu-id="65439-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="65439-129">![Pare o Servidor Livy](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="65439-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="65439-130">Repita as etapas anteriores para **hn1... host**.</span><span class="sxs-lookup"><span data-stu-id="65439-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="65439-131">Enviar uma ação de script HDInsight</span><span class="sxs-lookup"><span data-stu-id="65439-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="65439-132">O `install-interactive-notebook.sh` é um script que instala .NET para Apache Spark e faz alterações em Apache Livy e sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="65439-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="65439-133">Antes de enviar uma ação de script para `install-interactive-notebook.sh`o HDInsight, você precisa criar e carregar .</span><span class="sxs-lookup"><span data-stu-id="65439-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="65439-134">Crie um novo arquivo chamado **install-interactive-notebook.sh** em seu computador local e cole o conteúdo do [conteúdo install-interactive-notebook.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="65439-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="65439-135">Faça upload do script para um [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) acessível a partir do cluster HDInsight.</span><span class="sxs-lookup"><span data-stu-id="65439-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="65439-136">Por exemplo, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="65439-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="65439-137">Execute `install-interactive-notebook.sh` no cluster usando as [Ações de Script do HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="65439-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="65439-138">Retorne ao seu cluster HDI no portal Azure e selecione ações de **Script** a partir das opções à esquerda.</span><span class="sxs-lookup"><span data-stu-id="65439-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="65439-139">Você envia uma ação de script para implantar o .NET para Apache Spark REPL no seu cluster HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="65439-140">Use as configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="65439-140">Use the following settings:</span></span>

   |<span data-ttu-id="65439-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="65439-141">Property</span></span>  |<span data-ttu-id="65439-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="65439-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="65439-143">Tipo de script</span><span class="sxs-lookup"><span data-stu-id="65439-143">Script type</span></span> | <span data-ttu-id="65439-144">Personalizado</span><span class="sxs-lookup"><span data-stu-id="65439-144">Custom</span></span> |
   | <span data-ttu-id="65439-145">Nome</span><span class="sxs-lookup"><span data-stu-id="65439-145">Name</span></span> | <span data-ttu-id="65439-146">*Instale .NET para Apache Spark Interactive Notebook Experience*</span><span class="sxs-lookup"><span data-stu-id="65439-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="65439-147">URI do script Bash</span><span class="sxs-lookup"><span data-stu-id="65439-147">Bash script URI</span></span> | <span data-ttu-id="65439-148">O URI para o qual você carregou `install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="65439-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="65439-149">Tipo(s) de nó</span><span class="sxs-lookup"><span data-stu-id="65439-149">Node type(s)</span></span>| <span data-ttu-id="65439-150">Chefe e Trabalhador</span><span class="sxs-lookup"><span data-stu-id="65439-150">Head and Worker</span></span> |
   | <span data-ttu-id="65439-151">parâmetros</span><span class="sxs-lookup"><span data-stu-id="65439-151">Parameters</span></span> | <span data-ttu-id="65439-152">.NET para versão Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="65439-153">Você pode verificar [.NET para ver siters Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="65439-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="65439-154">Por exemplo, se você quiser instalar a versão 0.6.0 `0.6.0`do Sparkdotnet, então seria .</span><span class="sxs-lookup"><span data-stu-id="65439-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="65439-155">Mova-se para o próximo passo quando as marcas de verificação verdes aparecerem ao lado do status da ação do script.</span><span class="sxs-lookup"><span data-stu-id="65439-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="65439-156">Inicie o servidor Livy</span><span class="sxs-lookup"><span data-stu-id="65439-156">Start the Livy server</span></span>

<span data-ttu-id="65439-157">Siga as instruções na seção [Stop Livy server](#stop-the-livy-server) para **Iniciar** (em vez **de parar**) o Servidor Livy for Spark2 para hosts **hn0** e **hn1**.</span><span class="sxs-lookup"><span data-stu-id="65439-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="65439-158">Configurar configurações padrão do Spark</span><span class="sxs-lookup"><span data-stu-id="65439-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="65439-159">No portal, selecione **Visão Geral**e selecione **ambari home**.</span><span class="sxs-lookup"><span data-stu-id="65439-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="65439-160">Em caso de solicitação, insira as credenciais de logon do cluster.</span><span class="sxs-lookup"><span data-stu-id="65439-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="65439-161">Selecione **Spark2** e **CONFIGS**.</span><span class="sxs-lookup"><span data-stu-id="65439-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="65439-162">Em seguida, selecione **Padrões personalizados de spark2**.</span><span class="sxs-lookup"><span data-stu-id="65439-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="65439-164">Selecione **Adicionar propriedade...** para adicionar configurações padrão do Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Adicionar propriedade](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="65439-166">Há três propriedades individuais.</span><span class="sxs-lookup"><span data-stu-id="65439-166">There are three individual properties.</span></span> <span data-ttu-id="65439-167">Adicione-os um de cada vez usando o tipo de propriedade **TEXT** no modo de adicionar propriedade única.</span><span class="sxs-lookup"><span data-stu-id="65439-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="65439-168">Verifique se você não tem espaços extras antes ou depois de qualquer uma das chaves/valores.</span><span class="sxs-lookup"><span data-stu-id="65439-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="65439-169">**Propriedade 1**</span><span class="sxs-lookup"><span data-stu-id="65439-169">**Property 1**</span></span>
       * <span data-ttu-id="65439-170">Chave:&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="65439-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="65439-171">Valor: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="65439-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="65439-172">**Propriedade 2** Use a versão de .NET para Apache Spark que você havia incluído na ação de script anterior.</span><span class="sxs-lookup"><span data-stu-id="65439-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="65439-173">Chave:&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="65439-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="65439-174">Valor: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="65439-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="65439-175">**Propriedade 3**</span><span class="sxs-lookup"><span data-stu-id="65439-175">**Property 3**</span></span>
       * <span data-ttu-id="65439-176">Chave:&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="65439-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="65439-177">Valor: `try`</span><span class="sxs-lookup"><span data-stu-id="65439-177">Value: `try`</span></span>

   <span data-ttu-id="65439-178">Por exemplo, a imagem a seguir captura a configuração para adicionar a propriedade 1:</span><span class="sxs-lookup"><span data-stu-id="65439-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="65439-180">Depois de adicionar as três propriedades, selecione **SAVE**.</span><span class="sxs-lookup"><span data-stu-id="65439-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="65439-181">Se você vir uma tela de aviso de recomendações de config, selecione **PROCEDER DE QUALQUER MANEIRA**.</span><span class="sxs-lookup"><span data-stu-id="65439-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="65439-182">Reiniciar os componentes afetados.</span><span class="sxs-lookup"><span data-stu-id="65439-182">Restart affected components.</span></span>

   <span data-ttu-id="65439-183">Depois de adicionar as novas propriedades, você precisa reiniciar componentes que foram afetados pelas alterações.</span><span class="sxs-lookup"><span data-stu-id="65439-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="65439-184">Na parte superior, selecione **RESTART**e, em seguida, **reinicie todos os afetados** a partir da queda.</span><span class="sxs-lookup"><span data-stu-id="65439-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Definir configurações](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="65439-186">Quando solicitado, **selecione CONFIRMAR REINICIAR TUDO** para continuar e, em seguida, clique em **OK** para terminar.</span><span class="sxs-lookup"><span data-stu-id="65439-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="65439-187">Enviar trabalhos através de um caderno Jupyter</span><span class="sxs-lookup"><span data-stu-id="65439-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="65439-188">Depois de terminar as etapas anteriores, agora você pode enviar seu .NET para trabalhos Apache Spark através de notebooks Jupyter.</span><span class="sxs-lookup"><span data-stu-id="65439-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="65439-189">Crie um novo notebook .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="65439-190">Inicie um notebook Jupyter do seu cluster HDI no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="65439-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Lançar o Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="65439-192">Em seguida, selecione **Nova** > **Faísca .NET (C#)** para criar um notebook.</span><span class="sxs-lookup"><span data-stu-id="65439-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Bloco de anotações do Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="65439-194">Envie trabalhos usando .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="65439-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="65439-195">Use o seguinte trecho de código para criar um DataFrame:</span><span class="sxs-lookup"><span data-stu-id="65439-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Enviar trabalho de faísca](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="65439-197">Use o seguinte trecho de código para registrar uma função definida pelo usuário (UDF) e use o UDF com DataFrames:</span><span class="sxs-lookup"><span data-stu-id="65439-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Enviar trabalho de faísca](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="65439-199">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="65439-199">Next steps</span></span>

* [<span data-ttu-id="65439-200">Implantar um aplicativo .NET para Apache Spark no Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="65439-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="65439-201">Documentação HDInsight</span><span class="sxs-lookup"><span data-stu-id="65439-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
