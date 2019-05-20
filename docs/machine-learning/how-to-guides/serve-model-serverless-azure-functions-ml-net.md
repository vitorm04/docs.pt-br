---
title: Implantar um modelo no Azure Functions
description: Usar um modelo de machine learning para Análise de Sentimento com o ML.NET para previsão pela internet usando o Azure Functions
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 9e62d8826227aed07451387cc733d27094327f99
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645106"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="ef15a-103">Implantar um modelo no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ef15a-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="ef15a-104">Saiba como implantar um modelo de machine learning do ML.NET pré-treinado para previsões por HTTP por meio de um ambiente sem servidor do Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="ef15a-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="ef15a-105">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="ef15a-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef15a-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ef15a-106">Prerequisites</span></span>

- <span data-ttu-id="ef15a-107">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" e “desenvolvimento do Azure” instalados.</span><span class="sxs-lookup"><span data-stu-id="ef15a-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="ef15a-108">Ferramentas do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ef15a-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="ef15a-109">Powershell</span><span class="sxs-lookup"><span data-stu-id="ef15a-109">Powershell</span></span>
- <span data-ttu-id="ef15a-110">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="ef15a-110">Pre-trained model.</span></span> <span data-ttu-id="ef15a-111">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="ef15a-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="ef15a-112">Criar um projeto no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ef15a-112">Create Azure Functions project</span></span>

1. <span data-ttu-id="ef15a-113">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ef15a-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="ef15a-114">Selecione **Arquivo** > **Novo** > **Projeto** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="ef15a-114">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="ef15a-115">Na caixa de diálogo **Novo projeto**, selecione o nó **Visual C#** seguido pelo nó **Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-115">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="ef15a-116">Em seguida, selecione o modelo de projeto do **Azure Functions**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-116">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="ef15a-117">Na caixa de texto **Nome**, digite "SentimentAnalysisFunctionsApp" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-117">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="ef15a-118">Na caixa de diálogo **Novo Projeto**, abra a lista suspensa acima das opções de projeto e selecione **Azure Functions v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-118">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="ef15a-119">Depois, selecione o projeto de **Gatilho de HTTP** e, em seguida, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-119">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="ef15a-120">Crie um diretório chamado *MLModels* em seu projeto para salvar o modelo:</span><span class="sxs-lookup"><span data-stu-id="ef15a-120">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="ef15a-121">No **Gerenciador de Soluções**, clique com o botão direito do mouse no seu projeto e selecione **Adicionar** > **Nova Pasta**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-121">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="ef15a-122">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ef15a-122">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="ef15a-123">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="ef15a-123">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="ef15a-124">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-124">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ef15a-125">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-125">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ef15a-126">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ef15a-126">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="ef15a-127">Instalar o **Pacote do NuGet Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="ef15a-127">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="ef15a-128">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="ef15a-129">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="ef15a-130">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="ef15a-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="ef15a-131">Adicionar modelo pré-treinado ao projeto</span><span class="sxs-lookup"><span data-stu-id="ef15a-131">Add pre-trained model to project</span></span>

1. <span data-ttu-id="ef15a-132">Copie o modelo previamente criado para o diretório *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="ef15a-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="ef15a-133">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo do modelo criado previamente e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="ef15a-134">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="ef15a-135">Criar Função do Azure para analisar o sentimento</span><span class="sxs-lookup"><span data-stu-id="ef15a-135">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="ef15a-136">Crie uma classe para prever o sentimento.</span><span class="sxs-lookup"><span data-stu-id="ef15a-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="ef15a-137">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="ef15a-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="ef15a-138">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="ef15a-139">Na caixa de diálogo **Adicionar novo item**, selecione **Função do Azure** e altere o campo **Nome** para *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef15a-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="ef15a-140">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="ef15a-141">Na caixa de diálogo **Nova Função do Azure**, selecione **Gatilho de HTTP**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="ef15a-142">Depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="ef15a-143">O arquivo *AnalyzeSentiment.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ef15a-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="ef15a-144">Adicione a seguinte instrução `using` acima de *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-144">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using Microsoft.AspNetCore.Http;
    using Microsoft.Extensions.Logging;
    using Newtonsoft.Json;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="ef15a-145">Por padrão, a classe `AnalyzeSentiment` é `static`.</span><span class="sxs-lookup"><span data-stu-id="ef15a-145">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="ef15a-146">Remova a palavra-chave `static` da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="ef15a-146">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="ef15a-147">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="ef15a-147">Create data models</span></span>

<span data-ttu-id="ef15a-148">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="ef15a-148">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="ef15a-149">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="ef15a-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="ef15a-150">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados: No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Adicionar > Nova pasta**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-150">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="ef15a-151">Digite "DataModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ef15a-151">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="ef15a-152">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-152">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="ef15a-153">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef15a-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="ef15a-154">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-154">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="ef15a-155">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ef15a-155">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="ef15a-156">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-156">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="ef15a-157">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-157">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="ef15a-158">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-158">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="ef15a-159">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef15a-159">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="ef15a-160">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-160">Then, select the **Add** button.</span></span> <span data-ttu-id="ef15a-161">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ef15a-161">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="ef15a-162">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-162">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="ef15a-163">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-163">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="ef15a-164">`SentimentPrediction` herda de `SentimentData`, que dá acesso aos dados originais na propriedade `SentimentText`, bem como a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="ef15a-164">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="ef15a-165">Registrar serviço PredictionEnginePool</span><span class="sxs-lookup"><span data-stu-id="ef15a-165">Register PredictionEnginePool service</span></span>

<span data-ttu-id="ef15a-166">Para fazer uma única previsão, você pode usar o [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="ef15a-166">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="ef15a-167">Para usar [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) em seu aplicativo, você deve criá-lo quando ele for necessário.</span><span class="sxs-lookup"><span data-stu-id="ef15a-167">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="ef15a-168">Nesse caso, a prática recomendada é considerar sua injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="ef15a-168">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="ef15a-169">O link a seguir fornece mais informações sobre a [injeção de dependência](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="ef15a-169">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="ef15a-170">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-170">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ef15a-171">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef15a-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="ef15a-172">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-172">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="ef15a-173">O arquivo *Startup.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ef15a-173">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="ef15a-174">Adicione a seguinte instrução using na parte superior do *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-174">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="ef15a-175">Remova o código existente abaixo do usando instruções e adicione o seguinte código para ao arquivo *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-175">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="ef15a-176">Em um alto nível, esse código inicializa os objetos e serviços automaticamente quando solicitado pelo aplicativo em vez de precisar fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="ef15a-176">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="ef15a-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="ef15a-177">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="ef15a-178">Para melhorar o desempenho e o acesso thread-safe, use o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos `PredictionEngine` para uso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef15a-178">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="register-startup-as-an-azure-functions-extension"></a><span data-ttu-id="ef15a-179">Registrar a Inicialização como uma extensão do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ef15a-179">Register Startup as an Azure Functions extension</span></span>

<span data-ttu-id="ef15a-180">Para usar `Startup` em seu aplicativo, você precisa registrá-lo como uma extensão do Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="ef15a-180">In order to use `Startup` in your application, you need to register it as an Azure Functions extension.</span></span> <span data-ttu-id="ef15a-181">Crie um novo arquivo chamado *extensions.json* em seu projeto, se ele ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="ef15a-181">Create a new file called *extensions.json* in your project if one does not already exist.</span></span>

1. <span data-ttu-id="ef15a-182">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-182">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="ef15a-183">Na caixa de diálogo **Novo Item**, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-183">In the **New Item** dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="ef15a-184">Em seguida, selecione a opção **Arquivo Json**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-184">Then select the **Json File** option.</span></span> <span data-ttu-id="ef15a-185">Na caixa de texto **Nome**, digite "extensions.json" e, em seguida, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-185">In the **Name** text box, type "extensions.json" and then select the **OK** button.</span></span>

    <span data-ttu-id="ef15a-186">O arquivo *extensions.json* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="ef15a-186">The *extensions.json* file opens in the code editor.</span></span> <span data-ttu-id="ef15a-187">Adicione o seguinte conteúdo a *extensions.json*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-187">Add the following content to *extensions.json*:</span></span>
    
    ```json
    {
      "extensions": [
        {
          "name": "Startup",
          "typename": "SentimentAnalysisFunctionsApp.Startup, SentimentAnalysisFunctionsApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"
        }
      ]
    }
    ```

1. <span data-ttu-id="ef15a-188">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo *extensions.json* e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-188">In Solution Explorer, right-click your *extensions.json* file and select **Properties**.</span></span> <span data-ttu-id="ef15a-189">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="ef15a-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="ef15a-190">Carregar o modelo na função</span><span class="sxs-lookup"><span data-stu-id="ef15a-190">Load the model into the function</span></span>

<span data-ttu-id="ef15a-191">Insira o seguinte código dentro da classe *AnalyzeSentiment*:</span><span class="sxs-lookup"><span data-stu-id="ef15a-191">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="ef15a-192">Esse código atribui o `PredictionEnginePool` passando-o para o construtor da função que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="ef15a-192">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="ef15a-193">Usar o modelo para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="ef15a-193">Use the model to make predictions</span></span>

<span data-ttu-id="ef15a-194">Substitua a implementação existente do método *Run* na classe *AnalyzeSentiment* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ef15a-194">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="ef15a-195">Quando o método `Run` é executado, os dados de entrada da solicitação HTTP são desserializados e usados como entrada para o `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="ef15a-195">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="ef15a-196">O método `Predict` é chamado para gerar uma previsão e retornar o resultado ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ef15a-196">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="ef15a-197">Testar localmente</span><span class="sxs-lookup"><span data-stu-id="ef15a-197">Test locally</span></span>

<span data-ttu-id="ef15a-198">Agora que está tudo definido, é hora de testar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ef15a-198">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="ef15a-199">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ef15a-199">Run the application</span></span>
1. <span data-ttu-id="ef15a-200">Abra o PowerShell e digite o seguinte código no prompt, em que PORT é a porta em que seu aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ef15a-200">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="ef15a-201">Normalmente, a porta é a 7071.</span><span class="sxs-lookup"><span data-stu-id="ef15a-201">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="ef15a-202">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="ef15a-202">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="ef15a-203">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ef15a-203">Congratulations!</span></span> <span data-ttu-id="ef15a-204">Você usou com êxito o modelo para fazer previsões pela internet usando uma função do Azure.</span><span class="sxs-lookup"><span data-stu-id="ef15a-204">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ef15a-205">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ef15a-205">Next Steps</span></span>

- [<span data-ttu-id="ef15a-206">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="ef15a-206">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
