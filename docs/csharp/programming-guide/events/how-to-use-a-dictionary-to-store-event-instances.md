---
title: 'Como: usar um dicionário para armazenar instâncias de eventos – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f3b8e313bd0b1bd3973102caebb9bbc9da620ae6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203026"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="e5451-102">Como: usar um dicionário para armazenar instâncias de eventos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e5451-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="e5451-103">Um uso de `accessor-declarations` é expor muitos eventos sem alocar um campo para cada evento em vez de usar um dicionário para armazenar as instâncias de eventos.</span><span class="sxs-lookup"><span data-stu-id="e5451-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="e5451-104">Isso só é útil se você tiver muitos eventos, mas espera que a maioria dos eventos não seja implementada.</span><span class="sxs-lookup"><span data-stu-id="e5451-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5451-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5451-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e5451-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5451-106">See also</span></span>

- [<span data-ttu-id="e5451-107">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e5451-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e5451-108">Eventos</span><span class="sxs-lookup"><span data-stu-id="e5451-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="e5451-109">Delegados</span><span class="sxs-lookup"><span data-stu-id="e5451-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
