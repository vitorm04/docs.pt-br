---
title: "Instrução yield (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 393a9f4de3e801aed5932aef0e2b13d76b003965
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="60591-102">Instrução Yield (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60591-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="60591-103">Envia o próximo elemento de uma coleção para um `For Each...Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="60591-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60591-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60591-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60591-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60591-105">Parameters</span></span>  
  
|<span data-ttu-id="60591-106">Termo</span><span class="sxs-lookup"><span data-stu-id="60591-106">Term</span></span>|<span data-ttu-id="60591-107">Definição</span><span class="sxs-lookup"><span data-stu-id="60591-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="60591-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60591-108">Required.</span></span> <span data-ttu-id="60591-109">Uma expressão que é implicitamente conversível para o tipo da função iterador ou `Get` acessador que contém o `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="60591-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60591-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="60591-110">Remarks</span></span>  
 <span data-ttu-id="60591-111">O `Yield` instrução retorna um elemento de uma coleção de cada vez.</span><span class="sxs-lookup"><span data-stu-id="60591-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="60591-112">O `Yield` instrução é incluída em uma função de iterador ou `Get` acessador, que executa iterações personalizadas em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="60591-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="60591-113">Consumir uma função de iterador usando um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="60591-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="60591-114">Cada iteração de `For Each` loop chama a função do iterador.</span><span class="sxs-lookup"><span data-stu-id="60591-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="60591-115">Quando um `Yield` instrução for alcançada na função iterador, `expression` for retornado, e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="60591-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="60591-116">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="60591-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="60591-117">Deve existir uma conversão implícita de tipo de `expression` no `Yield` instrução para o tipo de retorno do iterador.</span><span class="sxs-lookup"><span data-stu-id="60591-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="60591-118">Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.</span><span class="sxs-lookup"><span data-stu-id="60591-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="60591-119">"Yield" não é uma palavra reservada e tem um significado especial somente quando ela é usada em uma `Iterator` função ou `Get` acessador.</span><span class="sxs-lookup"><span data-stu-id="60591-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="60591-120">Para obter mais informações sobre funções de iterador e `Get` acessadores, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="60591-120">For more information about iterator functions and `Get` accessors, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="60591-121">Funções de iterador e acessadores Get</span><span class="sxs-lookup"><span data-stu-id="60591-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="60591-122">A declaração de uma função de iterador ou `Get` acessador deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="60591-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="60591-123">Ele deve incluir uma [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="60591-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="60591-124">O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="60591-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="60591-125">Ele não pode ter nenhum `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="60591-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="60591-126">Uma função do iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.</span><span class="sxs-lookup"><span data-stu-id="60591-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="60591-127">Uma função do iterador pode ser uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="60591-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="60591-128">Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="60591-128">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="60591-129">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="60591-129">Exception Handling</span></span>  
 <span data-ttu-id="60591-130">A `Yield` instrução pode ser dentro de uma `Try` bloco de um [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="60591-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="60591-131">A `Try` bloco tem uma `Yield` instrução pode ter `Catch` blocos e pode ter um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="60591-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="60591-132">A `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="60591-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="60591-133">Se o `For Each` corpo (fora da função de iterador) gera uma exceção, uma `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função iterador é executado.</span><span class="sxs-lookup"><span data-stu-id="60591-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="60591-134">Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.</span><span class="sxs-lookup"><span data-stu-id="60591-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="60591-135">Implementação Técnica</span><span class="sxs-lookup"><span data-stu-id="60591-135">Technical Implementation</span></span>  
 <span data-ttu-id="60591-136">O código a seguir retorna um `IEnumerable (Of String)` de uma função de iterador e itera através dos elementos do `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="60591-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="60591-137">A chamada para `MyIteratorFunction` não executa o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="60591-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="60591-138">Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.</span><span class="sxs-lookup"><span data-stu-id="60591-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="60591-139">Em uma iteração de `For Each` loop, o <xref:System.Collections.IEnumerator.MoveNext%2A>método é chamado para `elements`.</xref:System.Collections.IEnumerator.MoveNext%2A></span><span class="sxs-lookup"><span data-stu-id="60591-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="60591-140">Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida.</span><span class="sxs-lookup"><span data-stu-id="60591-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="60591-141">O `Yield` instrução retorna uma expressão que determina não apenas o valor da `element` variável para consumo pelo corpo do loop, mas também o <xref:System.Collections.Generic.IEnumerator%601.Current%2A>propriedade de elementos, que é uma `IEnumerable (Of String)`.</xref:System.Collections.Generic.IEnumerator%601.Current%2A></span><span class="sxs-lookup"><span data-stu-id="60591-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="60591-142">Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="60591-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="60591-143">O `For Each` loop é concluído quando o final da função iterador ou uma `Return` ou `Exit Function` instrução seja atingida.</span><span class="sxs-lookup"><span data-stu-id="60591-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60591-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60591-144">Example</span></span>  
 <span data-ttu-id="60591-145">O exemplo a seguir tem uma `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="60591-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="60591-146">Cada iteração de [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterador.</span><span class="sxs-lookup"><span data-stu-id="60591-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="60591-147">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="60591-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="60591-148">O tipo de retorno do método iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface de iterador.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="60591-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="60591-149">Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.</span><span class="sxs-lookup"><span data-stu-id="60591-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 <span data-ttu-id="60591-150">[!code-vb[VbVbalrStatements&#98;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="60591-150">[!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="60591-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60591-151">Example</span></span>  
 <span data-ttu-id="60591-152">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="60591-152">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="60591-153">A declaração de propriedade inclui um `Iterator` modificador.</span><span class="sxs-lookup"><span data-stu-id="60591-153">The property declaration includes an `Iterator` modifier.</span></span>  
  
 <span data-ttu-id="60591-154">[!code-vb[VbVbalrStatements&#99;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="60591-154">[!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="60591-155">Para obter exemplos adicionais, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="60591-155">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60591-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60591-156">Requirements</span></span>  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60591-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60591-157">See Also</span></span>  
 <span data-ttu-id="60591-158">[Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) </span><span class="sxs-lookup"><span data-stu-id="60591-158">[Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7) </span></span>  
<span data-ttu-id="60591-159"> [Instruções](../../../visual-basic/language-reference/statements/index.md)</span><span class="sxs-lookup"><span data-stu-id="60591-159"> [Statements](../../../visual-basic/language-reference/statements/index.md)</span></span>
