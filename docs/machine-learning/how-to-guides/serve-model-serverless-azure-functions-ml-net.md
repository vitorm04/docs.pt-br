---
title: Implantar um modelo no Azure Functions
description: Usar um modelo de machine learning para Análise de Sentimento com o ML.NET para previsão pela internet usando o Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 74a7a5b941596ba9fffc62ef87a01763937d88c0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608771"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="ad224-103">Implantar um modelo no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ad224-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="ad224-104">Saiba como implantar um modelo de machine learning do ML.NET pré-treinado para previsões por HTTP por meio de um ambiente sem servidor do Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="ad224-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="ad224-105">Este exemplo executa uma versão de visualização do `PredictionEnginePool` serviço.</span><span class="sxs-lookup"><span data-stu-id="ad224-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad224-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ad224-106">Prerequisites</span></span>

- <span data-ttu-id="ad224-107">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou posterior ou visual Studio 2017 versão 15,6 ou posterior com as cargas de trabalho "desenvolvimento de plataforma cruzada do .NET Core" e "desenvolvimento do Azure" instalados.</span><span class="sxs-lookup"><span data-stu-id="ad224-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- [<span data-ttu-id="ad224-108">Ferramentas de Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ad224-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="ad224-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad224-109">PowerShell</span></span>
- <span data-ttu-id="ad224-110">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="ad224-110">Pre-trained model.</span></span> <span data-ttu-id="ad224-111">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="ad224-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="ad224-112">Visão geral de Azure Functions de exemplo</span><span class="sxs-lookup"><span data-stu-id="ad224-112">Azure Functions sample overview</span></span>

<span data-ttu-id="ad224-113">Este exemplo é um **gatilho http C# Azure Functions aplicativo** que usa um modelo de classificação binária pretreinado para categorizar a notação de texto como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="ad224-114">Azure Functions fornece uma maneira fácil de executar pequenas partes de código em escala em um ambiente gerenciado sem servidor na nuvem.</span><span class="sxs-lookup"><span data-stu-id="ad224-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="ad224-115">O código para este exemplo pode ser encontrado no repositório [dotnet/MachineLearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) no github.</span><span class="sxs-lookup"><span data-stu-id="ad224-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="ad224-116">Criar um projeto do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ad224-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="ad224-117">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ad224-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="ad224-118">Selecione **arquivo**  >  **novo**  >  **projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="ad224-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ad224-119">Na caixa de diálogo **Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="ad224-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="ad224-120">Em seguida, selecione o modelo de projeto do **Azure Functions**.</span><span class="sxs-lookup"><span data-stu-id="ad224-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="ad224-121">Na caixa de texto **Nome**, digite "SentimentAnalysisFunctionsApp" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ad224-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="ad224-122">Na caixa de diálogo **Novo Projeto**, abra a lista suspensa acima das opções de projeto e selecione **Azure Functions v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="ad224-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="ad224-123">Depois, selecione o projeto de **Gatilho de HTTP** e, em seguida, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ad224-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="ad224-124">Crie um diretório chamado *MLModels* em seu projeto para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="ad224-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="ad224-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="ad224-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ad224-126">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ad224-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="ad224-127">Instale o **pacote Microsoft.ml NuGet** versão **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="ad224-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="ad224-128">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ad224-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad224-129">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad224-130">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ad224-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad224-131">Instale o **Pacote NuGet Microsoft.Azure.Functions.Extensions**:</span><span class="sxs-lookup"><span data-stu-id="ad224-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="ad224-132">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ad224-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad224-133">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, procure por **Microsoft.Azure.Functions.Extensions**, selecione o pacote na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad224-134">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ad224-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad224-135">Instale o **pacote Microsoft.Extensions.ml NuGet** versão **0.15.1**:</span><span class="sxs-lookup"><span data-stu-id="ad224-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="ad224-136">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ad224-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad224-137">Escolha "nuget.org" como a origem do pacote, selecione a guia procurar, procure **Microsoft.Extensions.ml**, selecione o pacote na lista e selecione o botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="ad224-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ad224-138">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ad224-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ad224-139">Instale a versão **1.0.31**do **pacote NUGET Microsoft. net. Sdk. Functions** :</span><span class="sxs-lookup"><span data-stu-id="ad224-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="ad224-140">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ad224-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ad224-141">Escolha "nuget.org" como a origem do pacote, selecione a guia instalado, pesquise por **Microsoft. net. Sdk. Functions**, selecione esse pacote na lista, selecione **1.0.31** no menu suspenso versão e selecione o botão **Atualizar** .</span><span class="sxs-lookup"><span data-stu-id="ad224-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="ad224-142">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ad224-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="ad224-143">Adicionar modelo pré-treinado ao projeto</span><span class="sxs-lookup"><span data-stu-id="ad224-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="ad224-144">Copie o modelo previamente criado para o diretório *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="ad224-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="ad224-145">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo do modelo criado previamente e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ad224-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="ad224-146">Em **avançado**, altere o valor de **copiar para diretório de saída** para **copiar se mais recente**.</span><span class="sxs-lookup"><span data-stu-id="ad224-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="ad224-147">Criar Função do Azure para analisar o sentimento</span><span class="sxs-lookup"><span data-stu-id="ad224-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="ad224-148">Crie uma classe para prever o sentimento.</span><span class="sxs-lookup"><span data-stu-id="ad224-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="ad224-149">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="ad224-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="ad224-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ad224-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ad224-151">Na caixa de diálogo **Adicionar novo item**, selecione **Função do Azure** e altere o campo **Nome** para *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="ad224-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="ad224-152">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="ad224-153">Na caixa de diálogo **Nova Função do Azure**, selecione **Gatilho de HTTP**.</span><span class="sxs-lookup"><span data-stu-id="ad224-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="ad224-154">Depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ad224-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="ad224-155">O arquivo *AnalyzeSentiment.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ad224-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad224-156">Adicione a seguinte instrução `using` acima de *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="ad224-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="ad224-157">Por padrão, a classe `AnalyzeSentiment` é `static`.</span><span class="sxs-lookup"><span data-stu-id="ad224-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="ad224-158">Remova a palavra-chave `static` da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="ad224-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="ad224-159">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="ad224-159">Create data models</span></span>

<span data-ttu-id="ad224-160">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="ad224-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ad224-161">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="ad224-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="ad224-162">Crie um diretório chamado *Datamodels* em seu projeto para salvar seus modelos de dados: no Gerenciador de soluções, clique com o botão direito do mouse no seu projeto e selecione **Adicionar > nova pasta**.</span><span class="sxs-lookup"><span data-stu-id="ad224-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="ad224-163">Digite "DataModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ad224-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="ad224-164">Em Gerenciador de Soluções, clique com o botão direito do mouse no diretório *datamodelos* e selecione **Adicionar > novo item**.</span><span class="sxs-lookup"><span data-stu-id="ad224-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="ad224-165">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ad224-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ad224-166">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="ad224-167">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ad224-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad224-168">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ad224-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="ad224-169">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="ad224-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="ad224-170">Em Gerenciador de Soluções, clique com o botão direito do mouse no diretório *datamodelos* e selecione **Adicionar > novo item**.</span><span class="sxs-lookup"><span data-stu-id="ad224-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="ad224-171">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="ad224-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="ad224-172">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-172">Then, select the **Add** button.</span></span> <span data-ttu-id="ad224-173">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ad224-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ad224-174">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ad224-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="ad224-175">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ad224-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="ad224-176">`SentimentPrediction` herda de `SentimentData`, que dá acesso aos dados originais na propriedade `SentimentText`, bem como a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="ad224-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="ad224-177">Registrar serviço PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="ad224-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="ad224-178">Para fazer uma única previsão, você precisa criar um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) .</span><span class="sxs-lookup"><span data-stu-id="ad224-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ad224-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) Não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="ad224-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ad224-180">Além disso, você precisa criar uma instância dela em qualquer lugar em que seja necessário dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="ad224-181">À medida que seu aplicativo cresce, esse processo pode se tornar não gerenciável.</span><span class="sxs-lookup"><span data-stu-id="ad224-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="ad224-182">Para melhorar o desempenho e a segurança do thread, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) dos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="ad224-183">O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="ad224-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="ad224-184">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ad224-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ad224-185">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="ad224-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="ad224-186">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ad224-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="ad224-187">Adicione as seguintes instruções using à parte superior de *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="ad224-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="ad224-188">Remova o código existente abaixo das instruções using e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ad224-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="ad224-189">Defina variáveis para armazenar o ambiente no qual o aplicativo está sendo executado e o caminho do arquivo em que o modelo está localizado dentro da `Startup` classe</span><span class="sxs-lookup"><span data-stu-id="ad224-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="ad224-190">Abaixo disso, crie um construtor para definir os valores das `_environment` variáveis e `_modelPath` .</span><span class="sxs-lookup"><span data-stu-id="ad224-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="ad224-191">Quando o aplicativo é executado localmente, o ambiente padrão é *desenvolvimento*.</span><span class="sxs-lookup"><span data-stu-id="ad224-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="ad224-192">Em seguida, adicione um novo método chamado `Configure` para registrar o `PredictionEnginePool` serviço abaixo do construtor.</span><span class="sxs-lookup"><span data-stu-id="ad224-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="ad224-193">Em um alto nível, esse código inicializa os objetos e os serviços automaticamente para uso posterior quando solicitado pelo aplicativo em vez de ter que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="ad224-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="ad224-194">Os modelos de aprendizado de máquina não são estáticos.</span><span class="sxs-lookup"><span data-stu-id="ad224-194">Machine learning models are not static.</span></span> <span data-ttu-id="ad224-195">À medida que novos dados de treinamento ficam disponíveis, o modelo é retreinado e reimplantado.</span><span class="sxs-lookup"><span data-stu-id="ad224-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="ad224-196">Uma maneira de obter a versão mais recente do modelo em seu aplicativo é reimplantar o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="ad224-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="ad224-197">No entanto, isso introduz o tempo de inatividade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-197">However, this introduces application downtime.</span></span> <span data-ttu-id="ad224-198">O `PredictionEnginePool` serviço fornece um mecanismo para recarregar um modelo atualizado sem desativar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="ad224-199">Defina o `watchForChanges` parâmetro como `true` e o `PredictionEnginePool` inicia um [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) que escuta as notificações de alteração do sistema de arquivos e gera eventos quando há uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="ad224-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="ad224-200">Isso solicita que o `PredictionEnginePool` recarregue automaticamente o modelo.</span><span class="sxs-lookup"><span data-stu-id="ad224-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="ad224-201">O modelo é identificado pelo `modelName` parâmetro para que mais de um modelo por aplicativo possa ser recarregado após a alteração.</span><span class="sxs-lookup"><span data-stu-id="ad224-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="ad224-202">Como alternativa, você pode usar o `FromUri` método ao trabalhar com modelos armazenados remotamente.</span><span class="sxs-lookup"><span data-stu-id="ad224-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="ad224-203">Em vez de observar os eventos de alteração de arquivo, `FromUri` o pesquisa o local remoto em busca de alterações.</span><span class="sxs-lookup"><span data-stu-id="ad224-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="ad224-204">O padrão do intervalo de sondagem é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="ad224-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="ad224-205">Você pode aumentar ou diminuir o intervalo de sondagem com base nos requisitos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad224-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="ad224-206">No exemplo de código abaixo, o `PredictionEnginePool` sonda o modelo armazenado no URI especificado a cada minuto.</span><span class="sxs-lookup"><span data-stu-id="ad224-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="ad224-207">Carregar o modelo na função</span><span class="sxs-lookup"><span data-stu-id="ad224-207">Load the model into the function</span></span>

<span data-ttu-id="ad224-208">Insira o seguinte código dentro da classe *AnalyzeSentiment*:</span><span class="sxs-lookup"><span data-stu-id="ad224-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="ad224-209">Esse código atribui o `PredictionEnginePool` passando-o para o construtor da função que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="ad224-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="ad224-210">Usar o modelo para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="ad224-210">Use the model to make predictions</span></span>

<span data-ttu-id="ad224-211">Substitua a implementação existente do método *Run* na classe *AnalyzeSentiment* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ad224-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="ad224-212">Quando o método `Run` é executado, os dados de entrada da solicitação HTTP são desserializados e usados como entrada para o `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="ad224-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="ad224-213">O `Predict` método é chamado para fazer previsões usando o `SentimentAnalysisModel` registrado na `Startup` classe e retorna os resultados para o usuário, se for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="ad224-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="ad224-214">Testar localmente</span><span class="sxs-lookup"><span data-stu-id="ad224-214">Test locally</span></span>

<span data-ttu-id="ad224-215">Agora que está tudo definido, é hora de testar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ad224-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="ad224-216">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad224-216">Run the application</span></span>
1. <span data-ttu-id="ad224-217">Abra o PowerShell e digite o seguinte código no prompt, em que PORT é a porta em que seu aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ad224-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="ad224-218">Normalmente, a porta é a 7071.</span><span class="sxs-lookup"><span data-stu-id="ad224-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="ad224-219">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="ad224-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="ad224-220">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ad224-220">Congratulations!</span></span> <span data-ttu-id="ad224-221">Você usou com êxito o modelo para fazer previsões pela internet usando uma função do Azure.</span><span class="sxs-lookup"><span data-stu-id="ad224-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad224-222">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ad224-222">Next Steps</span></span>

- [<span data-ttu-id="ad224-223">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="ad224-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
