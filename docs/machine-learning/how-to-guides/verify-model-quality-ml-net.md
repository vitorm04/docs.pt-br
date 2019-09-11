---
title: Calcular métricas para avaliar a qualidade do modelo de machine learning
description: Saiba como calcular métricas para avaliar e verificar a qualidade do modelo de machine learning com o ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 529003913b166c966e131b006800f944096605b7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855571"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="f04f3-103">Calcular métricas para avaliar a qualidade do modelo de machine learning</span><span class="sxs-lookup"><span data-stu-id="f04f3-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="f04f3-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="f04f3-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f04f3-105">Para obter mais informações, visite a página [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="f04f3-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="f04f3-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="f04f3-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f04f3-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f04f3-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="f04f3-108">Como avaliar a qualidade depois de treinar o modelo?</span><span class="sxs-lookup"><span data-stu-id="f04f3-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="f04f3-109">Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.</span><span class="sxs-lookup"><span data-stu-id="f04f3-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="f04f3-110">Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="f04f3-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
