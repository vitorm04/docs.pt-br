---
title: Usar um modelo de Machine Learning em ASP.NET Core Web API
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 07b751caff8ef0ca9a23bed68ddf88feb7b5ae4f
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57856695"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a><span data-ttu-id="e5c3d-103">Como fazer: Usar um modelo de Machine Learning por meio do ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="e5c3d-103">How-To: Serve Machine Learning Model Through ASP.NET Core Web API</span></span>

<span data-ttu-id="e5c3d-104">Estas instruções mostram como usar um modelo de machine learning com ML.NET, previamente criado, na Web usando um ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-104">This how-to shows how to serve a pre-built ML.NET machine learning model to the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="e5c3d-105">Fazer isso permite que os usuários acessem a API para fins de previsão por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-105">By doing so it allows for users to access the API for prediction purposes via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c3d-106">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="e5c3d-107">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e5c3d-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="e5c3d-108">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-108">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="e5c3d-109">Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="e5c3d-109">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5c3d-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e5c3d-110">Prerequisites</span></span>

- <span data-ttu-id="e5c3d-111">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-111">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="e5c3d-112">Powershell.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-112">Powershell.</span></span>
- <span data-ttu-id="e5c3d-113">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-113">Pre-trained model.</span></span>
    - <span data-ttu-id="e5c3d-114">Use o [tutorial de Análise de Sentimento com ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="e5c3d-115">Baixe este [modelo de machine learning previamente treinado para análise de sentimento](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="e5c3d-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="e5c3d-116">Criar o projeto do ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e5c3d-116">Create ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="e5c3d-117">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="e5c3d-118">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-118">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="e5c3d-119">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-119">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="e5c3d-120">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-120">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="e5c3d-121">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-121">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>
1. <span data-ttu-id="e5c3d-122">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-122">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>
1. <span data-ttu-id="e5c3d-123">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-123">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="e5c3d-124">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-124">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="e5c3d-125">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-125">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="e5c3d-126">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="e5c3d-127">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e5c3d-128">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="e5c3d-129">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="e5c3d-130">Adicionar um modelo ao Projeto do ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="e5c3d-130">Add Model to ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="e5c3d-131">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="e5c3d-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="e5c3d-132">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="e5c3d-133">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="build-data-models"></a><span data-ttu-id="e5c3d-134">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="e5c3d-134">Build Data Models</span></span>

<span data-ttu-id="e5c3d-135">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="e5c3d-136">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="e5c3d-137">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="e5c3d-138">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="e5c3d-139">Digite "DataModels" e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="e5c3d-140">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="e5c3d-141">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="e5c3d-142">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-142">Then, select the **Add** button.</span></span> <span data-ttu-id="e5c3d-143">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="e5c3d-144">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="e5c3d-145">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. <span data-ttu-id="e5c3d-146">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="e5c3d-147">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="e5c3d-148">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-148">Then, select the Add button.</span></span> <span data-ttu-id="e5c3d-149">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="e5c3d-150">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="e5c3d-151">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="create-prediction-service"></a><span data-ttu-id="e5c3d-152">Criar o serviço de previsão</span><span class="sxs-lookup"><span data-stu-id="e5c3d-152">Create Prediction Service</span></span>

<span data-ttu-id="e5c3d-153">Para organizar e reutilizar a lógica de previsão em todo o aplicativo, crie um serviço de previsão.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-153">To organize and re-use the prediction logic throughout the entire application, create a prediction service.</span></span>

1. <span data-ttu-id="e5c3d-154">Crie um diretório chamado *Services* em seu projeto para manter os serviços a serem usados pelo aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-154">Create a directory named *Services* in your project to hold services to be used by the application:</span></span>

    <span data-ttu-id="e5c3d-155">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Adicionar > Nova pasta**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-155">In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="e5c3d-156">Digite "Services" e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-156">Type "Services" and hit **Enter**.</span></span>

1. <span data-ttu-id="e5c3d-157">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Services* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-157">In Solution Explorer, right-click the *Services* directory, and then select **Add > New Item**.</span></span>
1. <span data-ttu-id="e5c3d-158">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *PredictionService.cs*.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-158">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *PredictionService.cs*.</span></span> <span data-ttu-id="e5c3d-159">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-159">Then, select the **Add** button.</span></span> <span data-ttu-id="e5c3d-160">O arquivo *PredictionService.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-160">The *PredictionService.cs* file opens in the code editor.</span></span> <span data-ttu-id="e5c3d-161">Adicione a seguinte instrução using na parte superior do *PredictionService.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-161">Add the following using statement to the top of *PredictionService.cs*:</span></span>

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
```

<span data-ttu-id="e5c3d-162">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictionService.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-162">Remove the existing class definition and add the following code to the *PredictionService.cs* file:</span></span>

```csharp
public class PredictionService
{
    private readonly PredictionEngine<SentimentData, SentimentPrediction> _predictionEngine;
    public PredictionService(PredictionEngine<SentimentData,SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine;
    }

    public string Predict(SentimentData input)
    {
        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return isToxic;

    }
}
```

## <a name="register-predictions-service-for-use-in-application"></a><span data-ttu-id="e5c3d-163">Registrar o serviço de previsões para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="e5c3d-163">Register Predictions Service for Use in Application</span></span>

<span data-ttu-id="e5c3d-164">Para usar o serviço de previsão no aplicativo, será preciso criá-lo sempre que ele for necessário.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-164">To use the prediction service in your application you will have to create it every time it is needed.</span></span> <span data-ttu-id="e5c3d-165">Nesse caso, a prática recomendada é a injeção de dependência do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-165">In that case, a best practice to consider is ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="e5c3d-166">O link a seguir fornece mais informações sobre a [injeção de dependência](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="e5c3d-166">The following link provides more information if you want to learn about [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="e5c3d-167">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-167">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

```csharp
using System.IO;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

1. <span data-ttu-id="e5c3d-168">Adicione as seguintes linhas de código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-168">Add the following lines of code to the *ConfigureServices* method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddSingleton<MLContext>();
    services.AddSingleton<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
    {
        MLContext mlContext = ctx.GetRequiredService<MLContext>();
        string modelFilePathName = "MLModels/sentiment_model.zip";

        //Load model from file
        ITransformer model;
        using (var stream = File.OpenRead(modelFilePathName))
        {
            model = mlContext.Model.Load(stream);
        }

        // Return prediction engine
        return model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);
    });
    services.AddSingleton<PredictionService>();
}
```

<span data-ttu-id="e5c3d-169">Em um alto nível, esse código inicializa os objetos e serviços automaticamente quando solicitado pelo aplicativo em vez de precisar fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-169">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

## <a name="create-predict-controller"></a><span data-ttu-id="e5c3d-170">Criar o Predict Controller</span><span class="sxs-lookup"><span data-stu-id="e5c3d-170">Create Predict Controller</span></span>

<span data-ttu-id="e5c3d-171">Para processar as solicitações HTTP de entrada, será necessário criar um controlador.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-171">To process your incoming HTTP requests, you need to create a controller.</span></span>

1. <span data-ttu-id="e5c3d-172">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-172">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="e5c3d-173">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-173">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="e5c3d-174">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-174">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="e5c3d-175">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-175">Then, select the Add button.</span></span> <span data-ttu-id="e5c3d-176">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-176">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="e5c3d-177">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-177">Add the following using statement to the top of *PredictController.cs*:</span></span>

```csharp
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using SentimentAnalysisWebAPI.Services;
```

<span data-ttu-id="e5c3d-178">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-178">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

```csharp
public class PredictController : ControllerBase
{

    private readonly PredictionService _predictionService;

    public PredictController(PredictionService predictionService)
    {
        _predictionService = predictionService; //Define prediction service
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }
        return Ok(_predictionService.Predict(input));
    }

}
```

<span data-ttu-id="e5c3d-179">Com isso, o serviço de previsão é atribuído passando-o para o construtor de controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-179">This is assigning the Prediction service by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="e5c3d-180">Em seguida, no método POST desse controlador, o serviço a previsão está sendo usado para fazer previsões e retornar os resultados para o usuário, se obtiver êxito.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-180">Then, in the POST method of this controller the Prediction service is being used to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="e5c3d-181">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="e5c3d-181">Test Web API Locally</span></span>

<span data-ttu-id="e5c3d-182">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-182">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="e5c3d-183">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-183">Run the application.</span></span>
1. <span data-ttu-id="e5c3d-184">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-184">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="e5c3d-185">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="e5c3d-185">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="e5c3d-186">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="e5c3d-186">Congratulations!</span></span> <span data-ttu-id="e5c3d-187">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API.</span><span class="sxs-lookup"><span data-stu-id="e5c3d-187">You have successfully served your model to make predictions over the internet using an ASP.NET Core API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e5c3d-188">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e5c3d-188">Next Steps</span></span>

- [<span data-ttu-id="e5c3d-189">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="e5c3d-189">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)