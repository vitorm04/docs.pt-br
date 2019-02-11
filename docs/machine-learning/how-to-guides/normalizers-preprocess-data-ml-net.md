---
title: Pré-processar dados de treinamento com normalizadores a serem usados no processamento de dados – ML.NET
description: Saiba como usar normalizadores para pré-processar dados de treinamento para uso na criação, no treinamento e na pontuação do modelo de machine learning com o ML.NET
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4311307f5410a96bb4a30fcedd88bc43afd25c12
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738572"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>Pré-processar dados de treinamento com normalizadores a serem usados no processamento de dados – ML.NET

O ML.NET expõe inúmeros [algoritmos paramétricos e não paramétricos](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).

O normalizador escolhido **não** é tão importante quanto o **uso** de um normalizador durante o treinamento de modelos lineares ou outros modelos paramétricos.

Sempre inclua o normalizador diretamente no pipeline de aprendizado do ML.NET, para que ele:

- seja treinado somente nos dados de treinamento, e não nos dados de teste;
- seja aplicado corretamente a todos os novos dados recebidos, sem a necessidade de pré-processamento extra em tempo de previsão.

Veja a seguir um snippet de código que demonstra a normalização em pipelines de aprendizado. Ele pressupõe o conjunto de dados Iris:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features",DataKind.R4,0,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has comma.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
        new NormalizingEstimator.MinMaxColumn("Features", "MinMaxNormalized", fixZero: true),
        new NormalizingEstimator.MeanVarColumn("Features", "MeanVarNormalized", fixZero: true),
        new NormalizingEstimator.BinningColumn("Features", "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
