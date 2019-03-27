---
title: Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET
description: Descubra como usar o ML.NET para carregar dados de treinamento que não estão em um arquivo para o treinamento do modelo de machine learning durante o pipeline de previsão.
ms.date: 03/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 32de37e45b9e19669ea06d74c7f252ec885fe004
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186085"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="61eaa-103">Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET</span><span class="sxs-lookup"><span data-stu-id="61eaa-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="61eaa-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="61eaa-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="61eaa-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="61eaa-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="61eaa-106">Esta instrução e a amostra relacionada atualmente usam o **ML.NET versão 0.11**.</span><span class="sxs-lookup"><span data-stu-id="61eaa-106">This how-to and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="61eaa-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="61eaa-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="61eaa-108">O caso de uso do ML.NET que normalmente é demonstrado é usar o `TextLoader` para ler os dados de treinamento de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="61eaa-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="61eaa-109">No entanto, em cenários de treinamento em tempo real, os dados podem ser obtidos de outra forma, como:</span><span class="sxs-lookup"><span data-stu-id="61eaa-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="61eaa-110">em tabelas SQL</span><span class="sxs-lookup"><span data-stu-id="61eaa-110">in SQL tables</span></span>
* <span data-ttu-id="61eaa-111">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="61eaa-111">JSON/XML</span></span>
* <span data-ttu-id="61eaa-112">extraídos de arquivos de log</span><span class="sxs-lookup"><span data-stu-id="61eaa-112">extracted from log files</span></span>
* <span data-ttu-id="61eaa-113">gerados em tempo real</span><span class="sxs-lookup"><span data-stu-id="61eaa-113">generated on the fly</span></span>

<span data-ttu-id="61eaa-114">Use a [compreensão do esquema](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) para levar um `IEnumerable` em C# existente ao ML.NET como uma `DataView`.</span><span class="sxs-lookup"><span data-stu-id="61eaa-114">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="61eaa-115">Neste exemplo, você criará o modelo de previsão de variação do cliente e extrairá estes recursos do seu sistema de produção:</span><span class="sxs-lookup"><span data-stu-id="61eaa-115">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="61eaa-116">ID do cliente (ignorada pelo modelo)</span><span class="sxs-lookup"><span data-stu-id="61eaa-116">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="61eaa-117">Se o cliente variou (o 'rótulo' de destino)</span><span class="sxs-lookup"><span data-stu-id="61eaa-117">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="61eaa-118">A 'categoria demográfica' (uma cadeia de caracteres como 'jovens adultos' etc.)</span><span class="sxs-lookup"><span data-stu-id="61eaa-118">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="61eaa-119">O número de visitas nos últimos cinco dias.</span><span class="sxs-lookup"><span data-stu-id="61eaa-119">The number of visits from the last 5 days.</span></span>

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

<span data-ttu-id="61eaa-120">Carregue esses dados no `DataView` e treine o modelo usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="61eaa-120">Load this data into the `DataView` and train the model, using the following code:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.LoadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
