---
title: Usar Modelos aditivos generalizados e funções de forma para explicação do modelo no ML.NET
description: Usar Modelos aditivos generalizados e funções de forma para explicação do modelo no ML.NET
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 489aee34d0404293bc080b934636c01bdab92fe9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156624"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="429df-103">Usar Modelos aditivos generalizados e funções de forma para explicação do modelo no ML.NET</span><span class="sxs-lookup"><span data-stu-id="429df-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

<span data-ttu-id="429df-104">Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="429df-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="429df-105">Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho.</span><span class="sxs-lookup"><span data-stu-id="429df-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="429df-106">Os **Modelos aditivos generalizados (GAMs)** são usados internamente na Microsoft para explicar o modelo e ajudar os desenvolvedores de aprendizado de máquina a criar modelos de alta capacidade que podem ser facilmente interpretados por outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="429df-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="429df-107">Os GAMs são uma classe de **modelos interpretáveis**, ou seja, modelos lineares em que os termos são funções não lineares, chamadas de "funções de forma" de uma única variável.</span><span class="sxs-lookup"><span data-stu-id="429df-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="429df-108">Como modelos lineares, eles são facilmente interpretados. No entanto, como os modelos aprendem funções de recursos em vez de um único peso, eles podem modelar relacionamentos mais complexos do que um modelo linear simples.</span><span class="sxs-lookup"><span data-stu-id="429df-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="429df-109">A previsão resultante do GAM possui um termo de interceptação que representa a previsão média sobre o conjunto de treinamento e as funções de forma que representam o desvio da previsão média.</span><span class="sxs-lookup"><span data-stu-id="429df-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="429df-110">As funções de forma podem ser visualmente inspecionadas para ver a resposta do modelo em relação a valores diferentes de um recurso e visualizadas como o gráfico a seguir criado no final do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="429df-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="429df-111">O instrutor do GAM no ML.NET é implementado usando árvores superficiais de gradiente aumentado (por exemplo, tocos de árvores) para aprender funções não paramétricas de forma e se baseia no método descrito em [Modelos inteligentes para classificação e regressão](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) de Lou, Caruana e Gehrke.</span><span class="sxs-lookup"><span data-stu-id="429df-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var gamTrainer = mlContext.Regression.Trainers.GeneralizedAdditiveModels()
var gamModel = gamTrainer.Fit(data);
 
// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Get the index of a variable from the training data
var myFeatureIndex = featureNames.ToList().FindIndex(str => str.Equals("MyFeature"));
 
// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetFeatureBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetFeatureWeights(myFeatureIndex);
 
// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
  Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
```

![Gráfico de função de forma de Modelos aditivos generalizados](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="429df-113">Para obter um exemplo de como treinar um modelo GAM e inspecionar e interpretar os resultados, confira o [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="429df-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>