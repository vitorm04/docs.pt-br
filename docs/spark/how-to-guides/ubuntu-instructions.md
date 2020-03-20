---
title: Construa um aplicativo .NET para Apache Spark no Ubuntu
description: Saiba como construir seu aplicativo .NET para Apache Spark no Ubuntu
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 6dd6f60bb89a51c47fe17182fc47de818cd00b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187564"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="b0278-103">Saiba como construir seu aplicativo .NET para Apache Spark no Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b0278-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="b0278-104">Este artigo ensina como construir seus aplicativos .NET para Apache Spark no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b0278-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0278-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b0278-105">Prerequisites</span></span>

<span data-ttu-id="b0278-106">Se você já tiver todos os seguintes pré-requisitos, pule para as etapas [de construção.](#build)</span><span class="sxs-lookup"><span data-stu-id="b0278-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="b0278-107">Baixe e instale **[o .NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** ou o **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - a instalação do SDK adiciona a `dotnet` cadeia de ferramentas ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="b0278-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="b0278-108">.NET Core 2.1, 2.2 e 3.1 são suportados.</span><span class="sxs-lookup"><span data-stu-id="b0278-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="b0278-109">Instale **[o OpenJDK 8](https://openjdk.java.net/install/)**.</span><span class="sxs-lookup"><span data-stu-id="b0278-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="b0278-110">Você pode usar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b0278-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="b0278-111">Verifique se você `java` é capaz de executar a partir de sua linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b0278-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="b0278-112">Amostra de saída da versão java:</span><span class="sxs-lookup"><span data-stu-id="b0278-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="b0278-113">Se você já tiver várias versões OpenJDK instaladas e quiser selecionar OpenJDK 8, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b0278-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="b0278-114">Instale **[o Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span><span class="sxs-lookup"><span data-stu-id="b0278-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="b0278-115">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b0278-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       <span data-ttu-id="b0278-116">Observe que essas variáveis de ambiente serão perdidas quando você fechar seu terminal.</span><span class="sxs-lookup"><span data-stu-id="b0278-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="b0278-117">Se você quiser que as alterações sejam permanentes, adicione as `export` linhas ao seu `~/.bashrc` arquivo.</span><span class="sxs-lookup"><span data-stu-id="b0278-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="b0278-118">Verifique se você `mvn` é capaz de executar a partir de sua linha de comando</span><span class="sxs-lookup"><span data-stu-id="b0278-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="b0278-119">Produção de versão mvn de amostra:</span><span class="sxs-lookup"><span data-stu-id="b0278-119">Sample mvn -version output:</span></span>

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="b0278-120">Instale **[o Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span><span class="sxs-lookup"><span data-stu-id="b0278-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="b0278-121">Baixe [Apache Spark 2.3+](https://spark.apache.org/downloads.html) e extrai-o em `~/bin/spark-2.3.2-bin-hadoop2.7`uma pasta local (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="b0278-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="b0278-122">(As versões de faísca suportadas são 2.3.\*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="b0278-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="b0278-123">Adicione as [variáveis de ambiente necessárias](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (por exemplo, `~/bin/spark-2.3.2-bin-hadoop2.7/`) e `PATH` (por exemplo, `$SPARK_HOME/bin:$PATH`)</span><span class="sxs-lookup"><span data-stu-id="b0278-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="b0278-124">Observe que essas variáveis de ambiente serão perdidas quando você fechar seu terminal.</span><span class="sxs-lookup"><span data-stu-id="b0278-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="b0278-125">Se você quiser que as alterações sejam permanentes, adicione as `export` linhas ao seu `~/.bashrc` arquivo.</span><span class="sxs-lookup"><span data-stu-id="b0278-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="b0278-126">Verifique se você `spark-shell` é capaz de executar a partir de sua linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b0278-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="b0278-127">Saída do console de amostra:</span><span class="sxs-lookup"><span data-stu-id="b0278-127">Sample console output:</span></span>

      ```
      Welcome to
            ____              __
           / __/__  ___ _____/ /__
          _\ \/ _ \/ _ `/ __/  '_/
         /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
            /_/

      Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
      Type in expressions to have them evaluated.
      Type :help for more information.

      scala> sc
      res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
      ```

<span data-ttu-id="b0278-128">Certifique-se de que `dotnet` `java`você `mvn` `spark-shell` é capaz de executar , , a partir de sua linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="b0278-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="b0278-129">Sente que há uma maneira melhor?</span><span class="sxs-lookup"><span data-stu-id="b0278-129">Feel there is a better way?</span></span> <span data-ttu-id="b0278-130">Por [favor, abra um problema](https://github.com/dotnet/spark/issues) e sinta-se livre para contribuir.</span><span class="sxs-lookup"><span data-stu-id="b0278-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="b0278-131">Build</span><span class="sxs-lookup"><span data-stu-id="b0278-131">Build</span></span>

<span data-ttu-id="b0278-132">Para o restante deste guia, você precisará ter clonado o .NET para o repositório Apache Spark em sua máquina, por exemplo, `~/dotnet.spark/`.</span><span class="sxs-lookup"><span data-stu-id="b0278-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="b0278-133">Construir a camada de extensões .NET para Spark Scala</span><span class="sxs-lookup"><span data-stu-id="b0278-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="b0278-134">Quando você envia um aplicativo .NET, .NET para Apache Spark tem a lógica necessária escrita no Scala que informa o Apache Spark como lidar com suas solicitações (por exemplo, solicitar a criação de uma nova Sessão spark, solicitar a transferência de dados do lado .NET para o lado JVM etc.).</span><span class="sxs-lookup"><span data-stu-id="b0278-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="b0278-135">Esta lógica pode ser encontrada no [.NET para Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="b0278-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="b0278-136">O próximo passo é construir a camada de extensão .NET para Apache Spark Scala:</span><span class="sxs-lookup"><span data-stu-id="b0278-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="b0278-137">Você deve ver JARs criados para as versões spark suportadas:</span><span class="sxs-lookup"><span data-stu-id="b0278-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="b0278-138">Criar aplicativos de amostra .NET usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="b0278-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="b0278-139">Esta seção explica como construir os [aplicativos de amostra](https://github.com/dotnet/spark/tree/master/examples) para .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b0278-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="b0278-140">Essas etapas ajudarão a entender o processo de construção global para qualquer aplicativo .NET for Spark.</span><span class="sxs-lookup"><span data-stu-id="b0278-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="b0278-141">Construa o trabalhador:</span><span class="sxs-lookup"><span data-stu-id="b0278-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="b0278-142">Saída do console de amostra:</span><span class="sxs-lookup"><span data-stu-id="b0278-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="b0278-143">Construa as amostras:</span><span class="sxs-lookup"><span data-stu-id="b0278-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="b0278-144">Saída do console de amostra:</span><span class="sxs-lookup"><span data-stu-id="b0278-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="b0278-145">Execute as aplicações de amostra .NET para Spark</span><span class="sxs-lookup"><span data-stu-id="b0278-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="b0278-146">Depois de construir as amostras, você pode usar `spark-submit` para enviar seus aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0278-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="b0278-147">Certifique-se de ter seguido a seção [de pré-requisitos](#prerequisites) e instalado apache spark.</span><span class="sxs-lookup"><span data-stu-id="b0278-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="b0278-148">Defina `DOTNET_WORKER_DIR` `PATH` a variável ou ambiente `Microsoft.Spark.Worker` para incluir o caminho onde o `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`binário foi gerado (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="b0278-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="b0278-149">Abra um terminal e vá para o diretório onde o binário `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`do aplicativo foi gerado (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="b0278-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="b0278-150">A execução do seu aplicativo segue a estrutura básica:</span><span class="sxs-lookup"><span data-stu-id="b0278-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="b0278-151">Aqui estão alguns exemplos que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="b0278-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="b0278-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="b0278-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="b0278-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b0278-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="b0278-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven acessível)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b0278-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="b0278-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (frascos fornecidos)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="b0278-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
