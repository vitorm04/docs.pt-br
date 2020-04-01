---
title: Treinar e avaliar um modelo
description: Saiba como criar modelos de machine learning, coletar métricas e medir o desempenho com o ML.NET. Um modelo de machine learning identifica padrões nos dados de treinamento para fazer previsões usando novos dados.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523851"
---
# <a name="train-and-evaluate-a-model"></a>Treinar e avaliar um modelo

Saiba como criar modelos de machine learning, coletar métricas e medir o desempenho com o ML.NET. Embora este exemplo prepare um modelo de regressão, os conceitos são aplicáveis à maioria dos outros algoritmos.

## <a name="split-data-for-training-and-testing"></a>Dividir dados para treinamento e teste

A meta de um modelo de machine learning é identificar padrões nos dados de treinamento. Esses padrões são usados para fazer previsões usando novos dados.

Os dados podem ser modelados por uma classe como `HousingData`.

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

Dado os seguintes dados [`IDataView`](xref:Microsoft.ML.IDataView)que são carregados em um .

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

Use [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) o método para dividir os dados em conjuntos de trem e teste. O resultado será [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) um objeto [`IDataView`](xref:Microsoft.ML.IDataView) que contém dois membros, um para o conjunto de trens e outro para o conjunto de testes. O percentual de divisão de dados é determinado pelo parâmetro `testFraction`. O snippet a seguir está mantendo 20% dos dados originais para o conjunto de teste.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Preparar os dados

Os dados precisam ser pré-processados antes do treinamento de um modelo de machine learning. Encontre mais informações sobre preparação de dados no [artigo de instruções de preparação de dados](prepare-data-ml-net.md), bem como na [`transforms page`](../resources/transforms.md).

Algoritmos do ML.NET têm restrições nos tipos de coluna de entrada. Além disso, os valores padrão são usados para nomes de coluna de entrada e saída quando nenhum valor é especificado.

### <a name="working-with-expected-column-types"></a>Trabalhando com tipos de coluna esperados

Os algoritmos de aprendizado de máquina no ML.NET esperam um vetor flutuante de tamanho conhecido como entrada. Aplique [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) o atributo ao seu modelo de dados quando todos os dados já estão em formato numérico e se destinam a ser processados em conjunto (ou seja, pixels de imagem).

Se os dados não forem todos numéricos e você quiser aplicar diferentes [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) transformações de dados em cada uma das colunas individualmente, use o método depois que todas as colunas tiverem sido processadas para combinar todas as colunas individuais em um único vetor de recurso que é output para uma nova coluna.

O snippet a seguir combina as colunas `Size` e `HistoricalPrices` em um vetor de recurso único que é a saída para uma nova coluna chamada `Features`. Como há uma diferença de [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) escalas, `Features` é aplicado à coluna para normalizar os dados.

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

### <a name="working-with-default-column-names"></a>Trabalhando com nomes de coluna padrão

Algoritmos do ML.NET usam nomes de coluna padrão quando nenhum é especificado. Todos os treinadores têm um parâmetro chamado `featureColumnName` para as entradas do algoritmo e, quando aplicável, também têm um parâmetro para o valor esperado chamado `labelColumnName`. Por padrão, esses valores são `Features` e `Label`, respectivamente.

Ao usar [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) o método durante o pré-processamento `Features`para criar uma nova coluna chamada, não há necessidade de especificar o `IDataView`nome da coluna de recurso nos parâmetros do algoritmo, uma vez que ele já existe no pré-processado . A coluna `CurrentPrice`de rótulo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) é , mas como o atributo `CurrentPrice` é `Label` usado no modelo de `labelColumnName` dados, ML.NET renomeia a coluna para a qual remove a necessidade de fornecer o parâmetro para o estimador de algoritmo de aprendizagem de máquina.

Se você não quiser usar os nomes de coluna padrão, passe os nomes das colunas de rótulo e de recurso como parâmetros ao definir o estimador do algoritmo de aprendizado de máquina como demonstrado pelo snippet subsequente:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a>Cache de dados

Por padrão, quando os dados são processados, ele é carregado preguiçosamente ou transmitido, o que significa que os treinadores podem carregar os dados do disco e iterar sobre eles várias vezes durante o treinamento. Portanto, o cache é recomendado para conjuntos de dados que se encaixam na memória para reduzir o número de vezes que os dados são carregados a partir do disco. O cache é feito [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) como [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)parte de um uso .

Recomenda-se usar [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) antes de qualquer treinador no oleoduto.

Usando o [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)seguinte [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) , [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) adicionando antes que o treinador cachê os resultados dos estimadores anteriores para uso posterior pelo treinador.

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a>Treinar o modelo de machine learning

Uma vez que os dados são [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) pré-processados, use [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) o método para treinar o modelo de aprendizagem de máquina com o algoritmo de regressão.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Extrair parâmetros do modelo

Após a formação do modelo, [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) extraia o aprendido para inspeção ou retreinamento. O [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) fornecer o viés e os coeficientes aprendidos ou pesos do modelo treinado.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Outros modelos têm parâmetros específicos para suas tarefas. Por exemplo, o [algoritmo K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) coloca dados em cluster baseado em centroides e o [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contém uma propriedade que armazena esses centroides aprendidos. Para saber mais, visite a [ `Microsoft.ML.Trainers` Documentação](xref:Microsoft.ML.Trainers) da `ModelParameters` API e procure por aulas que contenham em seu nome.

## <a name="evaluate-model-quality"></a>Avaliar a qualidade do modelo

Para ajudar a escolher o modelo com melhor desempenho, é essencial avaliar seu desempenho nos dados de teste. Use [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) o método, para medir várias métricas para o modelo treinado.

> [!NOTE]
> O método `Evaluate` produz métricas diferentes dependendo de qual tarefa de aprendizado de máquina foi executada. Para obter mais detalhes, visite a [ `Microsoft.ML.Data` Documentação](xref:Microsoft.ML.Data) da API e procure por classes que contenham `Metrics` em seu nome.

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

No exemplo de código anterior:

1. O conjunto de dados de teste é pré-processado usando as transformações de preparação de dados definidas anteriormente.
2. O modelo de machine learning treinado é usado para fazer previsões sobre os dados de teste.
3. No método `Evaluate`, os valores na coluna `CurrentPrice` do conjunto de dados de teste são comparados com a coluna `Score` das previsões de geradas recentemente para calcular as métricas para a regressão de modelo, uma das quais, R ao quadrado, é armazenada na variável `rSquared`.

> [!NOTE]
> Neste breve exemplo, o R ao quadrado é um número que não está no intervalo de 0 a 1 devido ao tamanho limitado dos dados. Em um cenário do mundo real, você deve esperar ver um valor entre 0 e 1.
