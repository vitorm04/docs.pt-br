---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577003"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="5a111-103">Tutorial: Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="5a111-104">Este tutorial ensina como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="5a111-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="5a111-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="5a111-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="5a111-106">Preparar seu ambiente do Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5a111-107">Baixe o **Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="5a111-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="5a111-108">Compilar e executar um aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="5a111-109">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="5a111-109">Prepare your environment</span></span>

<span data-ttu-id="5a111-110">Antes de começar, verifique se você pode executar `dotnet` `mvn`, `java`,, `spark-shell` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5a111-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="5a111-111">Se seu ambiente já estiver preparado, você poderá pular para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="5a111-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="5a111-112">Se você não puder executar um ou todos os comandos, siga as etapas abaixo.</span><span class="sxs-lookup"><span data-stu-id="5a111-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="5a111-113">Baixe e instale o [SDK do .NET Core 2.1 x](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="5a111-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="5a111-114">A instalação do SDK adiciona `dotnet` o ferramentas ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="5a111-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="5a111-115">Use o comando `dotnet --version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="5a111-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="5a111-116">Instale o [visual studio 2017](https://www.visualstudio.com/downloads/) ou o [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) com as atualizações mais recentes.</span><span class="sxs-lookup"><span data-stu-id="5a111-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="5a111-117">Você pode usar o Community, o Professional ou o Enterprise.</span><span class="sxs-lookup"><span data-stu-id="5a111-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="5a111-118">A versão da Comunidade é gratuita.</span><span class="sxs-lookup"><span data-stu-id="5a111-118">The Community version is free.</span></span>

   <span data-ttu-id="5a111-119">Escolha as seguintes cargas de trabalho durante a instalação:</span><span class="sxs-lookup"><span data-stu-id="5a111-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="5a111-120">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="5a111-120">.NET desktop development</span></span>
          * <span data-ttu-id="5a111-121">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="5a111-121">All required components</span></span>
          * <span data-ttu-id="5a111-122">Ferramentas de desenvolvimento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="5a111-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="5a111-123">Desenvolvimento de plataforma cruzada do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a111-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="5a111-124">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="5a111-124">All required components</span></span>

3. <span data-ttu-id="5a111-125">Instale o [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="5a111-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="5a111-126">Selecione a versão apropriada para seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5a111-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="5a111-127">Por exemplo, selecione **JDK-8u201-Windows-x64. exe** para um computador x64 do Windows.</span><span class="sxs-lookup"><span data-stu-id="5a111-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="5a111-128">Use o comando `java -version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="5a111-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="5a111-129">Instale o [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).</span><span class="sxs-lookup"><span data-stu-id="5a111-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="5a111-130">Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="5a111-130">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
    * <span data-ttu-id="5a111-131">Extrair para um diretório local.</span><span class="sxs-lookup"><span data-stu-id="5a111-131">Extract to a local directory.</span></span> <span data-ttu-id="5a111-132">Por exemplo, `c:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="5a111-132">For example, `c:\bin\apache-maven-3.6.0\`.</span></span>
    * <span data-ttu-id="5a111-133">Adicione o Apache Maven à sua [variável de ambiente path](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="5a111-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="5a111-134">Se você tiver extraído para `c:\bin\apache-maven-3.6.0\`o, você adicionaria `c:\bin\apache-maven-3.6.0\bin` ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="5a111-134">If you extracted to `c:\bin\apache-maven-3.6.0\`, you would add `c:\bin\apache-maven-3.6.0\bin` to your PATH.</span></span>
    * <span data-ttu-id="5a111-135">Use o comando `mvn -version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="5a111-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="5a111-136">Instale o [Apache Spark 2.3 +](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="5a111-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="5a111-137">Não há suporte para o Apache Spark 2.4 +.</span><span class="sxs-lookup"><span data-stu-id="5a111-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="5a111-138">Baixe [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) e extraia-o em uma pasta local usando uma ferramenta como [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="5a111-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="5a111-139">Por exemplo, você pode extraí-lo `c:\bin\spark-2.3.2-bin-hadoop2.7\`para.</span><span class="sxs-lookup"><span data-stu-id="5a111-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="5a111-140">Adicione Apache Spark à [variável de ambiente path](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="5a111-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="5a111-141">Se você tiver extraído para `c:\bin\spark-2.3.2-bin-hadoop2.7\`o, você adicionaria `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="5a111-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="5a111-142">Adicione uma [nova variável](https://www.java.com/en/download/help/path.xml) de ambiente `SPARK_HOME`chamada.</span><span class="sxs-lookup"><span data-stu-id="5a111-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="5a111-143">Se você tiver extraído `C:\bin\spark-2.3.2-bin-hadoop2.7\`para `C:\bin\spark-2.3.2-bin-hadoop2.7\` , use para o **valor da variável**.</span><span class="sxs-lookup"><span data-stu-id="5a111-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="5a111-144">Verifique se você pode executar `spark-shell` a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5a111-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="5a111-145">Configurar o [WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="5a111-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="5a111-146">Baixe o binário **winutils. exe** do [repositório winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="5a111-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="5a111-147">Selecione a versão do Hadoop com a qual a distribuição do Spark foi compilada.</span><span class="sxs-lookup"><span data-stu-id="5a111-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="5a111-148">Por exemplo, você usa o **Hadoop-2.7.1** para o **Spark 2.3.2**.</span><span class="sxs-lookup"><span data-stu-id="5a111-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="5a111-149">A versão do Hadoop é anotada no final do nome da pasta de instalação do Spark.</span><span class="sxs-lookup"><span data-stu-id="5a111-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="5a111-150">Salve o binário **winutils. exe** em um diretório de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="5a111-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="5a111-151">Por exemplo, `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="5a111-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="5a111-152">Defina `HADOOP_HOME` para refletir o diretório com **winutils. exe** sem `bin`.</span><span class="sxs-lookup"><span data-stu-id="5a111-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="5a111-153">Por exemplo, `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="5a111-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="5a111-154">Defina a variável de ambiente PATH como `%HADOOP_HOME%\bin`include.</span><span class="sxs-lookup"><span data-stu-id="5a111-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="5a111-155">Verifique se você `dotnet`pode executar `mvn`, `java`,, `spark-shell` da linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="5a111-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="5a111-156">Baixe a versão Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="5a111-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="5a111-157">Baixe a versão [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) do .net para Apache Spark página de versões do GitHub para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="5a111-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="5a111-158">Por exemplo, você pode baixá-lo no caminho, `c:\bin\Microsoft.Spark.Worker\`.</span><span class="sxs-lookup"><span data-stu-id="5a111-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="5a111-159">Crie uma [nova variável](https://www.java.com/en/download/help/path.xml) de ambiente `DotnetWorkerPath` chamada e defina-a para o diretório em que você baixou e extraiu o **Microsoft. Spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="5a111-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DotnetWorkerPath` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="5a111-160">Por exemplo, `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="5a111-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="5a111-161">Clonar o .NET para Apache Spark repositório GitHub</span><span class="sxs-lookup"><span data-stu-id="5a111-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="5a111-162">Use o comando [GitBash](https://gitforwindows.org/) a seguir para clonar o .net para Apache Spark repositório em seu computador.</span><span class="sxs-lookup"><span data-stu-id="5a111-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="5a111-163">Gravar um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5a111-164">Abra o **Visual Studio** e navegue até **arquivo > criar novo projeto > aplicativo de console (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="5a111-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="5a111-165">Nomeie o aplicativo **HelloSpark**.</span><span class="sxs-lookup"><span data-stu-id="5a111-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="5a111-166">Instale o [pacote NuGet do Microsoft. Spark](https://www.nuget.org/profiles/spark).</span><span class="sxs-lookup"><span data-stu-id="5a111-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="5a111-167">Para obter mais informações sobre como instalar pacotes NuGet, consulte [diferentes maneiras de instalar um pacote NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="5a111-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="5a111-168">No **Gerenciador de soluções**, abra **Program.cs** e escreva o código C# a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a111-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="5a111-169">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="5a111-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="5a111-170">Execute seu .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="5a111-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5a111-171">Abra o **PowerShell** e altere o diretório para a pasta onde seu aplicativo está armazenado.</span><span class="sxs-lookup"><span data-stu-id="5a111-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="5a111-172">Crie um arquivo chamado **People. JSON** com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="5a111-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="5a111-173">Use o seguinte comando do PowerShell para executar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5a111-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="5a111-174">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="5a111-174">Congratulations!</span></span> <span data-ttu-id="5a111-175">Você criou e executou com êxito um .NET para Apache Spark aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a111-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5a111-176">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5a111-176">Next steps</span></span>

<span data-ttu-id="5a111-177">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="5a111-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5a111-178">Preparar seu ambiente do Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="5a111-179">Baixe o **Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="5a111-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="5a111-180">Compilar e executar um aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="5a111-181">Confira a página de recursos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="5a111-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5a111-182">.NET para recursos Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5a111-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
