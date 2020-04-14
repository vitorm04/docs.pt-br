---
title: Interprete modelos ML.NET com Modelos Aditivos Generalizados
description: Use modelos aditivos generalizados e funções de forma para a interpretação do modelo em ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 29eac7a609ada57283a7c5b55b935e30709930dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243122"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="6bb15-103">Use modelos aditivos generalizados e funções de forma para a interpretação do modelo em ML.NET</span><span class="sxs-lookup"><span data-stu-id="6bb15-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="6bb15-104">Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="6bb15-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="6bb15-105">Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho.</span><span class="sxs-lookup"><span data-stu-id="6bb15-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="6bb15-106">**Os GAMs (Generalized Additive Models, modelos aditivos generalizados)** são usados internamente na Microsoft para a interpretação do modelo para ajudar os desenvolvedores de aprendizado de máquina a criar modelos de alta capacidade que podem ser facilmente interpretados por outros.</span><span class="sxs-lookup"><span data-stu-id="6bb15-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="6bb15-107">Os GAMs são uma classe de **modelos interpretáveis**, ou seja, modelos lineares em que os termos são funções não lineares, chamadas de "funções de forma" de uma única variável.</span><span class="sxs-lookup"><span data-stu-id="6bb15-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="6bb15-108">Como modelos lineares, eles são facilmente interpretados. No entanto, como os modelos aprendem funções de recursos em vez de um único peso, eles podem modelar relacionamentos mais complexos do que um modelo linear simples.</span><span class="sxs-lookup"><span data-stu-id="6bb15-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="6bb15-109">A previsão resultante do GAM possui um termo de interceptação que representa a previsão média sobre o conjunto de treinamento e as funções de forma que representam o desvio da previsão média.</span><span class="sxs-lookup"><span data-stu-id="6bb15-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="6bb15-110">As funções de forma podem ser visualmente inspecionadas para ver a resposta do modelo em relação a valores diferentes de um recurso e visualizadas como o gráfico a seguir criado no final do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="6bb15-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="6bb15-111">O instrutor do GAM no ML.NET é implementado usando árvores superficiais de gradiente aumentado (por exemplo, tocos de árvores) para aprender funções não paramétricas de forma e se baseia no método descrito em [Modelos inteligentes para classificação e regressão](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) de Lou, Caruana e Gehrke.</span><span class="sxs-lookup"><span data-stu-id="6bb15-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Gráfico de função de forma de Modelos aditivos generalizados](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="6bb15-113">Para um exemplo de como treinar um modelo GAM e inspecionar e interpretar os resultados, consulte a amostra do [treinador de classificação binária](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span><span class="sxs-lookup"><span data-stu-id="6bb15-113">For an example of how to train a GAM model and inspect and interpret the results, see the [binary classification trainer sample](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span></span>
