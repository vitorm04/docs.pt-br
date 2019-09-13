---
title: Treinar e avaliar um modelo
description: Saiba como criar modelos de machine learning, coletar métricas e medir o desempenho com o ML.NET. Um modelo de machine learning identifica padrões nos dados de treinamento para fazer previsões usando novos dados.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: fc735f28bad91b9714d7e6bf2a9c7c620acacc4d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929340"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="5032e-104">Treinar e avaliar um modelo</span><span class="sxs-lookup"><span data-stu-id="5032e-104">Train and evaluate a model</span></span>

<span data-ttu-id="5032e-105">Saiba como criar modelos de machine learning, coletar métricas e medir o desempenho com o ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5032e-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="5032e-106">Embora este exemplo prepare um modelo de regressão, os conceitos são aplicáveis à maioria dos outros algoritmos.</span><span class="sxs-lookup"><span data-stu-id="5032e-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="5032e-107">Dividir dados para treinamento e teste</span><span class="sxs-lookup"><span data-stu-id="5032e-107">Split data for training and testing</span></span>

<span data-ttu-id="5032e-108">A meta de um modelo de machine learning é identificar padrões nos dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="5032e-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="5032e-109">Esses padrões são usados para fazer previsões usando novos dados.</span><span class="sxs-lookup"><span data-stu-id="5032e-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="5032e-110">Os dados podem ser modelados por uma classe como `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="5032e-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="5032e-111">Considerando os dados a seguir, que são carregados em uma [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="5032e-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
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
    },
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
```

<span data-ttu-id="5032e-112">Use o método [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) para dividir os dados em conjuntos de treinamento e de testes.</span><span class="sxs-lookup"><span data-stu-id="5032e-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="5032e-113">O resultado será um objeto [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) que contém dois membros [`IDataView`](xref:Microsoft.ML.IDataView), um para o conjunto de treinamento e outro para o conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="5032e-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="5032e-114">O percentual de divisão de dados é determinado pelo parâmetro `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="5032e-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="5032e-115">O snippet a seguir está mantendo 20% dos dados originais para o conjunto de teste.</span><span class="sxs-lookup"><span data-stu-id="5032e-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="5032e-116">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="5032e-116">Prepare the data</span></span>

<span data-ttu-id="5032e-117">Os dados precisam ser pré-processados antes do treinamento de um modelo de machine learning.</span><span class="sxs-lookup"><span data-stu-id="5032e-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="5032e-118">Encontre mais informações sobre preparação de dados no [artigo de instruções de preparação de dados](prepare-data-ml-net.md), bem como na [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="5032e-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="5032e-119">Algoritmos do ML.NET têm restrições nos tipos de coluna de entrada.</span><span class="sxs-lookup"><span data-stu-id="5032e-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="5032e-120">Além disso, os valores padrão são usados para nomes de coluna de entrada e saída quando nenhum valor é especificado.</span><span class="sxs-lookup"><span data-stu-id="5032e-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="5032e-121">Trabalhando com tipos de coluna esperados</span><span class="sxs-lookup"><span data-stu-id="5032e-121">Working with expected column types</span></span>

<span data-ttu-id="5032e-122">Os algoritmos de aprendizado de máquina no ML.NET esperam um vetor flutuante de tamanho conhecido como entrada.</span><span class="sxs-lookup"><span data-stu-id="5032e-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="5032e-123">Aplicar o atributo [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) ao modelo de dados quando todos os dados já estão em um formato numérico e destinam-se a serem processados em conjunto (ou seja, pixels da imagem).</span><span class="sxs-lookup"><span data-stu-id="5032e-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="5032e-124">Se os dados não forem todos numéricos e você desejar aplicar transformações de dados diferentes a cada uma das colunas individualmente, use o método [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) depois de todas as colunas terem sido processadas para combinar todas as colunas individuais em um vetor de recurso único que é enviado como saída para uma nova coluna.</span><span class="sxs-lookup"><span data-stu-id="5032e-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="5032e-125">O snippet a seguir combina as colunas `Size` e `HistoricalPrices` em um vetor de recurso único que é a saída para uma nova coluna chamada `Features`.</span><span class="sxs-lookup"><span data-stu-id="5032e-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="5032e-126">Porque há uma diferença em escalas, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) é aplicado à coluna `Features` para normalizar os dados.</span><span class="sxs-lookup"><span data-stu-id="5032e-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="5032e-127">Trabalhando com nomes de coluna padrão</span><span class="sxs-lookup"><span data-stu-id="5032e-127">Working with default column names</span></span>

<span data-ttu-id="5032e-128">Algoritmos do ML.NET usam nomes de coluna padrão quando nenhum é especificado.</span><span class="sxs-lookup"><span data-stu-id="5032e-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="5032e-129">Todos os treinadores têm um parâmetro chamado `featureColumnName` para as entradas do algoritmo e, quando aplicável, também têm um parâmetro para o valor esperado chamado `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="5032e-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="5032e-130">Por padrão, esses valores são `Features` e `Label`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5032e-130">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="5032e-131">Ao usar o método [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) durante o pré-processamento para criar uma nova coluna chamada `Features`, não é necessário especificar o nome da coluna de recurso nos parâmetros do algoritmo, já que ela já existe na `IDataView` pré-processada.</span><span class="sxs-lookup"><span data-stu-id="5032e-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="5032e-132">A coluna de rótulo é `CurrentPrice`, porém, como o atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) é usado no modelo de dados, o ML.NET renomeia a coluna `CurrentPrice` como `Label`, o que elimina a necessidade de fornecer o parâmetro `labelColumnName` para o estimador de algoritmo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="5032e-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="5032e-133">Se você não quiser usar os nomes de coluna padrão, passe os nomes das colunas de rótulo e de recurso como parâmetros ao definir o estimador do algoritmo de aprendizado de máquina como demonstrado pelo snippet subsequente:</span><span class="sxs-lookup"><span data-stu-id="5032e-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="5032e-134">Treinar o modelo de machine learning</span><span class="sxs-lookup"><span data-stu-id="5032e-134">Train the machine learning model</span></span>

<span data-ttu-id="5032e-135">Depois que os dados tiverem sido pré-processados, use o método [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) para treinar o modelo de machine learning com o algoritmo de regressão [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).</span><span class="sxs-lookup"><span data-stu-id="5032e-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="5032e-136">Extrair parâmetros do modelo</span><span class="sxs-lookup"><span data-stu-id="5032e-136">Extract model parameters</span></span>

<span data-ttu-id="5032e-137">Depois que o modelo tiver sido treinado, extraia o [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) aprendido para inspeção ou novo treinamento.</span><span class="sxs-lookup"><span data-stu-id="5032e-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="5032e-138">O [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) fornece os desvios e os coeficientes aprendidos ou os pesos do modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="5032e-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="5032e-139">Outros modelos têm parâmetros específicos para suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="5032e-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="5032e-140">Por exemplo, o [algoritmo K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) coloca dados em cluster baseado em centroides e o [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contém uma propriedade que armazena esses centroides aprendidos.</span><span class="sxs-lookup"><span data-stu-id="5032e-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="5032e-141">Para saber mais, acesse a [Documentação da API `Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) e procure classes que contenham `ModelParameters` em seu nome.</span><span class="sxs-lookup"><span data-stu-id="5032e-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="5032e-142">Avaliar a qualidade do modelo</span><span class="sxs-lookup"><span data-stu-id="5032e-142">Evaluate model quality</span></span>

<span data-ttu-id="5032e-143">Para ajudar a escolher o modelo com melhor desempenho, é essencial avaliar seu desempenho nos dados de teste.</span><span class="sxs-lookup"><span data-stu-id="5032e-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="5032e-144">Use o método [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) para medir várias métricas para o modelo treinado.</span><span class="sxs-lookup"><span data-stu-id="5032e-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="5032e-145">O método `Evaluate` produz métricas diferentes dependendo de qual tarefa de aprendizado de máquina foi executada.</span><span class="sxs-lookup"><span data-stu-id="5032e-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="5032e-146">Para obter mais detalhes, acesse a [Documentação da API `Microsoft.ML.Data`](xref:Microsoft.ML.Data) e procure classes que contenham `Metrics` em seu nome.</span><span class="sxs-lookup"><span data-stu-id="5032e-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="5032e-147">No exemplo de código anterior:</span><span class="sxs-lookup"><span data-stu-id="5032e-147">In the previous code sample:</span></span>  

1. <span data-ttu-id="5032e-148">O conjunto de dados de teste é pré-processado usando as transformações de preparação de dados definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5032e-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="5032e-149">O modelo de machine learning treinado é usado para fazer previsões sobre os dados de teste.</span><span class="sxs-lookup"><span data-stu-id="5032e-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="5032e-150">No método `Evaluate`, os valores na coluna `CurrentPrice` do conjunto de dados de teste são comparados com a coluna `Score` das previsões de geradas recentemente para calcular as métricas para a regressão de modelo, uma das quais, R ao quadrado, é armazenada na variável `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="5032e-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="5032e-151">Neste breve exemplo, o R ao quadrado é um número que não está no intervalo de 0 a 1 devido ao tamanho limitado dos dados.</span><span class="sxs-lookup"><span data-stu-id="5032e-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="5032e-152">Em um cenário do mundo real, você deve esperar ver um valor entre 0 e 1.</span><span class="sxs-lookup"><span data-stu-id="5032e-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
