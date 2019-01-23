---
title: Instrução Yield (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: da01d3f1bdfa3e76afcc28e7b70240beb06f74f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506479"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="3f378-102">Instrução Yield (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f378-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="3f378-103">Envia o próximo elemento de uma coleção para um `For Each...Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="3f378-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f378-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f378-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f378-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f378-105">Parameters</span></span>  
  
|<span data-ttu-id="3f378-106">Termo</span><span class="sxs-lookup"><span data-stu-id="3f378-106">Term</span></span>|<span data-ttu-id="3f378-107">Definição</span><span class="sxs-lookup"><span data-stu-id="3f378-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="3f378-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f378-108">Required.</span></span> <span data-ttu-id="3f378-109">Uma expressão que é implicitamente conversível para o tipo de função iteradora ou `Get` acessador que contém o `Yield` instrução.</span><span class="sxs-lookup"><span data-stu-id="3f378-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f378-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f378-110">Remarks</span></span>  
 <span data-ttu-id="3f378-111">O `Yield` instrução retorna um elemento de uma coleção cada vez.</span><span class="sxs-lookup"><span data-stu-id="3f378-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="3f378-112">O `Yield` instrução é incluída em uma função de iterador ou `Get` acessador, o que executar iterações personalizadas em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3f378-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="3f378-113">Consumir uma função de iterador usando uma [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="3f378-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="3f378-114">Cada iteração do `For Each` loop chama a função de iterador.</span><span class="sxs-lookup"><span data-stu-id="3f378-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="3f378-115">Quando um `Yield` instrução seja atingida na função de iterador, `expression` for retornado, e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="3f378-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="3f378-116">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="3f378-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="3f378-117">Uma conversão implícita deve existir do tipo de `expression` no `Yield` instrução para o tipo de retorno do iterador.</span><span class="sxs-lookup"><span data-stu-id="3f378-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="3f378-118">Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.</span><span class="sxs-lookup"><span data-stu-id="3f378-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="3f378-119">"Yield" não é uma palavra reservada e tem um significado especial somente quando ele é usado em uma `Iterator` função ou `Get` acessador.</span><span class="sxs-lookup"><span data-stu-id="3f378-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="3f378-120">Para obter mais informações sobre as funções de iterador e `Get` acessadores, consulte [iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3f378-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="3f378-121">Acessadores Get e funções de iterador</span><span class="sxs-lookup"><span data-stu-id="3f378-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="3f378-122">A declaração de uma função de iterador ou `Get` acessador deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="3f378-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="3f378-123">Ele deve incluir um [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="3f378-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="3f378-124">O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="3f378-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="3f378-125">Ele não pode ter nenhum `ByRef` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3f378-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="3f378-126">Uma função de iterador não pode ocorrer em um evento, construtor de instância, o construtor estático ou um destruidor estático.</span><span class="sxs-lookup"><span data-stu-id="3f378-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="3f378-127">Uma função de iterador pode ser uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="3f378-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="3f378-128">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3f378-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="3f378-129">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="3f378-129">Exception Handling</span></span>  
 <span data-ttu-id="3f378-130">Um `Yield` instrução pode ser dentro de uma `Try` block de um [tente... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3f378-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="3f378-131">Um `Try` bloco tem um `Yield` instrução pode ter `Catch` bloqueia e pode ter um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="3f378-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="3f378-132">Um `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="3f378-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="3f378-133">Se o `For Each` corpo (fora da função de iterador) lança uma exceção, uma `Catch` bloco na função de iterador não é executado, mas um `Finally` bloco na função de iterador será executado.</span><span class="sxs-lookup"><span data-stu-id="3f378-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="3f378-134">Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.</span><span class="sxs-lookup"><span data-stu-id="3f378-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="3f378-135">Implementação Técnica</span><span class="sxs-lookup"><span data-stu-id="3f378-135">Technical Implementation</span></span>  
 <span data-ttu-id="3f378-136">O código a seguir retorna uma `IEnumerable (Of String)` de uma função de iterador e itera por meio dos elementos do `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="3f378-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="3f378-137">A chamada para `MyIteratorFunction` não executa o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="3f378-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="3f378-138">Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.</span><span class="sxs-lookup"><span data-stu-id="3f378-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="3f378-139">Em uma iteração do loop `For Each`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`.</span><span class="sxs-lookup"><span data-stu-id="3f378-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="3f378-140">Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida.</span><span class="sxs-lookup"><span data-stu-id="3f378-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="3f378-141">O `Yield` instrução retorna uma expressão que determina não apenas o valor da `element` variável para consumo pelo corpo do loop, mas também a <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriedade dos elementos, que é um `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="3f378-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="3f378-142">Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="3f378-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="3f378-143">O `For Each` loop é concluído quando o final da função de iterador ou uma `Return` ou `Exit Function` instrução seja atingida.</span><span class="sxs-lookup"><span data-stu-id="3f378-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f378-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f378-144">Example</span></span>  
 <span data-ttu-id="3f378-145">O exemplo a seguir tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="3f378-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="3f378-146">Cada iteração do [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iteradora.</span><span class="sxs-lookup"><span data-stu-id="3f378-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="3f378-147">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="3f378-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="3f378-148">O tipo de retorno do método iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface de iterador.</span><span class="sxs-lookup"><span data-stu-id="3f378-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="3f378-149">Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.</span><span class="sxs-lookup"><span data-stu-id="3f378-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3f378-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f378-150">Example</span></span>  
 <span data-ttu-id="3f378-151">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="3f378-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="3f378-152">A declaração de propriedade inclui um `Iterator` modificador.</span><span class="sxs-lookup"><span data-stu-id="3f378-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="3f378-153">Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="3f378-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f378-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f378-154">See also</span></span>
- [<span data-ttu-id="3f378-155">Instruções</span><span class="sxs-lookup"><span data-stu-id="3f378-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
