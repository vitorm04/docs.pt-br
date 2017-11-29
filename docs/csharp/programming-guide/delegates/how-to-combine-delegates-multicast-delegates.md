---
title: "Como combinar delegados (delegados multicast) (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="f9b2a-102">Como combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f9b2a-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="f9b2a-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="f9b2a-104">Uma propriedade útil de objetos [delegados](../../../csharp/language-reference/keywords/delegate.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="f9b2a-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="f9b2a-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="f9b2a-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="f9b2a-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="f9b2a-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b2a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9b2a-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f9b2a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9b2a-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="f9b2a-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f9b2a-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9b2a-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="f9b2a-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
