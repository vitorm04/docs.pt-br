---
title: Treinar um modelo de machine learning usando a validação cruzada – ML.NET
description: Descubra como treinar um modelo de machine learning usando a validação cruzada com o ML.NET para ter um maior nível de precisão para as previsões do modelo
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 9ed139aacb41e8f8529f30747486ab1b13183df0
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739326"
---
# <a name="train-a-machine-learning-model-using-cross-validation---mlnet"></a>Treinar um modelo de machine learning usando a validação cruzada – ML.NET

A [validação cruzada](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) é uma técnica útil para aplicativos de ML. Ela ajuda a estimar a variação da qualidade do modelo de uma execução para outra e também elimina a necessidade de extrair um conjunto de testes separado para avaliação.

O ML.NET automaticamente aplica a personalização corretamente (desde que todo o pré-processamento resida em um pipeline de aprendizado) e, em seguida, usa o conceito de 'coluna de estratificação' para garantir que os exemplos relacionados não fiquem separados.

Este é um exemplo de treinamento em um conjunto de dados Iris usando uma divisão de teste de treinamento 90/10 aleatória e uma validação cruzada de 5 vezes:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("SepalLength",DataKind.R4,0),
        new TextLoader.Column("SepalWidth",DataKind.R4,1),
        new TextLoader.Column("PetalLength",DataKind.R4,2),
        new TextLoader.Column("PetalWidth",DataKind.R4,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has semicolon.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);


// Read the data.
var data = reader.Read(dataPath);

// Build the training pipeline.
var dynamicPipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent());

// Split the data 90:10 into train and test sets, train and evaluate.
var (trainData, testData) = mlContext.MulticlassClassification.TrainTestSplit(data, testFraction: 0.1);

// Train the model.
var model = dynamicPipeline.Fit(trainData);
// Compute quality metrics on the test set.
var metrics = mlContext.MulticlassClassification.Evaluate(model.Transform(testData));
Console.WriteLine(metrics.AccuracyMicro);

// Now run the 5-fold cross-validation experiment, using the same pipeline.
var cvResults = mlContext.MulticlassClassification.CrossValidate(data, dynamicPipeline, numFolds: 5);

// The results object is an array of 5 elements. For each of the 5 folds, we have metrics, model and scored test data.
// Let's compute the average micro-accuracy.
var microAccuracies = cvResults.Select(r => r.metrics.AccuracyMicro);
Console.WriteLine(microAccuracies.Average());
```
