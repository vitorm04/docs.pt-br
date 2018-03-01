---
title: Iterador (Visual Basic)
ms.date: 07/20/2015
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="0629d-102">Iterador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0629d-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="0629d-103">Especifica que uma função ou `Get` acessador é um iterador.</span><span class="sxs-lookup"><span data-stu-id="0629d-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0629d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0629d-104">Remarks</span></span>  
 <span data-ttu-id="0629d-105">Um *iterador* executa uma iteração personalizada em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0629d-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="0629d-106">Um iterador usa o [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção por vez.</span><span class="sxs-lookup"><span data-stu-id="0629d-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="0629d-107">Quando um `Yield` instrução for atingida, o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="0629d-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="0629d-108">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="0629d-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="0629d-109">Um iterador pode ser implementado como uma função ou um `Get` acessador de uma definição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="0629d-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="0629d-110">O `Iterator` modificador aparece na declaração da função iterador ou `Get` acessador.</span><span class="sxs-lookup"><span data-stu-id="0629d-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="0629d-111">Chamar um iterador no código do cliente usando um [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0629d-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="0629d-112">O tipo de retorno da função de um iterador ou `Get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="0629d-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="0629d-113">Um iterador não pode conter qualquer `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0629d-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="0629d-114">Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.</span><span class="sxs-lookup"><span data-stu-id="0629d-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="0629d-115">Um iterador pode ser uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="0629d-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="0629d-116">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0629d-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="0629d-117">Uso</span><span class="sxs-lookup"><span data-stu-id="0629d-117">Usage</span></span>  
 <span data-ttu-id="0629d-118">O `Iterator` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="0629d-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="0629d-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="0629d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="0629d-120">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0629d-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="0629d-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0629d-121">Example</span></span>  
 <span data-ttu-id="0629d-122">O exemplo a seguir demonstra uma função de iterador.</span><span class="sxs-lookup"><span data-stu-id="0629d-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="0629d-123">A função de iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="0629d-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="0629d-124">Cada iteração do [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterator.</span><span class="sxs-lookup"><span data-stu-id="0629d-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="0629d-125">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="0629d-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="0629d-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0629d-126">Example</span></span>  
 <span data-ttu-id="0629d-127">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="0629d-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="0629d-128">O `Iterator` modificador é na declaração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0629d-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="0629d-129">Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0629d-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0629d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0629d-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="0629d-131">Iteradores</span><span class="sxs-lookup"><span data-stu-id="0629d-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)  
 [<span data-ttu-id="0629d-132">Instrução Yield</span><span class="sxs-lookup"><span data-stu-id="0629d-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
