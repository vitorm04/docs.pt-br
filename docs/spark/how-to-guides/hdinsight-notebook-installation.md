---
title: Instale .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark
description: Saiba como instalar o .NET para Apache Spark nos notebooks Jupyter do Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 953bffe5f6ec56cd0adf4224afd2eedfe0001aa9
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607409"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Instale .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark

Este artigo ensina como instalar .NET para Apache Spark em notebooks Jupyter em clusters Azure HDInsight Spark. Você pode implantar .NET para Apache Spark em clusters Azure HDInsight através de uma combinação da linha de comando e do portal Azure (para obter mais informações, veja [como implantar um aplicativo .NET para Apache Spark no Azure HDInsight),](../tutorials/hdinsight-deployment.md)mas os notebooks fornecem uma experiência mais interativa e iterativa.

Os clusters Azure HDInsight já vêm com notebooks Jupyter, então tudo o que você precisa fazer é configurar os notebooks Jupyter para executar o .NET para Apache Spark. Para usar o .NET para Apache Spark em seus notebooks Jupyter, um C# REPL é necessário para executar o seu código C# linha por linha e para preservar o estado de execução quando necessário. [Try .NET](https://github.com/dotnet/try) foi integrado como o .NET REPL oficial.

Para habilitar o .NET para Apache Spark através da experiência jupyter Notebooks, você precisa seguir alguns passos manuais através [do Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) e enviar [ações de script](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) no cluster HDInsight Spark.

> [!NOTE]
> Este recurso é *experimental* e não é suportado pela equipe do HDInsight Spark.

## <a name="prerequisites"></a>Pré-requisitos

Se você ainda não tiver um, crie um cluster [Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)

1. Visite o [portal Dozure](https://portal.azure.com) e selecione **+ Criar um Recurso**.

1. Crie um novo recurso de cluster Azure HDInsight. Selecione **Spark 2.4** e **HDI 4.0** durante a criação do cluster.

## <a name="install-net-for-apache-spark"></a>Instale .NET para Apache Spark

No portal Azure, selecione o **cluster HDInsight Spark** que você criou na etapa anterior.

### <a name="stop-the-livy-server"></a>Pare o servidor Da Livy

1. No portal, selecione **Visão Geral**e selecione **ambari home**. Se solicitado, digite as credenciais de login para o cluster.

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-ambari.png)

2. Selecione **Spark2** no menu de navegação à esquerda e selecione **LIVY FOR SPARK2 SERVER**.

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-livyserver.png)

3. Selecione **hn0... host**.

   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/select-host.png)

4. Selecione a elipse ao lado **de Livy para Spark2 Server** e selecione **Stop**. Quando solicitado, selecione **OK** para prosseguir.

   Pare a Livy para o Servidor Spark2.
   ![Pare o Servidor Livy](./media/hdinsight-notebook-installation/stop-server.png)

5. Repita as etapas anteriores para **hn1... host**.

### <a name="submit-an-hdinsight-script-action"></a>Enviar uma ação de script HDInsight

1. O `install-interactive-notebook.sh` é um script que instala .NET para Apache Spark e faz alterações em Apache Livy e sparkmagic. Antes de enviar uma ação de script para `install-interactive-notebook.sh`o HDInsight, você precisa criar e carregar .

   Crie um novo arquivo chamado **install-interactive-notebook.sh** em seu computador local e cole o conteúdo do [conteúdo install-interactive-notebook.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).

   Faça upload do script para um [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) acessível a partir do cluster HDInsight. Por exemplo, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. Execute `install-interactive-notebook.sh` no cluster usando as [Ações de Script do HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

   Retorne ao seu cluster HDI no portal Azure e selecione ações de **Script** a partir das opções à esquerda. Você envia uma ação de script para implantar o .NET para Apache Spark REPL no seu cluster HDInsight Spark. Use as configurações a seguir:

   |Propriedade  |Descrição  |
   |---------|---------|
   | Tipo de script | Personalizado |
   | Nome | *Instale .NET para Apache Spark Interactive Notebook Experience* |
   | URI do script Bash | O URI para o qual você carregou `install-interactive-notebook.sh`. |
   | Tipo(s) de nó| Chefe e Trabalhador |
   | Parâmetros | .NET para versão Apache Spark. Você pode verificar [.NET para ver siters Apache Spark](https://github.com/dotnet/spark/releases). Por exemplo, se você quiser instalar a versão 0.6.0 `0.6.0`do Sparkdotnet, então seria .

   Mova-se para o próximo passo quando as marcas de verificação verdes aparecerem ao lado do status da ação do script.

### <a name="start-the-livy-server"></a>Inicie o servidor Livy

Siga as instruções na seção [Stop Livy server](#stop-the-livy-server) para **Iniciar** (em vez **de parar**) o Servidor Livy for Spark2 para hosts **hn0** e **hn1**.

### <a name="set-up-spark-default-configurations"></a>Configurar configurações padrão do Spark

1. No portal, selecione **Visão Geral**e selecione **ambari home**. Em caso de solicitação, insira as credenciais de logon do cluster.

2. Selecione **Spark2** e **CONFIGS**. Em seguida, selecione **Padrões personalizados de spark2**.

   ![Definir configurações](./media/hdinsight-notebook-installation/spark-configs.png)

3. Selecione **Adicionar propriedade...** para adicionar configurações padrão do Spark.

   ![Adicionar propriedade](./media/hdinsight-notebook-installation/add-property.png)

   Há três propriedades individuais. Adicione-os um de cada vez usando o tipo de propriedade **TEXT** no modo de adicionar propriedade única. Verifique se você não tem espaços extras antes ou depois de qualquer uma das chaves/valores.

   * **Propriedade 1**
       * Chave:&ensp;&ensp;`spark.dotnet.shell.command`
       * Valor: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Propriedade 2** Use a versão de .NET para Apache Spark que você havia incluído na ação de script anterior.
       * Chave:&ensp;&ensp;`spark.dotnet.packages`
       * Valor: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Propriedade 3**
       * Chave:&ensp;&ensp;`spark.dotnet.interpreter`
       * Valor: `try`

   Por exemplo, a imagem a seguir captura a configuração para adicionar a propriedade 1:

   ![Definir configurações](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Depois de adicionar as três propriedades, selecione **SAVE**. Se você vir uma tela de aviso de recomendações de config, selecione **PROCEDER DE QUALQUER MANEIRA**.

4. Reiniciar os componentes afetados.

   Depois de adicionar as novas propriedades, você precisa reiniciar componentes que foram afetados pelas alterações. Na parte superior, selecione **RESTART**e, em seguida, **reinicie todos os afetados** a partir da queda.

   ![Definir configurações](./media/hdinsight-notebook-installation/restart-affected.png)

   Quando solicitado, **selecione CONFIRMAR REINICIAR TUDO** para continuar e, em seguida, clique em **OK** para terminar.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Enviar trabalhos através de um caderno Jupyter

Depois de terminar as etapas anteriores, agora você pode enviar seu .NET para trabalhos Apache Spark através de notebooks Jupyter.

1. Crie um novo notebook .NET para Apache Spark. Inicie um notebook Jupyter do seu cluster HDI no portal Azure.

   ![Lançar o Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   Em seguida, selecione **Nova** > **Faísca .NET (C#)** para criar um notebook.

   ![Bloco de anotações do Jupyter](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Envie trabalhos usando .NET para Apache Spark.

   Use o seguinte trecho de código para criar um DataFrame:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Enviar trabalho de faísca](./media/hdinsight-notebook-installation/create-df.png)

   Use o seguinte trecho de código para registrar uma função definida pelo usuário (UDF) e use o UDF com DataFrames:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Enviar trabalho de faísca](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Próximas etapas

* [Implantar um aplicativo .NET para Apache Spark no Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Documentação HDInsight](https://docs.microsoft.com/azure/hdinsight/)
