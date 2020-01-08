---
title: Como combinar delegados (delegados multicast) – C# guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 1a552c0203a4307994b80a1d3d37d12f577c02c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346393"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="1be55-102">Como combinar delegados (delegados de multicast) (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="1be55-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="1be55-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="1be55-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="1be55-104">Uma propriedade útil de objetos [delegados](../../language-reference/builtin-types/reference-types.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="1be55-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="1be55-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="1be55-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="1be55-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="1be55-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="1be55-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="1be55-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="1be55-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="1be55-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be55-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1be55-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1be55-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="1be55-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="1be55-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1be55-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1be55-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="1be55-112">Events</span></span>](../events/index.md)
