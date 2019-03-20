---
title: Como usar um dicionário para armazenar instâncias de eventos - Guia de Programação em C#
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57845262"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="82abc-102">Como usar um dicionário para armazenar instâncias de eventos - Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="82abc-102">How to: use a dictionary to store event instances (C# Programming Guide)</span></span>

<span data-ttu-id="82abc-103">Um uso para os acessadores de eventos personalizados `add` e `remove` é expor muitos eventos sem alocar um campo para cada um deles; em vez disso, usando uma instância <xref:System.Collections.Generic.Dictionary%602> para armazenar as instâncias de eventos, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="82abc-103">One use for the `add` and `remove` custom event accessors is to expose many events without allocating a field for each event, but instead using a <xref:System.Collections.Generic.Dictionary%602> instance to store the event instances, as the example below demonstrates.</span></span> <span data-ttu-id="82abc-104">Isso só será útil se você tiver muitos eventos, mas presume que não haverá subscrição à maioria deles.</span><span class="sxs-lookup"><span data-stu-id="82abc-104">This is only useful if a type has many events, but you expect that most of the events will not be subscribed to.</span></span>

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

<span data-ttu-id="82abc-105">Essa implementação está de acordo com o comportamento de [adição e remoção de delegados](~/_csharplang/spec/delegates.md#delegate-invocation) na especificação da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="82abc-105">This implementation conforms to the behavior for [adding and removing delegates](~/_csharplang/spec/delegates.md#delegate-invocation) in the C# language specification.</span></span>

<span data-ttu-id="82abc-106">Observe que a instrução [lock](../../language-reference/keywords/lock-statement.md) é usada somente para *acessar* o dicionário com manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="82abc-106">Note that the [lock](../../language-reference/keywords/lock-statement.md) statement is used only to *access* the dictionary with event handlers.</span></span> <span data-ttu-id="82abc-107">Não invoque um manipulador de eventos dentro do corpo da instrução `lock`, pois ela poderia levar a deadlocks ou contenção de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="82abc-107">Don't invoke an event handler inside the body of the `lock` statement, as it could lead to deadlocks or lock contention.</span></span>

## <a name="see-also"></a><span data-ttu-id="82abc-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82abc-108">See also</span></span>

- [<span data-ttu-id="82abc-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="82abc-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="82abc-110">Eventos</span><span class="sxs-lookup"><span data-stu-id="82abc-110">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="82abc-111">Delegados</span><span class="sxs-lookup"><span data-stu-id="82abc-111">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
