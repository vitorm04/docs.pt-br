---
title: Implantar um aplicativo .NET para Apache Spark no Azure HDInsight
description: Descubra como implantar um aplicativo .NET para Apache Spark no HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4769c194520790ce217d46d1d3197b20742d4f1a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "69576943"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Implantar um aplicativo .NET para Apache Spark no Azure HDInsight

Este tutorial ensina como implantar um aplicativo .NET para Apache Spark no Azure HDInsight.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Preparar o Microsoft. Spark. Worker
> * Publicar seu aplicativo Spark .NET
> * Implantar seu aplicativo no Azure HDInsight
> * Executar seu aplicativo

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça o seguinte:

* Baixar [Gerenciador de armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/).
* Baixe o [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) no computador local. Esse é um script auxiliar que você usa posteriormente para copiar o .NET para Apache Spark arquivos dependentes nos nós de trabalho do seu cluster Spark.

## <a name="prepare-worker-dependencies"></a>Preparar dependências de trabalhador

**Microsoft. Spark. Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster Spark. Quando você deseja executar uma C# UDF (função definida pelo usuário), o Spark precisa entender como iniciar o .NET CLR para executar o UDF. **O Microsoft. Spark. Worker** fornece uma coleção de classes para Spark que habilitam essa funcionalidade.

1. Selecione uma versão do [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) netcoreapp do Linux para ser implantada em seu cluster.

   Por exemplo, se você quiser `.NET for Apache Spark v0.1.0` usar `netcoreapp2.1`o, você baixará [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso.

## <a name="prepare-your-net-for-apache-spark-app"></a>Preparar o aplicativo .NET para Apache Spark

1. Siga o tutorial de [introdução](get-started.md) para compilar seu aplicativo.

2. Publique seu aplicativo .NET Spark como independente.

   Você pode executar o comando a seguir no Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produzir `<your app>.zip` para os arquivos publicados.

   Você pode executar o comando a seguir no Linux `zip`usando.

   ```bash
   zip -r <your app>.zip .
   ```

4. Carregue o seguinte em um sistema de arquivos distribuído (por exemplo, HDFS, WASB, ADLS) ao qual seu cluster tem acesso:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote NuGet do [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída da compilação do seu aplicativo.
   * `<your app>.zip`
   * Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas que `app` dependem) serão colocados no diretório de trabalho de cada executor.

## <a name="deploy-to-azure-hdinsight-spark"></a>Implantar no Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) é a implementação da Microsoft de Apache Spark na nuvem que permite que os usuários iniciem e configurem clusters Spark no Azure. Você pode usar clusters Spark do HDInsight para processar seus dados armazenados no [armazenamento do Azure](https://azure.microsoft.com/services/storage/) ou [Azure data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> O Azure HDInsight Spark é baseado em Linux. Se você estiver interessado em implantar seu aplicativo para Azure HDInsight Spark, verifique se seu aplicativo é .NET Standard compatível e se você usa o [compilador .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.

### <a name="deploy-microsoftsparkworker"></a>Implantar Microsoft. Spark. Worker

Essa etapa é necessária apenas uma vez para o cluster.

Execute `install-worker.sh` no cluster usando as [ações de script do HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Configuração|Valor|
|-------|-----|
|Tipo de script|Personalizado|
|Nome|Instalar Microsoft. Spark. Worker|
|URI do script bash|O URI para o qual você `install-worker.sh`carregou. Por exemplo, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|Tipo (s) de nó|Funcionários|
|Parâmetros|Parâmetros para `install-worker.sh`. Por exemplo, se você carregou `install-worker.sh` para Azure data Lake Gen 2, `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`seria.|

![Imagem de ação de script](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Executar seu aplicativo

Você pode enviar seu trabalho para o Azure HDInsight `spark-submit` usando o ou o Apache Livy.

### <a name="use-spark-submit"></a>Usar Spark-enviar

Você pode usar o comando [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar Apache Spark trabalhos do .net para o Azure HDInsight.
 
1. `ssh`em um dos nós de cabeçalho no cluster.

1. Executar `spark-submit`:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Usar o Apache Livy

Você pode usar o [Apache Livy](https://livy.incubator.apache.org/), a API REST do Apache Spark, para enviar trabalhos .net para Apache Spark a um cluster Azure HDInsight Spark. Para obter mais informações, consulte [trabalhos remotos com o Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Você pode executar o seguinte comando no Linux usando `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu .NET para Apache Spark aplicativo para o Azure HDInsight. Para saber mais sobre o HDInsight, continue na documentação do Azure HDInsight.

> [!div class="nextstepaction"]
> [Documentação do Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
