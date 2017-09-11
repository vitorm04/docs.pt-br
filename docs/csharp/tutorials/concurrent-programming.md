---
title: "Programação simultânea - Guia do C#"
description: "Conheça as técnicas para execução em paralelo de tarefas (provavelmente vinculadas à CPU)"
keywords: "C#, assíncrono, associado à CPU, limite de rede"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0f8b42de-858a-44a3-87d9-998211f26377
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00cf3b04178ca48c9f8f35eb16bc216389e6b272
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="-concurrent-programming"></a><span data-ttu-id="5f717-104">🔧 Programação simultânea</span><span class="sxs-lookup"><span data-stu-id="5f717-104">🔧 Concurrent Programming</span></span>

> <span data-ttu-id="5f717-105">**Observação**</span><span class="sxs-lookup"><span data-stu-id="5f717-105">**Note**</span></span>
> 
> <span data-ttu-id="5f717-106">Este tópico ainda não foi criado!</span><span class="sxs-lookup"><span data-stu-id="5f717-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="5f717-107">Agradecemos a sua contribuição para ajudar a moldar o escopo e a abordagem.</span><span class="sxs-lookup"><span data-stu-id="5f717-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="5f717-108">Você pode acompanhar o status e fornecer comentários sobre esse [problema](https://github.com/dotnet/docs/issues/953) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5f717-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/953) at GitHub.</span></span>
> 
> <span data-ttu-id="5f717-109">Se você quiser examinar os primeiros rascunhos e esboços deste tópico, deixe uma nota com suas informações de contato no problema.</span><span class="sxs-lookup"><span data-stu-id="5f717-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="5f717-110">Saiba mais sobre como você pode contribuir com o [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="5f717-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

