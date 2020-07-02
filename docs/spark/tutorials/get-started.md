---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows, no MacOS e no Ubuntu.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617646"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="871e9-103">Tutorial: introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="871e9-104">Este tutorial ensina como executar um .NET para Apache Spark aplicativo usando o .NET Core no Windows, no MacOS e no Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="871e9-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="871e9-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="871e9-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="871e9-106">Prepare seu ambiente para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="871e9-107">Escreva seu primeiro .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="871e9-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="871e9-108">Crie e execute seu aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-108">Build and run your simple .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="871e9-109">Prepare o seu ambiente</span><span class="sxs-lookup"><span data-stu-id="871e9-109">Prepare your environment</span></span>

<span data-ttu-id="871e9-110">Antes de começar a escrever seu aplicativo, você precisa configurar algumas dependências de pré-requisito.</span><span class="sxs-lookup"><span data-stu-id="871e9-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="871e9-111">Se você puder executar `dotnet` `java` o,, `mvn` , `spark-shell` do ambiente de linha de comando, seu ambiente já estará preparado e você poderá pular para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="871e9-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="871e9-112">Se você não puder executar um ou todos os comandos, execute as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="871e9-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="871e9-113">1. instalar o .NET</span><span class="sxs-lookup"><span data-stu-id="871e9-113">1. Install .NET</span></span>

<span data-ttu-id="871e9-114">Para começar a criar aplicativos .NET, você precisa baixar e instalar o SDK do .NET (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="871e9-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="871e9-115">Baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="871e9-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="871e9-116">A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho.</span><span class="sxs-lookup"><span data-stu-id="871e9-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="871e9-117">Depois de instalar o SDK do .NET Core, abra um novo prompt de comando ou terminal e execute `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="871e9-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="871e9-118">Se o comando executar e imprimir as informações sobre como usar dotnet, o poderá passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="871e9-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="871e9-119">Se você receber um `'dotnet' is not recognized as an internal or external command` erro, verifique se você abriu um **novo** prompt de comando ou terminal antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="871e9-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="871e9-120">2. instalar o Java</span><span class="sxs-lookup"><span data-stu-id="871e9-120">2. Install Java</span></span>

<span data-ttu-id="871e9-121">Instale o [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) para Windows e MacOS, ou [OpenJDK 8](https://openjdk.java.net/install/) para Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="871e9-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="871e9-122">Selecione a versão apropriada para seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="871e9-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="871e9-123">Por exemplo, selecione **jdk-8u201-windows-x64.exe** para um computador x64 do Windows (como mostrado abaixo) ou **JDK-8u231-MacOSX-x64. dmg** para MacOS.</span><span class="sxs-lookup"><span data-stu-id="871e9-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="871e9-124">Em seguida, use o comando `java` para verificar a instalação.</span><span class="sxs-lookup"><span data-stu-id="871e9-124">Then, use the command `java` to verify the installation.</span></span>

![Download do Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="871e9-126">3. instalar o software de compactação</span><span class="sxs-lookup"><span data-stu-id="871e9-126">3. Install compression software</span></span>

<span data-ttu-id="871e9-127">Apache Spark é baixado como um arquivo. tgz compactado.</span><span class="sxs-lookup"><span data-stu-id="871e9-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="871e9-128">Use um programa de extração, como [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/), para extrair o arquivo.</span><span class="sxs-lookup"><span data-stu-id="871e9-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="871e9-129">4. instalar o Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-129">4. Install Apache Spark</span></span>

<span data-ttu-id="871e9-130">[Baixe e instale o Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="871e9-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="871e9-131">Você precisará selecionar a partir da versão 2,3. \* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET para Apache Spark não é compatível com outras versões do Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="871e9-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="871e9-132">Os comandos usados nas etapas a seguir pressupõem que você tenha [baixado e instalado Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="871e9-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="871e9-133">Se você quiser usar uma versão diferente, substitua **2.4.1** pelo número de versão apropriado.</span><span class="sxs-lookup"><span data-stu-id="871e9-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="871e9-134">Em seguida, extraia o arquivo **. tar** e os arquivos de Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="871e9-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="871e9-135">Para extrair o arquivo **. tar** aninhado:</span><span class="sxs-lookup"><span data-stu-id="871e9-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="871e9-136">Localize o arquivo **Spark-2.4.1-bin-Hadoop 2.7. tgz** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="871e9-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="871e9-137">Clique com o botão direito do mouse no arquivo e selecione **7-zip-> extrair aqui**.</span><span class="sxs-lookup"><span data-stu-id="871e9-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="871e9-138">**Spark-2.4.1-bin-Hadoop 2.7. tar** é criado junto com o arquivo **. tgz** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="871e9-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="871e9-139">Para extrair os arquivos de Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="871e9-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="871e9-140">Clique com o botão direito do mouse em **Spark-2.4.1-bin-Hadoop 2.7. tar** e selecione **7-zip-> extrair arquivos...**</span><span class="sxs-lookup"><span data-stu-id="871e9-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="871e9-141">Insira **C:\bin** no campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="871e9-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="871e9-142">Desmarque a caixa de seleção abaixo do campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="871e9-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="871e9-143">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="871e9-143">Select **OK**.</span></span>
* <span data-ttu-id="871e9-144">Os arquivos de Apache Spark são extraídos para C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="871e9-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Instalar Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="871e9-146">Execute os comandos a seguir para definir as variáveis de ambiente usadas para localizar Apache Spark no **Windows**:</span><span class="sxs-lookup"><span data-stu-id="871e9-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="871e9-147">Execute os comandos a seguir para definir as variáveis de ambiente usadas para localizar Apache Spark no **MacOS** e no **Ubuntu**:</span><span class="sxs-lookup"><span data-stu-id="871e9-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="871e9-148">Depois de instalar tudo e definir suas variáveis de ambiente, abra um **novo** prompt de comando ou terminal e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="871e9-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="871e9-149">Se o comando executar e imprimir as informações de versão, você poderá passar para a próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="871e9-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="871e9-150">Se você receber um `'spark-submit' is not recognized as an internal or external command` erro, certifique-se de ter aberto um **novo** prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="871e9-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="871e9-151">5. instalar o .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="871e9-152">Baixe a versão [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) do .net para Apache Spark github.</span><span class="sxs-lookup"><span data-stu-id="871e9-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="871e9-153">Por exemplo, se você estiver em um computador Windows e planeja usar o .NET Core, [Baixe a versão Windows x64 netcoreapp 3.1](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="871e9-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="871e9-154">Para extrair o Microsoft. Spark. Worker:</span><span class="sxs-lookup"><span data-stu-id="871e9-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="871e9-155">Localize o arquivo de **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que você baixou.</span><span class="sxs-lookup"><span data-stu-id="871e9-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="871e9-156">Clique com o botão direito do mouse e selecione **7-zip-> extrair arquivos...**.</span><span class="sxs-lookup"><span data-stu-id="871e9-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="871e9-157">Insira **C:\bin** no campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="871e9-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="871e9-158">Desmarque a caixa de seleção abaixo do campo **extrair para** .</span><span class="sxs-lookup"><span data-stu-id="871e9-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="871e9-159">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="871e9-159">Select **OK**.</span></span>

![Instalar o .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="871e9-161">6. instalar o WinUtils (somente Windows)</span><span class="sxs-lookup"><span data-stu-id="871e9-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="871e9-162">O .NET para Apache Spark requer que o WinUtils seja instalado junto com Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="871e9-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="871e9-163">[Baixar winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="871e9-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="871e9-164">Em seguida, copie WinUtils para **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="871e9-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="871e9-165">Se você estiver usando uma versão diferente do Hadoop, que é anotada no final do nome da pasta de instalação do Spark, [Selecione a versão do WinUtils](https://github.com/steveloughran/winutils) que é compatível com sua versão do Hadoop.</span><span class="sxs-lookup"><span data-stu-id="871e9-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="871e9-166">7. definir DOTNET_WORKER_DIR e verificar dependências</span><span class="sxs-lookup"><span data-stu-id="871e9-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="871e9-167">Execute um dos comandos a seguir para definir a `DOTNET_WORKER_DIR` variável de ambiente, que é usada pelos aplicativos .net para localizar o .net para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="871e9-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="871e9-168">No **Windows**, crie uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` e defina-a para o diretório em que você baixou e extraiu o Microsoft. Spark. Worker (por exemplo, `C:\bin\Microsoft.Spark.Worker\` ).</span><span class="sxs-lookup"><span data-stu-id="871e9-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="871e9-169">No **MacOS**, crie uma nova variável de ambiente usando `export DOTNET_WORKER_DIR <your_path>` e defina-a no diretório em que você baixou e extraiu o Microsoft. Spark. Worker (por exemplo, *~/bin/Microsoft.Spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="871e9-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="871e9-170">No **Ubuntu**, crie uma [nova variável de ambiente](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` e defina-a para o diretório em que você baixou e extraiu o Microsoft. Spark. Worker (por exemplo, *~/bin/Microsoft.Spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="871e9-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="871e9-171">Por fim, verifique se você pode executar `dotnet` ,, `java` `mvn` , `spark-shell` a partir de sua linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="871e9-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="871e9-172">Escrever um aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="871e9-173">1. criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="871e9-173">1. Create a console app</span></span>

<span data-ttu-id="871e9-174">No prompt de comando ou terminal, execute os seguintes comandos para criar um novo aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="871e9-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="871e9-175">O `dotnet` comando cria um `new` aplicativo do tipo `console` para você.</span><span class="sxs-lookup"><span data-stu-id="871e9-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="871e9-176">O `-o` parâmetro cria um diretório chamado *mySparkApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="871e9-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="871e9-177">O `cd mySparkApp` comando altera o diretório para o diretório de aplicativo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="871e9-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="871e9-178">2. instalar o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="871e9-178">2. Install NuGet package</span></span>

<span data-ttu-id="871e9-179">Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="871e9-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="871e9-180">No prompt de comando ou terminal, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="871e9-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="871e9-181">3. Codifique seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="871e9-181">3. Code your app</span></span>

<span data-ttu-id="871e9-182">Abra *Program.cs* no Visual Studio Code, ou em qualquer editor de texto, e substitua todo o código pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="871e9-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
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

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="871e9-183">4. criar e adicionar um arquivo de dados</span><span class="sxs-lookup"><span data-stu-id="871e9-183">4. Create and add a data file</span></span>

<span data-ttu-id="871e9-184">Abra o prompt de comando ou o terminal e navegue até a pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="871e9-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="871e9-185">Seu aplicativo processa um arquivo que contém linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="871e9-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="871e9-186">Crie um arquivo de *input.txt* no diretório *mySparkApp* , contendo o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="871e9-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="871e9-187">Executar seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="871e9-188">Execute o seguinte comando para compilar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="871e9-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="871e9-189">Execute o seguinte comando para enviar seu aplicativo para execução no Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="871e9-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="871e9-190">Esse comando pressupõe que você tenha baixado Apache Spark e adicionado-o à variável de ambiente PATH para poder usar `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="871e9-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="871e9-191">Caso contrário, você precisaria usar o caminho completo (por exemplo, *C:\bin\apache-spark\bin\spark-Submit* ou *~/Spark/bin/Spark-Submit*).</span><span class="sxs-lookup"><span data-stu-id="871e9-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="871e9-192">Quando seu aplicativo é executado, os dados de contagem de palavras do arquivo de *input.txt* são gravados no console do.</span><span class="sxs-lookup"><span data-stu-id="871e9-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="871e9-193">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="871e9-193">Congratulations!</span></span> <span data-ttu-id="871e9-194">Você criou e executou com êxito um aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="871e9-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="871e9-195">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="871e9-195">Next steps</span></span>

<span data-ttu-id="871e9-196">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="871e9-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="871e9-197">Prepare seu ambiente Windows para .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="871e9-198">Escreva seu primeiro .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="871e9-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="871e9-199">Crie e execute seu aplicativo .NET simples para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="871e9-200">Para ver um vídeo explicando as etapas acima, faça checkout da [série de vídeos .net para Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="871e9-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="871e9-201">Confira a página de recursos para saber mais.</span><span class="sxs-lookup"><span data-stu-id="871e9-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="871e9-202">Recursos do .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="871e9-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
