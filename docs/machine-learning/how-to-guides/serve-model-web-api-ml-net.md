---
title: Implantar um modelo em uma API Web do ASP.NET Core
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398926"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="2de7b-103">Implantar um modelo em uma API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2de7b-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="2de7b-104">Saiba como fornecer um modelo de machine Learning do ML.NET previamente treinado na Web usando uma API Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2de7b-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="2de7b-105">Veicular um modelo por uma API Web habilita previsões por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="2de7b-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2de7b-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2de7b-106">Prerequisites</span></span>

- <span data-ttu-id="2de7b-107">[Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" instalada.</span><span class="sxs-lookup"><span data-stu-id="2de7b-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="2de7b-108">Powershell.</span><span class="sxs-lookup"><span data-stu-id="2de7b-108">Powershell.</span></span>
- <span data-ttu-id="2de7b-109">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="2de7b-109">Pre-trained model.</span></span> <span data-ttu-id="2de7b-110">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="2de7b-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="2de7b-111">Criar o projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2de7b-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="2de7b-112">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2de7b-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="2de7b-113">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="2de7b-114">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="2de7b-115">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="2de7b-116">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="2de7b-117">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="2de7b-118">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="2de7b-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="2de7b-119">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="2de7b-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="2de7b-120">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="2de7b-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="2de7b-121">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="2de7b-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2de7b-122">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2de7b-123">Escolha "nuget.org" como a Origem do pacote, selecione a guia Procurar, pesquise por **Microsoft.ML**, selecione o pacote na lista e escolha o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="2de7b-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="2de7b-124">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="2de7b-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="2de7b-125">Instalar o **Pacote do Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="2de7b-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="2de7b-126">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2de7b-127">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="2de7b-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="2de7b-128">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="2de7b-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="2de7b-129">Adicionar um modelo ao projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2de7b-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="2de7b-130">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="2de7b-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="2de7b-131">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="2de7b-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="2de7b-132">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="2de7b-133">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="2de7b-133">Create data models</span></span>

<span data-ttu-id="2de7b-134">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="2de7b-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="2de7b-135">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="2de7b-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="2de7b-136">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="2de7b-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="2de7b-137">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="2de7b-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="2de7b-138">Digite "DataModels" e aperte **Enter**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="2de7b-139">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="2de7b-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="2de7b-140">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2de7b-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="2de7b-141">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-141">Then, select the **Add** button.</span></span> <span data-ttu-id="2de7b-142">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2de7b-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2de7b-143">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="2de7b-144">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs:**</span><span class="sxs-lookup"><span data-stu-id="2de7b-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

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

4. <span data-ttu-id="2de7b-145">No Solution Explorer, clique com o botão direito do mouse no diretório *DataModels* e, em seguida, **selecione Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="2de7b-146">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="2de7b-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="2de7b-147">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="2de7b-147">Then, select the Add button.</span></span> <span data-ttu-id="2de7b-148">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2de7b-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="2de7b-149">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="2de7b-150">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="2de7b-151">`SentimentPrediction` herda de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="2de7b-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="2de7b-152">Isso torna mais fácil ver os dados originais na propriedade `SentimentText` junto com a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="2de7b-153">Registrar PredictionEnginePool para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="2de7b-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="2de7b-154">Para fazer uma única previsão, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)você tem que criar um .</span><span class="sxs-lookup"><span data-stu-id="2de7b-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="2de7b-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)não é seguro para rosca.</span><span class="sxs-lookup"><span data-stu-id="2de7b-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2de7b-156">Além disso, você tem que criar uma instância dele em todos os lugares necessários dentro de sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2de7b-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="2de7b-157">À medida que sua aplicação cresce, esse processo pode se tornar incontrolável.</span><span class="sxs-lookup"><span data-stu-id="2de7b-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="2de7b-158">Para melhorar o desempenho e a segurança dos fios, use uma combinação de injeção de dependência e o `PredictionEnginePool` serviço, que cria um de [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objetos para uso em toda a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="2de7b-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="2de7b-159">O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="2de7b-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="2de7b-160">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="2de7b-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="2de7b-161">Adicione o seguinte código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="2de7b-162">Em um alto nível, esse código inicializa os objetos e serviços automaticamente para uso posterior quando solicitado pelo aplicativo, em vez de ter que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="2de7b-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="2de7b-163">Modelos de aprendizado de máquina não são estáticos.</span><span class="sxs-lookup"><span data-stu-id="2de7b-163">Machine learning models are not static.</span></span> <span data-ttu-id="2de7b-164">À medida que novos dados de treinamento se tornam disponíveis, o modelo é retreinado e reimplantado.</span><span class="sxs-lookup"><span data-stu-id="2de7b-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="2de7b-165">Uma maneira de colocar a versão mais recente do modelo em seu aplicativo é reimplantar todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="2de7b-166">No entanto, isso introduz o tempo de inatividade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-166">However, this introduces application downtime.</span></span> <span data-ttu-id="2de7b-167">O `PredictionEnginePool` serviço fornece um mecanismo para recarregar um modelo atualizado sem retirar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="2de7b-168">Defina `watchForChanges` o `true`parâmetro para `PredictionEnginePool` , [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) e as iniciações a que ouve o sistema de arquivos alterar notificações e levanta eventos quando há uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="2de7b-169">Isso solicita `PredictionEnginePool` a recarga automática do modelo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="2de7b-170">O modelo é `modelName` identificado pelo parâmetro para que mais de um modelo por aplicativo possa ser recarregado após a alteração.</span><span class="sxs-lookup"><span data-stu-id="2de7b-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="2de7b-171">Alternativamente, você pode `FromUri` usar o método ao trabalhar com modelos armazenados remotamente.</span><span class="sxs-lookup"><span data-stu-id="2de7b-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="2de7b-172">Em vez de assistir `FromUri` a eventos alterados por arquivos, pesquisa o local remoto para alterações.</span><span class="sxs-lookup"><span data-stu-id="2de7b-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="2de7b-173">O intervalo de votação é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="2de7b-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="2de7b-174">Você pode aumentar ou diminuir o intervalo de votação com base nos requisitos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="2de7b-175">Na amostra de código `PredictionEnginePool` abaixo, as pesquisas o modelo armazenado no URI especificado a cada minuto.</span><span class="sxs-lookup"><span data-stu-id="2de7b-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="2de7b-176">Criar o Controlador de Previsão</span><span class="sxs-lookup"><span data-stu-id="2de7b-176">Create Predict controller</span></span>

<span data-ttu-id="2de7b-177">Para processar as solicitações HTTP de entrada, crie um controlador.</span><span class="sxs-lookup"><span data-stu-id="2de7b-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="2de7b-178">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="2de7b-179">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2de7b-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="2de7b-180">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="2de7b-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="2de7b-181">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="2de7b-181">Then, select the Add button.</span></span> <span data-ttu-id="2de7b-182">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2de7b-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="2de7b-183">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="2de7b-184">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="2de7b-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

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

<span data-ttu-id="2de7b-185">Esse código atribui o `PredictionEnginePool` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="2de7b-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="2de7b-186">Em seguida, `Predict` o `Post` método `PredictionEnginePool` do controlador usa `SentimentAnalysisModel` o para `Startup` fazer previsões usando o registrado na classe e retorna os resultados de volta ao usuário se for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2de7b-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="2de7b-187">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="2de7b-187">Test web API locally</span></span>

<span data-ttu-id="2de7b-188">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="2de7b-189">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de7b-189">Run the application.</span></span>
1. <span data-ttu-id="2de7b-190">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="2de7b-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="2de7b-191">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="2de7b-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="2de7b-192">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="2de7b-192">Congratulations!</span></span> <span data-ttu-id="2de7b-193">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API Web.</span><span class="sxs-lookup"><span data-stu-id="2de7b-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2de7b-194">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2de7b-194">Next Steps</span></span>

- [<span data-ttu-id="2de7b-195">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="2de7b-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
