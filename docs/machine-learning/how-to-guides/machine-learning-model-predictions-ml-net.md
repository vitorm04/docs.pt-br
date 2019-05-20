---
title: Fazer previsões com um modelo treinado
description: Aprenda a fazer previsões usando um modelo treinado
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: dac3b3bfa68776975a2e5e762f46db16e39d61fb
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065599"
---
# <a name="make-predictions-with-a-trained-model"></a>Fazer previsões com um modelo treinado

Saiba como usar um modelo treinado para fazer previsões

## <a name="create-data-models"></a>Criar modelo de dados

### <a name="input-data"></a>Dados de entrada

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

### <a name="output-data"></a>Dados de saída

Como os nomes de coluna de entrada `Features` e `Label`, do ML.NET tem nomes padrão para as colunas de valor previsto produzidas por um modelo. Dependendo da tarefa, o nome pode diferir.

Como o algoritmo usado neste exemplo é um algoritmo de regressão linear, o nome padrão da coluna de saída é `Score`, que é definido pelo atributo [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) na propriedade `PredictedPrice`.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

O modelo de dados `HousingPrediction` herda de `HousingData` para facilitar a visualização dos dados de entrada originais junto com a saída gerada pelo modelo.  

## <a name="set-up-a-prediction-pipeline"></a>Configurar um pipeline de previsão

Seja fazendo uma previsão única ou em lotes, o pipeline de previsão precisa ser carregado no aplicativo. Esse pipeline contém as transformações de pré-processamento de dados, bem como o modelo treinado. O snippet de código a seguir carrega o pipeline de previsão de um arquivo chamado `model.zip`.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Previsão única

Para criar uma previsão única, crie um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) usando o pipeline de previsão carregado.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Em seguida, use o método [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) e passe seus dados de entrada como um parâmetro. Observe que usar o método [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) não exige que a entrada seja uma [`IDataView`](xref:Microsoft.ML.IDataView). Isso ocorre porque ele internaliza convenientemente a manipulação do tipo de dados de entrada para que você possa passar um objeto do tipo de dados de entrada. Além disso, uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se não há nenhum valor para ele no momento.

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

Se você acessar a propriedade `Score` do objeto `prediction`, deverá obter um valor semelhante ao `150079`.

## <a name="batch-prediction"></a>Previsão em lote

Considerando os seguintes dados, carregue-os em um [`IDataView`](xref:Microsoft.ML.IDataView). Uma vez que `CurrentPrice` é o destino ou o rótulo que você está tentando prever usando novos dados, supõe-se que não há valor para ele no momento.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
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

Em seguida, use o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) para aplicar as transformações de dados e gerar previsões.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Inspecione os valores previstos usando o método [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*).

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Os valores previstos da coluna de pontuação devem ser semelhantes aos seguintes:

| Observação | Previsão |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
