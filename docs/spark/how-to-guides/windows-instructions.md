---
title: Criar um aplicativo .NET para Apache Spark no Windows
description: Saiba como criar seu .NET para Apache Spark aplicativo no Windows.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: d355380e92235e799d366dca02eaf8450f563f33
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609272"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="ffd70-103">Saiba como criar seu .NET para Apache Spark aplicativo no Windows</span><span class="sxs-lookup"><span data-stu-id="ffd70-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="ffd70-104">Este artigo ensina como criar seu .NET para aplicativos Apache Spark no Windows.</span><span class="sxs-lookup"><span data-stu-id="ffd70-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="ffd70-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ffd70-105">Prerequisites</span></span>

<span data-ttu-id="ffd70-106">Se você já tiver todos os pré-requisitos a seguir, pule para as etapas de [compilação](#build) .</span><span class="sxs-lookup"><span data-stu-id="ffd70-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="ffd70-107">Baixar e instalar o **[SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/2.1)** -a instalação do SDK adicionará o `dotnet` ferramentas ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="ffd70-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="ffd70-108">Há suporte para o .NET Core 2,1, 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="ffd70-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="ffd70-109">Instale o **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (versão 16,3 ou posterior).</span><span class="sxs-lookup"><span data-stu-id="ffd70-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="ffd70-110">A versão da Comunidade é totalmente gratuita.</span><span class="sxs-lookup"><span data-stu-id="ffd70-110">The Community version is completely free.</span></span> <span data-ttu-id="ffd70-111">Ao configurar sua instalação, inclua estes componentes no mínimo:</span><span class="sxs-lookup"><span data-stu-id="ffd70-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="ffd70-112">Desenvolvimento para área de trabalho com .NET</span><span class="sxs-lookup"><span data-stu-id="ffd70-112">.NET desktop development</span></span>
       * <span data-ttu-id="ffd70-113">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="ffd70-113">All Required Components</span></span>
         * <span data-ttu-id="ffd70-114">Ferramentas de desenvolvimento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ffd70-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="ffd70-115">Desenvolvimento multiplataforma com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="ffd70-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="ffd70-116">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="ffd70-116">All Required Components</span></span>
  3. <span data-ttu-id="ffd70-117">Instale o **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span><span class="sxs-lookup"><span data-stu-id="ffd70-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="ffd70-118">Selecione a versão apropriada para seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ffd70-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="ffd70-119">Por exemplo, *jdk-8u201-windows-x64.exe* para o computador Windows x64.</span><span class="sxs-lookup"><span data-stu-id="ffd70-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="ffd70-120">Instale o usando o instalador e verifique se você consegue executar a `java` partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ffd70-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="ffd70-121">Instale o **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**.</span><span class="sxs-lookup"><span data-stu-id="ffd70-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="ffd70-122">Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="ffd70-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="ffd70-123">Extraia para um diretório local.</span><span class="sxs-lookup"><span data-stu-id="ffd70-123">Extract to a local directory.</span></span> <span data-ttu-id="ffd70-124">Por exemplo, \* C:\bin\apache-Maven-3.6.0 \* .</span><span class="sxs-lookup"><span data-stu-id="ffd70-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="ffd70-125">Adicione o Apache Maven à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="ffd70-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="ffd70-126">Por exemplo, *C:\bin\apache-Maven-3.6.0\Bin*.</span><span class="sxs-lookup"><span data-stu-id="ffd70-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="ffd70-127">Verifique se você pode executar a `mvn` partir de sua linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ffd70-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="ffd70-128">Instale o **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**.</span><span class="sxs-lookup"><span data-stu-id="ffd70-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="ffd70-129">Baixe [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) e extraia-o em uma pasta local (por exemplo, *C:\bin\spark-2.3.2-bin-hadoop2.7 \* ) usando [7-zip](https://www.7-zip.org/). (As versões do Spark com suporte são 2,3.*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="ffd70-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="ffd70-130">Adicione uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` .</span><span class="sxs-lookup"><span data-stu-id="ffd70-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="ffd70-131">Por exemplo, \* C:\bin\spark-2.3.2-bin-hadoop2.7 \* .</span><span class="sxs-lookup"><span data-stu-id="ffd70-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - <span data-ttu-id="ffd70-132">Adicione o Apache Spark à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="ffd70-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="ffd70-133">Por exemplo, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span><span class="sxs-lookup"><span data-stu-id="ffd70-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="ffd70-134">Verifique se você pode executar a `spark-shell` partir de sua linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ffd70-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="ffd70-135">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="ffd70-135">Sample console output:</span></span>

        ```output
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

  6. <span data-ttu-id="ffd70-136">Instale o **[WinUtils](https://github.com/steveloughran/winutils)**.</span><span class="sxs-lookup"><span data-stu-id="ffd70-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="ffd70-137">Baixe o `winutils.exe` binário do [repositório WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="ffd70-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="ffd70-138">Você deve selecionar a versão do Hadoop com a qual a distribuição do Spark foi compilada.</span><span class="sxs-lookup"><span data-stu-id="ffd70-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="ffd70-139">Para exammple, use Hadoop-2.7.1 para Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="ffd70-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="ffd70-140">Salve `winutils.exe` Binary em um diretório de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="ffd70-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="ffd70-141">Por exemplo, *C:\hadoop\bin*.</span><span class="sxs-lookup"><span data-stu-id="ffd70-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="ffd70-142">Defina `HADOOP_HOME` para refletir o diretório com winutils.exe (sem bin).</span><span class="sxs-lookup"><span data-stu-id="ffd70-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="ffd70-143">Por exemplo, usando a linha de comando:</span><span class="sxs-lookup"><span data-stu-id="ffd70-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="ffd70-144">Defina a variável de ambiente PATH como include `%HADOOP_HOME%\bin` .</span><span class="sxs-lookup"><span data-stu-id="ffd70-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="ffd70-145">Por exemplo, usando a linha de comando:</span><span class="sxs-lookup"><span data-stu-id="ffd70-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="ffd70-146">Verifique se você pode executar `dotnet` o,, `java` `mvn` , `spark-shell` da linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="ffd70-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="ffd70-147">Existe uma maneira melhor?</span><span class="sxs-lookup"><span data-stu-id="ffd70-147">Feel there is a better way?</span></span> <span data-ttu-id="ffd70-148">[Abra um problema](https://github.com/dotnet/spark/issues) e sinta-se à vontade para contribuir.</span><span class="sxs-lookup"><span data-stu-id="ffd70-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="ffd70-149">Uma nova instância da linha de comando poderá ser necessária se qualquer variável de ambiente tiver sido atualizada.</span><span class="sxs-lookup"><span data-stu-id="ffd70-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="ffd70-150">Compilação</span><span class="sxs-lookup"><span data-stu-id="ffd70-150">Build</span></span>

<span data-ttu-id="ffd70-151">Para o restante deste guia, você precisará ter clonado o .NET para Apache Spark repositório em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ffd70-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="ffd70-152">Você pode escolher qualquer local para o repositório clonado.</span><span class="sxs-lookup"><span data-stu-id="ffd70-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="ffd70-153">Por exemplo, \* C:\github\dotnet-Spark \* .</span><span class="sxs-lookup"><span data-stu-id="ffd70-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="ffd70-154">Compilar .NET para Apache Spark camada de extensões escalares</span><span class="sxs-lookup"><span data-stu-id="ffd70-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="ffd70-155">Quando você envia um aplicativo .NET, o .NET para Apache Spark tem a lógica necessária escrita em escalares que informa Apache Spark como lidar com suas solicitações (por exemplo, solicitação para criar uma nova sessão do Spark, solicitação para transferir dados do lado do .NET para o lado da JVM, etc.).</span><span class="sxs-lookup"><span data-stu-id="ffd70-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="ffd70-156">Essa lógica pode ser encontrada no [código-fonte do .net para Spark escala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="ffd70-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="ffd70-157">Independentemente de você estar usando o .NET Framework ou o .NET Core, será necessário criar o .NET para Apache Spark camada de extensão escalabilidade:</span><span class="sxs-lookup"><span data-stu-id="ffd70-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="ffd70-158">Você deve ver os JARs criados para as versões do Spark com suporte:</span><span class="sxs-lookup"><span data-stu-id="ffd70-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="ffd70-159">Compilar o .NET para aplicativos de exemplo do Spark</span><span class="sxs-lookup"><span data-stu-id="ffd70-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="ffd70-160">Esta seção explica como criar os [aplicativos de exemplo](https://github.com/dotnet/spark/tree/master/examples) para .net para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="ffd70-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="ffd70-161">Essas etapas ajudarão a compreender o processo de criação geral de qualquer aplicativo .NET para Spark.</span><span class="sxs-lookup"><span data-stu-id="ffd70-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="ffd70-162">Usando o Visual Studio para .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ffd70-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="ffd70-163">Abra `src\csharp\Microsoft.Spark.sln` no Visual Studio e compile o `Microsoft.Spark.CSharp.Examples` projeto na `examples` pasta (isso, por sua vez, criará também o projeto de associações .net).</span><span class="sxs-lookup"><span data-stu-id="ffd70-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="ffd70-164">Se desejar, você pode escrever seu próprio código no `Microsoft.Spark.Examples` projeto (o ' input_file.jsem ' neste exemplo é um arquivo JSON com os dados com os quais você deseja criar o dataframe):</span><span class="sxs-lookup"><span data-stu-id="ffd70-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
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

     <span data-ttu-id="ffd70-165">Depois que a compilação for bem-sucedida, você verá os binários apropriados produzidos no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="ffd70-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="ffd70-166">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="ffd70-166">Sample console output:</span></span>

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

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="ffd70-167">Usando o CLI do .NET Core para .NET Core</span><span class="sxs-lookup"><span data-stu-id="ffd70-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="ffd70-168">No momento, estamos trabalhando para automatizar as compilações do .NET Core para Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="ffd70-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="ffd70-169">Até lá, agradecemos sua paciência em executar algumas das etapas manualmente.</span><span class="sxs-lookup"><span data-stu-id="ffd70-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="ffd70-170">Crie o trabalho:</span><span class="sxs-lookup"><span data-stu-id="ffd70-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="ffd70-171">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="ffd70-171">Sample console output:</span></span>

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

  2. <span data-ttu-id="ffd70-172">Compile os exemplos:</span><span class="sxs-lookup"><span data-stu-id="ffd70-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="ffd70-173">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="ffd70-173">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="ffd70-174">Executar o .NET para aplicativos de exemplo do Spark</span><span class="sxs-lookup"><span data-stu-id="ffd70-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="ffd70-175">Depois de criar os exemplos, executá-los será por meio `spark-submit` de você, independentemente de você estar se concentrando .NET Framework ou no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ffd70-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="ffd70-176">Verifique se você seguiu a seção de [pré-requisitos](#prerequisites) e instalou o Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="ffd70-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="ffd70-177">Defina a `DOTNET_WORKER_DIR` `PATH` variável de ambiente ou para incluir o caminho em que o `Microsoft.Spark.Worker` binário foi gerado (por exemplo, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* para .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* para .NET Core):</span><span class="sxs-lookup"><span data-stu-id="ffd70-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="ffd70-178">Abra o PowerShell e vá para o diretório em que o binário do aplicativo foi gerado (por exemplo, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* para .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* para .NET Core):</span><span class="sxs-lookup"><span data-stu-id="ffd70-178">Open PowerShell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="ffd70-179">A execução do aplicativo segue a estrutura básica:</span><span class="sxs-lookup"><span data-stu-id="ffd70-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="ffd70-180">Aqui estão alguns exemplos que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="ffd70-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="ffd70-181">**[Microsoft.Spark.Examples.Sql.Batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="ffd70-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="ffd70-182">**[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="ffd70-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="ffd70-183">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (com acesso ao Maven)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="ffd70-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="ffd70-184">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (jars fornecidos)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="ffd70-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
