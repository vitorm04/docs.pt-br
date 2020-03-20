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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Saiba como construir seu aplicativo .NET para Apache Spark no Ubuntu

Este artigo ensina como construir seus aplicativos .NET para Apache Spark no Ubuntu.

## <a name="prerequisites"></a>Pré-requisitos

Se você já tiver todos os seguintes pré-requisitos, pule para as etapas [de construção.](#build)

1. Baixe e instale **[o .NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** ou o **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - a instalação do SDK adiciona a `dotnet` cadeia de ferramentas ao seu caminho.  .NET Core 2.1, 2.2 e 3.1 são suportados.

2. Instale **[o OpenJDK 8](https://openjdk.java.net/install/)**.

   - Você pode usar o seguinte comando:

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Verifique se você `java` é capaz de executar a partir de sua linha de comando.

      Amostra de saída da versão java:

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Se você já tiver várias versões OpenJDK instaladas e quiser selecionar OpenJDK 8, use o seguinte comando:

      ```bash
      sudo update-alternatives --config java
      ```

3. Instale **[o Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.

   * Execute o comando a seguir:

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

       Observe que essas variáveis de ambiente serão perdidas quando você fechar seu terminal. Se você quiser que as alterações sejam permanentes, adicione as `export` linhas ao seu `~/.bashrc` arquivo.

   * Verifique se você `mvn` é capaz de executar a partir de sua linha de comando

       Produção de versão mvn de amostra:

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Instale **[o Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.
Baixe [Apache Spark 2.3+](https://spark.apache.org/downloads.html) e extrai-o em `~/bin/spark-2.3.2-bin-hadoop2.7`uma pasta local (por exemplo, ). (As versões de faísca suportadas são 2.3.*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * Adicione as [variáveis de ambiente necessárias](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (por exemplo, `~/bin/spark-2.3.2-bin-hadoop2.7/`) e `PATH` (por exemplo, `$SPARK_HOME/bin:$PATH`)

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Observe que essas variáveis de ambiente serão perdidas quando você fechar seu terminal. Se você quiser que as alterações sejam permanentes, adicione as `export` linhas ao seu `~/.bashrc` arquivo.

   * Verifique se você `spark-shell` é capaz de executar a partir de sua linha de comando.

      Saída do console de amostra:

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

Certifique-se de que `dotnet` `java`você `mvn` `spark-shell` é capaz de executar , , a partir de sua linha de comando antes de passar para a próxima seção. Sente que há uma maneira melhor? Por [favor, abra um problema](https://github.com/dotnet/spark/issues) e sinta-se livre para contribuir.

## <a name="build"></a>Build

Para o restante deste guia, você precisará ter clonado o .NET para o repositório Apache Spark em sua máquina, por exemplo, `~/dotnet.spark/`.

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Construir a camada de extensões .NET para Spark Scala

Quando você envia um aplicativo .NET, .NET para Apache Spark tem a lógica necessária escrita no Scala que informa o Apache Spark como lidar com suas solicitações (por exemplo, solicitar a criação de uma nova Sessão spark, solicitar a transferência de dados do lado .NET para o lado JVM etc.). Esta lógica pode ser encontrada no [.NET para Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).

O próximo passo é construir a camada de extensão .NET para Apache Spark Scala:

```bash
cd src/scala
mvn clean package
```

Você deve ver JARs criados para as versões spark suportadas:

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Criar aplicativos de amostra .NET usando o .NET Core CLI

Esta seção explica como construir os [aplicativos de amostra](https://github.com/dotnet/spark/tree/master/examples) para .NET para Apache Spark. Essas etapas ajudarão a entender o processo de construção global para qualquer aplicativo .NET for Spark.

1. Construa o trabalhador:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Saída do console de amostra:

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

2. Construa as amostras:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   Saída do console de amostra:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Execute as aplicações de amostra .NET para Spark

Depois de construir as amostras, você pode usar `spark-submit` para enviar seus aplicativos .NET Core. Certifique-se de ter seguido a seção [de pré-requisitos](#prerequisites) e instalado apache spark.

1. Defina `DOTNET_WORKER_DIR` `PATH` a variável ou ambiente `Microsoft.Spark.Worker` para incluir o caminho onde o `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`binário foi gerado (por exemplo, ).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. Abra um terminal e vá para o diretório onde o binário `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`do aplicativo foi gerado (por exemplo, ).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. A execução do seu aplicativo segue a estrutura básica:

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Aqui estão alguns exemplos que você pode executar:

   * **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven acessível)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (frascos fornecidos)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
