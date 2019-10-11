---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c4dbce74d0d8c0a682250a8021d983ef2990971f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250319"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="7b74b-103">Tutorial: Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="7b74b-104">Este tutorial ensina como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="7b74b-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="7b74b-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="7b74b-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7b74b-106">Prepare seu ambiente Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="7b74b-107">Baixe o **Microsoft.Spark.Worker**</span><span class="sxs-lookup"><span data-stu-id="7b74b-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="7b74b-108">Compilar e executar um aplicativo .NET para Apache Spark simples</span><span class="sxs-lookup"><span data-stu-id="7b74b-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="7b74b-109">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="7b74b-109">Prepare your environment</span></span>

<span data-ttu-id="7b74b-110">Antes de começar, verifique se você pode executar `dotnet`, `java`, `mvn`, `spark-shell` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7b74b-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="7b74b-111">Se seu ambiente já estiver preparado, você poderá pular para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="7b74b-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="7b74b-112">Se você não puder executar um ou todos os comandos, siga as etapas abaixo.</span><span class="sxs-lookup"><span data-stu-id="7b74b-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="7b74b-113">Baixe e instale o [SDK do .NET Core 2.1x](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="7b74b-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="7b74b-114">A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho.</span><span class="sxs-lookup"><span data-stu-id="7b74b-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="7b74b-115">Use o comando `dotnet --version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="7b74b-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="7b74b-116">Instale o [Visual Studio 2017](https://www.visualstudio.com/downloads/) ou o [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) com as atualizações mais recentes.</span><span class="sxs-lookup"><span data-stu-id="7b74b-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="7b74b-117">Você pode usar Community, Professional ou Enterprise.</span><span class="sxs-lookup"><span data-stu-id="7b74b-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="7b74b-118">A versão Community é gratuita.</span><span class="sxs-lookup"><span data-stu-id="7b74b-118">The Community version is free.</span></span>

   <span data-ttu-id="7b74b-119">Escolha as seguintes cargas de trabalho durante a instalação:</span><span class="sxs-lookup"><span data-stu-id="7b74b-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="7b74b-120">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="7b74b-120">.NET desktop development</span></span>
          * <span data-ttu-id="7b74b-121">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="7b74b-121">All required components</span></span>
          * <span data-ttu-id="7b74b-122">Ferramentas de desenvolvimento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7b74b-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="7b74b-123">Desenvolvimento de plataforma cruzada do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b74b-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="7b74b-124">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="7b74b-124">All required components</span></span>

3. <span data-ttu-id="7b74b-125">Instale o [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="7b74b-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="7b74b-126">Selecione a versão apropriada para seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7b74b-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="7b74b-127">Por exemplo, selecione **jdk-8u201-windows-x64.exe** para um computador x64 do Windows.</span><span class="sxs-lookup"><span data-stu-id="7b74b-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="7b74b-128">Use o comando `java -version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="7b74b-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="7b74b-129">Instale o [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span><span class="sxs-lookup"><span data-stu-id="7b74b-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="7b74b-130">Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="7b74b-130">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
    * <span data-ttu-id="7b74b-131">Extraia para um diretório local.</span><span class="sxs-lookup"><span data-stu-id="7b74b-131">Extract to a local directory.</span></span> <span data-ttu-id="7b74b-132">Por exemplo: `c:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-132">For example, `c:\bin\apache-maven-3.6.0\`.</span></span>
    * <span data-ttu-id="7b74b-133">Adicione o Apache Maven à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="7b74b-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="7b74b-134">Se você tiver extraído para o `c:\bin\apache-maven-3.6.0\`, adicionará `c:\bin\apache-maven-3.6.0\bin` a seu PATH.</span><span class="sxs-lookup"><span data-stu-id="7b74b-134">If you extracted to `c:\bin\apache-maven-3.6.0\`, you would add `c:\bin\apache-maven-3.6.0\bin` to your PATH.</span></span>
    * <span data-ttu-id="7b74b-135">Use o comando `mvn -version` do PowerShell para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="7b74b-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="7b74b-136">Instale o [Apache Spark 2.3 ou superior](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="7b74b-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="7b74b-137">Não há suporte para o Apache Spark 2.4 ou superior.</span><span class="sxs-lookup"><span data-stu-id="7b74b-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="7b74b-138">Baixe o [Apache Spark 2.3+](https://spark.apache.org/downloads.html) e extraia-o para uma pasta local usando uma ferramenta como [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="7b74b-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="7b74b-139">Por exemplo, você pode extraí-lo para `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="7b74b-140">Adicione o Apache Spark à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="7b74b-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="7b74b-141">Se você tiver extraído para o `c:\bin\spark-2.3.2-bin-hadoop2.7\`, adicionará `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` a seu PATH.</span><span class="sxs-lookup"><span data-stu-id="7b74b-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="7b74b-142">Adicione uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) chamada `SPARK_HOME`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="7b74b-143">Se você tiver extraído para `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use `C:\bin\spark-2.3.2-bin-hadoop2.7\` para o **Valor da variável**.</span><span class="sxs-lookup"><span data-stu-id="7b74b-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="7b74b-144">Verifique se você pode executar `spark-shell` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7b74b-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="7b74b-145">Configure o [WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="7b74b-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="7b74b-146">Baixe o binário **winutils.exe** do [repositório WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="7b74b-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="7b74b-147">Selecione a versão do Hadoop com a qual a distribuição do Spark foi compilada.</span><span class="sxs-lookup"><span data-stu-id="7b74b-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="7b74b-148">Por exemplo, você usa **hadoop-2.7.1** para **Spark 2.3.2**.</span><span class="sxs-lookup"><span data-stu-id="7b74b-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="7b74b-149">A versão do Hadoop é anotada no final do nome da pasta de instalação do Spark.</span><span class="sxs-lookup"><span data-stu-id="7b74b-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="7b74b-150">Salve o binário **winutils.exe** em um diretório de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="7b74b-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="7b74b-151">Por exemplo: `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="7b74b-152">Defina `HADOOP_HOME` para refletir o diretório com **winutils.exe** sem `bin`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="7b74b-153">Por exemplo: `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="7b74b-154">Defina a variável de ambiente PATH para incluir `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="7b74b-155">Verifique se você pode executar `dotnet`, `java`, `mvn`, `spark-shell` da linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="7b74b-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="7b74b-156">Baixe a versão Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="7b74b-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="7b74b-157">Baixe a versão [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) da página Versões do GitHub do .NET para Apache Spark para seu computador local.</span><span class="sxs-lookup"><span data-stu-id="7b74b-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="7b74b-158">Por exemplo, você pode baixá-lo para o caminho, `c:\bin\Microsoft.Spark.Worker\`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="7b74b-159">Crie uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) chamada `DOTNET_WORKER_DIR` e defina-a para o diretório em que você baixou e extraiu **Microsoft.Spark.Worker**.</span><span class="sxs-lookup"><span data-stu-id="7b74b-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="7b74b-160">Por exemplo: `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="7b74b-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="7b74b-161">Clonar o repositório do GitHub do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="7b74b-162">Use o comando [GitBash](https://gitforwindows.org/) a seguir para clonar o repositório do .NET para Apache Spark para seu computador.</span><span class="sxs-lookup"><span data-stu-id="7b74b-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="7b74b-163">Escrever um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="7b74b-164">Abra o **Visual Studio** e navegue até **Arquivo > Criar Projeto > Aplicativo de Console (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="7b74b-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="7b74b-165">Dê ao aplicativo o nome de **HelloSpark**.</span><span class="sxs-lookup"><span data-stu-id="7b74b-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="7b74b-166">Instale o [pacote NuGet do Microsoft.Spark](https://www.nuget.org/profiles/spark).</span><span class="sxs-lookup"><span data-stu-id="7b74b-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="7b74b-167">Para obter mais informações sobre como instalar pacotes do NuGet, confira [Diferentes maneiras de instalar um pacote do NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="7b74b-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="7b74b-168">No **Gerenciador de Soluções**, abra **Program.cse** e escreva o código C# a seguir:</span><span class="sxs-lookup"><span data-stu-id="7b74b-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="7b74b-169">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="7b74b-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="7b74b-170">Executar seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="7b74b-171">Abra o **PowerShell** e altere o diretório para a pasta em que seu aplicativo está armazenado.</span><span class="sxs-lookup"><span data-stu-id="7b74b-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="7b74b-172">Crie um arquivo chamado **people.json** com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="7b74b-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="7b74b-173">Use o seguinte comando do PowerShell para executar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7b74b-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="7b74b-174">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="7b74b-174">Congratulations!</span></span> <span data-ttu-id="7b74b-175">Você criou e executou com êxito um aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="7b74b-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b74b-176">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7b74b-176">Next steps</span></span>

<span data-ttu-id="7b74b-177">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="7b74b-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7b74b-178">Prepare seu ambiente Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="7b74b-179">Baixe o **Microsoft.Spark.Worker**</span><span class="sxs-lookup"><span data-stu-id="7b74b-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="7b74b-180">Compilar e executar um aplicativo .NET para Apache Spark simples</span><span class="sxs-lookup"><span data-stu-id="7b74b-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="7b74b-181">Confira a página de recursos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="7b74b-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7b74b-182">Recursos do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b74b-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
