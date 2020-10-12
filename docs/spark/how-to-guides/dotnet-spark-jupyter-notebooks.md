---
title: Usar notebooks Jupyter
titleSuffix: .NET for Apache Spark
description: Use o .NET para Apache Spark em ambientes interativos como Jupyter Notebook, Jupyter Lab ou Visual Studio Code (VS Code)
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: 38263c5ce4d1686777f33f5a9742d530eafa9d89
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955706"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="d8413-103">Usar o .NET para Apache Spark em notebooks Jupyter</span><span class="sxs-lookup"><span data-stu-id="d8413-103">Use .NET for Apache Spark in Jupyter notebooks</span></span>

<span data-ttu-id="d8413-104">Neste artigo, você aprenderá a executar o .NET para trabalhos de Apache Spark interativamente no Jupyter Notebook e no Visual Studio Code (VS Code) com o .NET Interactive.</span><span class="sxs-lookup"><span data-stu-id="d8413-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="d8413-105">Sobre o Jupyter</span><span class="sxs-lookup"><span data-stu-id="d8413-105">About Jupyter</span></span>

<span data-ttu-id="d8413-106">O [Jupyter](https://jupyter.org/) é um ambiente de computação de plataforma cruzada de software livre que fornece uma maneira para os usuários criarem protótipos e desenvolverem aplicativos interativamente.</span><span class="sxs-lookup"><span data-stu-id="d8413-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="d8413-107">Você pode interagir com o Jupyter por meio de uma ampla variedade de interfaces, como Jupyter Notebook, Jupyter Lab e VS Code.</span><span class="sxs-lookup"><span data-stu-id="d8413-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="d8413-108">No contexto do .NET, o [.net Interactive](https://github.com/dotnet/interactive), uma ferramenta global do .NET Core, fornece um kernel para escrever código .net (C#/f #) em ambientes de computação interativa, como Jupyter notebook.</span><span class="sxs-lookup"><span data-stu-id="d8413-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8413-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d8413-109">Prerequisites</span></span>

- [<span data-ttu-id="d8413-110">SDK do .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d8413-110">.NET Core 3.1 SDK</span></span>](https://docs.microsoft.com/dotnet/core/install/)
- [<span data-ttu-id="d8413-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d8413-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="d8413-112">Apache Spark o trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="d8413-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="d8413-113">Consulte o [tutorial de introdução](../tutorials/get-started.md) para obter mais informações sobre como configurar seu .net para Apache Spark ambiente.</span><span class="sxs-lookup"><span data-stu-id="d8413-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="d8413-114">Preparar o ambiente</span><span class="sxs-lookup"><span data-stu-id="d8413-114">Prepare environment</span></span>

<span data-ttu-id="d8413-115">Para trabalhar com notebooks Jupyter, você precisará de duas coisas.</span><span class="sxs-lookup"><span data-stu-id="d8413-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="d8413-116">Instalar a [ferramenta global .net interativa do .net](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span><span class="sxs-lookup"><span data-stu-id="d8413-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="d8413-117">Baixe o `Microsoft.Spark` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d8413-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="d8413-118">Navegue até a página do pacote NuGet do [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) .</span><span class="sxs-lookup"><span data-stu-id="d8413-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="d8413-119">Por padrão, a versão mais recente do pacote é baixada.</span><span class="sxs-lookup"><span data-stu-id="d8413-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="d8413-120">**Certifique-se de que a versão baixada seja a mesma do seu Apache Spark .NET Worker.**</span><span class="sxs-lookup"><span data-stu-id="d8413-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="d8413-121">No painel **informações** , selecione **baixar pacote** para baixar a versão mais recente do pacote.</span><span class="sxs-lookup"><span data-stu-id="d8413-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="d8413-122">O nome do pacote é semelhante a  *Microsoft. Spark. [ PACOTE-versão]. nupkg*.</span><span class="sxs-lookup"><span data-stu-id="d8413-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="d8413-123">Descompacte o pacote baixado.</span><span class="sxs-lookup"><span data-stu-id="d8413-123">Unzip the downloaded package.</span></span> <span data-ttu-id="d8413-124">O diretório descompactado deve conter um subdiretório chamado *jars*.</span><span class="sxs-lookup"><span data-stu-id="d8413-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="d8413-125">Anote o caminho, uma vez que ele é usado mais tarde.</span><span class="sxs-lookup"><span data-stu-id="d8413-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="d8413-126">Iniciar o .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d8413-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="d8413-127">Execute o comando a seguir para iniciar o .NET para Apache Spark no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="d8413-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="d8413-128">Esse `spark-submit` comando inicia um processo e aguarda conexões de um [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="d8413-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="d8413-129">Certifique-se de fornecer o caminho para o `microsoft-spark-<version>.jar` para a respectiva versão do .net para Apache Spark que você está usando.</span><span class="sxs-lookup"><span data-stu-id="d8413-129">Make sure to provide the path to the `microsoft-spark-<version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="d8413-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="d8413-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="d8413-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="d8413-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="d8413-132">Criar um notebook</span><span class="sxs-lookup"><span data-stu-id="d8413-132">Create a notebook</span></span>

<span data-ttu-id="d8413-133">Você pode usar interfaces diferentes para interagir com o Jupyter.</span><span class="sxs-lookup"><span data-stu-id="d8413-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="d8413-134">Para uma interface baseada em navegador, use Jupyter notebooks ou Jupyter Lab.</span><span class="sxs-lookup"><span data-stu-id="d8413-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="d8413-135">Para obter uma experiência de editor local, use VS Code.</span><span class="sxs-lookup"><span data-stu-id="d8413-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="d8413-136">Jupyter notebooks & Jupyter Lab</span><span class="sxs-lookup"><span data-stu-id="d8413-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="d8413-137">Em outro prompt de comando, inicie o Jupyter Notebook ou o Jupyter Lab usando um dos comandos abaixo:</span><span class="sxs-lookup"><span data-stu-id="d8413-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="d8413-138">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="d8413-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="d8413-139">**Laboratório de Jupyter**</span><span class="sxs-lookup"><span data-stu-id="d8413-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="d8413-140">Esses comandos iniciam uma janela do navegador com a interface de laboratório Jupyter Notebook ou Jupyter.</span><span class="sxs-lookup"><span data-stu-id="d8413-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="d8413-141">No navegador, crie um novo bloco de anotações.</span><span class="sxs-lookup"><span data-stu-id="d8413-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="d8413-142">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="d8413-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="d8413-143">Selecione **novo > .net (C#)** ou **novo > .net (F #)**</span><span class="sxs-lookup"><span data-stu-id="d8413-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="d8413-144">**Laboratório de Jupyter**</span><span class="sxs-lookup"><span data-stu-id="d8413-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="d8413-145">Na janela do iniciador, selecione **.net (C#)** ou **.net (F #)**</span><span class="sxs-lookup"><span data-stu-id="d8413-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="d8413-146">Visual Studio Code (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="d8413-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8413-147">Para usar os blocos de anotações do Jupyter no VS Code, você precisa instalar:</span><span class="sxs-lookup"><span data-stu-id="d8413-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="d8413-148">Pessoas VS Codes</span><span class="sxs-lookup"><span data-stu-id="d8413-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="d8413-149">Extensão de blocos de anotações interativos do .NET</span><span class="sxs-lookup"><span data-stu-id="d8413-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="d8413-150">Abra o VS Code.</span><span class="sxs-lookup"><span data-stu-id="d8413-150">Open VS Code.</span></span>
1. <span data-ttu-id="d8413-151">Abra a exibição paleta de comandos **> paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="d8413-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="d8413-152">Quando a paleta de comandos for exibida, digite o seguinte comando para criar um novo notebook interativo .NET:</span><span class="sxs-lookup"><span data-stu-id="d8413-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="d8413-153">Como alternativa, se você quiser abrir um notebook interativo .NET existente com a extensão *. ipynb* , use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d8413-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="d8413-154">Inicializar uma sessão do Spark</span><span class="sxs-lookup"><span data-stu-id="d8413-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="d8413-155">Quando o notebook for aberto, instale o `Microsoft.Spark` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d8413-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="d8413-156">Verifique se a versão instalada é a mesma do trabalho do .NET.</span><span class="sxs-lookup"><span data-stu-id="d8413-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. <span data-ttu-id="d8413-157">Adicione a seguinte instrução using ao bloco de anotações.</span><span class="sxs-lookup"><span data-stu-id="d8413-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="d8413-158">Inicialize seu [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span><span class="sxs-lookup"><span data-stu-id="d8413-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="d8413-159">O notebook deve ser semelhante ao mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8413-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="d8413-160">Este exemplo usa VS Code, mas Jupyter Notebook e Jupyter Lab devem ter a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="d8413-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="d8413-161">![.NET para Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="d8413-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="d8413-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d8413-162">Next Steps</span></span>

- [<span data-ttu-id="d8413-163">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d8413-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="d8413-164">Prever sentimentos usando .NET para Apache Spark e ML.NET</span><span class="sxs-lookup"><span data-stu-id="d8413-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="d8413-165">Para obter mais informações sobre o .NET Interactive, consulte a [documentação interativa do .net](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span><span class="sxs-lookup"><span data-stu-id="d8413-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
