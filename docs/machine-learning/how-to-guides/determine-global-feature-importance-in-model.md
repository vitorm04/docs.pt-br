---
title: Determinar a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
description: Entender a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b0457bc07168579403e5a00383864c5612e1d17f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675544"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="2ad16-103">Determinar a importância de recursos de modelos com a Importância de recursos de permutação no ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ad16-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="2ad16-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="2ad16-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="2ad16-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="2ad16-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="2ad16-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="2ad16-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="2ad16-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="2ad16-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="2ad16-108">Ao criar modelos de aprendizado de máquina, muitas vezes não é suficiente simplesmente fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="2ad16-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="2ad16-109">Frequentemente, os desenvolvedores de aprendizado de máquina, os tomadores de decisão e aqueles que são afetados pelos modelos precisam entender como os modelos de aprendizado de máquina tomam decisões e quais recursos contribuem para seu desempenho.</span><span class="sxs-lookup"><span data-stu-id="2ad16-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="2ad16-110">A `Permutation Feature Importance` (PFI) é uma ferramenta de explicação do modelo que é usada internamente na Microsoft para ajudar os desenvolvedores de aprendizado de máquina a compreender melhor a importância do recurso de modelos.</span><span class="sxs-lookup"><span data-stu-id="2ad16-110">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="2ad16-111">A PFI é uma técnica para determinar a **importância global do recurso** em um modelo de aprendizado de máquina treinado, motivada por Breiman no [artigo “Random Forests”, seção 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span><span class="sxs-lookup"><span data-stu-id="2ad16-111">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="2ad16-112">A PFI mede a importância do recurso fazendo a pergunta: “Qual seria o efeito no modelo se os valores de um recurso fossem definidos como um aleatórios\*?”.</span><span class="sxs-lookup"><span data-stu-id="2ad16-112">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="2ad16-113">A vantagem do método PFI é que ele é independente do modelo (isto é, funciona com qualquer modelo que possa ser avaliado) e pode usar qualquer conjunto de dados, não apenas o conjunto de treinamento, para calcular a importância do recurso.</span><span class="sxs-lookup"><span data-stu-id="2ad16-113">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="2ad16-114">Você pode usar a PFI dessa forma para produzir importâncias de recurso, como este gráfico:</span><span class="sxs-lookup"><span data-stu-id="2ad16-114">You can use PFI like so to produce feature importances like this graph:</span></span>

![Gráfico de importância do recurso de permutação](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

<span data-ttu-id="2ad16-116">Para obter um exemplo de como usar a PFI para analisar a importância do recurso de um modelo, consulte o [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span><span class="sxs-lookup"><span data-stu-id="2ad16-116">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span></span>

<span data-ttu-id="2ad16-117">/\* Bem, não é exatamente aleatório, mas permutado no conjunto de exemplos.</span><span class="sxs-lookup"><span data-stu-id="2ad16-117">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
