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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>Use modelos aditivos generalizados e funções de forma para a interpretação do modelo em ML.NET

Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões. Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho. **Os GAMs (Generalized Additive Models, modelos aditivos generalizados)** são usados internamente na Microsoft para a interpretação do modelo para ajudar os desenvolvedores de aprendizado de máquina a criar modelos de alta capacidade que podem ser facilmente interpretados por outros.

Os GAMs são uma classe de **modelos interpretáveis**, ou seja, modelos lineares em que os termos são funções não lineares, chamadas de "funções de forma" de uma única variável. Como modelos lineares, eles são facilmente interpretados. No entanto, como os modelos aprendem funções de recursos em vez de um único peso, eles podem modelar relacionamentos mais complexos do que um modelo linear simples. A previsão resultante do GAM possui um termo de interceptação que representa a previsão média sobre o conjunto de treinamento e as funções de forma que representam o desvio da previsão média. As funções de forma podem ser visualmente inspecionadas para ver a resposta do modelo em relação a valores diferentes de um recurso e visualizadas como o gráfico a seguir criado no final do exemplo de código. O instrutor do GAM no ML.NET é implementado usando árvores superficiais de gradiente aumentado (por exemplo, tocos de árvores) para aprender funções não paramétricas de forma e se baseia no método descrito em [Modelos inteligentes para classificação e regressão](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) de Lou, Caruana e Gehrke.

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

Para um exemplo de como treinar um modelo GAM e inspecionar e interpretar os resultados, consulte a amostra do [treinador de classificação binária](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).
