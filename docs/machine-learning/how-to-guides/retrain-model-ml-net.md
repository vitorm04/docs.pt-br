---
title: Treinar novamente um modelo
description: Saiba como treinar novamente um modelo no ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976961"
---
# <a name="re-train-a-model"></a><span data-ttu-id="cd4e5-103">Treinar novamente um modelo</span><span class="sxs-lookup"><span data-stu-id="cd4e5-103">Re-train a model</span></span>

<span data-ttu-id="cd4e5-104">Saiba como treinar novamente um modelo de machine learning no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="cd4e5-105">O mundo e os dados ao redor dele mudam a um ritmo constante.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="cd4e5-106">Dessa forma, os modelos precisam mudar e se atualizar também.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="cd4e5-107">O ML.NET fornece funcionalidade para treinar novamente os modelos usando parâmetros de modelo aprendidos como um ponto de partida para criar continuamente com base em experiência anterior em vez de começar do zero toda vez.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="cd4e5-108">Os seguintes algoritmos podem ser treinados novamente do ML.NET:</span><span class="sxs-lookup"><span data-stu-id="cd4e5-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="cd4e5-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="cd4e5-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="cd4e5-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="cd4e5-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="cd4e5-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="cd4e5-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="cd4e5-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="cd4e5-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="cd4e5-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="cd4e5-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="cd4e5-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="cd4e5-119">Carregar modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="cd4e5-119">Load pre-trained model</span></span>

<span data-ttu-id="cd4e5-120">Primeiro, carregue o modelo pré-treinado no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="cd4e5-121">Para saber mais sobre como carregar os pipelines e modelos de treinamento, consulte [salvar e carregar um modelo treinado](save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="cd4e5-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="cd4e5-122">Extrair os parâmetros de modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="cd4e5-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="cd4e5-123">Depois que o modelo é carregado, extraia os parâmetros do modelo aprendido acessando a propriedade [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) do modelo pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="cd4e5-124">O modelo pré-treinado foi treinado usando o modelo de regressão linear [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) que cria um[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) que gera [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="cd4e5-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="cd4e5-125">Esses parâmetros de modelo de regressão linear contêm o desvio aprendido e os pesos ou os coeficientes do modelo.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="cd4e5-126">Esses valores serão usados como ponto de partida para o novo modelo treinado novamente.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="cd4e5-127">Treinar novamente o modelo</span><span class="sxs-lookup"><span data-stu-id="cd4e5-127">Re-train model</span></span>

<span data-ttu-id="cd4e5-128">O processo de treinar novamente um modelo não é diferente daquele de treinar um modelo.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="cd4e5-129">A única diferença é que o método [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*), além dos dados, também utiliza como entrada os parâmetros de modelo aprendidos originais e os usa como um ponto de partida no processo de novo treinamento.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel =
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a><span data-ttu-id="cd4e5-130">Comparar parâmetros de modelo</span><span class="sxs-lookup"><span data-stu-id="cd4e5-130">Compare model parameters</span></span>

<span data-ttu-id="cd4e5-131">Como você saberá se o novo treinamento realmente aconteceu?</span><span class="sxs-lookup"><span data-stu-id="cd4e5-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="cd4e5-132">Uma maneira seria comparar se os parâmetros do modelo treinado novamente são diferentes do modelo original.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="cd4e5-133">O exemplo de código a seguir compara o original em relação os pesos do modelo treinado novamente e envia a saída ao console.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs =
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

<span data-ttu-id="cd4e5-134">A tabela a seguir mostra como poderia ser a saída.</span><span class="sxs-lookup"><span data-stu-id="cd4e5-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="cd4e5-135">Original</span><span class="sxs-lookup"><span data-stu-id="cd4e5-135">Original</span></span> | <span data-ttu-id="cd4e5-136">Treinado novamente</span><span class="sxs-lookup"><span data-stu-id="cd4e5-136">Retrained</span></span> | <span data-ttu-id="cd4e5-137">Diferença</span><span class="sxs-lookup"><span data-stu-id="cd4e5-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="cd4e5-138">33039,86</span><span class="sxs-lookup"><span data-stu-id="cd4e5-138">33039.86</span></span> | <span data-ttu-id="cd4e5-139">56293,76</span><span class="sxs-lookup"><span data-stu-id="cd4e5-139">56293.76</span></span> | <span data-ttu-id="cd4e5-140">-23253,9</span><span class="sxs-lookup"><span data-stu-id="cd4e5-140">-23253.9</span></span> |
| <span data-ttu-id="cd4e5-141">29099,14</span><span class="sxs-lookup"><span data-stu-id="cd4e5-141">29099.14</span></span> | <span data-ttu-id="cd4e5-142">49586,03</span><span class="sxs-lookup"><span data-stu-id="cd4e5-142">49586.03</span></span> | <span data-ttu-id="cd4e5-143">-20486,89</span><span class="sxs-lookup"><span data-stu-id="cd4e5-143">-20486.89</span></span> |
| <span data-ttu-id="cd4e5-144">28938,38</span><span class="sxs-lookup"><span data-stu-id="cd4e5-144">28938.38</span></span> | <span data-ttu-id="cd4e5-145">48609,23</span><span class="sxs-lookup"><span data-stu-id="cd4e5-145">48609.23</span></span> | <span data-ttu-id="cd4e5-146">-19670,85</span><span class="sxs-lookup"><span data-stu-id="cd4e5-146">-19670.85</span></span> |
| <span data-ttu-id="cd4e5-147">30484,02</span><span class="sxs-lookup"><span data-stu-id="cd4e5-147">30484.02</span></span> | <span data-ttu-id="cd4e5-148">53745,43</span><span class="sxs-lookup"><span data-stu-id="cd4e5-148">53745.43</span></span> | <span data-ttu-id="cd4e5-149">-23261,41</span><span class="sxs-lookup"><span data-stu-id="cd4e5-149">-23261.41</span></span> |
