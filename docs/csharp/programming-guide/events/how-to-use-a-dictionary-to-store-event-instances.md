---
title: Como usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: c3a804ce1bf1f5ac8db47f0f0c1f37d1ca5f781b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213167"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="e2977-102">Como usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e2977-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="e2977-103">Um uso de `accessor-declarations` é expor muitos eventos sem alocar um campo para cada evento em vez de usar um dicionário para armazenar as instâncias de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2977-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="e2977-104">Isso só é útil se você tiver muitos eventos, mas espera que a maioria dos eventos não seja implementada.</span><span class="sxs-lookup"><span data-stu-id="e2977-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2977-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2977-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e2977-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2977-106">See Also</span></span>

- [<span data-ttu-id="e2977-107">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e2977-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e2977-108">Eventos</span><span class="sxs-lookup"><span data-stu-id="e2977-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="e2977-109">Delegados</span><span class="sxs-lookup"><span data-stu-id="e2977-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
