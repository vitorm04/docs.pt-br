---
title: Instrução Yield
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352719"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="4ad0d-102">Instrução Yield (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ad0d-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="4ad0d-103">Envia o próximo elemento de uma coleção para uma instrução `For Each...Next`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ad0d-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ad0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ad0d-105">Parameters</span></span>  
  
|<span data-ttu-id="4ad0d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="4ad0d-106">Term</span></span>|<span data-ttu-id="4ad0d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="4ad0d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="4ad0d-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-108">Required.</span></span> <span data-ttu-id="4ad0d-109">Uma expressão que é conversível implicitamente no tipo da função de iterador ou `Get` acessador que contém a instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad0d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ad0d-110">Remarks</span></span>  
 <span data-ttu-id="4ad0d-111">A instrução `Yield` retorna um elemento de uma coleção por vez.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="4ad0d-112">A instrução `Yield` é incluída em uma função de iterador ou `Get` acessador, que executam iterações personalizadas em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="4ad0d-113">Você consome uma função de iterador usando um [para cada... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="4ad0d-114">Cada iteração do loop de `For Each` chama a função de iterador.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="4ad0d-115">Quando uma instrução `Yield` é atingida na função de iterador, `expression` é retornado e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="4ad0d-116">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="4ad0d-117">Uma conversão implícita deve existir a partir do tipo de `expression` na instrução `Yield` para o tipo de retorno do iterador.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="4ad0d-118">Você pode usar uma instrução `Exit Function` ou `Return` para encerrar a iteração.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="4ad0d-119">"Yield" não é uma palavra reservada e tem um significado especial apenas quando é usado em uma função `Iterator` ou acessador de `Get`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="4ad0d-120">Para obter mais informações sobre as funções de iteradores e acessadores `Get`, consulte [iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4ad0d-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="4ad0d-121">Funções de iterador e get acessadores</span><span class="sxs-lookup"><span data-stu-id="4ad0d-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="4ad0d-122">A declaração de uma função de iterador ou acessador de `Get` deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="4ad0d-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="4ad0d-123">Ele deve incluir um modificador de [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="4ad0d-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="4ad0d-124">O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="4ad0d-125">Ele não pode ter parâmetros de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="4ad0d-126">Uma função de iterador não pode ocorrer em um evento, Construtor de instância, construtor estático ou destruidor estático.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="4ad0d-127">Uma função de iterador pode ser uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="4ad0d-128">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4ad0d-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="4ad0d-129">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="4ad0d-129">Exception Handling</span></span>  
 <span data-ttu-id="4ad0d-130">Uma instrução `Yield` pode estar dentro de um bloco de `Try` de uma [tentativa... Capturar... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4ad0d-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="4ad0d-131">Um bloco de `Try` que tem uma instrução `Yield` pode ter blocos de `Catch` e pode ter um bloco de `Finally`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="4ad0d-132">Uma instrução `Yield` não pode estar dentro de um bloco de `Catch` ou um bloco de `Finally`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="4ad0d-133">Se o corpo de `For Each` (fora da função de iterador) gerar uma exceção, um bloco de `Catch` na função de iterador não será executado, mas um bloco de `Finally` na função de iterador será executado.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="4ad0d-134">Um bloco de `Catch` dentro de uma função de iterador captura apenas as exceções que ocorrem dentro da função de iterador.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="4ad0d-135">Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="4ad0d-135">Technical Implementation</span></span>  
 <span data-ttu-id="4ad0d-136">O código a seguir retorna uma `IEnumerable (Of String)` de uma função de iterador e, em seguida, itera pelos elementos da `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="4ad0d-137">A chamada para `MyIteratorFunction` não executa o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="4ad0d-138">Em vez disso, a chamada retorna `IEnumerable(Of String)` na variável `elements`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="4ad0d-139">Em uma iteração do loop `For Each`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="4ad0d-140">Essa chamada executará o corpo de `MyIteratorFunction` até que a próxima instrução `Yield` seja atingida.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="4ad0d-141">A instrução `Yield` retorna uma expressão que determina não apenas o valor da variável `element` para consumo pelo corpo do loop, mas também a propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de elementos, que é uma `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="4ad0d-142">Em cada iteração subsequente do loop `For Each`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="4ad0d-143">O loop de `For Each` é concluído quando o final da função de iterador ou uma instrução `Return` ou `Exit Function` é atingido.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ad0d-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ad0d-144">Example</span></span>  
 <span data-ttu-id="4ad0d-145">O exemplo a seguir tem uma instrução `Yield` que está dentro de um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="4ad0d-146">Cada iteração do corpo da instrução [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) no `Main` cria uma chamada para a função de iterador `Power`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="4ad0d-147">Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="4ad0d-148">O tipo de retorno do método do iterador é <xref:System.Collections.Generic.IEnumerable%601>, um tipo de interface do iterador.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="4ad0d-149">Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="4ad0d-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ad0d-150">Example</span></span>  
 <span data-ttu-id="4ad0d-151">O exemplo a seguir demonstra um acessador `Get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="4ad0d-152">A declaração de propriedade inclui um modificador de `Iterator`.</span><span class="sxs-lookup"><span data-stu-id="4ad0d-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="4ad0d-153">Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4ad0d-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad0d-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ad0d-154">See also</span></span>

- [<span data-ttu-id="4ad0d-155">Instruções</span><span class="sxs-lookup"><span data-stu-id="4ad0d-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
