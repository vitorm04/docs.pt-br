---
title: Implantar um aplicativo .NET para Apache Spark no Databricks
description: Descubra como implantar um aplicativo do .NET para Apache Spark no Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 035a3c36337413153ee0370aec154d48b84a4711
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957247"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Implantar um aplicativo .NET para Apache Spark no Databricks

Este tutorial ensina a implantar um aplicativo do .NET para Apache Spark para o Databricks.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Preparar o Microsoft.Spark.Worker
> - Publicar seu aplicativo Spark .NET
> - Implantar seu aplicativo no Databricks
> - Executar seu aplicativo

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça o seguinte:

- Baixe a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).
- Baixe o [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para seu computador local. Esse é um script auxiliar que você usa posteriormente para copiar arquivos dependentes do .NET para Apache Spark para os nós de trabalho do cluster do Spark.

## <a name="prepare-worker-dependencies"></a>Preparar dependências de trabalho

O **Microsoft.Spark.Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster do Spark. Quando você deseja executar uma UDF (função definida pelo usuário) em C#, o Spark precisa entender como iniciar o CLR .NET para executar a UDF. O **Microsoft.Spark.Worker** fornece uma coleção de classes para o Spark que habilitam essa funcionalidade.

1. Selecione uma versão do netcoreapp do Linux do [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) para ser implantada em seu cluster.

   Por exemplo, se quiser `.NET for Apache Spark v0.1.0` usando o `netcoreapp2.1`, você baixará o [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, DBFS) ao qual seu cluster tem acesso.

## <a name="prepare-your-net-for-apache-spark-app"></a>Preparar seu aplicativo .NET para Apache Spark

1. Siga o tutorial de [Introdução](get-started.md) para compilar seu aplicativo.

2. Publique seu aplicativo .NET do Spark como independente.

   Você pode executar o comando a seguir no Linux.

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produza `<your app>.zip` para os arquivos publicados.

   Você pode executar o comando a seguir no Linux usando `zip`.

   ```bash
   zip -r <your app>.zip .
   ```

4. Carregue o seguinte para um sistema de arquivos distribuído (por exemplo, DBFS) ao qual seu cluster tem acesso:

   - `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote do NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída do build do aplicativo.
   - `<your app>.zip`
   - Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu aplicativo depende) serão colocados no diretório de trabalho de cada executor.

## <a name="deploy-to-databricks"></a>Implantar no Databricks

O [Databricks](https://databricks.com) é uma plataforma que fornece processamento de Big Data baseado em nuvem usando o Apache Spark.

> [!Note] 
> O [Azure Databricks](https://azure.microsoft.com/services/databricks/) e o [AWS Databricks](https://databricks.com/aws) são baseados em Linux. Portanto, se você estiver interessado em implantar seu aplicativo no Databricks, verifique se ele é compatível com o .Net Standard e se você usa o [compilador do .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.

O Databricks permite que você envie aplicativos .NET para Apache Spark a um cluster ativo existente ou crie um novo cluster sempre que iniciar um trabalho. Isso exige que o **Microsoft.Spark.Worker** seja instalado antes de você enviar um aplicativo .NET para Apache Spark.

### <a name="deploy-microsoftsparkworker"></a>Implantar o Microsoft.Spark.Worker

Esta etapa é necessária apenas uma vez para um cluster.

1. Baixe [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) para seu computador local.

2. Modifique **db-init.sh** para apontar para a versão do **Microsoft.Spark.Worker** que você deseja baixar e instalar em seu cluster.

3. Instale a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).

4. Detalhes de [Configurar autenticação](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) para a CLI do Databricks.

5. Carregue os arquivos para o cluster do Databricks usando o seguinte comando:

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Vá para o espaço de trabalho do databricks. Selecione **Clusters** no menu do lado esquerdo e, em seguida, selecione **Criar Cluster**.

7. Depois de configurar o cluster adequadamente, defina o **Script Init** e crie o cluster.

   ![Imagem de Ação do Script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>Executar seu aplicativo 

Você pode usar `set JAR` ou `spark-submit` para enviar o trabalho para o Databricks.

### <a name="use-set-jar"></a>Usar o Set JAR

O [Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) permite que você envie um trabalho para um cluster ativo existente.

#### <a name="one-time-setup"></a>Configuração única

1. Acesse seu cluster do Databricks e selecione **Trabalhos** no menu do lado esquerdo. Em seguida, selecione **Set JAR**.

2. Carregue o arquivo `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` apropriado.

3. Defina os parâmetros adequadamente.

   | Parâmetro   | Valor                                                |
   |-------------|------------------------------------------------------|
   | Classe principal  | org. Apache. Spark. Deploy. dotnet. DotnetRunner          |
   | Argumentos   | /dBFS/apps/< your-app-Name >. zip < sua classe-App-Main-> |

4. Configure o **Cluster** para apontar para o cluster existente criado no **Init Script** na seção anterior.

#### <a name="publish-and-run-your-app"></a>Publicar e executar seu aplicativo

1. Use a [CLI do Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) para carregar seu aplicativo para o cluster do Databricks.

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. Esta etapa será necessária apenas se os assemblies do aplicativo (por exemplo, DLLs que contêm funções definidas pelo usuário junto com as respectivas dependências) precisarem ser colocados no diretório de trabalho de cada **Microsoft.Spark.Worker**.

   - Carregar os assemblies do aplicativo para o cluster do Databricks
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - Remova a marca de comentário e modifique a seção de dependências do aplicativo em [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) para apontar para o caminho de dependências do aplicativo e carregar para o cluster do Databricks.
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - Reinicie seu cluster.

3. Vá para o cluster do Databricks em seu workspace do Databricks. Em **Trabalhos**, selecione seu trabalho e, em seguida, selecione **Executar Agora** para executá-lo.

### <a name="use-spark-submit"></a>Usar spark-submit

O comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) permite que você envie um trabalho para um novo cluster.

1. [Crie um trabalho](https://docs.databricks.com/user-guide/jobs.html) e selecione **configurar spark-submit**.

2. Configure `spark-submit` com os seguintes parâmetros:

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Vá para o cluster do Databricks em seu workspace do Databricks. Em **Trabalhos**, selecione seu trabalho e, em seguida, selecione **Executar Agora** para executá-lo.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Databricks. Para saber mais sobre o Databricks, leia a documentação do Azure Databricks.

> [!div class="nextstepaction"]
> [Documentação do Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
