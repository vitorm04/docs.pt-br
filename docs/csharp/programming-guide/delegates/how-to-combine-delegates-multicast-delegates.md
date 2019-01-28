---
title: 'Como: combinar delegados (delegados multicast) – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: ebfcba4d2ebebe2697aa01b7109bbf50b8f144e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631549"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="4af02-102">Como: combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4af02-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="4af02-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="4af02-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="4af02-104">Uma propriedade útil de objetos [delegados](../../../csharp/language-reference/keywords/delegate.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="4af02-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="4af02-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="4af02-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="4af02-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="4af02-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="4af02-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="4af02-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="4af02-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="4af02-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4af02-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4af02-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4af02-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4af02-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="4af02-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4af02-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4af02-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="4af02-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
