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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Tutorial: Implante um aplicativo .NET para Apache Spark no Azure HDInsight

Este tutorial ensina como implantar seu aplicativo .NET para Apache Spark na nuvem através de um cluster Azure HDInsight. O HDInsight facilita a criação e a configuração de um cluster Spark no Azure, uma vez que os clusters Spark no HDInsight são compatíveis com o Azure Storage e o Azure Data Lake Storage.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Acesse suas contas de armazenamento usando o Azure Storage Explorer.
> * Crie um cluster Azure HDInsight.
> * Publique seu aplicativo .NET para Apache Spark.
> * Crie e execute uma ação de script HDInsight.
> * Execute um aplicativo .NET para Apache Spark em um cluster HDInsight.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça as seguintes tarefas:

* Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/).
* Faça login no [portal Azure](https://portal.azure.com/).
* Instale o Azure Storage Explorer no seu computador [Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)ou [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)
* Complete o .NET para Apache Spark - Comece no tutorial [de 10 minutos.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)

## <a name="access-your-storage-accounts"></a>Acesse suas contas de armazenamento

1. Abra o Gerenciador de Armazenamento do Azure.

2. Selecione **Adicionar conta** no menu esquerdo e faça login na sua conta do Azure.

    ![Faça login na conta do Azure no Storage Explorer](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   Depois de fazer login, você deve ver todas as contas de armazenamento que você tem e quaisquer recursos que você tenha carregado em suas contas de armazenamento.

## <a name="create-an-hdinsight-cluster"></a>Crie um cluster HDInsight

> [!IMPORTANT]
> O faturamento dos clusters HDInsight é rateado por minuto, mesmo que você não esteja usando-os. Exclua seu cluster depois de terminar de usá-lo. Para obter mais informações, consulte a seção [Limpar recursos](#clean-up-resources) deste tutorial.

1. Visite o [Portal do Azure](https://portal.azure.com).

2. Selecione **+ Crie um recurso**. Em seguida, selecione **HDInsight** na categoria **Analytics.**

    ![Crie recurso HDInsight a partir do portal Azure](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. Em **Noções básicas**, forneça os seguintes valores:

    |Propriedade  |Descrição  |
    |---------|---------|
    |Subscription  | A partir do drop-down, escolha uma de suas assinaturas ativas do Azure. |
    |Resource group | Especifique se deseja criar um novo grupo de recursos ou usar um existente. Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure. |
    |Nome do cluster | Dê um nome para seu cluster HDInsight Spark.|
    |Location   | Selecione um local para o grupo de recursos. O modelo usa esse local para criar o cluster, bem como para o armazenamento de cluster padrão. |
    |Tipo de cluster| Selecione **Spark** como o tipo de cluster.|
    |Versão do cluster|Este campo será preenchido automaticamente com a versão padrão uma vez que o tipo de cluster tenha sido selecionado. Selecione uma versão 2.3 ou 2.4 do Spark.|
    |Nome de usuário de logon do cluster| Insira o nome de logon do usuário do cluster.  O nome padrão é *admin*. |
    |Senha de logon do cluster| Digite qualquer senha de login. |
    |Nome de usuário do Secure Shell (SSH)| Insira um Nome de Usuário SSH. Por padrão, essa conta tem a mesma senha que a conta de*nome de usuário de logon do cluster*. |

4. Selecione **A seguir: O >>de armazenamento** para continuar na página **Armazenamento.** Em **Armazenamento**, forneça os seguintes valores:

    |Propriedade  |Descrição  |
    |---------|---------|
    |Tipo de armazenamento primário|Use o valor padrão **Armazenamento do Azure**.|
    |Método de seleção|Use o valor padrão **Selecione na lista**.|
    |Conta de armazenamento primária|Escolha sua assinatura e uma de suas contas de armazenamento ativas dentro dessa assinatura.|
    |Contêiner|Este contêiner é o recipiente blob específico em sua conta de armazenamento onde seu cluster procura arquivos para executar seu aplicativo na nuvem. Você pode dar-lhe qualquer nome disponível.|

5. Em **Examinar + criar**, selecione **Criar**. Demora cerca de 20 minutos para criar o cluster. O cluster deve ser criado antes que você possa continuar até o próximo passo.

## <a name="publish-your-app"></a>Publicar seu aplicativo

Em seguida, você publica o *mySparkApp* criado no .NET para Apache Spark - Comece no tutorial [de 10 minutos,](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) que dá ao seu cluster Spark acesso a todos os arquivos necessários para executar o seu aplicativo.

1. Execute os seguintes comandos para publicar o *mySparkApp*:

   **No Windows:**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **No Linux:**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Faça as seguintes tarefas para fechar os arquivos do aplicativo publicados para que você possa facilmente carregá-los para o seu cluster HDInsight.

   **No Windows:**

   Navegue até *o mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*. Em seguida, clique com o botão direito do mouse na pasta **Publicar** e **selecione Enviar para > pasta Compactada (fechada).** Nomeie a nova pasta **publish.zip**.

   **No Linux, execute o seguinte comando:**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>Enviar arquivos para o Azure

Em seguida, você usa o Azure Storage Explorer para carregar os cinco arquivos a seguir para o contêiner blob que você escolheu para o armazenamento do seu cluster:

* Microsoft.Spark.Worker
* install-worker.sh
* publish.zip
* microsoft-spark-2.3.x-0.3.0.jar
* input.txt.

1. Abra o Azure Storage Explorer e navegue até sua conta de armazenamento no menu esquerdo. Aprofunde-se no recipiente blob para o cluster em **Blob Containers** em sua conta de armazenamento.

2. *O Microsoft.Spark.Worker* ajuda o Apache Spark a executar seu aplicativo, como quaisquer funções definidas pelo usuário (UDFs) que você possa ter escrito. Baixe [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz). Em seguida, **selecione Upload** no Azure Storage Explorer para carregar o trabalhador.

   ![Carregar arquivos para o Azure Storage Explorer](./media/hdinsight-deployment/upload-files-to-storage.png)

3. O *install-worker.sh* é um script que permite copiar .NET para arquivos dependentes apache spark nos nós do seu cluster.

   Crie um novo arquivo chamado **install-worker.sh** seu computador local e cole o [conteúdo install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no GitHub. Em seguida, carregue *install-worker.sh* para o seu recipiente de bolha.

4. Seu cluster precisa do arquivo publish.zip que contém os arquivos publicados do aplicativo. Navegue até sua pasta publicada, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, e **localize publish.zip**. Em seguida, carregue *publish.zip* para o seu recipiente blob.

5. Seu cluster precisa do código de aplicativo que foi embalado em um arquivo de frasco. Navegue até sua pasta publicada, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, e localize **microsoft-spark-2.3.x-0.3.0.jar**. Em seguida, carregue o arquivo do frasco para o recipiente blob.

   Pode haver vários arquivos .jar (para versões 2.3.x e 2.4.x de Spark). Você precisa escolher o arquivo .jar que corresponde à versão do Spark que você escolheu durante a criação do cluster. Por exemplo, escolha *o microsoft-spark-2.3.x-0.3.0.jar* se você escolheu o Spark 2.3.2 durante a criação do cluster.

6. Seu cluster precisa da entrada do seu aplicativo. Navegue até o diretório **mySparkApp** e localize **input.txt**. Carregue seu arquivo de entrada para o diretório **usuário/sshuser** no recipiente blob. Você estará se conectando ao seu cluster através de ssh, e esta pasta é onde seu cluster procura sua entrada. O arquivo *input.txt* é o único arquivo carregado para um diretório específico.

## <a name="run-the-hdinsight-script-action"></a>Execute a ação de script HDInsight

Uma vez que seu cluster está sendo executado e você carregou seus arquivos para o Azure, você executa o **script install-worker.sh** no cluster.

1. Navegue até o cluster HDInsight Spark no portal Azure e selecione **ações de script**.

2. Selecione **+ Envie novos** e forneça os seguintes valores:

   |Propriedade  |Descrição  |
   |---------|---------|
   | Tipo de script |Personalizado|
   | Nome | Instalar o Worker|
   | URI do script Bash |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> Para confirmar este URI, clique com o botão direito do mouse em install-worker.sh no Azure Storage Explorer e selecione Propriedades. |
   | Tipo(s) de nó| Trabalho|
   | parâmetros | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. Selecione **Criar** para enviar seu script.

## <a name="run-your-app"></a>Executar seu aplicativo

1. Navegue até o cluster HDInsight Spark no portal Azure e selecione **o login SSH + Cluster**.

2. Copie as informações de login ssh e cole o login em um terminal. Faça login no cluster usando a senha definida durante a criação do cluster. Você deve ver mensagens de boas-vindas ao Ubuntu e ao Spark.

3. Use o comando **spark-submit** para executar seu aplicativo no cluster HDInsight. Lembre-se de substituir **mycontainer** e **mystorageaccount** no script de exemplo com os nomes reais de sua conta de contêiner e armazenamento blob.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   Quando o aplicativo é executado, você vê a mesma tabela de contagem de palavras desde o início da execução local escrita para o console. Parabéns, você executou seu primeiro aplicativo .NET para Apache Spark na nuvem!

## <a name="clean-up-resources"></a>Limpar recursos

O HDInsight salva seus dados no Azure Storage, para que você possa excluir com segurança um cluster quando ele não estiver em uso. Você também é cobrado por um cluster HDInsight, mesmo quando ele não está em uso. Como os encargos para o cluster são muitas vezes maiores do que os encargos para armazenamento, faz sentido, do ponto de vista econômico, excluir os clusters quando não estiverem em uso.

Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**. Ao excluir o grupo de recursos, você exclui o cluster Spark do HDInsight e a conta de armazenamento padrão.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight. Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentação do Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
