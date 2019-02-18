---
title: Pré-processar dados de treinamento com normalizadores a serem usados no processamento de dados – ML.NET
description: Saiba como usar normalizadores para pré-processar dados de treinamento para uso na criação, no treinamento e na pontuação do modelo de machine learning com o ML.NET
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 28d358cd381f71b4116e1dd25d847fc51835f09e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093041"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="e7e56-103">Pré-processar dados de treinamento com normalizadores a serem usados no processamento de dados – ML.NET</span><span class="sxs-lookup"><span data-stu-id="e7e56-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

<span data-ttu-id="e7e56-104">O ML.NET expõe inúmeros [algoritmos paramétricos e não paramétricos](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span><span class="sxs-lookup"><span data-stu-id="e7e56-104">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="e7e56-105">O normalizador escolhido **não** é tão importante quanto o **uso** de um normalizador durante o treinamento de modelos lineares ou outros modelos paramétricos.</span><span class="sxs-lookup"><span data-stu-id="e7e56-105">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="e7e56-106">Sempre inclua o normalizador diretamente no pipeline de aprendizado do ML.NET, para que ele:</span><span class="sxs-lookup"><span data-stu-id="e7e56-106">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="e7e56-107">seja treinado somente nos dados de treinamento, e não nos dados de teste;</span><span class="sxs-lookup"><span data-stu-id="e7e56-107">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="e7e56-108">seja aplicado corretamente a todos os novos dados recebidos, sem a necessidade de pré-processamento extra em tempo de previsão.</span><span class="sxs-lookup"><span data-stu-id="e7e56-108">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="e7e56-109">Veja a seguir um snippet de código que demonstra a normalização em pipelines de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="e7e56-109">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="e7e56-110">Ele pressupõe o conjunto de dados Iris:</span><span class="sxs-lookup"><span data-stu-id="e7e56-110">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
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
            new NormalizingEstimator.MinMaxColumn(inputColumnName:"Features", outputColumnName:"MinMaxNormalized", fixZero: true),
            new NormalizingEstimator.MeanVarColumn(inputColumnName: "Features", outputColumnName: "MeanVarNormalized", fixZero: true),
            new NormalizingEstimator.BinningColumn(inputColumnName: "Features", outputColumnName: "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
