---
title: Construa um aplicativo .NET para Apache Spark no Windows
description: Aprenda a construir seu aplicativo .NET para Apache Spark no Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185751"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Saiba como construir seu aplicativo .NET para Apache Spark no Windows

Este artigo ensina como construir seus aplicativos .NET para Apache Spark no Windows.

## <a name="prerequisites"></a>Pré-requisitos

Se você já tiver todos os seguintes pré-requisitos, pule para as etapas [de construção.](#build)

  1. Baixe e instale o **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - `dotnet` a instalação do SDK adicionará a cadeia de ferramentas ao seu caminho. .NET Core 2.1, 2.2 e 3.1 são suportados.
  2. Instale **[o Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Versão 16.3 ou posterior). A versão comunitária é completamente gratuita. Ao configurar sua instalação, inclua esses componentes no mínimo:
     * Desenvolvimento de área de trabalho do .NET
       * Todos os componentes necessários
         * Ferramentas de desenvolvimento do .NET Framework 4.6.1
     * Desenvolvimento multiplataforma com o .NET Core
       * Todos os componentes necessários
  3. Instale **[java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Selecione a versão apropriada para seu sistema operacional. Por exemplo, *jdk-8u201-windows-x64.exe* para a máquina Windows x64.
     - Instale usando o instalador e `java` verifique se você é capaz de executar a partir de sua linha de comando.
  4. Instale **[o Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.
     - Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Extraia para um diretório local. Por exemplo, *C:\bin\apache-maven-3.6.0\*.
     - Adicione o Apache Maven à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml). Por exemplo, *C:\bin\apache-maven-3.6.0\bin*.
     - Verifique se você `mvn` é capaz de executar a partir de sua linha de comando.
  5. Instale **[o Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.
     - Baixe [Apache Spark 2.3+](https://spark.apache.org/downloads.html) e extrai-o em uma pasta local (por exemplo, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) usando [7-zip](https://www.7-zip.org/). (As versões de faísca suportadas são 2.3.*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)
     - Adicione uma [nova variável](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`de ambiente . Por exemplo, *C:\bin\spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - Adicione o Apache Spark à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml). Por exemplo, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Verifique se você `spark-shell` é capaz de executar a partir de sua linha de comando.
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

        </details>

  6. Instale **[o WinUtils](https://github.com/steveloughran/winutils)**.
     - Baixar `winutils.exe` binário do [repositório WinUtils](https://github.com/steveloughran/winutils). Você deve selecionar a versão de Hadoop com a distribuição Spark foi compilada. Para o exame, use hadoop-2.7.1 para a Centelha 2.3.2.
     - Salve `winutils.exe` o binário em um diretório de sua escolha. Por exemplo, *C:\hadoop\bin*.
     - Definido `HADOOP_HOME` para refletir o diretório com winutils.exe (sem bin). Por exemplo, usando linha de comando:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Definir a variável `%HADOOP_HOME%\bin`de ambiente PATH para incluir . Por exemplo, usando a linha de comando:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Certifique-se de que `dotnet` `java`você `mvn` `spark-shell` é capaz de executar , , a partir de sua linha de comando antes de passar para a próxima seção. Sente que há uma maneira melhor? [Abra um problema](https://github.com/dotnet/spark/issues) e sinta-se livre para contribuir.

> [!NOTE]
> Uma nova instância da linha de comando pode ser necessária se quaisquer variáveis de ambiente forem atualizadas.

## <a name="build"></a>Build

Para o restante deste guia, você precisará ter clonado o .NET para o repositório Apache Spark em sua máquina. Você pode escolher qualquer local para o repositório clonado. Por exemplo, *C:\github\dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Construir .NET para a camada de extensões Apache Spark Scala

Quando você envia um aplicativo .NET, .NET para Apache Spark tem a lógica necessária escrita no Scala que informa o Apache Spark como lidar com suas solicitações (por exemplo, solicitar a criação de uma nova Sessão spark, solicitar a transferência de dados do lado .NET para o lado JVM etc.). Essa lógica pode ser encontrada no [.NET para Código Fonte Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).

Independentemente de você estar usando .NET Framework ou .NET Core, você precisará construir a camada de extensão .NET para Apache Spark Scala:

```powershell
cd src\scala
mvn clean package
```

Você deve ver JARs criados para as versões spark suportadas:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Construa as aplicações de amostra .NET para Spark

Esta seção explica como construir os [aplicativos de amostra](https://github.com/dotnet/spark/tree/master/examples) para .NET para Apache Spark. Essas etapas ajudarão a entender o processo de construção global para qualquer aplicativo .NET for Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Usando o Visual Studio para .NET Framework

  1. Abra `src\csharp\Microsoft.Spark.sln` no Visual Studio `Microsoft.Spark.CSharp.Examples` e `examples` construa o projeto a pasta (isso, por sua vez, construirá o projeto de vinculações .NET também). Se você quiser, você pode escrever `Microsoft.Spark.Examples` seu próprio código no projeto (o 'input_file.json' neste exemplo é um arquivo json com os dados com os quais você deseja criar o dataframe):
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     Uma vez que a compilação seja bem sucedida, você verá os binários apropriados produzidos no diretório de saída.
     Saída do console de amostra:

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a>Usando o .NET Core CLI para .NET Core

> [!NOTE]
> No momento, estamos trabalhando na automação de compilações .NET Core para Spark .NET. Até lá, agradecemos sua paciência em executar algumas das etapas manualmente.

  1. Construa o trabalhador:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Saída do console de amostra:

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. Construa as amostras:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Saída do console de amostra:

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>Execute as aplicações de amostra .NET para Spark

Uma vez que você construa `spark-submit` as amostras, executá-las será através de qualquer maneira se você está mirando .NET Framework ou .NET Core. Certifique-se de ter seguido a seção [de pré-requisitos](#prerequisites) e instalado apache spark.

  1. Defina `DOTNET_WORKER_DIR` `PATH` a variável ou ambiente `Microsoft.Spark.Worker` para incluir o caminho onde o binário foi gerado (por exemplo, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark Worker\Debug\netcore2.1\win10-x64\publish* for .NET

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Abra o Powershell e vá para o diretório onde o binário do aplicativo foi gerado (por exemplo, *C:\github\dotnet\spark\artefatos\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* para .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. A execução do seu aplicativo segue a estrutura básica:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Aqui estão alguns exemplos que você pode executar:

     - **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven acessível)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (frascos fornecidos)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
