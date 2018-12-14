---
title: Determinar a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
description: Entender a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 4b93e085dbb99e7f6f5a0a839b863aad1c69c7ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156564"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="4f60a-103">Determinar a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET</span><span class="sxs-lookup"><span data-stu-id="4f60a-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

<span data-ttu-id="4f60a-104">Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="4f60a-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="4f60a-105">Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho.</span><span class="sxs-lookup"><span data-stu-id="4f60a-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="4f60a-106">A `Permutation Feature Importance` (PFI) é uma ferramenta de explicação do modelo que é usada internamente na Microsoft para ajudar os desenvolvedores de aprendizado de máquina a compreender melhor a importância do recurso de modelos.</span><span class="sxs-lookup"><span data-stu-id="4f60a-106">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="4f60a-107">A PFI é uma técnica para determinar a **importância global do recurso** em um modelo de aprendizado de máquina treinado, motivada por Breiman no [artigo “Random Forests”, seção 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span><span class="sxs-lookup"><span data-stu-id="4f60a-107">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="4f60a-108">A PFI mede a importância do recurso fazendo a pergunta: “Qual seria o efeito no modelo se os valores de um recurso fossem definidos como um aleatórios\*?”.</span><span class="sxs-lookup"><span data-stu-id="4f60a-108">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="4f60a-109">A vantagem do método PFI é que ele é independente do modelo (isto é, funciona com qualquer modelo que possa ser avaliado) e pode usar qualquer conjunto de dados, não apenas o conjunto de treinamento, para calcular a importância do recurso.</span><span class="sxs-lookup"><span data-stu-id="4f60a-109">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="4f60a-110">Você pode usar a PFI dessa forma para produzir importâncias de recurso, como este gráfico:</span><span class="sxs-lookup"><span data-stu-id="4f60a-110">You can use PFI like so to produce feature importances like this graph:</span></span>

![Gráfico de importância do recurso de permutação](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model, data);
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Write out the feature names and their importance to the model's R-squared value
for (int i = 0; i < featureNames.Length; i++)
  Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].rSquared:G4}");
```

<span data-ttu-id="4f60a-112">Para obter um exemplo de como usar a PFI para analisar a importância do recurso de um modelo, consulte o [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).</span><span class="sxs-lookup"><span data-stu-id="4f60a-112">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).</span></span>

<span data-ttu-id="4f60a-113">/\* Bem, não é exatamente aleatório, mas permutado no conjunto de exemplos.</span><span class="sxs-lookup"><span data-stu-id="4f60a-113">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
