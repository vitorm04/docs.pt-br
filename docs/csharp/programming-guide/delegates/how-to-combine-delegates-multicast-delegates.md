---
title: Como combinar delegados (delegados multicast) – guia de programação C#
description: Saiba como combinar delegados para criar delegados multicast. Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302731"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="b3d6b-104">Como combinar delegados (delegados multicast) (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b3d6b-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="b3d6b-105">Este exemplo demonstra como criar delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="b3d6b-106">Uma propriedade útil de objetos [delegados](../../language-reference/builtin-types/reference-types.md) é que vários objetos podem ser atribuídos a uma instância delegada usando o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="b3d6b-107">O delegado multicast contém uma lista dos delegados atribuídos.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="b3d6b-108">Quando o delegado multicast é chamado, ele invoca os delegados da lista, em ordem.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="b3d6b-109">Apenas os delegados do mesmo tipo podem ser combinados.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="b3d6b-110">O operador `-` pode ser usado para remover um delegado de componente de um delegado multicast.</span><span class="sxs-lookup"><span data-stu-id="b3d6b-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d6b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3d6b-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b3d6b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3d6b-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="b3d6b-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b3d6b-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3d6b-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="b3d6b-114">Events</span></span>](../events/index.md)
