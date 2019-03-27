---
title: Usar um modelo de Machine Learning em ASP.NET Core Web API
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0cc13ec22b3a8805ec4aa17bf10560b2564ccd63
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307909"
---
# <a name="how-to-serve-machine-learning-model-through-aspnet-core-web-api"></a><span data-ttu-id="f2404-103">Como fazer: Usar um modelo de Machine Learning por meio do ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="f2404-103">How-To: Serve Machine Learning Model Through ASP.NET Core Web API</span></span>

<span data-ttu-id="f2404-104">Estas instruções mostram como usar um modelo de machine learning com ML.NET, previamente criado, na Web usando um ASP.NET Core Web API.</span><span class="sxs-lookup"><span data-stu-id="f2404-104">This how-to shows how to serve a pre-built ML.NET machine learning model to the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="f2404-105">Fazer isso permite que os usuários acessem a API para fins de previsão por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="f2404-105">By doing so it allows for users to access the API for prediction purposes via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="f2404-106">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="f2404-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f2404-107">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f2404-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f2404-108">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="f2404-108">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f2404-109">Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f2404-109">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2404-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f2404-110">Prerequisites</span></span>

- <span data-ttu-id="f2404-111">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="f2404-111">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="f2404-112">Powershell.</span><span class="sxs-lookup"><span data-stu-id="f2404-112">Powershell.</span></span>
- <span data-ttu-id="f2404-113">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="f2404-113">Pre-trained model.</span></span>
    - <span data-ttu-id="f2404-114">Use o [tutorial de Análise de Sentimento com ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo.</span><span class="sxs-lookup"><span data-stu-id="f2404-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
    - <span data-ttu-id="f2404-115">Baixe este [modelo de machine learning previamente treinado para análise de sentimento](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="f2404-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="f2404-116">Criar o projeto do ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f2404-116">Create ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="f2404-117">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f2404-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="f2404-118">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="f2404-118">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="f2404-119">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="f2404-119">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="f2404-120">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="f2404-120">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="f2404-121">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2404-121">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>
1. <span data-ttu-id="f2404-122">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2404-122">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>
1. <span data-ttu-id="f2404-123">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="f2404-123">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="f2404-124">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="f2404-124">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="f2404-125">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="f2404-125">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="f2404-126">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="f2404-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="f2404-127">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f2404-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f2404-128">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="f2404-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="f2404-129">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="f2404-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="f2404-130">Adicionar um modelo ao Projeto do ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f2404-130">Add Model to ASP.NET Core Web API Project</span></span>

1. <span data-ttu-id="f2404-131">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="f2404-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="f2404-132">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="f2404-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="f2404-133">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="f2404-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="build-data-models"></a><span data-ttu-id="f2404-134">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="f2404-134">Build Data Models</span></span>

<span data-ttu-id="f2404-135">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="f2404-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="f2404-136">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="f2404-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="f2404-137">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="f2404-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="f2404-138">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="f2404-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="f2404-139">Digite "DataModels" e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="f2404-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="f2404-140">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="f2404-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="f2404-141">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f2404-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="f2404-142">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f2404-142">Then, select the **Add** button.</span></span> <span data-ttu-id="f2404-143">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="f2404-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="f2404-144">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="f2404-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="f2404-145">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:</span><span class="sxs-lookup"><span data-stu-id="f2404-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

```csharp
public class SentimentData
{
    [LoadColumn(0)]
    public bool Label { get; set; }
    [LoadColumn(1)]
    public string Text { get; set; }   
}
```

4. <span data-ttu-id="f2404-146">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="f2404-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="f2404-147">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="f2404-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="f2404-148">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="f2404-148">Then, select the Add button.</span></span> <span data-ttu-id="f2404-149">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="f2404-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="f2404-150">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="f2404-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.ML.Data;
```

<span data-ttu-id="f2404-151">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="f2404-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

```csharp
public class SentimentPrediction
{
    [ColumnName("PredictedLabel")]
    public bool Prediction { get; set; }
}
```

## <a name="register-predictionengine-for-use-in-application"></a><span data-ttu-id="f2404-152">Registrar o PredictionEngine para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="f2404-152">Register PredictionEngine for Use in Application</span></span>

<span data-ttu-id="f2404-153">Para fazer uma única previsão, você pode usar o `PredictionEngine`.</span><span class="sxs-lookup"><span data-stu-id="f2404-153">To make a single prediction, you can use `PredictionEngine`.</span></span> <span data-ttu-id="f2404-154">Para usar o `PredictionEngine` em seu aplicativo, você precisará criá-lo sempre que necessário.</span><span class="sxs-lookup"><span data-stu-id="f2404-154">In order to use `PredictionEngine` in your application you will have to create it every time it is needed.</span></span> <span data-ttu-id="f2404-155">Nesse caso, a prática recomendada é a injeção de dependência do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2404-155">In that case, a best practice to consider is ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="f2404-156">O link a seguir fornece mais informações sobre a [injeção de dependência](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="f2404-156">The following link provides more information if you want to learn about [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="f2404-157">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="f2404-157">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

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
```

2. <span data-ttu-id="f2404-158">Adicione as seguintes linhas de código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="f2404-158">Add the following lines of code to the *ConfigureServices* method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);

    services.AddScoped<MLContext>();
    services.AddScoped<PredictionEngine<SentimentData, SentimentPrediction>>((ctx) =>
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
}
```

> [!WARNING]
> <span data-ttu-id="f2404-159">`PredictionEngine` não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="f2404-159">`PredictionEngine` is not thread-safe.</span></span> <span data-ttu-id="f2404-160">Uma maneira de limitar o custo da criação do objeto é definir o tempo de vida do serviço *Com escopo*.</span><span class="sxs-lookup"><span data-stu-id="f2404-160">A way that you can limit the cost of creating the object is by making its service lifetime *Scoped*.</span></span> <span data-ttu-id="f2404-161">Os objetos *com escopo* são os mesmos em uma solicitação, mas diferentes entre solicitações.</span><span class="sxs-lookup"><span data-stu-id="f2404-161">*Scoped* objects are the same within a request but different across requests.</span></span> <span data-ttu-id="f2404-162">Visite o link a seguir para saber mais sobre [tempos de vida do serviço](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="f2404-162">Visit the following link to learn more about [service lifetimes](/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1#service-lifetimes).</span></span>

<span data-ttu-id="f2404-163">Em um alto nível, esse código inicializa os objetos e serviços automaticamente quando solicitado pelo aplicativo em vez de precisar fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="f2404-163">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

## <a name="create-predict-controller"></a><span data-ttu-id="f2404-164">Criar o Predict Controller</span><span class="sxs-lookup"><span data-stu-id="f2404-164">Create Predict Controller</span></span>

<span data-ttu-id="f2404-165">Para processar as solicitações HTTP de entrada, será necessário criar um controlador.</span><span class="sxs-lookup"><span data-stu-id="f2404-165">To process your incoming HTTP requests, you need to create a controller.</span></span>

1. <span data-ttu-id="f2404-166">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="f2404-166">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="f2404-167">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f2404-167">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="f2404-168">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="f2404-168">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="f2404-169">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="f2404-169">Then, select the Add button.</span></span> <span data-ttu-id="f2404-170">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="f2404-170">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="f2404-171">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="f2404-171">Add the following using statement to the top of *PredictController.cs*:</span></span>

```csharp
using System;
using Microsoft.AspNetCore.Mvc;
using SentimentAnalysisWebAPI.DataModels;
using Microsoft.ML;
```

<span data-ttu-id="f2404-172">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="f2404-172">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

```csharp
public class PredictController : ControllerBase
{
    
    private readonly PredictionEngine<SentimentData,SentimentPrediction> _predictionEngine;

    public PredictController(PredictionEngine<SentimentData, SentimentPrediction> predictionEngine)
    {
        _predictionEngine = predictionEngine; //Define prediction engine
    }

    [HttpPost]
    public ActionResult<string> Post([FromBody]SentimentData input)
    {
        if(!ModelState.IsValid)
        {
            return BadRequest();
        }

        // Make a prediction
        SentimentPrediction prediction = _predictionEngine.Predict(input);

        //If prediction is true then it is toxic. If it is false, the it is not.
        string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

        return Ok(isToxic);
    }
    
}
```

<span data-ttu-id="f2404-173">Isso atribui o `PredictionEngine` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="f2404-173">This is assigning the `PredictionEngine` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="f2404-174">Em seguida, no método POST desse controlador, o `PredictionEngine` está sendo usado para fazer previsões e retornar os resultados para o usuário, em caso de êxito.</span><span class="sxs-lookup"><span data-stu-id="f2404-174">Then, in the POST method of this controller the `PredictionEngine` is being used to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="f2404-175">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="f2404-175">Test Web API Locally</span></span>

<span data-ttu-id="f2404-176">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2404-176">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="f2404-177">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2404-177">Run the application.</span></span>
1. <span data-ttu-id="f2404-178">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="f2404-178">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

```powershell
Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="f2404-179">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="f2404-179">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="f2404-180">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="f2404-180">Congratulations!</span></span> <span data-ttu-id="f2404-181">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API.</span><span class="sxs-lookup"><span data-stu-id="f2404-181">You have successfully served your model to make predictions over the internet using an ASP.NET Core API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2404-182">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f2404-182">Next Steps</span></span>

- [<span data-ttu-id="f2404-183">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="f2404-183">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.1#deploy-the-app-to-azure)