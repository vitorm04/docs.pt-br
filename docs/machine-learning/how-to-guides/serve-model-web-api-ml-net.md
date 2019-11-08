---
title: Implantar um modelo em uma API Web do ASP.NET Core
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733311"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="89dc9-103">Implantar um modelo em uma API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89dc9-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="89dc9-104">Saiba como fornecer um modelo de machine Learning do ML.NET previamente treinado na Web usando uma API Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="89dc9-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="89dc9-105">Veicular um modelo por uma API Web habilita previsões por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="89dc9-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89dc9-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="89dc9-106">Prerequisites</span></span>

- <span data-ttu-id="89dc9-107">[Visual Studio 2017 versão 15,6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="89dc9-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="89dc9-108">Powershell.</span><span class="sxs-lookup"><span data-stu-id="89dc9-108">Powershell.</span></span>
- <span data-ttu-id="89dc9-109">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="89dc9-109">Pre-trained model.</span></span> <span data-ttu-id="89dc9-110">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="89dc9-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="89dc9-111">Criar o projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89dc9-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="89dc9-112">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="89dc9-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="89dc9-113">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="89dc9-114">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="89dc9-115">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="89dc9-116">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="89dc9-117">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="89dc9-118">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="89dc9-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="89dc9-119">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="89dc9-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="89dc9-120">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="89dc9-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="89dc9-121">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="89dc9-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="89dc9-122">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="89dc9-123">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="89dc9-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="89dc9-124">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="89dc9-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="89dc9-125">Instalar o **Pacote do Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="89dc9-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="89dc9-126">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="89dc9-127">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="89dc9-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="89dc9-128">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="89dc9-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="89dc9-129">Adicionar um modelo ao projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89dc9-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="89dc9-130">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="89dc9-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="89dc9-131">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="89dc9-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="89dc9-132">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="89dc9-133">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="89dc9-133">Create data models</span></span>

<span data-ttu-id="89dc9-134">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="89dc9-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="89dc9-135">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="89dc9-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="89dc9-136">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="89dc9-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="89dc9-137">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="89dc9-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="89dc9-138">Digite "DataModels" e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="89dc9-139">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="89dc9-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="89dc9-140">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="89dc9-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="89dc9-141">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-141">Then, select the **Add** button.</span></span> <span data-ttu-id="89dc9-142">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="89dc9-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="89dc9-143">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="89dc9-144">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:</span><span class="sxs-lookup"><span data-stu-id="89dc9-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

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

4. <span data-ttu-id="89dc9-145">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="89dc9-146">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="89dc9-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="89dc9-147">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="89dc9-147">Then, select the Add button.</span></span> <span data-ttu-id="89dc9-148">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="89dc9-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="89dc9-149">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="89dc9-150">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="89dc9-151">`SentimentPrediction` herda de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="89dc9-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="89dc9-152">Isso torna mais fácil ver os dados originais na propriedade `SentimentText` junto com a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="89dc9-153">Registrar PredictionEnginePool para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="89dc9-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="89dc9-154">Para fazer uma única previsão, você precisa criar um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="89dc9-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="89dc9-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="89dc9-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="89dc9-156">Além disso, você precisa criar uma instância dela em qualquer lugar em que seja necessário dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="89dc9-157">À medida que seu aplicativo cresce, esse processo pode se tornar não gerenciável.</span><span class="sxs-lookup"><span data-stu-id="89dc9-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="89dc9-158">Para melhorar o desempenho e a segurança do thread, use uma combinação de injeção de dependência e o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="89dc9-159">O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência em ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="89dc9-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="89dc9-160">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="89dc9-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="89dc9-161">Adicione o seguinte código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="89dc9-162">Em um alto nível, esse código inicializa os objetos e os serviços automaticamente para uso posterior quando solicitado pelo aplicativo em vez de ter que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="89dc9-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="89dc9-163">Os modelos de aprendizado de máquina não são estáticos.</span><span class="sxs-lookup"><span data-stu-id="89dc9-163">Machine learning models are not static.</span></span> <span data-ttu-id="89dc9-164">À medida que novos dados de treinamento ficam disponíveis, o modelo é retreinado e reimplantado.</span><span class="sxs-lookup"><span data-stu-id="89dc9-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="89dc9-165">Uma maneira de obter a versão mais recente do modelo em seu aplicativo é reimplantar o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="89dc9-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="89dc9-166">No entanto, isso introduz o tempo de inatividade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-166">However, this introduces application downtime.</span></span> <span data-ttu-id="89dc9-167">O serviço `PredictionEnginePool` fornece um mecanismo para recarregar um modelo atualizado sem levar seu aplicativo para baixo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="89dc9-168">Defina o parâmetro `watchForChanges` como `true`, e o `PredictionEnginePool` inicia um [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) que escuta as notificações de alteração do sistema de arquivos e gera eventos quando há uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="89dc9-169">Isso solicita que o `PredictionEnginePool` recarregue o modelo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="89dc9-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="89dc9-170">O modelo é identificado pelo parâmetro `modelName` para que mais de um modelo por aplicativo possa ser recarregado após a alteração.</span><span class="sxs-lookup"><span data-stu-id="89dc9-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="89dc9-171">Como alternativa, você pode usar o método `FromUri` ao trabalhar com modelos armazenados remotamente.</span><span class="sxs-lookup"><span data-stu-id="89dc9-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="89dc9-172">Em vez de observar os eventos de alteração de arquivo, `FromUri` pesquisa o local remoto em busca de alterações.</span><span class="sxs-lookup"><span data-stu-id="89dc9-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="89dc9-173">O padrão do intervalo de sondagem é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="89dc9-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="89dc9-174">Você pode aumentar ou diminuir o intervalo de sondagem com base nos requisitos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="89dc9-175">No exemplo de código abaixo, o `PredictionEnginePool` sonda o modelo armazenado no URI especificado a cada minuto.</span><span class="sxs-lookup"><span data-stu-id="89dc9-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="89dc9-176">Criar o Controlador de Previsão</span><span class="sxs-lookup"><span data-stu-id="89dc9-176">Create Predict controller</span></span>

<span data-ttu-id="89dc9-177">Para processar as solicitações HTTP de entrada, crie um controlador.</span><span class="sxs-lookup"><span data-stu-id="89dc9-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="89dc9-178">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="89dc9-179">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="89dc9-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="89dc9-180">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="89dc9-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="89dc9-181">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="89dc9-181">Then, select the Add button.</span></span> <span data-ttu-id="89dc9-182">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="89dc9-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="89dc9-183">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="89dc9-184">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="89dc9-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

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

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="89dc9-185">Esse código atribui o `PredictionEnginePool` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="89dc9-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="89dc9-186">Em seguida, o método `Post` do controlador de `Predict` usa o `PredictionEnginePool` para fazer previsões usando o `SentimentAnalysisModel` registrado na classe `Startup` e retorna os resultados para o usuário, se for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="89dc9-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="89dc9-187">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="89dc9-187">Test web API locally</span></span>

<span data-ttu-id="89dc9-188">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="89dc9-189">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89dc9-189">Run the application.</span></span>
1. <span data-ttu-id="89dc9-190">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="89dc9-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="89dc9-191">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="89dc9-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="89dc9-192">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="89dc9-192">Congratulations!</span></span> <span data-ttu-id="89dc9-193">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API Web.</span><span class="sxs-lookup"><span data-stu-id="89dc9-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="89dc9-194">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="89dc9-194">Next Steps</span></span>

- [<span data-ttu-id="89dc9-195">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="89dc9-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
