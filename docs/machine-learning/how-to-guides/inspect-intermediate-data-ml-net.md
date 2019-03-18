---
title: Inspecionar valores de dados intermediários durante o processamento de pipeline do ML.NET
description: Saiba como inspecionar valores de dados intermediários reais durante o processamento de pipeline de aprendizado de máquina do ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 362cb9351c3cb77b6aa67d59154854e882869ad9
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843410"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="862a6-103">Inspecionar valores de dados intermediários durante o processamento de pipeline do ML.NET</span><span class="sxs-lookup"><span data-stu-id="862a6-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

> [!NOTE]
> <span data-ttu-id="862a6-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="862a6-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="862a6-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="862a6-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="862a6-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="862a6-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="862a6-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="862a6-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="862a6-108">Durante o experimento, talvez você deseje observar e validar os resultados do processamento de dados em determinado momento.</span><span class="sxs-lookup"><span data-stu-id="862a6-108">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="862a6-109">Isso não é fácil, pois as operações do ML.NET são lentas, construindo objetos que são 'promessas' de dados.</span><span class="sxs-lookup"><span data-stu-id="862a6-109">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="862a6-110">O método de extensão `GetColumn<T>` permite que você inspecione os dados intermediários.</span><span class="sxs-lookup"><span data-stu-id="862a6-110">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="862a6-111">Ele retorna o conteúdo de uma coluna de dados como um `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="862a6-111">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="862a6-112">O seguinte exemplo mostra como usar o método de extensão `GetColumn<T>`:</span><span class="sxs-lookup"><span data-stu-id="862a6-112">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="862a6-113">[Arquivo de exemplo](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="862a6-113">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>

<!-- markdownlint-disable MD010 -->
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="862a6-114">Nossa classe é definida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="862a6-114">Our class is defined as follows:</span></span>

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```
