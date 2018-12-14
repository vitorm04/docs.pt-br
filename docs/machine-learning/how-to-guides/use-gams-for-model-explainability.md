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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>Usar Modelos aditivos generalizados e funções de forma para explicação do modelo no ML.NET

Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões. Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho. Os **Modelos aditivos generalizados (GAMs)** são usados internamente na Microsoft para explicar o modelo e ajudar os desenvolvedores de aprendizado de máquina a criar modelos de alta capacidade que podem ser facilmente interpretados por outras pessoas.

Os GAMs são uma classe de **modelos interpretáveis**, ou seja, modelos lineares em que os termos são funções não lineares, chamadas de "funções de forma" de uma única variável. Como modelos lineares, eles são facilmente interpretados. No entanto, como os modelos aprendem funções de recursos em vez de um único peso, eles podem modelar relacionamentos mais complexos do que um modelo linear simples. A previsão resultante do GAM possui um termo de interceptação que representa a previsão média sobre o conjunto de treinamento e as funções de forma que representam o desvio da previsão média. As funções de forma podem ser visualmente inspecionadas para ver a resposta do modelo em relação a valores diferentes de um recurso e visualizadas como o gráfico a seguir criado no final do exemplo de código. O instrutor do GAM no ML.NET é implementado usando árvores superficiais de gradiente aumentado (por exemplo, tocos de árvores) para aprender funções não paramétricas de forma e se baseia no método descrito em [Modelos inteligentes para classificação e regressão](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) de Lou, Caruana e Gehrke.

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

Para obter um exemplo de como treinar um modelo GAM e inspecionar e interpretar os resultados, confira o [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).