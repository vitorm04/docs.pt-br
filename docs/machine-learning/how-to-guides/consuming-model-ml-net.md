---
title: Operacionalizar um modelo de aprendizado de máquina treinado em aplicativos – ML.NET
description: Descubra como usar o ML.NET para consumir um modelo de aprendizado de máquina treinado e avaliado em aplicativos
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ff3f0a8856382d020129693bcf722f572fd87606
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131640"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="2dce8-103">Operacionalizar um modelo de aprendizado de máquina treinado em aplicativos – ML.NET</span><span class="sxs-lookup"><span data-stu-id="2dce8-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

<span data-ttu-id="2dce8-104">Quando as métricas do modelo estiverem do seu agrado, é hora de "operacionalizar" o modelo.</span><span class="sxs-lookup"><span data-stu-id="2dce8-104">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="2dce8-105">O objeto `model` que você criou pode ser consumido, persistido e reutilizado em diferentes ambientes, aplicando as mesmas etapas "aprendidas" durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="2dce8-105">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="2dce8-106">Para salvar o modelo em um arquivo e recarregá-lo (potencialmente em um contexto diferente), use o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2dce8-106">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

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
