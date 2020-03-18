---
title: Calcular métricas para avaliar a qualidade do modelo de machine learning
description: Saiba como calcular métricas para avaliar e verificar a qualidade do modelo de machine learning com o ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975836"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Calcular métricas para avaliar a qualidade do modelo de machine learning

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para mais informações, visite a página [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Para obter mais informações, consulte as notas de versão no [repo Dotnet/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Como avaliar a qualidade depois de treinar o modelo? Cada tarefa de aprendizado de máquina expõe métricas de avaliação da qualidade.

Você pode usar o 'contexto' correspondente da tarefa para avaliar o modelo, como no seguinte exemplo:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
