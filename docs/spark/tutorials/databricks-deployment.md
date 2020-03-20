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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Tutorial: Implante um aplicativo .NET para Apache Spark no Databricks

Este tutorial ensina como implantar seu aplicativo na nuvem através do Azure Databricks, uma plataforma de análise baseada no Apache Spark com configuração de um clique, fluxos de trabalho simplificados e espaço de trabalho interativo que permite a colaboração.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Criar um workspace do Azure Databricks.
> - Publique seu aplicativo .NET para Apache Spark.
> - Crie um cluster Spark e Spark.
> - Execute seu aplicativo no cluster Spark.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça as seguintes tarefas:

* Se você não tiver uma conta no Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/).
* Faça login no [portal Azure](https://portal.azure.com/).
* Complete o .NET para Apache Spark - Comece no tutorial [de 10 minutos.](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)

## <a name="create-an-azure-databricks-workspace"></a>Criar um workspace do Azure Databricks

> [!Note]
> Este tutorial não pode ser realizado usando a **Assinatura de avaliação gratuita do Azure**.
> Se você tiver uma conta gratuita, acesse seu perfil e altere para uma assinatura **pré-paga**. Para saber mais, confira [Conta gratuita do Azure](https://azure.microsoft.com/free/). Em seguida, [remova o limite de gastos](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit) e [solicite um aumento de cota](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) para as vCPUs da sua região. Quando você cria seu espaço de trabalho do Azure Databricks, pode selecionar o tipo de preço **Versão de avaliação (Premium - DBUs gratuitas por 14 dias)** para conceder ao espaço de trabalho acesso gratuito aos DBUs do Premium Azure Databricks por 14 dias.

Nesta seção, você deve cria um workspace do Azure Databricks usando o Portal do Azure.

1. No portal Azure, selecione **Criar um recurso** > **Analytics** > **Azure Databricks**.

   ![Crie um recurso do Azure Databricks no portal Azure](./media/databricks-deployment/create-databricks-resource.png)

2. Em **Serviço do Azure Databricks**, forneça os valores para criar um workspace do Databricks.

    |Propriedade  |Descrição  |
    |---------|---------|
    |**Nome do workspace**     | Forneça um nome para o seu workspace do Databricks.        |
    |**Assinatura**     | Na lista suspensa, selecione sua assinatura do Azure.        |
    |**Grupo de recursos**     | Especifique se deseja criar um novo grupo de recursos ou usar um existente. Um grupo de recursos é um contêiner que mantém os recursos relacionados a uma solução do Azure. Para obter mais informações, consulte [Visão geral do Grupo de Recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview). |
    |**Local**     | Selecione sua região preferida. Para obter informações sobre as regiões disponíveis, consulte [os serviços do Azure disponíveis por região](https://azure.microsoft.com/regions/services/).        |
    |**Nível de preços**     |  Escolha entre o cluster **Standard**, **Premium** ou **Avaliação**. Para saber mais sobre essas camadas, confira [Página de preços do Databricks](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Rede Virtual**     |   Não       |

3. Selecione **Criar**. A criação do workspace leva alguns minutos. Durante a criação do workspace, você pode exibir o status da implantação em **Notificações**.

## <a name="install-azure-databricks-tools"></a>Instale ferramentas do Azure Databricks

Você pode usar o **Databricks CLI** para conectar-se aos clusters do Azure Databricks e enviar arquivos para eles a partir de sua máquina local. Databricks clusters arquivos de acesso através do DBFS (Databricks File System).

1. O Databricks CLI requer Python 3.6 ou superior. Se você já tiver o Python instalado, você pode pular este passo.

   **Para windows:**

   [Baixar Python para Windows](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Para Linux:** Python vem pré-instalado na maioria das distribuições Linux. Execute o seguinte comando para ver qual versão você instalou:

   ```bash
   python3 --version
   ```

2. Use pip para instalar o Databricks CLI. Python 3.4 e posteriormente incluir pip por padrão. Use pip3 para Python 3. Execute o comando a seguir:

   ```bash
   pip3 install databricks-cli
   ```

3. Depois de instalar o Databricks CLI, abra um novo `databricks`prompt de comando e execute o comando . Se você receber um **'databricks' não for reconhecido como um erro de comando interno ou externo,** certifique-se de abrir um novo prompt de comando.

## <a name="set-up-azure-databricks"></a>Configure os Databricks do Azure

Agora que você tem o Databricks CLI instalado, você precisa configurar detalhes de autenticação.

1. Execute o comando `databricks configure --token`Databricks CLI .

2. Depois de executar o comando configurar, você é solicitado a inserir um host. O URL do host usa o formato: **https://<\Location>.azuredatabricks.net**. Por exemplo, se você selecionou **eastus2** durante a criação do **https://eastus2.azuredatabricks.net**Azure Databricks Service, o host seria .

3. Depois de inserir seu host, você é solicitado a inserir um token. No portal Azure, selecione **Iniciar espaço de trabalho** para iniciar seu espaço de trabalho do Azure Databricks.

   ![Inicie o Azure Databricks Workspace](./media/databricks-deployment/launch-databricks-workspace.png)

4. Na página inicial do seu espaço de trabalho, selecione **Configurações do usuário**.

   ![Configurações do usuário no espaço de trabalho do Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. Na página Configurações do usuário, você pode gerar um novo token. Copie o token gerado e cole-o de volta no seu prompt de comando.

   ![Gerar novo token de acesso no espaço de trabalho do Azure Databricks](./media/databricks-deployment/generate-token.png)

Agora você deve ser capaz de acessar quaisquer clusters do Azure Databricks que você criar e carregar arquivos para o DBFS.

## <a name="download-worker-dependencies"></a>Baixar dependências de trabalhadores

1. O Microsoft.Spark.Worker ajuda o Apache Spark a executar seu aplicativo, como quaisquer funções definidas pelo usuário (UDFs) que você possa ter escrito. Baixe [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).

2. O *install-worker.sh* é um script que permite copiar .NET para arquivos dependentes apache spark nos nós do seu cluster.

   Crie um novo arquivo chamado **install-worker.sh** em seu computador local e cole o [conteúdo install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) localizado no GitHub.

3. O *db-init.sh* é um script que instala dependências no cluster Databricks Spark.

   Crie um novo arquivo chamado **db-init.sh** em seu computador local e cole o [conteúdo db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) localizado no GitHub.

   No arquivo que você acabou `DOTNET_SPARK_RELEASE` de `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`criar, defina a variável para . Deixe o resto do *arquivo db-init.sh* como está.

> [!Note]
> Se você estiver usando o Windows, verifique se as terminações de linha em seus *scripts install-worker.sh* e *db-init.sh* são no estilo Unix (LF). Você pode alterar finais de linha através de editores de texto como Notepad++ e Átomo.

## <a name="publish-your-app"></a>Publicar seu aplicativo

Em seguida, você publica o *mySparkApp* criado no .NET para Apache Spark - Comece no tutorial [de 10 minutos](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) para garantir que seu cluster Spark tenha acesso a todos os arquivos necessários para executar o seu aplicativo.

1. Execute os seguintes comandos para publicar o *mySparkApp*:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. Faça as seguintes tarefas para fechar os arquivos do aplicativo publicados para que você possa facilmente carregá-los para o seu cluster Databricks Spark.

   **No Windows:**

   Navegue até o mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64. Em seguida, clique com o botão direito do mouse na pasta **Publicar** e **selecione Enviar para > pasta Compactada (fechada).** Nomeie a nova pasta **publish.zip**.

   **No Linux, execute o seguinte comando:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Carregar arquivos

Nesta seção, você carrega vários arquivos para o DBFS para que seu cluster tenha tudo o que precisa para executar seu aplicativo na nuvem. Cada vez que você carregar um arquivo para o DBFS, certifique-se de que você está no diretório onde esse arquivo está localizado em seu computador.

1. Execute os seguintes comandos para carregar os *db-init.sh,* *install-worker.sh*e *Microsoft.Spark.Worker* para DBFS:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. Execute os seguintes comandos para carregar os arquivos restantes que seu cluster precisará para executar seu aplicativo: a pasta de publicação com zíper, *input.txt*e *microsoft-spark-2.4.x-0.3.0.jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>Criar um trabalho

Seu aplicativo é executado no Azure Databricks através de um trabalho que executa **o spark-submit**, que é o comando que você usa para executar .NET para trabalhos Apache Spark.

1. Em seu Espaço de Trabalho do Azure Databricks, selecione o ícone **Empregos** **e, em seguida, + Criar trabalho**.

   ![Crie um trabalho no Azure Databricks](./media/databricks-deployment/create-job.png)

2. Escolha um título para o seu trabalho e, em seguida, selecione **Configurar envio de faíscas**.

   ![Configure o envio de faíscas para o trabalho databricks](./media/databricks-deployment/configure-spark-submit.png)

3. Cole os seguintes parâmetros na configuração do trabalho. Em seguida, **selecione Confirmar**.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Criar um cluster

1. Navegue até o seu trabalho e selecione **Editar** para configurar o cluster do seu trabalho.

2. Defina seu cluster como **Spark 2.4.1**. Em seguida, selecione **Scripts init de opções** > **avançadas**. Definir init script `dbfs:/spark-dotnet/db-init.sh`path como .

   ![Configure cluster de faíscas no Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. Selecione **Confirmar** para confirmar as configurações do cluster.

## <a name="run-your-app"></a>Executar seu aplicativo

1. Navegue até o seu trabalho e selecione **Executar agora** para executar seu trabalho no cluster Spark recém-configurado.

2. Leva alguns minutos para o cluster do trabalho criar. Uma vez criado, seu trabalho será enviado, e você poderá visualizar a saída.

3. Selecione **Clusters** no menu esquerdo e, em seguida, o nome e execução do seu trabalho.

4. Selecione **Registros de driver** para exibir a saída do seu trabalho. Quando o aplicativo termina de executar, você vê a mesma tabela de contagem de palavras desde a execução local iniciada escrita até o console de saída padrão.

   ![Tabela de saída de trabalho do Azure Databricks](./media/databricks-deployment/table-output.png)

   Parabéns, você executou seu primeiro aplicativo .NET para Apache Spark na nuvem!

## <a name="clean-up-resources"></a>Limpar recursos

Se você não precisar mais do espaço de trabalho Databricks, você pode excluir o recurso Azure Databricks no portal Azure. Também é possível selecionar o nome do grupo de recursos para abrir a página do grupo de recursos, e depois selecionar **Excluir grupo de recursos**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Databricks. Para saber mais sobre o Databricks, leia a documentação do Azure Databricks.

> [!div class="nextstepaction"]
> [Documentação do Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
