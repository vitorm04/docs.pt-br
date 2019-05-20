---
title: Calcular métricas para avaliar a qualidade do modelo de machine learning
description: Saiba como calcular métricas para avaliar e verificar a qualidade do modelo de machine learning com o ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2c7749205b862a42f42b857972057c441ab84364
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641104"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="f6123-103">Calcular métricas para avaliar a qualidade do modelo de machine learning</span><span class="sxs-lookup"><span data-stu-id="f6123-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="f6123-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="f6123-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f6123-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f6123-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f6123-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="f6123-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f6123-107">Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f6123-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="f6123-108">Como avaliar a qualidade depois de treinar o modelo?</span><span class="sxs-lookup"><span data-stu-id="f6123-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="f6123-109">Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.</span><span class="sxs-lookup"><span data-stu-id="f6123-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="f6123-110">Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="f6123-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
