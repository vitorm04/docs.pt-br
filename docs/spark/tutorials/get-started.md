---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1b736e078eea40e399882c0df020062b6aa758ad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740519"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="66905-103">Tutorial: introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="66905-104">Este tutorial ensina como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="66905-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="66905-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="66905-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="66905-106">Prepare seu ambiente Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="66905-107">Escreva seu primeiro .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="66905-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="66905-108">Crie e execute seu aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="66905-109">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="66905-109">Prepare your environment</span></span>

<span data-ttu-id="66905-110">Antes de começar a escrever seu aplicativo, você precisa configurar algumas dependências de pré-requisito.</span><span class="sxs-lookup"><span data-stu-id="66905-110">Before you begin writing your app, you need to setup some prerequisite dependencies.</span></span> <span data-ttu-id="66905-111">Se você puder executar `dotnet`, `java`, `mvn``spark-shell` de seu ambiente de linha de comando, seu ambiente já estará preparado e você poderá pular para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="66905-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="66905-112">Se você não puder executar um ou todos os comandos, execute as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="66905-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="66905-113">1. instalar o .NET</span><span class="sxs-lookup"><span data-stu-id="66905-113">1. Install .NET</span></span>

<span data-ttu-id="66905-114">Para começar a criar aplicativos .NET, você precisa baixar e instalar o SDK do .NET (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="66905-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="66905-115">faça download e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="66905-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="66905-116">A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho.</span><span class="sxs-lookup"><span data-stu-id="66905-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> 

<span data-ttu-id="66905-117">Depois de instalar o SDK do .NET Core, abra um novo prompt de comando e execute `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="66905-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="66905-118">Se o comando executar e imprimir as informações sobre como usar dotnet, o poderá passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="66905-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="66905-119">Se você receber um erro de `'dotnet' is not recognized as an internal or external command`, certifique-se de ter aberto um **novo** prompt de comando antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="66905-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span> 

### <a name="2-install-java"></a><span data-ttu-id="66905-120">2. instalar o Java</span><span class="sxs-lookup"><span data-stu-id="66905-120">2. Install Java</span></span>

<span data-ttu-id="66905-121">Instale o [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="66905-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="66905-122">Selecione a versão apropriada para seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="66905-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="66905-123">Por exemplo, selecione **jdk-8u201-windows-x64.exe** para um computador x64 do Windows.</span><span class="sxs-lookup"><span data-stu-id="66905-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="66905-124">Em seguida, use o comando `java` para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="66905-124">Then, use the command `java` to verify the installation.</span></span>
   
![Download do Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="66905-126">3. instalar o 7-zip</span><span class="sxs-lookup"><span data-stu-id="66905-126">3. Install 7-zip</span></span>

<span data-ttu-id="66905-127">Apache Spark é baixado como um arquivo. tgz compactado.</span><span class="sxs-lookup"><span data-stu-id="66905-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="66905-128">Use um programa de extração, como 7-zip, para extrair o arquivo.</span><span class="sxs-lookup"><span data-stu-id="66905-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="66905-129">Visite [7-Downloads de zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="66905-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="66905-130">Na primeira tabela da página, selecione o download do x86 de 32 bits ou de 64 bits x64, dependendo do seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="66905-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="66905-131">Quando o download for concluído, execute o instalador.</span><span class="sxs-lookup"><span data-stu-id="66905-131">When the download completes, run the installer.</span></span>
   
![Download do 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="66905-133">4. instalar o Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-133">4. Install Apache Spark</span></span>

<span data-ttu-id="66905-134">[Baixe e instale o Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="66905-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="66905-135">Você precisará selecionar a partir da versão 2,3. \* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET para Apache Spark não é compatível com outras versões do Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="66905-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>  

<span data-ttu-id="66905-136">Os comandos usados nas etapas a seguir pressupõem que você tenha [baixado e instalado Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="66905-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="66905-137">Se você quiser usar uma versão diferente, substitua **2.4.1** pelo número de versão apropriado.</span><span class="sxs-lookup"><span data-stu-id="66905-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="66905-138">Em seguida, extraia o arquivo **. tar** e os arquivos de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="66905-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="66905-139">Para extrair o arquivo **. tar** aninhado:</span><span class="sxs-lookup"><span data-stu-id="66905-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="66905-140">Localize o arquivo **Spark-2.4.1-bin-Hadoop 2.7. tgz** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="66905-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="66905-141">Clique com o botão direito do mouse no arquivo e selecione **7-zip-> extrair aqui**.</span><span class="sxs-lookup"><span data-stu-id="66905-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="66905-142">**Spark-2.4.1-bin-Hadoop 2.7. tar** é criado junto com o arquivo **. tgz** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="66905-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="66905-143">Para extrair os arquivos de Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="66905-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="66905-144">Clique com o botão direito do mouse em **Spark-2.4.1-bin-Hadoop 2.7. tar** e selecione **7-zip-> extrair arquivos...**</span><span class="sxs-lookup"><span data-stu-id="66905-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="66905-145">Insira **C:\bin** no campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="66905-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="66905-146">Desmarque a caixa de seleção abaixo do campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="66905-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="66905-147">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="66905-147">Select **OK**.</span></span>
* <span data-ttu-id="66905-148">Os arquivos de Apache Spark são extraídos para C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="66905-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\
      
![Instalar o Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)
    
<span data-ttu-id="66905-150">Execute os seguintes comandos para definir as variáveis de ambiente usadas para localizar Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="66905-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="66905-151">Depois de instalar tudo e definir suas variáveis de ambiente, abra um **novo** prompt de comando e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="66905-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="66905-152">Se o comando executar e imprimir as informações de versão, você poderá passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="66905-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="66905-153">Se você receber um erro de `'spark-submit' is not recognized as an internal or external command`, certifique-se de ter aberto um **novo** prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="66905-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="66905-154">5. instalar o .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="66905-155">Baixe a versão [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) do .net para Apache Spark github.</span><span class="sxs-lookup"><span data-stu-id="66905-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="66905-156">Por exemplo, se você estiver em um computador Windows e planeja usar o .NET Core, [Baixe a versão Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.5.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span><span class="sxs-lookup"><span data-stu-id="66905-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.5.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="66905-157">Para extrair o Microsoft. Spark. Worker:</span><span class="sxs-lookup"><span data-stu-id="66905-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="66905-158">Localize o arquivo **Microsoft. Spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="66905-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="66905-159">Clique com o botão direito do mouse e selecione **7-zip-> extrair arquivos...** .</span><span class="sxs-lookup"><span data-stu-id="66905-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="66905-160">Insira **C:\bin** no campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="66905-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="66905-161">Desmarque a caixa de seleção abaixo do campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="66905-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="66905-162">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="66905-162">Select **OK**.</span></span>
  
![Instalar o .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="66905-164">6. instalar o WinUtils</span><span class="sxs-lookup"><span data-stu-id="66905-164">6. Install WinUtils</span></span>

<span data-ttu-id="66905-165">O .NET para Apache Spark requer que o WinUtils seja instalado junto com Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="66905-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="66905-166">[Baixe o winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="66905-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="66905-167">Em seguida, copie WinUtils para **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="66905-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="66905-168">Se você estiver usando uma versão diferente do Hadoop, que é anotada no final do nome da pasta de instalação do Spark, [Selecione a versão do WinUtils](https://github.com/steveloughran/winutils) que é compatível com sua versão do Hadoop.</span><span class="sxs-lookup"><span data-stu-id="66905-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span> 

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="66905-169">7. definir DOTNET_WORKER_DIR e verificar dependências</span><span class="sxs-lookup"><span data-stu-id="66905-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="66905-170">Execute o comando a seguir para definir a variável de ambiente `DOTNET_WORKER_DIR`, que é usada pelos aplicativos .NET para localizar o .NET para Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="66905-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="66905-171">Por fim, verifique se você pode executar `dotnet`, `java`, `mvn``spark-shell` da linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="66905-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="66905-172">Escrever um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="66905-173">1. criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="66905-173">1. Create a console app</span></span>

<span data-ttu-id="66905-174">No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="66905-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="66905-175">O comando `dotnet` cria um aplicativo `new` do tipo `console` para você.</span><span class="sxs-lookup"><span data-stu-id="66905-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="66905-176">O parâmetro `-o` cria um diretório chamado *mySparkApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="66905-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="66905-177">O comando `cd mySparkApp` altera o diretório para o diretório de aplicativo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="66905-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="66905-178">2. instalar o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="66905-178">2. Install NuGet package</span></span>

<span data-ttu-id="66905-179">Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="66905-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="66905-180">No prompt de comando, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="66905-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="66905-181">3. Codifique seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="66905-181">3. Code your app</span></span>

<span data-ttu-id="66905-182">Abra *Program.cs* no Visual Studio Code, ou em qualquer editor de texto, e substitua todo o código pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="66905-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-add-data-file"></a><span data-ttu-id="66905-183">4. Adicionar arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="66905-183">4. Add data file</span></span>

<span data-ttu-id="66905-184">Seu aplicativo processa um arquivo que contém linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="66905-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="66905-185">Crie um arquivo *Input. txt* no diretório *mySparkApp* , contendo o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="66905-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="66905-186">Executar seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="66905-187">Execute o seguinte comando para compilar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="66905-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="66905-188">Execute o seguinte comando para enviar seu aplicativo para execução no Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="66905-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="66905-189">Quando seu aplicativo é executado, os dados de contagem de palavras do arquivo *Input. txt* são gravados no console do.</span><span class="sxs-lookup"><span data-stu-id="66905-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="66905-190">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="66905-190">Congratulations!</span></span> <span data-ttu-id="66905-191">Você criou e executou com êxito um aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="66905-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="66905-192">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="66905-192">Next steps</span></span>

<span data-ttu-id="66905-193">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="66905-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="66905-194">Prepare seu ambiente Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="66905-195">Escreva seu primeiro .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="66905-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="66905-196">Crie e execute seu aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="66905-197">Para ver um vídeo explicando as etapas acima, faça checkout da [série de vídeos .net para Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="66905-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="66905-198">Confira a página de recursos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="66905-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="66905-199">Recursos do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="66905-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
