---
title: Treinar um modelo de machine learning usando validação cruzada
description: Saiba como usar a validação cruzada para criar modelos de aprendizado de máquina mais robustos no ML.NET. A validação cruzada é uma técnica de avaliação de modelo e treinamento que divide os dados em várias partições e treina vários algoritmos nessas partições.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: f29103d0cf59cdec10a641b05ce359bf95c01ccd
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169053"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="e1a43-104">Treinar um modelo de machine learning usando validação cruzada</span><span class="sxs-lookup"><span data-stu-id="e1a43-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="e1a43-105">Saiba como usar a validação cruzada para treinar modelos de aprendizado de máquina mais robustos no ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e1a43-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="e1a43-106">A validação cruzada é uma técnica de avaliação de modelo e treinamento que divide os dados em várias partições e treina vários algoritmos nessas partições.</span><span class="sxs-lookup"><span data-stu-id="e1a43-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="e1a43-107">Essa técnica melhora a robustez do modelo mantendo os dados do processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="e1a43-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="e1a43-108">Além de melhorar o desempenho em observações não vistas, em ambientes com restrições de dados, pode ser uma ferramenta eficiente para treinar modelos com um conjunto de dados menor.</span><span class="sxs-lookup"><span data-stu-id="e1a43-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="e1a43-109">Os dados e o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="e1a43-109">The data and data model</span></span>

<span data-ttu-id="e1a43-110">Considerando os dados de um arquivo que tem o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="e1a43-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="e1a43-111">Os dados podem ser modelados por uma classe como `HousingData` e carregados em uma [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="e1a43-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="prepare-the-data"></a><span data-ttu-id="e1a43-112">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="e1a43-112">Prepare the data</span></span>

<span data-ttu-id="e1a43-113">Pré-processe os dados antes de usá-lo para criar o modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="e1a43-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="e1a43-114">Neste exemplo, as colunas `Size` e `HistoricalPrices` são combinadas em um único vetor de recurso, que é enviado como saída para uma nova coluna chamada `Features` usando o método [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*).</span><span class="sxs-lookup"><span data-stu-id="e1a43-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="e1a43-115">Além de obter os dados no formato esperado por algoritmos do ML.NET, concatenar as colunas otimiza as operações subsequentes no pipeline, aplicando a operação uma vez para a coluna concatenada, em vez de a cada uma das colunas separadas.</span><span class="sxs-lookup"><span data-stu-id="e1a43-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="e1a43-116">Depois que as colunas são combinadas em um único vetor, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) é aplicado à coluna `Features` para obter `Size` e `HistoricalPrices` no mesmo intervalo entre 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="e1a43-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator = 
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="e1a43-117">Treinar modelo com validação cruzada</span><span class="sxs-lookup"><span data-stu-id="e1a43-117">Train model with cross validation</span></span>

<span data-ttu-id="e1a43-118">Depois que os dados foram pré-processados, é hora de treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="e1a43-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="e1a43-119">Primeiro, selecione o algoritmo que melhor se alinha com a tarefa de aprendizado de máquina a ser executada.</span><span class="sxs-lookup"><span data-stu-id="e1a43-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="e1a43-120">Como o valor previsto é um valor contínuo numericamente, a tarefa é regressão.</span><span class="sxs-lookup"><span data-stu-id="e1a43-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="e1a43-121">Um dos algoritmos de regressão implementados do ML.NET é o [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).</span><span class="sxs-lookup"><span data-stu-id="e1a43-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="e1a43-122">Para treinar o modelo com validação cruzada, use o método [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*).</span><span class="sxs-lookup"><span data-stu-id="e1a43-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="e1a43-123">Embora este exemplo use um modelo de regressão linear, CrossValidate é aplicável a todas as outra tarefas aprendizado de máquina do ML.NET, exceto por detecção de anomalias.</span><span class="sxs-lookup"><span data-stu-id="e1a43-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="e1a43-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) executa as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="e1a43-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="e1a43-125">Particiona os dados em um número de partições iguais ao valor especificado no parâmetro `numberOfFolds`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="e1a43-126">O resultado de cada partição é um objeto [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).</span><span class="sxs-lookup"><span data-stu-id="e1a43-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="e1a43-127">Um modelo é treinado em cada uma das partições usando o estimador de algoritmo de aprendizado de máquina no conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="e1a43-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="e1a43-128">O desempenho de cada modelo é avaliado usando o método [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) no conjunto de dados de teste.</span><span class="sxs-lookup"><span data-stu-id="e1a43-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="e1a43-129">O modelo, juntamente com as métricas, é retornado para cada um dos modelos.</span><span class="sxs-lookup"><span data-stu-id="e1a43-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="e1a43-130">O resultado armazenado em `cvResults` é uma coleção de objetos [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601).</span><span class="sxs-lookup"><span data-stu-id="e1a43-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="e1a43-131">Esse objeto inclui o modelo treinado, bem como as métricas acessíveis das propriedades [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) e [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e1a43-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="e1a43-132">Neste exemplo, a propriedade `Model` é do tipo [`ITransformer`](xref:Microsoft.ML.ITransformer) e a propriedade `Metrics` é do tipo [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="e1a43-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="evaluate-the-model"></a><span data-ttu-id="e1a43-133">Avaliar o modelo</span><span class="sxs-lookup"><span data-stu-id="e1a43-133">Evaluate the model</span></span>

<span data-ttu-id="e1a43-134">As métricas para os diferentes modelos treinados podem ser acessadas por meio de propriedade `Metrics` do objeto [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) individual.</span><span class="sxs-lookup"><span data-stu-id="e1a43-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="e1a43-135">Neste caso, a [métrica de R ao quadrado](https://en.wikipedia.org/wiki/Coefficient_of_determination) é acessada e armazenada na variável `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="e1a43-136">Se você inspecionar o conteúdo da variável `rSquared`, a saída deverá ter cinco valores que variam de 0 a 1, em que estar mais perto de 1 é melhor.</span><span class="sxs-lookup"><span data-stu-id="e1a43-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="e1a43-137">Usando métricas como R ao quadrado, selecione os modelos do melhor ao pior desempenho.</span><span class="sxs-lookup"><span data-stu-id="e1a43-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="e1a43-138">Em seguida, selecione o melhor modelo com o qual fazer previsões ou executar operações adicionais.</span><span class="sxs-lookup"><span data-stu-id="e1a43-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
