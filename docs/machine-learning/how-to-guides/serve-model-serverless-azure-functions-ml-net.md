---
title: Implantar um modelo no Azure Functions
description: Usar um modelo de machine learning para Análise de Sentimento com o ML.NET para previsão pela internet usando o Azure Functions
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f340805200a14e0e145ffe1bf20f8059df63555
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608043"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="8ec24-103">Implantar um modelo no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8ec24-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="8ec24-104">Saiba como implantar um modelo de machine learning do ML.NET pré-treinado para previsões por HTTP por meio de um ambiente sem servidor do Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="8ec24-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="8ec24-105">Esta amostra executa uma `PredictionEnginePool` versão de pré-visualização do serviço.</span><span class="sxs-lookup"><span data-stu-id="8ec24-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ec24-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8ec24-106">Prerequisites</span></span>

- <span data-ttu-id="8ec24-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou posterior ou Visual Studio 2017 versão 15.6 ou posterior com as cargas de trabalho ".NET Core cross-platform" e "Desenvolvimento Azure" instaladas.</span><span class="sxs-lookup"><span data-stu-id="8ec24-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- [<span data-ttu-id="8ec24-108">Ferramentas de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="8ec24-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="8ec24-109">Powershell</span><span class="sxs-lookup"><span data-stu-id="8ec24-109">Powershell</span></span>
- <span data-ttu-id="8ec24-110">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="8ec24-110">Pre-trained model.</span></span> <span data-ttu-id="8ec24-111">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="8ec24-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="8ec24-112">Visão geral da amostra de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="8ec24-112">Azure Functions sample overview</span></span>

<span data-ttu-id="8ec24-113">Esta amostra é um **aplicativo C# HTTP Trigger Azure Functions** que usa um modelo de classificação binária pré-treinado para categorizar o sentimento do texto como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="8ec24-114">O Azure Functions fornece uma maneira fácil de executar pequenos pedaços de código em escala em um ambiente sem servidor gerenciado na nuvem.</span><span class="sxs-lookup"><span data-stu-id="8ec24-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="8ec24-115">O código para esta amostra pode ser encontrado no repositório [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="8ec24-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="8ec24-116">Criar um projeto do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="8ec24-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="8ec24-117">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8ec24-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="8ec24-118">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="8ec24-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8ec24-119">Na caixa de diálogo **Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="8ec24-120">Em seguida, selecione o modelo de projeto do **Azure Functions**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="8ec24-121">Na caixa de texto **Nome**, digite "SentimentAnalysisFunctionsApp" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="8ec24-122">Na caixa de diálogo **Novo Projeto**, abra a lista suspensa acima das opções de projeto e selecione **Azure Functions v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="8ec24-123">Depois, selecione o projeto de **Gatilho de HTTP** e, em seguida, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="8ec24-124">Crie um diretório chamado *MLModels* em seu projeto para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="8ec24-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="8ec24-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8ec24-126">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="8ec24-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="8ec24-127">Instale o **Microsoft.ML NuGet Package** versão **1.3.1**:</span><span class="sxs-lookup"><span data-stu-id="8ec24-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="8ec24-128">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8ec24-129">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8ec24-130">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8ec24-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8ec24-131">Instale o **Pacote NuGet Microsoft.Azure.Functions.Extensions**:</span><span class="sxs-lookup"><span data-stu-id="8ec24-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="8ec24-132">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8ec24-133">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, procure por **Microsoft.Azure.Functions.Extensions**, selecione o pacote na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8ec24-134">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8ec24-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8ec24-135">Instale o **Microsoft.Extensions.ML nuget package** versão **0.15.1**:</span><span class="sxs-lookup"><span data-stu-id="8ec24-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="8ec24-136">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8ec24-137">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, procure **Microsoft.Extensions.ML,** selecione esse pacote na lista e selecione o botão **Instalar.**</span><span class="sxs-lookup"><span data-stu-id="8ec24-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8ec24-138">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8ec24-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8ec24-139">Instale o **Pacote Microsoft.NET.Sdk.Funções NuGet Versão** **1.0.31**:</span><span class="sxs-lookup"><span data-stu-id="8ec24-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="8ec24-140">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8ec24-141">Escolha "nuget.org" como a origem do pacote, selecione a guia Instalado, procure **por Funções Microsoft.NET.Sdk.,** selecione esse pacote na lista, selecione **1.0.31** na versão suspensa e selecione o botão **Atualizar.**</span><span class="sxs-lookup"><span data-stu-id="8ec24-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="8ec24-142">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="8ec24-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="8ec24-143">Adicionar modelo pré-treinado ao projeto</span><span class="sxs-lookup"><span data-stu-id="8ec24-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="8ec24-144">Copie o modelo previamente criado para o diretório *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="8ec24-145">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo do modelo criado previamente e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="8ec24-146">Em **Avançado,** altere o valor de **Copiar para Diretório de Saída** para Copiar se mais **novo**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="8ec24-147">Criar Função do Azure para analisar o sentimento</span><span class="sxs-lookup"><span data-stu-id="8ec24-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="8ec24-148">Crie uma classe para prever o sentimento.</span><span class="sxs-lookup"><span data-stu-id="8ec24-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="8ec24-149">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="8ec24-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="8ec24-150">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="8ec24-151">Na caixa de diálogo **Adicionar novo item**, selecione **Função do Azure** e altere o campo **Nome** para *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="8ec24-152">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="8ec24-153">Na caixa de diálogo **Nova Função do Azure**, selecione **Gatilho de HTTP**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="8ec24-154">Depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="8ec24-155">O arquivo *AnalyzeSentiment.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="8ec24-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="8ec24-156">Adicione a seguinte instrução `using` acima de *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="8ec24-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="8ec24-157">Por padrão, a classe `AnalyzeSentiment` é `static`.</span><span class="sxs-lookup"><span data-stu-id="8ec24-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="8ec24-158">Remova a palavra-chave `static` da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="8ec24-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="8ec24-159">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="8ec24-159">Create data models</span></span>

<span data-ttu-id="8ec24-160">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="8ec24-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="8ec24-161">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="8ec24-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="8ec24-162">Crie um diretório chamado *DataModels* em seu projeto para salvar seus modelos de dados: No Solution Explorer, clique com o botão direito do mouse no seu projeto e **selecione Adicionar > Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="8ec24-163">Digite "DataModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="8ec24-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="8ec24-164">No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="8ec24-165">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="8ec24-166">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8ec24-167">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="8ec24-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8ec24-168">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="8ec24-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="8ec24-169">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="8ec24-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="8ec24-170">No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="8ec24-171">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="8ec24-172">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-172">Then, select the **Add** button.</span></span> <span data-ttu-id="8ec24-173">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="8ec24-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="8ec24-174">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="8ec24-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="8ec24-175">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="8ec24-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="8ec24-176">`SentimentPrediction` herda de `SentimentData`, que dá acesso aos dados originais na propriedade `SentimentText`, bem como a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="8ec24-177">Registrar serviço PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="8ec24-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="8ec24-178">Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um .</span><span class="sxs-lookup"><span data-stu-id="8ec24-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="8ec24-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca.</span><span class="sxs-lookup"><span data-stu-id="8ec24-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="8ec24-180">Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="8ec24-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="8ec24-181">À medida que sua aplicação cresce, esse processo pode se tornar incontrolável.</span><span class="sxs-lookup"><span data-stu-id="8ec24-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="8ec24-182">Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="8ec24-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="8ec24-183">O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="8ec24-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="8ec24-184">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8ec24-185">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="8ec24-186">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8ec24-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8ec24-187">Adicione as seguintes instruções usando a parte superior do *Startup.cs:*</span><span class="sxs-lookup"><span data-stu-id="8ec24-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="8ec24-188">Remova o código existente abaixo das instruções de uso e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8ec24-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="8ec24-189">Defina variáveis para armazenar o ambiente em que o aplicativo está sendo `Startup` executado e o caminho do arquivo onde o modelo está localizado dentro da classe</span><span class="sxs-lookup"><span data-stu-id="8ec24-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="8ec24-190">Abaixo disso, crie um construtor para `_environment` definir `_modelPath` os valores das variáveis.</span><span class="sxs-lookup"><span data-stu-id="8ec24-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="8ec24-191">Quando o aplicativo está sendo executado localmente, o ambiente padrão é *Desenvolvimento*.</span><span class="sxs-lookup"><span data-stu-id="8ec24-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="8ec24-192">Em seguida, adicione `Configure` um novo `PredictionEnginePool` método chamado para registrar o serviço abaixo do construtor.</span><span class="sxs-lookup"><span data-stu-id="8ec24-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="8ec24-193">Em um alto nível, esse código inicializa os objetos e serviços automaticamente para uso posterior quando solicitado pelo aplicativo, em vez de ter que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="8ec24-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="8ec24-194">Modelos de aprendizado de máquina não são estáticos.</span><span class="sxs-lookup"><span data-stu-id="8ec24-194">Machine learning models are not static.</span></span> <span data-ttu-id="8ec24-195">À medida que novos dados de treinamento se tornam disponíveis, o modelo é retreinado e reimplantado.</span><span class="sxs-lookup"><span data-stu-id="8ec24-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="8ec24-196">Uma maneira de colocar a versão mais recente do modelo em seu aplicativo é reimplantar todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="8ec24-197">No entanto, isso introduz o tempo de inatividade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-197">However, this introduces application downtime.</span></span> <span data-ttu-id="8ec24-198">O `PredictionEnginePool` serviço fornece um mecanismo para recarregar um modelo atualizado sem retirar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="8ec24-199">Defina `watchForChanges` o `true`parâmetro para `PredictionEnginePool` , [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) e as iniciações a que ouve o sistema de arquivos alterar notificações e levanta eventos quando há uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="8ec24-200">Isso solicita `PredictionEnginePool` a recarga automática do modelo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="8ec24-201">O modelo é `modelName` identificado pelo parâmetro para que mais de um modelo por aplicativo possa ser recarregado após a alteração.</span><span class="sxs-lookup"><span data-stu-id="8ec24-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="8ec24-202">Alternativamente, você pode `FromUri` usar o método ao trabalhar com modelos armazenados remotamente.</span><span class="sxs-lookup"><span data-stu-id="8ec24-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="8ec24-203">Em vez de assistir `FromUri` a eventos alterados por arquivos, pesquisa o local remoto para alterações.</span><span class="sxs-lookup"><span data-stu-id="8ec24-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="8ec24-204">O intervalo de votação é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="8ec24-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="8ec24-205">Você pode aumentar ou diminuir o intervalo de votação com base nos requisitos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ec24-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="8ec24-206">Na amostra de código `PredictionEnginePool` abaixo, as pesquisas o modelo armazenado no URI especificado a cada minuto.</span><span class="sxs-lookup"><span data-stu-id="8ec24-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="8ec24-207">Carregar o modelo na função</span><span class="sxs-lookup"><span data-stu-id="8ec24-207">Load the model into the function</span></span>

<span data-ttu-id="8ec24-208">Insira o seguinte código dentro da classe *AnalyzeSentiment*:</span><span class="sxs-lookup"><span data-stu-id="8ec24-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="8ec24-209">Esse código atribui o `PredictionEnginePool` passando-o para o construtor da função que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="8ec24-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="8ec24-210">Usar o modelo para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="8ec24-210">Use the model to make predictions</span></span>

<span data-ttu-id="8ec24-211">Substitua a implementação existente do método *Run* na classe *AnalyzeSentiment* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ec24-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="8ec24-212">Quando o método `Run` é executado, os dados de entrada da solicitação HTTP são desserializados e usados como entrada para o `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="8ec24-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="8ec24-213">O `Predict` método é então chamado `SentimentAnalysisModel` para fazer `Startup` previsões usando o registrado na classe e retorna os resultados ao usuário se for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8ec24-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="8ec24-214">Testar localmente</span><span class="sxs-lookup"><span data-stu-id="8ec24-214">Test locally</span></span>

<span data-ttu-id="8ec24-215">Agora que está tudo definido, é hora de testar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="8ec24-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="8ec24-216">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="8ec24-216">Run the application</span></span>
1. <span data-ttu-id="8ec24-217">Abra o PowerShell e digite o seguinte código no prompt, em que PORT é a porta em que seu aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="8ec24-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="8ec24-218">Normalmente, a porta é a 7071.</span><span class="sxs-lookup"><span data-stu-id="8ec24-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="8ec24-219">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="8ec24-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="8ec24-220">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="8ec24-220">Congratulations!</span></span> <span data-ttu-id="8ec24-221">Você usou com êxito o modelo para fazer previsões pela internet usando uma função do Azure.</span><span class="sxs-lookup"><span data-stu-id="8ec24-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ec24-222">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8ec24-222">Next Steps</span></span>

- [<span data-ttu-id="8ec24-223">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="8ec24-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
