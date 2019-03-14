---
title: Operacionalizar um modelo de aprendizado de máquina treinado em aplicativos – ML.NET
description: Descubra como usar o ML.NET para consumir um modelo de aprendizado de máquina treinado e avaliado em aplicativos
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675128"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Operacionalizar um modelo de aprendizado de máquina treinado em aplicativos – ML.NET

> [!NOTE]
> Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações. Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento. Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Quando as métricas do modelo estiverem do seu agrado, é hora de "operacionalizar" o modelo. O objeto `model` que você criou pode ser consumido, persistido e reutilizado em diferentes ambientes, aplicando as mesmas etapas "aprendidas" durante o treinamento.

Para salvar o modelo em um arquivo e recarregá-lo (potencialmente em um contexto diferente), use o exemplo a seguir:

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```
