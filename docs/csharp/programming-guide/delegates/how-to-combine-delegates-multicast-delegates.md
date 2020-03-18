---
title: Como combinar delegados (Delegados Multicast) - Guia de Programação C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705373"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="3e334-102">Como combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3e334-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="3e334-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="3e334-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="3e334-104">Uma propriedade útil de objetos [delegados](../../language-reference/builtin-types/reference-types.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="3e334-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="3e334-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="3e334-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="3e334-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="3e334-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="3e334-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="3e334-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="3e334-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="3e334-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e334-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e334-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3e334-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="3e334-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="3e334-111">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="3e334-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3e334-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="3e334-112">Events</span></span>](../events/index.md)
