---
title: Palavra-chave contextual yield – referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: 0d2c3f67715b9b2161a6c908576ac9f964ff13d6
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363121"
---
# <a name="yield-c-reference"></a><span data-ttu-id="7d0b9-102">yield (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7d0b9-102">yield (C# Reference)</span></span>

<span data-ttu-id="7d0b9-103">Ao usar a [palavra-chave contextual](index.md#contextual-keywords) `yield` em uma instrução, você indica que o método, o operador ou o acessador `get` em que ela é exibida é um iterador.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="7d0b9-104">Usar `yield` para definir um iterador elimina a necessidade de uma classe adicional explícita (a classe que mantém o estado de uma enumeração, consulte <xref:System.Collections.Generic.IEnumerator%601> para obter um exemplo) ao implementar o padrão <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para um tipo de coleção personalizado.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="7d0b9-105">O exemplo a seguir mostra as duas formas de instrução `yield`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="7d0b9-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d0b9-106">Remarks</span></span>

<span data-ttu-id="7d0b9-107">Você usa uma instrução `yield return` para retornar cada elemento individualmente.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="7d0b9-108">A sequência retornada de um método iterador pode ser consumida usando uma instrução [foreach](foreach-in.md) ou uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="7d0b9-109">Cada iteração do loop `foreach` chama o método iterador.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="7d0b9-110">Quando uma instrução `yield return` é atingida no método iterador, `expression` é retornado e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="7d0b9-111">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="7d0b9-112">Você pode usar uma instrução `yield break` para terminar a iteração.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="7d0b9-113">Para obter mais informações sobre iteradores, consulte [Iteradores](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b9-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="7d0b9-114">Métodos de iterador e acessadores get</span><span class="sxs-lookup"><span data-stu-id="7d0b9-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="7d0b9-115">A declaração de um iterador deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="7d0b9-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="7d0b9-116">O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="7d0b9-117">A declaração não pode ter os parâmetros [in](in-parameter-modifier.md), [ref](ref.md) nem [out](out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b9-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="7d0b9-118">O tipo `yield` de um iterador que retorna <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> é `object`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="7d0b9-119">Se o iterador retornar <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, uma conversão implícita deverá existir do tipo da expressão na instrução `yield return` para o parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="7d0b9-120">Você não pode incluir uma instrução `yield return` ou `yield break` em:</span><span class="sxs-lookup"><span data-stu-id="7d0b9-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="7d0b9-121">[Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) e [métodos anônimos](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b9-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="7d0b9-122">Métodos que contêm blocos inseguros.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="7d0b9-123">Para obter mais informações, consulte [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b9-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="7d0b9-124">Tratamento de exceções</span><span class="sxs-lookup"><span data-stu-id="7d0b9-124">Exception handling</span></span>

<span data-ttu-id="7d0b9-125">Uma instrução `yield return` não pode estar localizada em um bloco try-catch.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="7d0b9-126">Uma instrução `yield return` pode estar localizada no bloco try de uma instrução try-finally.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="7d0b9-127">Uma instrução `yield break` pode estar localizada em um bloco try ou em um bloco catch, mas não em um bloco finally.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="7d0b9-128">Se o corpo `foreach` (fora do método iterador) acionar uma exceção, um bloco `finally` no método iterador será executado.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="7d0b9-129">Implementação técnica</span><span class="sxs-lookup"><span data-stu-id="7d0b9-129">Technical implementation</span></span>

<span data-ttu-id="7d0b9-130">O código a seguir retorna uma `IEnumerable<string>` de um método iterador e itera através de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="7d0b9-131">A chamada a `MyIteratorMethod` não executa o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="7d0b9-132">Em vez disso, a chamada retorna `IEnumerable<string>` na variável `elements`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="7d0b9-133">Em uma iteração do loop `foreach`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="7d0b9-134">Essa chamada executará o corpo de `MyIteratorMethod` até que a próxima instrução `yield return` seja atingida.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="7d0b9-135">A expressão retornada pela instrução `yield return` determina não apenas o valor da variável `element` para o consumo do corpo do loop, mas também a propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de `elements`, que é uma `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="7d0b9-136">Em cada iteração subsequente do loop `foreach`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="7d0b9-137">O loop `foreach` é concluído quando o fim do método iterador ou uma instrução `yield break` é atingida.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="7d0b9-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d0b9-138">Example</span></span>

<span data-ttu-id="7d0b9-139">O exemplo a seguir contém uma instrução `yield return` dentro de um loop `for`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="7d0b9-140">Cada iteração do corpo da instrução `foreach` no método `Main` cria uma chamada à função iteradora `Power`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="7d0b9-141">Cada chamada à função iteradora prossegue para a próxima execução da instrução `yield return` que ocorre durante a próxima iteração do loop `for`.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="7d0b9-142">O tipo de retorno do método iterador é <xref:System.Collections.IEnumerable> que é um tipo de interface de iterador.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="7d0b9-143">Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="7d0b9-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d0b9-144">Example</span></span>

<span data-ttu-id="7d0b9-145">O exemplo a seguir demonstra um acessador `get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="7d0b9-146">No exemplo, cada instrução `yield return` retorna uma instância de uma classe definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7d0b9-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="7d0b9-147">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7d0b9-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7d0b9-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d0b9-148">See also</span></span>

- [<span data-ttu-id="7d0b9-149">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7d0b9-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="7d0b9-150">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7d0b9-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7d0b9-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="7d0b9-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="7d0b9-152">Iteradores</span><span class="sxs-lookup"><span data-stu-id="7d0b9-152">Iterators</span></span>](../../iterators.md)
