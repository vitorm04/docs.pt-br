---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo do .NET para Apache Spark no HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2e8da5497035a83fde75bf91a7d21437d510b480
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117978"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Implantar um aplicativo .NET para Apache Spark no Azure HDInsight

Este tutorial ensina a implantar um aplicativo do .NET para Apache Spark no Azure HDInsight.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Preparar o Microsoft.Spark.Worker
> * Publicar seu aplicativo Spark .NET
> * Implantar seu aplicativo no Azure HDInsight
> * Executar seu aplicativo

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça o seguinte:

* Baixe o [Gerenciador de Armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/).
* Baixe o [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para seu computador local. Esse é um script auxiliar que você usa posteriormente para copiar arquivos dependentes do .NET para Apache Spark para os nós de trabalho do cluster do Spark.

## <a name="prepare-worker-dependencies"></a>Preparar dependências de trabalho

O **Microsoft.Spark.Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster do Spark. Quando você deseja executar uma UDF (função definida pelo usuário) em C#, o Spark precisa entender como iniciar o CLR .NET para executar a UDF. O **Microsoft.Spark.Worker** fornece uma coleção de classes para o Spark que habilitam essa funcionalidade.

1. Selecione uma versão do netcoreapp do Linux do [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) para ser implantada em seu cluster.

   Por exemplo, se quiser `.NET for Apache Spark v0.1.0` usando o `netcoreapp2.1`, você baixará o [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso.

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

4. Carregue o seguinte para um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote do NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída do build do aplicativo.
   * `<your app>.zip`
   * Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou Assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu `app` depende) serão colocados no diretório de trabalho de cada executor.

## <a name="deploy-to-azure-hdinsight-spark"></a>Implantar no Azure HDInsight Spark

O [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) é a implementação da Microsoft do Apache Spark na nuvem que permite que os usuários iniciem e configurem clusters do Spark no Azure. Você pode usar clusters do Spark do HDInsight para processar seus dados armazenados no [Armazenamento do Azure](https://azure.microsoft.com/services/storage/) ou no [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> O Azure HDInsight Spark é baseado em Linux. Se você estiver interessado em implantar seu aplicativo no Azure HDInsight Spark, verifique se seu aplicativo é compatível com o .Net Standard e se você usa o [compilador do .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.

### <a name="deploy-microsoftsparkworker"></a>Implantar o Microsoft.Spark.Worker

Esta etapa é necessária apenas uma vez para seu cluster.

Execute `install-worker.sh` no cluster usando as [Ações de Script do HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Configuração|Valor|
|-------|-----|
|Tipo de script|Personalizado|
|Nome|Instalar o Microsoft.Spark.Worker|
|URI do script bash|O URI para o qual você carregou `install-worker.sh`. Por exemplo, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|Tipo (s) de nó|Funcionários|
|Parâmetros|Parâmetros para `install-worker.sh`. Por exemplo, se você carregasse o `install-worker.sh` para o Azure Data Lake Gen 2, ele seria `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.|

![Imagem de Ação do Script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Executar seu aplicativo

Você pode enviar seu trabalho para o Azure HDInsight usando `spark-submit` o ou o Apache Livy.

### <a name="use-spark-submit"></a>Usar spark-submit

Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar trabalhos do .NET para Apache Spark para o Azure HDInsight.
 
1. `ssh` em um dos nós de cabeçalho no cluster.

1. Executar `spark-submit`:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Usar o Apache Livy

Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos do .NET para Apache Spark a um cluster do Azure HDInsight Spark. Para obter mais informações, consulte [Trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Você pode executar o comando a seguir no Linux usando `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu aplicativo .NET para Apache Spark para o Azure HDInsight. Para saber mais sobre o HDInsight, continue na Documentação do Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentação do Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
