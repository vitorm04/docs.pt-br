---
title: Iterador
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351530"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="e67cd-102">Iterador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e67cd-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="e67cd-103">Specifies that a function or `Get` accessor is an iterator.</span><span class="sxs-lookup"><span data-stu-id="e67cd-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e67cd-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e67cd-104">Remarks</span></span>  
 <span data-ttu-id="e67cd-105">An *iterator* performs a custom iteration over a collection.</span><span class="sxs-lookup"><span data-stu-id="e67cd-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="e67cd-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span><span class="sxs-lookup"><span data-stu-id="e67cd-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="e67cd-107">When a `Yield` statement is reached, the current location in code is retained.</span><span class="sxs-lookup"><span data-stu-id="e67cd-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="e67cd-108">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="e67cd-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="e67cd-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span><span class="sxs-lookup"><span data-stu-id="e67cd-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="e67cd-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span><span class="sxs-lookup"><span data-stu-id="e67cd-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="e67cd-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e67cd-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="e67cd-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="e67cd-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="e67cd-113">An iterator cannot have any `ByRef` parameters.</span><span class="sxs-lookup"><span data-stu-id="e67cd-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="e67cd-114">Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.</span><span class="sxs-lookup"><span data-stu-id="e67cd-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="e67cd-115">An iterator can be an anonymous function.</span><span class="sxs-lookup"><span data-stu-id="e67cd-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="e67cd-116">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e67cd-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e67cd-117">Uso</span><span class="sxs-lookup"><span data-stu-id="e67cd-117">Usage</span></span>  
 <span data-ttu-id="e67cd-118">The `Iterator` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="e67cd-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="e67cd-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="e67cd-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="e67cd-120">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e67cd-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="e67cd-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e67cd-121">Example</span></span>  
 <span data-ttu-id="e67cd-122">The following example demonstrates an iterator function.</span><span class="sxs-lookup"><span data-stu-id="e67cd-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="e67cd-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="e67cd-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="e67cd-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span><span class="sxs-lookup"><span data-stu-id="e67cd-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="e67cd-125">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="e67cd-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="e67cd-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e67cd-126">Example</span></span>  
 <span data-ttu-id="e67cd-127">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="e67cd-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="e67cd-128">The `Iterator` modifier is in the property declaration.</span><span class="sxs-lookup"><span data-stu-id="e67cd-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="e67cd-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e67cd-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67cd-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e67cd-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="e67cd-131">Iteradores</span><span class="sxs-lookup"><span data-stu-id="e67cd-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="e67cd-132">Instrução Yield</span><span class="sxs-lookup"><span data-stu-id="e67cd-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
