---
title: Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET
description: Descubra como usar o ML.NET para carregar dados de treinamento que não estão em um arquivo para o treinamento do modelo de machine learning durante o pipeline de previsão.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 27b327a63cb55b7fce0f4ff7facd3ee7c4a1c85c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678601"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

O caso de uso do ML.NET que normalmente é demonstrado é usar o `TextLoader` para ler os dados de treinamento de um arquivo.
No entanto, em cenários de treinamento em tempo real, os dados podem ser obtidos de outra forma, como:

* em tabelas SQL
* extraídos de arquivos de log
* gerados em tempo real

Use a [compreensão do esquema](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) para levar um `IEnumerable` em C# existente ao ML.NET como uma `DataView`.

Neste exemplo, você criará o modelo de previsão de variação do cliente e extrairá estes recursos do seu sistema de produção:

* ID do cliente (ignorada pelo modelo)
* Se o cliente variou (o 'rótulo' de destino)
* A 'categoria demográfica' (uma cadeia de caracteres como 'jovens adultos' etc.)
* O número de visitas nos últimos cinco dias.

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

Carregue esses dados no `DataView` e treine o modelo usando o seguinte código:

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
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
