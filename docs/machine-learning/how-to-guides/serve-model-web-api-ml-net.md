---
title: Implantar um modelo em uma API Web do ASP.NET Core
description: Usar um modelo de Machine Learning para Análise de Sentimento com ML.NET pela internet usando o ASP.NET Web API
ms.date: 09/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 42f8d51f2547cd6f3240a05420b2da10b7cf52e3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179387"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="2f2bf-103">Implantar um modelo em uma API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2f2bf-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="2f2bf-104">Saiba como fornecer um modelo de machine Learning do ML.NET previamente treinado na Web usando uma API Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="2f2bf-105">Veicular um modelo por uma API Web habilita previsões por meio de métodos HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="2f2bf-106">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f2bf-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2f2bf-107">Prerequisites</span></span>

- <span data-ttu-id="2f2bf-108">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="2f2bf-109">Powershell.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-109">Powershell.</span></span>
- <span data-ttu-id="2f2bf-110">Modelo previamente treinado.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-110">Pre-trained model.</span></span> <span data-ttu-id="2f2bf-111">Use o [tutorial de Análise de Sentimento do ML.NET](../tutorials/sentiment-analysis.md) para criar seu próprio modelo ou baixe este [modelo de machine learning de análise de sentimento pré-treinado](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="2f2bf-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="2f2bf-112">Criar o projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2f2bf-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="2f2bf-113">Abra o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="2f2bf-114">No menu, selecione **Arquivo > Novo > Projeto**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="2f2bf-115">Na caixa de diálogo Novo projeto, selecione o nó **Visual C#** seguido pelo nó **Web**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="2f2bf-116">Em seguida, selecione o modelo de projeto **Aplicativo ASP.NET Core Web**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="2f2bf-117">Na caixa de texto **Nome**, digite "SentimentAnalysisWebAPI" e, depois, selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="2f2bf-118">Na janela que exibe os diferentes tipos de projetos do ASP.NET Core, selecione **API** e, depois, o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="2f2bf-119">Crie um diretório chamado *MLModels* em seu projeto para salvar os arquivos de modelo de machine learning criados previamente:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="2f2bf-120">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="2f2bf-121">Digite "MLModels" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="2f2bf-122">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2f2bf-123">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2f2bf-124">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="2f2bf-125">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="2f2bf-126">Instalar o **Pacote do Nuget Microsoft.Extensions.ML**:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="2f2bf-127">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2f2bf-128">Escolha "nuget.org" como a origem do pacote, selecione a guia Procurar, pesquise **Microsoft.Extensions.ML**, selecione o pacote na lista e selecione o botão Instalar.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="2f2bf-129">Selecione o botão **OK** na caixa de diálogo **Visualizar alterações** e, depois, o botão **Aceito** na caixa de diálogo Aceitação da Licença, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="2f2bf-130">Adicionar um modelo ao projeto da API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2f2bf-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="2f2bf-131">Copie seu modelo previamente criado para o diretório *MLModels*</span><span class="sxs-lookup"><span data-stu-id="2f2bf-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="2f2bf-132">No Gerenciador de Soluções, clique com o botão direito do mouse no arquivo zip e selecione Propriedades.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="2f2bf-133">Em Avançado, altere o valor de Copiar para diretório de saída para Copiar se for mais novo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="2f2bf-134">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="2f2bf-134">Create data models</span></span>

<span data-ttu-id="2f2bf-135">Você precisa criar algumas classes para os dados e previsões de entrada.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="2f2bf-136">Adicione uma nova classe ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="2f2bf-137">Crie um diretório chamado *DataModels* em seu projeto para salvar os modelos de dados:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="2f2bf-138">No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione Adicionar > Nova Pasta.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="2f2bf-139">Digite "DataModels" e pressione **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="2f2bf-140">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione Adicionar > Novo item.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="2f2bf-141">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="2f2bf-142">Em seguida, selecione o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-142">Then, select the **Add** button.</span></span> <span data-ttu-id="2f2bf-143">O arquivo *SentimentData.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2f2bf-144">Adicione a seguinte instrução using na parte superior do *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="2f2bf-145">Remova a definição de classe existente e adicione o seguinte código ao arquivo **SentimentData.cs**:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
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

4. <span data-ttu-id="2f2bf-146">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *DataModels* e selecione **Adicionar > Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="2f2bf-147">Na caixa de diálogo **Adicionar Novo Item**, selecione **Classe** e altere o campo **Nome** para *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="2f2bf-148">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-148">Then, select the Add button.</span></span> <span data-ttu-id="2f2bf-149">O arquivo *SentimentPrediction.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="2f2bf-150">Adicione a seguinte instrução "using" na parte superior do *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="2f2bf-151">Remova a definição de classe existente e adicione o seguinte código ao arquivo *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="2f2bf-152">`SentimentPrediction` herda de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="2f2bf-153">Isso torna mais fácil ver os dados originais na propriedade `SentimentText` junto com a saída gerada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="2f2bf-154">Registrar PredictionEnginePool para uso no aplicativo</span><span class="sxs-lookup"><span data-stu-id="2f2bf-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="2f2bf-155">Para fazer uma única previsão, você precisa criar um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="2f2bf-155">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="2f2bf-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-156">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2f2bf-157">Além disso, você precisa criar uma instância dela em qualquer lugar em que seja necessário dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-157">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="2f2bf-158">À medida que seu aplicativo cresce, esse processo pode se tornar não gerenciável.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-158">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="2f2bf-159">Para melhorar o desempenho e a segurança do thread, use uma combinação de injeção de dependência e o serviço `PredictionEnginePool`, que cria um [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de objetos [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) para uso em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-159">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="2f2bf-160">O link a seguir fornece mais informações se você quiser saber mais sobre [injeção de dependência em ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="2f2bf-160">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="2f2bf-161">Abra a classe *Startup.cs* e adicione a seguinte instrução using à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-161">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="2f2bf-162">Adicione o seguinte código ao método *ConfigureServices*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-162">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    }
    ```

<span data-ttu-id="2f2bf-163">Em um alto nível, esse código inicializa os objetos e os serviços automaticamente para uso posterior quando solicitado pelo aplicativo em vez de ter que fazê-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-163">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span> 

<span data-ttu-id="2f2bf-164">Os modelos de aprendizado de máquina não são estáticos.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-164">Machine learning models are not static.</span></span> <span data-ttu-id="2f2bf-165">À medida que novos dados de treinamento ficam disponíveis, o modelo é retreinado e reimplantado.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-165">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="2f2bf-166">Uma maneira de obter a versão mais recente do modelo em seu aplicativo é reimplantar o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-166">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="2f2bf-167">No entanto, isso introduz o tempo de inatividade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-167">However, this introduces application downtime.</span></span> <span data-ttu-id="2f2bf-168">O serviço `PredictionEnginePool` fornece um mecanismo para recarregar um modelo atualizado sem levar seu aplicativo para baixo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-168">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span> 

<span data-ttu-id="2f2bf-169">Defina o parâmetro `watchForChanges` como `true`, e o `PredictionEnginePool` inicia um [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) que escuta as notificações de alteração do sistema de arquivos e gera eventos quando há uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-169">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="2f2bf-170">Isso solicita que o `PredictionEnginePool` recarregue o modelo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-170">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="2f2bf-171">O modelo é identificado pelo parâmetro `modelName` para que mais de um modelo por aplicativo possa ser recarregado após a alteração.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-171">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span> 

> [!TIP]
> <span data-ttu-id="2f2bf-172">Como alternativa, você pode usar o método `FromUri` ao trabalhar com modelos armazenados remotamente.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-172">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="2f2bf-173">Em vez de observar os eventos de alteração de arquivo, `FromUri` pesquisa o local remoto em busca de alterações.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-173">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="2f2bf-174">O padrão do intervalo de sondagem é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-174">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="2f2bf-175">Você pode aumentar ou diminuir o intervalo de sondagem com base nos requisitos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-175">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="2f2bf-176">No exemplo de código abaixo, o `PredictionEnginePool` sonda o modelo armazenado no URI especificado a cada minuto.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-176">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>    
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel", 
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip", 
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="2f2bf-177">Criar o Controlador de Previsão</span><span class="sxs-lookup"><span data-stu-id="2f2bf-177">Create Predict controller</span></span>

<span data-ttu-id="2f2bf-178">Para processar as solicitações HTTP de entrada, crie um controlador.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-178">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="2f2bf-179">No Gerenciador de Soluções, clique com o botão direito do mouse no diretório *Controladores* e selecione **Adicionar > Controlador**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-179">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="2f2bf-180">Na caixa de diálogo **Adicionar Novo Item**, selecione **Controlador de API Vazio** e, então, **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-180">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="2f2bf-181">No prompt, altere o campo do **Nome do Controlador** para *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-181">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="2f2bf-182">Em seguida, selecione o botão Adicionar.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-182">Then, select the Add button.</span></span> <span data-ttu-id="2f2bf-183">O arquivo *PredictController.cs* é aberto no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-183">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="2f2bf-184">Adicione a seguinte instrução using na parte superior do *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-184">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="2f2bf-185">Remova a definição de classe existente e adicione o seguinte código ao arquivo *PredictController.cs*:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-185">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
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

<span data-ttu-id="2f2bf-186">Esse código atribui o `PredictionEnginePool` passando-o para o construtor do controlador que você obtém por meio da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-186">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="2f2bf-187">Em seguida, o método `Post` do controlador `Predict` usa o `PredictionEnginePool` para fazer previsões usando o `SentimentAnalysisModel` registrado na classe `Startup` e retorna os resultados de volta para o usuário, se for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-187">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="2f2bf-188">Testar a API Web localmente</span><span class="sxs-lookup"><span data-stu-id="2f2bf-188">Test web API locally</span></span>

<span data-ttu-id="2f2bf-189">Depois que tudo estiver definido, é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-189">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="2f2bf-190">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-190">Run the application.</span></span>
1. <span data-ttu-id="2f2bf-191">Abra o Powershell e digite o seguinte código, em que PORT é a porta em que seu aplicativo está escutando.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-191">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="2f2bf-192">Se houver êxito, a saída deverá ser semelhante ao texto abaixo:</span><span class="sxs-lookup"><span data-stu-id="2f2bf-192">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="2f2bf-193">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="2f2bf-193">Congratulations!</span></span> <span data-ttu-id="2f2bf-194">Você usou com êxito seu modelo para fazer previsões pela internet usando um ASP.NET Core API Web.</span><span class="sxs-lookup"><span data-stu-id="2f2bf-194">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f2bf-195">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2f2bf-195">Next Steps</span></span>

- [<span data-ttu-id="2f2bf-196">Implantar no Azure</span><span class="sxs-lookup"><span data-stu-id="2f2bf-196">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
