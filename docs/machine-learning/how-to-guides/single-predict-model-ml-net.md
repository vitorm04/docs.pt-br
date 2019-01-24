---
title: Usar o PredictionEngine para fazer uma previsão de cada vez – ML.NET
description: Saiba como usar o PredictionEngine do ML.NET para fazer uma previsão de cada vez
ms.date: 01/15/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0b3f60038fe7f49ffbff3c63fd2862ba67adb506
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333636"
---
# <a name="use-the-predictionengine-to-make-one-prediction-at-a-time---mlnet"></a><span data-ttu-id="02f62-103">Usar o PredictionEngine para fazer uma previsão de cada vez – ML.NET</span><span class="sxs-lookup"><span data-stu-id="02f62-103">Use the PredictionEngine to make one prediction at a time - ML.NET</span></span> 

<span data-ttu-id="02f62-104">Como qualquer modelo ML.NET é um transformador, você usa `model.Transform` para aplicar o modelo ao `DataView` para fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="02f62-104">Since any ML.NET model is a transformer, you use `model.Transform` to apply the model to the `DataView` to make predictions.</span></span> 

<span data-ttu-id="02f62-105">Um caso mais típico, no entanto, é quando não há um 'conjunto de dados' que você deseja prever, mas, em vez disso, você recebe um exemplo de cada vez.</span><span class="sxs-lookup"><span data-stu-id="02f62-105">A more typical case, though, is when there is no 'dataset' that you want to predict on, but instead you receive one example at a time.</span></span> <span data-ttu-id="02f62-106">Por exemplo, você executa o modelo como parte de seu site ASP.NET e precisa fazer uma previsão para uma solicitação HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="02f62-106">For instance, you run the model as part of your ASP.NET website, and need to make a prediction for an incoming HTTP request.</span></span>

<span data-ttu-id="02f62-107">O `PredictionEngine` executa um exemplo de cada vez por meio do pipeline de previsão.</span><span class="sxs-lookup"><span data-stu-id="02f62-107">The `PredictionEngine` runs one example at a time through the prediction pipeline.</span></span>

<span data-ttu-id="02f62-108">Veja o exemplo completo que usa um modelo de conjunto de dados de previsão Iris predefinido:</span><span class="sxs-lookup"><span data-stu-id="02f62-108">Here is the full example using a prebuilt Iris prediction dataset model:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(new TextLoader.Arguments
{
    Column = new[] {
        new TextLoader.Column("SepalLength", DataKind.R4, 0),
        new TextLoader.Column("SepalWidth", DataKind.R4, 1),
        new TextLoader.Column("PetalLength", DataKind.R4, 2),
        new TextLoader.Column("PetalWidth", DataKind.R4, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("PredictedLabel", "Data")));

// Train the model.
var model = pipeline.Fit(trainData);
```

<span data-ttu-id="02f62-109">Para usar a [compreensão do esquema](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) na previsão, defina um par de classes como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="02f62-109">To use [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) for prediction, define a pair of classes like the following:</span></span>

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

<span data-ttu-id="02f62-110">O código de previsão agora será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="02f62-110">The prediction code now looks as follows:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction engine, instead of
// creating one per prediction.
var predictionEngine = model.CreatePredictionEngine<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionEngine.
var prediction = predictionEngine.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```
