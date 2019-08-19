---
title: Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark
description: Descubra como implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5414bc20de3bb90a5d2144bd006d1b859e184a39
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "69576923"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark

Este tutorial ensina como implantar um aplicativo .NET para Apache Spark no Amazon EMR Spark.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Preparar o Microsoft. Spark. Worker
> * Publicar seu aplicativo Spark .NET
> * Implantar seu aplicativo no Amazon EMR Spark
> * Executar seu aplicativo

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, faça o seguinte:

* Baixe a [CLI do AWS](https://aws.amazon.com/cli/).
* Baixe o [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) no computador local. Esse é um script auxiliar que você usa posteriormente para copiar o .NET para Apache Spark arquivos dependentes nos nós de trabalho do seu cluster Spark.

## <a name="prepare-worker-dependencies"></a>Preparar dependências de trabalhador

**Microsoft. Spark. Worker** é um componente de back-end que reside nos nós de trabalho individuais do seu cluster Spark. Quando você deseja executar uma C# UDF (função definida pelo usuário), o Spark precisa entender como iniciar o .NET CLR para executar o UDF. **O Microsoft. Spark. Worker** fornece uma coleção de classes para Spark que habilitam essa funcionalidade.

1. Selecione uma versão do [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) netcoreapp do Linux para ser implantada em seu cluster.

   Por exemplo, se você quiser `.NET for Apache Spark v0.1.0` usar `netcoreapp2.1`o, você baixará [Microsoft. Spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Carregue `Microsoft.Spark.Worker.<release>.tar.gz` e [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) para um sistema de arquivos distribuído (por exemplo, S3) ao qual seu cluster tem acesso.

## <a name="prepare-your-net-for-apache-spark-app"></a>Preparar o aplicativo .NET para Apache Spark

1. Siga o tutorial de [introdução](get-started.md) para compilar seu aplicativo.

2. Publique seu aplicativo .NET Spark como independente.

   Execute o seguinte comando no Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Produzir `<your app>.zip` para os arquivos publicados.

   Execute o comando a seguir no Linux `zip`usando.

   ```bash
   zip -r <your app>.zip .
   ```

4. Carregue os seguintes itens em um sistema de arquivos distribuído (por exemplo, S3) ao qual seu cluster tem acesso:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Esse jar é incluído como parte do pacote NuGet do [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) e é colocado no diretório de saída da compilação do seu aplicativo.
   * `<your app>.zip`
   * Arquivos (como arquivos de dependência ou dados comuns acessíveis a cada trabalho) ou assemblies (como DLLs que contêm suas funções definidas pelo usuário ou bibliotecas das quais seu aplicativo depende) serão colocados no diretório de trabalho de cada executor.

## <a name="deploy-to-amazon-emr-spark"></a>Implantar no Amazon EMR Spark

O [Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) é uma plataforma de cluster gerenciada que simplifica a execução de estruturas Big data no AWS.

> [!NOTE] 
> O Amazon EMR Spark é baseado em Linux. Portanto, se você estiver interessado em implantar seu aplicativo no Amazon EMR Spark, verifique se seu aplicativo é .NET Standard compatível e se você usa o [compilador .NET Core](https://dotnet.microsoft.com/download) para compilar seu aplicativo.

### <a name="deploy-microsoftsparkworker"></a>Implantar Microsoft. Spark. Worker

Esta etapa só é necessária na criação do cluster.

Executar `install-worker.sh` durante a criação do cluster usando [ações de inicialização](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).

Execute o seguinte comando no Linux usando a CLI do AWS.

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>Executar seu aplicativo

Há duas maneiras de executar seu aplicativo no Amazon EMR Spark: Spark-Submit e nas etapas do Amazon EMR.

### <a name="use-spark-submit"></a>Usar Spark-enviar

Você pode usar o comando [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar Apache Spark trabalhos do .net para o Amazon EMR Spark.

1. `ssh`em um dos nós no cluster.

2. Execute `spark-submit`.

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Usar as etapas do Amazon EMR

[As etapas do Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) podem ser usadas para enviar trabalhos para a estrutura do Spark instalada no cluster EMR.

Execute o seguinte comando no Linux usando a CLI do AWS.

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você implantou seu .NET para Apache Spark aplicativo para o Amazon EMR Spark. Para .NET para Apache Spark projetos de exemplo, continue no GitHub.

> [!div class="nextstepaction"]
> [.NET para exemplos de Apache Spark](https://github.com/dotnet/spark/tree/master/examples)
