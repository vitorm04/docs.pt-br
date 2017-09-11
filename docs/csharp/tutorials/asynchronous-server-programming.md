---
title: "Programação assíncrona do servidor - Guia do C#"
description: "Aprenda técnicas para o descarregamento de cargas de trabalho do servidor usando técnicas de programação assíncronas"
keywords: "C#, assíncrono, associado à CPU, limite de rede"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7402b29b-1093-456d-be4c-f60ecb8926bb
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 390d0eb2c8416165984ffe6c80ed6977e61a2845
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="-asynchronous-server-programming"></a><span data-ttu-id="c17c6-104">🔧 Programação assíncrona do servidor</span><span class="sxs-lookup"><span data-stu-id="c17c6-104">🔧 Asynchronous Server Programming</span></span>

> <span data-ttu-id="c17c6-105">**Observação**</span><span class="sxs-lookup"><span data-stu-id="c17c6-105">**Note**</span></span>
> 
> <span data-ttu-id="c17c6-106">Este tópico ainda não foi criado!</span><span class="sxs-lookup"><span data-stu-id="c17c6-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="c17c6-107">Agradecemos a sua contribuição para ajudar a moldar o escopo e a abordagem.</span><span class="sxs-lookup"><span data-stu-id="c17c6-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="c17c6-108">Você pode acompanhar o status e fornecer comentários sobre esse [problema](https://github.com/dotnet/docs/issues/952) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="c17c6-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/952) at GitHub.</span></span>
> 
> <span data-ttu-id="c17c6-109">Se você quiser examinar os primeiros rascunhos e esboços deste tópico, deixe uma nota com suas informações de contato no problema.</span><span class="sxs-lookup"><span data-stu-id="c17c6-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="c17c6-110">Saiba mais sobre como você pode contribuir com o [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="c17c6-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

