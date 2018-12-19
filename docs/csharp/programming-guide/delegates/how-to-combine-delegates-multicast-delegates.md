---
title: 'Como: combinar delegados (delegados multicast) – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d835f9b22fef550d6e73cbd620a283bd71e393ec
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237786"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="dd4cc-102">Como: combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="dd4cc-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="dd4cc-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="dd4cc-104">Uma propriedade útil de objetos [delegados](../../../csharp/language-reference/keywords/delegate.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="dd4cc-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="dd4cc-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="dd4cc-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="dd4cc-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="dd4cc-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd4cc-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd4cc-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="dd4cc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd4cc-110">See Also</span></span>

- <xref:System.MulticastDelegate>  
- [<span data-ttu-id="dd4cc-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dd4cc-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dd4cc-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="dd4cc-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
