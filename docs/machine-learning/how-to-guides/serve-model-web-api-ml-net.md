---
title: Implantar um modelo em uma API Web do ASP.NET Core
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c78e58dbec6b2ba3065fc46c4d4fd65abdcd37cd
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063478"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="b3351-103">Implantar um modelo em uma API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3351-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="b3351-104">Saiba como fornecer um modelo de machine Learning do ML.NET previamente treinado na Web usando uma API Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3351-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="b3351-105">Veicular um modelo por uma API Web habilita previsões por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="b3351-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="b3351-106">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="b3351-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3351-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b3351-107">Prerequisites</span></span>

- <span data-ttu-id="b3351-108">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="b3351-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="b3351-109">Powershell.</span><span class="sxs-lookup"><span data-stu-id="b3351-109">Powershell.</span></span>
- <span data-ttu-id="b3351-110">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="b3351-110">Pre-trained model.</span></span> <span data-ttu-id="b3351-111">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="b3351-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="b3351-112">Criar o projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3351-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="b3351-113">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b3351-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="b3351-114">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="b3351-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="b3351-115">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="b3351-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="b3351-116">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="b3351-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="b3351-117">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3351-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="b3351-118">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3351-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="b3351-119">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="b3351-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="b3351-120">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="b3351-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="b3351-121">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b3351-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="b3351-122">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="b3351-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b3351-123">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b3351-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b3351-124">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="b3351-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="b3351-125">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="b3351-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b3351-126">Instalar o **Pacote do Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="b3351-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="b3351-127">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b3351-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b3351-128">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="b3351-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="b3351-129">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="b3351-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="b3351-130">Adicionar um modelo ao projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3351-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="b3351-131">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="b3351-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="b3351-132">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="b3351-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="b3351-133">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="b3351-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="b3351-134">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="b3351-134">Create data models</span></span>

<span data-ttu-id="b3351-135">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="b3351-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="b3351-136">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="b3351-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="b3351-137">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="b3351-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="b3351-138">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="b3351-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="b3351-139">Digite "DataModels" e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="b3351-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="b3351-140">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="b3351-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="b3351-141">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="b3351-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b3351-142">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b3351-142">Then, select the **Add** button.</span></span> <span data-ttu-id="b3351-143">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="b3351-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b3351-144">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3351-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="b3351-145">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:</span><span class="sxs-lookup"><span data-stu-id="b3351-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="b3351-146">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b3351-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="b3351-147">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="b3351-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="b3351-148">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="b3351-148">Then, select the Add button.</span></span> <span data-ttu-id="b3351-149">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="b3351-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="b3351-150">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3351-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="b3351-151">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3351-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="b3351-152">`SentimentPrediction` herda de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="b3351-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="b3351-153">Isso torna mais fácil ver os dados originais na propriedade `SentimentText` junto com a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="b3351-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="b3351-154">Registrar PredictionEnginePool para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="b3351-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="b3351-155">Para fazer uma única previsão, você pode usar o [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="b3351-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="b3351-156">Para usar [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) em seu aplicativo, você deve criá-lo quando ele for necessário.</span><span class="sxs-lookup"><span data-stu-id="b3351-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="b3351-157">Nesse caso, a prática recomendada é considerar sua injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3351-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="b3351-158">O link a seguir fornece mais informações sobre a [injeção de dependência no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="b3351-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="b3351-159">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="b3351-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="b3351-160">Adicione o seguinte código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="b3351-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="b3351-161">Em um alto nível, esse código inicializa os objetos e serviços automaticamente quando solicitado pelo aplicativo em vez de precisar fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="b3351-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="b3351-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="b3351-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b3351-163">Para melhorar o desempenho e o acesso thread-safe, use o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos `PredictionEngine` para uso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3351-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="b3351-164">Leia a postagem no blog para saber mais sobre [criar e usar pools de objeto `PredictionEngine` no ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="b3351-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="b3351-165">Criar o Controlador de Previsão</span><span class="sxs-lookup"><span data-stu-id="b3351-165">Create Predict controller</span></span>

<span data-ttu-id="b3351-166">Para processar as solicitações HTTP de entrada, crie um controlador.</span><span class="sxs-lookup"><span data-stu-id="b3351-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="b3351-167">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="b3351-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="b3351-168">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b3351-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="b3351-169">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="b3351-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="b3351-170">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="b3351-170">Then, select the Add button.</span></span> <span data-ttu-id="b3351-171">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="b3351-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="b3351-172">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3351-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="b3351-173">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="b3351-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="b3351-174">Esse código atribui o `PredictionEnginePool` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3351-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="b3351-175">Em seguida, o controlador `Predict`, com o método `Post`, usará o `PredictionEnginePool` para fazer previsões e retornará os resultados para o usuário se for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b3351-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="b3351-176">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="b3351-176">Test web API locally</span></span>

<span data-ttu-id="b3351-177">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3351-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="b3351-178">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3351-178">Run the application.</span></span>
1. <span data-ttu-id="b3351-179">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="b3351-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="b3351-180">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="b3351-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="b3351-181">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="b3351-181">Congratulations!</span></span> <span data-ttu-id="b3351-182">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API Web.</span><span class="sxs-lookup"><span data-stu-id="b3351-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b3351-183">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b3351-183">Next Steps</span></span>

- [<span data-ttu-id="b3351-184">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="b3351-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)
