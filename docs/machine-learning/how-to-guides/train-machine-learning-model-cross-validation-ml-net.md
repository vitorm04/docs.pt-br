---
title: Treinar um modelo de machine learning usando validação cruzada
description: Saiba como usar a validação cruzada para criar modelos de aprendizado de máquina mais robustos no ML.NET. A validação cruzada é uma técnica de avaliação de modelo e treinamento que divide os dados em várias partições e treina vários algoritmos nessas partições.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976922"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Treinar um modelo de machine learning usando validação cruzada

Saiba como usar a validação cruzada para treinar modelos de aprendizado de máquina mais robustos no ML.NET.

A validação cruzada é uma técnica de avaliação de modelo e treinamento que divide os dados em várias partições e treina vários algoritmos nessas partições. Essa técnica melhora a robustez do modelo mantendo os dados do processo de treinamento. Além de melhorar o desempenho em observações não vistas, em ambientes com restrições de dados, pode ser uma ferramenta eficiente para treinar modelos com um conjunto de dados menor.

## <a name="the-data-and-data-model"></a>Os dados e o modelo de dados

Considerando os dados de um arquivo que tem o seguinte formato:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Os dados podem ser modelados por uma classe como `HousingData` e carregados em um [`IDataView`](xref:Microsoft.ML.IDataView).

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

## <a name="prepare-the-data"></a>Preparar os dados

Pré-processe os dados antes de usá-lo para criar o modelo de machine learning. Nesta amostra, `Size` as `HistoricalPrices` colunas e colunas são combinadas em um único `Features` vetor de característica, que é a saída para uma nova coluna chamada usando o [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) método. Além de obter os dados no formato esperado por algoritmos do ML.NET, concatenar as colunas otimiza as operações subsequentes no pipeline, aplicando a operação uma vez para a coluna concatenada, em vez de a cada uma das colunas separadas.

Uma vez que as colunas são [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) combinadas em `Features` um `Size` único `HistoricalPrices` vetor, é aplicado à coluna para obter e na mesma faixa entre 0-1.

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

## <a name="train-model-with-cross-validation"></a>Treinar modelo com validação cruzada

Depois que os dados foram pré-processados, é hora de treinar o modelo. Primeiro, selecione o algoritmo que melhor se alinha com a tarefa de aprendizado de máquina a ser executada. Como o valor previsto é um valor contínuo numericamente, a tarefa é regressão. Um dos algoritmos de regressão implementados pela ML.NET é o [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmo. Para treinar o modelo com [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) validação cruzada use o método.

> [!NOTE]
> Embora este exemplo use um modelo de regressão linear, CrossValidate é aplicável a todas as outra tarefas aprendizado de máquina do ML.NET, exceto por detecção de anomalias.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)realiza as seguintes operações:

1. Particiona os dados em um número de partições iguais ao valor especificado no parâmetro `numberOfFolds`. O resultado de cada [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) partição é um objeto.
1. Um modelo é treinado em cada uma das partições usando o estimador de algoritmo de aprendizado de máquina no conjunto de dados de treinamento.
1. O desempenho de cada modelo [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) é avaliado usando o método no conjunto de dados do teste.
1. O modelo, juntamente com as métricas, é retornado para cada um dos modelos.

O resultado `cvResults` armazenado é [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) uma coleção de objetos. Este objeto inclui o modelo treinado, bem como métricas que são acessíveis e [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) propriedades, respectivamente. Nesta amostra, `Model` a propriedade [`ITransformer`](xref:Microsoft.ML.ITransformer) é `Metrics` de tipo [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)e a propriedade é do tipo .

## <a name="evaluate-the-model"></a>Avalie o modelo

As métricas para os diferentes modelos treinados podem ser acessadas através da `Metrics` propriedade do objeto individual. [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) Neste caso, a [métrica de R ao quadrado](https://en.wikipedia.org/wiki/Coefficient_of_determination) é acessada e armazenada na variável `rSquared`.

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Se você inspecionar o conteúdo da variável `rSquared`, a saída deverá ter cinco valores que variam de 0 a 1, em que estar mais perto de 1 é melhor. Usando métricas como R ao quadrado, selecione os modelos do melhor ao pior desempenho. Em seguida, selecione o melhor modelo com o qual fazer previsões ou executar operações adicionais.

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
