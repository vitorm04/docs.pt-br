---
title: Salvar e carregar modelos treinados
description: Saiba como salvar e carregar modelos treinados
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977002"
---
# <a name="save-and-load-trained-models"></a><span data-ttu-id="581ad-103">Salvar e carregar modelos treinados</span><span class="sxs-lookup"><span data-stu-id="581ad-103">Save and load trained models</span></span>

<span data-ttu-id="581ad-104">Saiba como salvar e carregar modelos treinados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="581ad-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="581ad-105">Em todo o processo de criação de modelo, um modelo reside na memória e é acessível em todo o ciclo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="581ad-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="581ad-106">No entanto, depois que o aplicativo terminar a execução, se o modelo não for salvo em algum lugar local ou remotamente, ele não ficará mais acessível.</span><span class="sxs-lookup"><span data-stu-id="581ad-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="581ad-107">Normalmente, os modelos são usados em algum momento após o treinamento em outros aplicativos para inferência de tipos ou novo treinamento.</span><span class="sxs-lookup"><span data-stu-id="581ad-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="581ad-108">Assim, é importante armazenar o modelo.</span><span class="sxs-lookup"><span data-stu-id="581ad-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="581ad-109">Salve e carregue modelos usando as etapas descritas nas seções subsequentes deste documento ao usar pipelines de treinamento de modelo e preparação de dados como os detalhados abaixo.</span><span class="sxs-lookup"><span data-stu-id="581ad-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="581ad-110">Embora este exemplo use um modelo de regressão linear, o mesmo processo se aplica a outros algoritmos do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="581ad-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

<span data-ttu-id="581ad-111">Porque a maioria dos pipelines de preparação de dados e modelos herda o mesmo conjunto de classes, as assinaturas do método salvar e carregar para esses componentes são iguais.</span><span class="sxs-lookup"><span data-stu-id="581ad-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="581ad-112">Dependendo do seu caso de uso, você pode tanto combinar o pipeline de preparação de dados e o modelo em um único [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) que geraria um único [`ITransformer`](xref:Microsoft.ML.ITransformer) quanto separá-los, criando um [`ITransformer`](xref:Microsoft.ML.ITransformer) separado para cada um.</span><span class="sxs-lookup"><span data-stu-id="581ad-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="581ad-113">Salvar um modelo localmente</span><span class="sxs-lookup"><span data-stu-id="581ad-113">Save a model locally</span></span>

<span data-ttu-id="581ad-114">Ao salvar um modelo, você precisa de dois itens:</span><span class="sxs-lookup"><span data-stu-id="581ad-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="581ad-115">O [`ITransformer`](xref:Microsoft.ML.ITransformer) do modelo.</span><span class="sxs-lookup"><span data-stu-id="581ad-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="581ad-116">O [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) da entrada esperada de [`ITransformer`](xref:Microsoft.ML.ITransformer).</span><span class="sxs-lookup"><span data-stu-id="581ad-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="581ad-117">Depois de treinar o modelo, use o método [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) para salvar o modelo treinado em um arquivo chamado `model.zip` usando o `DataViewSchema` dos dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="581ad-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="581ad-118">Carregar um modelo armazenado localmente</span><span class="sxs-lookup"><span data-stu-id="581ad-118">Load a model stored locally</span></span>

<span data-ttu-id="581ad-119">Os modelos armazenados localmente podem ser usados em outros processos ou aplicativos, como `ASP.NET Core` e `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="581ad-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="581ad-120">Veja os artigos de instruções [Usar ML.NET na API Web](./serve-model-web-api-ml-net.md) e [Implantar aplicativo Web sem servidor do ML.NET](./serve-model-serverless-azure-functions-ml-net.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="581ad-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="581ad-121">Em um aplicativo ou processo separado, use o método [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) juntamente com o caminho do arquivo para obter o modelo treinado em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="581ad-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="581ad-122">Carregar um modelo armazenado remotamente</span><span class="sxs-lookup"><span data-stu-id="581ad-122">Load a model stored remotely</span></span>

<span data-ttu-id="581ad-123">Para carregar os pipelines de preparação de dados e modelos armazenados em um local remoto em seu aplicativo, use [`Stream`](xref:System.IO.Stream) em vez de um caminho de arquivo no método [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*).</span><span class="sxs-lookup"><span data-stu-id="581ad-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="581ad-124">Trabalhando com pipelines de modelo e preparação de dados separados</span><span class="sxs-lookup"><span data-stu-id="581ad-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="581ad-125">Trabalhar com pipelines de treinamento de modelo e preparação de dados separados é opcional.</span><span class="sxs-lookup"><span data-stu-id="581ad-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="581ad-126">A separação de pipelines facilita a inspeção dos parâmetros do modelo aprendido.</span><span class="sxs-lookup"><span data-stu-id="581ad-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="581ad-127">Para obter previsões, é mais fácil de salvar e carregar um único pipeline que inclua as operações de treinamento de modelo e preparação de dados.</span><span class="sxs-lookup"><span data-stu-id="581ad-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="581ad-128">Ao trabalhar com modelos e pipelines de preparação de dados separados, aplica-se o mesmo processo que o para pipelines únicos, exceto que agora os dois pipelines precisam ser salvos e carregados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="581ad-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="581ad-129">Dados pipelines de treinamento de modelo e preparação de dados separados:</span><span class="sxs-lookup"><span data-stu-id="581ad-129">Given separate data preparation and model training pipelines:</span></span>

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="581ad-130">Salve o pipeline de preparação de dados e o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="581ad-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="581ad-131">Para salvar o pipeline de preparação de dados e o modelo treinado, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="581ad-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="581ad-132">Carregar o pipeline de preparação de dados e o modelo treinado</span><span class="sxs-lookup"><span data-stu-id="581ad-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="581ad-133">Em um processo ou aplicativo separado, carregue o modelo treinado e o pipeline de preparação de dados simultaneamente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="581ad-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
