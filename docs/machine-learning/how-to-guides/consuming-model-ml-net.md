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
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="3999b-103">Operacionalizar um modelo de aprendizado de máquina treinado em aplicativos – ML.NET</span><span class="sxs-lookup"><span data-stu-id="3999b-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="3999b-104">Este tópico se refere ao ML.NET, que está atualmente na Versão Prévia, e o material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="3999b-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="3999b-105">Para obter mais informações, visite [a introdução ao ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="3999b-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="3999b-106">Esta instrução e a amostra relacionada estão usando o **ML.NET versão 0.10** no momento.</span><span class="sxs-lookup"><span data-stu-id="3999b-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="3999b-107">Saiba mais nas notas de versão no [repositório do github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="3999b-107">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="3999b-108">Quando as métricas do modelo estiverem do seu agrado, é hora de "operacionalizar" o modelo.</span><span class="sxs-lookup"><span data-stu-id="3999b-108">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="3999b-109">O objeto `model` que você criou pode ser consumido, persistido e reutilizado em diferentes ambientes, aplicando as mesmas etapas "aprendidas" durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="3999b-109">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="3999b-110">Para salvar o modelo em um arquivo e recarregá-lo (potencialmente em um contexto diferente), use o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3999b-110">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

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
