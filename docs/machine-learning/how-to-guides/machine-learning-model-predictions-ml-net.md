---
title: Fazer previsões com um modelo treinado
description: Aprenda a fazer previsões usando um modelo treinado
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977041"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="c26cb-103">Fazer previsões com um modelo treinado</span><span class="sxs-lookup"><span data-stu-id="c26cb-103">Make predictions with a trained model</span></span>

<span data-ttu-id="c26cb-104">Saiba como usar um modelo treinado para fazer previsões</span><span class="sxs-lookup"><span data-stu-id="c26cb-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="c26cb-105">Criar modelo de dados</span><span class="sxs-lookup"><span data-stu-id="c26cb-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="c26cb-106">Dados de entrada</span><span class="sxs-lookup"><span data-stu-id="c26cb-106">Input data</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a><span data-ttu-id="c26cb-107">Dados de saída</span><span class="sxs-lookup"><span data-stu-id="c26cb-107">Output data</span></span>

<span data-ttu-id="c26cb-108">Como os nomes de coluna de entrada `Features` e `Label`, do ML.NET tem nomes padrão para as colunas de valor previsto produzidas por um modelo.</span><span class="sxs-lookup"><span data-stu-id="c26cb-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="c26cb-109">Dependendo da tarefa, o nome pode diferir.</span><span class="sxs-lookup"><span data-stu-id="c26cb-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="c26cb-110">Como o algoritmo usado neste exemplo é um algoritmo de regressão linear, o nome padrão da coluna de saída é `Score`, que é definido pelo atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) na propriedade `PredictedPrice`.</span><span class="sxs-lookup"><span data-stu-id="c26cb-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="c26cb-111">Configurar um pipeline de previsão</span><span class="sxs-lookup"><span data-stu-id="c26cb-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="c26cb-112">Seja fazendo uma previsão única ou em lotes, o pipeline de previsão precisa ser carregado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c26cb-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="c26cb-113">Esse pipeline contém as transformações de pré-processamento de dados, bem como o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="c26cb-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="c26cb-114">O snippet de código a seguir carrega o pipeline de previsão de um arquivo chamado `model.zip`.</span><span class="sxs-lookup"><span data-stu-id="c26cb-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="c26cb-115">Previsão única</span><span class="sxs-lookup"><span data-stu-id="c26cb-115">Single prediction</span></span>

<span data-ttu-id="c26cb-116">Para criar uma previsão única, crie um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) usando o pipeline de previsão carregado.</span><span class="sxs-lookup"><span data-stu-id="c26cb-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="c26cb-117">Em seguida, use o método [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) e passe seus dados de entrada como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c26cb-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="c26cb-118">Observe que usar o método [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) não exige que a entrada seja uma [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c26cb-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="c26cb-119">Isso ocorre porque ele internaliza convenientemente a manipulação do tipo de dados de entrada para que você possa passar um objeto do tipo de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="c26cb-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="c26cb-120">Além disso, uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se não há nenhum valor para ele no momento.</span><span class="sxs-lookup"><span data-stu-id="c26cb-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

<span data-ttu-id="c26cb-121">Se você acessar a propriedade `Score` do objeto `prediction`, deverá obter um valor semelhante ao `150079`.</span><span class="sxs-lookup"><span data-stu-id="c26cb-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="c26cb-122">Várias previsões</span><span class="sxs-lookup"><span data-stu-id="c26cb-122">Multiple predictions</span></span>

<span data-ttu-id="c26cb-123">Considerando os seguintes dados, carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="c26cb-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c26cb-124">Nesse caso, o nome do [`IDataView`](xref:Microsoft.ML.IDataView) é `inputData`.</span><span class="sxs-lookup"><span data-stu-id="c26cb-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="c26cb-125">Uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se que não há valor para ele no momento.</span><span class="sxs-lookup"><span data-stu-id="c26cb-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

<span data-ttu-id="c26cb-126">Em seguida, use o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) para aplicar as transformações de dados e gerar previsões.</span><span class="sxs-lookup"><span data-stu-id="c26cb-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="c26cb-127">Inspecione os valores previstos usando o método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*).</span><span class="sxs-lookup"><span data-stu-id="c26cb-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="c26cb-128">Os valores previstos da coluna de pontuação devem ser semelhantes aos seguintes:</span><span class="sxs-lookup"><span data-stu-id="c26cb-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="c26cb-129">Observação</span><span class="sxs-lookup"><span data-stu-id="c26cb-129">Observation</span></span> | <span data-ttu-id="c26cb-130">Previsão</span><span class="sxs-lookup"><span data-stu-id="c26cb-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="c26cb-131">1</span><span class="sxs-lookup"><span data-stu-id="c26cb-131">1</span></span> | <span data-ttu-id="c26cb-132">144638,2</span><span class="sxs-lookup"><span data-stu-id="c26cb-132">144638.2</span></span> |
| <span data-ttu-id="c26cb-133">2</span><span class="sxs-lookup"><span data-stu-id="c26cb-133">2</span></span> | <span data-ttu-id="c26cb-134">150079,4</span><span class="sxs-lookup"><span data-stu-id="c26cb-134">150079.4</span></span> |
| <span data-ttu-id="c26cb-135">3</span><span class="sxs-lookup"><span data-stu-id="c26cb-135">3</span></span> | <span data-ttu-id="c26cb-136">107789,8</span><span class="sxs-lookup"><span data-stu-id="c26cb-136">107789.8</span></span> |
