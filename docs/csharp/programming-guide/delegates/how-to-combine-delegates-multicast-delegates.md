---
title: Como combinar delegados (delegados multicast) – C# guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705373"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="2da23-102">Como combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2da23-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="2da23-103">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="2da23-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="2da23-104">Uma propriedade útil de objetos [delegados](../../language-reference/builtin-types/reference-types.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="2da23-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="2da23-105">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="2da23-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="2da23-106">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="2da23-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="2da23-107">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="2da23-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="2da23-108">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="2da23-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2da23-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2da23-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="2da23-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="2da23-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="2da23-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2da23-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2da23-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="2da23-112">Events</span></span>](../events/index.md)
