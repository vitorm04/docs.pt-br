---
title: Calcular métricas para avaliar a qualidade do modelo de machine learning – ML.NET
description: Saiba como calcular métricas para avaliar e verificar a qualidade do modelo de machine learning com o ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149517"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="cfe7d-103">Calcular métricas para avaliar a qualidade do modelo de machine learning – ML.NET</span><span class="sxs-lookup"><span data-stu-id="cfe7d-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

<span data-ttu-id="cfe7d-104">Como avaliar a qualidade depois de treinar o modelo?</span><span class="sxs-lookup"><span data-stu-id="cfe7d-104">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="cfe7d-105">Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.</span><span class="sxs-lookup"><span data-stu-id="cfe7d-105">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="cfe7d-106">Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="cfe7d-106">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```