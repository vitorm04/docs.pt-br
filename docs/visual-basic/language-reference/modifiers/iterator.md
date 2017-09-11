---
title: Iterador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 958dd76fb9348e678001f7df5ed0e3c89a57242f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="iterator-visual-basic"></a><span data-ttu-id="6d935-102">Iterador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d935-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="6d935-103">Especifica que uma função ou `Get` acessador é um iterador.</span><span class="sxs-lookup"><span data-stu-id="6d935-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d935-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d935-104">Remarks</span></span>  
 <span data-ttu-id="6d935-105">Um *iterador* realiza a uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6d935-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="6d935-106">Um iterador usa o [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção por vez.</span><span class="sxs-lookup"><span data-stu-id="6d935-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="6d935-107">Quando um `Yield` instrução é alcançada, o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="6d935-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="6d935-108">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="6d935-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="6d935-109">Um iterador pode ser implementado como uma função ou um `Get` acessador de uma definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="6d935-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="6d935-110">O `Iterator` modificador aparece na declaração da função iterador ou `Get` acessador.</span><span class="sxs-lookup"><span data-stu-id="6d935-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="6d935-111">Chamar um iterador no código do cliente usando um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d935-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="6d935-112">O tipo de retorno de uma função de iterador ou `Get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="6d935-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="6d935-113">Um iterador não pode ter nenhum `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6d935-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="6d935-114">Um iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.</span><span class="sxs-lookup"><span data-stu-id="6d935-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="6d935-115">Um iterador pode ser uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="6d935-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="6d935-116">Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6d935-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="6d935-117">Para obter mais informações sobre iteradores, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6d935-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6d935-118">Uso</span><span class="sxs-lookup"><span data-stu-id="6d935-118">Usage</span></span>  
 <span data-ttu-id="6d935-119">O `Iterator` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="6d935-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="6d935-120">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="6d935-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="6d935-121">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="6d935-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6d935-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d935-122">Example</span></span>  
 <span data-ttu-id="6d935-123">O exemplo a seguir demonstra uma função do iterador.</span><span class="sxs-lookup"><span data-stu-id="6d935-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="6d935-124">A função de iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="6d935-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="6d935-125">Cada iteração de [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterador.</span><span class="sxs-lookup"><span data-stu-id="6d935-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="6d935-126">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="6d935-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="6d935-127">[!code-vb[VbVbalrStatements&#98;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6d935-127">[!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d935-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d935-128">Example</span></span>  
 <span data-ttu-id="6d935-129">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="6d935-129">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="6d935-130">O `Iterator` modificador é na declaração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6d935-130">The `Iterator` modifier is in the property declaration.</span></span>  
  
 <span data-ttu-id="6d935-131">[!code-vb[VbVbalrStatements&#99;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6d935-131">[!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]</span></span>  
  
 <span data-ttu-id="6d935-132">Para obter exemplos adicionais, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6d935-132">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d935-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d935-133">See Also</span></span>  
 <span data-ttu-id="6d935-134"><xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute></xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute></span><span class="sxs-lookup"><span data-stu-id="6d935-134"><xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute></span></span>   
<span data-ttu-id="6d935-135"> [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) </span><span class="sxs-lookup"><span data-stu-id="6d935-135"> [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) </span></span>  
<span data-ttu-id="6d935-136"> [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6d935-136"> [Yield Statement](../../../visual-basic/language-reference/statements/yield-statement.md)</span></span>
