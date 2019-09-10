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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Calcular métricas para avaliar a qualidade do modelo de machine learning 

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite a página [ml.net](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Saiba mais nas notas de versão no [repositório do GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Como avaliar a qualidade depois de treinar o modelo? Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.

Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
