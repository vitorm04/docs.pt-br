---
title: yield – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: 7b718417fc421b9024e023964c4f29478b52c4ca
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239271"
---
# <a name="yield-c-reference"></a><span data-ttu-id="24744-102">yield (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="24744-102">yield (C# Reference)</span></span>
<span data-ttu-id="24744-103">Ao usar a [palavra-chave contextual](../../../csharp/language-reference/keywords/index.md#contextual-keywords) `yield` em uma instrução, você indica que o método, o operador ou o acessador `get` em que ela é exibida é um iterador.</span><span class="sxs-lookup"><span data-stu-id="24744-103">When you use the `yield` [contextual keyword](../../../csharp/language-reference/keywords/index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="24744-104">Usar `yield` para definir um iterador elimina a necessidade de uma classe adicional explícita (a classe que mantém o estado de uma enumeração, consulte <xref:System.Collections.Generic.IEnumerator%601> para obter um exemplo) ao implementar o padrão <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para um tipo de coleção personalizado.</span><span class="sxs-lookup"><span data-stu-id="24744-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="24744-105">O exemplo a seguir mostra as duas formas de instrução `yield`.</span><span class="sxs-lookup"><span data-stu-id="24744-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="24744-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="24744-106">Remarks</span></span>  
 <span data-ttu-id="24744-107">Você usa uma instrução `yield return` para retornar cada elemento individualmente.</span><span class="sxs-lookup"><span data-stu-id="24744-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="24744-108">Você consome um método iterador ao usar uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="24744-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="24744-109">Cada iteração do loop `foreach` chama o método iterador.</span><span class="sxs-lookup"><span data-stu-id="24744-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="24744-110">Quando uma instrução `yield return` é atingida no método iterador, `expression` é retornado e o local atual no código é retido.</span><span class="sxs-lookup"><span data-stu-id="24744-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="24744-111">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="24744-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="24744-112">Você pode usar uma instrução `yield break` para terminar a iteração.</span><span class="sxs-lookup"><span data-stu-id="24744-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="24744-113">Para obter mais informações sobre iteradores, consulte [Iteradores](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="24744-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="24744-114">Métodos de Iterador Acessadores get</span><span class="sxs-lookup"><span data-stu-id="24744-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="24744-115">A declaração de um iterador deve atender aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="24744-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="24744-116">O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="24744-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="24744-117">A declaração não pode ter os parâmetros [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="24744-117">The declaration can't have any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
 <span data-ttu-id="24744-118">O tipo `yield` de um iterador que retorna <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> é `object`.</span><span class="sxs-lookup"><span data-stu-id="24744-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="24744-119">Se o iterador retornar <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, uma conversão implícita deverá existir do tipo da expressão na instrução `yield return` para o parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="24744-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="24744-120">Você não pode incluir uma instrução `yield return` ou `yield break` nos métodos com as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="24744-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="24744-121">Métodos anônimos.</span><span class="sxs-lookup"><span data-stu-id="24744-121">Anonymous methods.</span></span> <span data-ttu-id="24744-122">Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="24744-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="24744-123">Métodos que contêm blocos inseguros.</span><span class="sxs-lookup"><span data-stu-id="24744-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="24744-124">Para obter mais informações, consulte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="24744-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="24744-125">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="24744-125">Exception Handling</span></span>  
 <span data-ttu-id="24744-126">Uma instrução `yield return` não pode estar localizada em um bloco try-catch.</span><span class="sxs-lookup"><span data-stu-id="24744-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="24744-127">Uma instrução `yield return` pode estar localizada no bloco try de uma instrução try-finally.</span><span class="sxs-lookup"><span data-stu-id="24744-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="24744-128">Uma instrução `yield break` pode estar localizada em um bloco try ou em um bloco catch, mas não em um bloco finally.</span><span class="sxs-lookup"><span data-stu-id="24744-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="24744-129">Se o corpo `foreach` (fora do método iterador) acionar uma exceção, um bloco `finally` no método iterador será executado.</span><span class="sxs-lookup"><span data-stu-id="24744-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="24744-130">Implementação Técnica</span><span class="sxs-lookup"><span data-stu-id="24744-130">Technical Implementation</span></span>  
 <span data-ttu-id="24744-131">O código a seguir retorna uma `IEnumerable<string>` de um método iterador e itera através de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="24744-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="24744-132">A chamada a `MyIteratorMethod` não executa o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="24744-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="24744-133">Em vez disso, a chamada retorna `IEnumerable<string>` na variável `elements`.</span><span class="sxs-lookup"><span data-stu-id="24744-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="24744-134">Em uma iteração do loop `foreach`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`.</span><span class="sxs-lookup"><span data-stu-id="24744-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="24744-135">Essa chamada executará o corpo de `MyIteratorMethod` até que a próxima instrução `yield return` seja atingida.</span><span class="sxs-lookup"><span data-stu-id="24744-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="24744-136">A expressão retornada pela instrução `yield return` determina não apenas o valor da variável `element` para o consumo do corpo do loop, mas também a propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de `elements`, que é uma `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="24744-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="24744-137">Em cada iteração subsequente do loop `foreach`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `yield return`.</span><span class="sxs-lookup"><span data-stu-id="24744-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="24744-138">O loop `foreach` é concluído quando o fim do método iterador ou uma instrução `yield break` é atingida.</span><span class="sxs-lookup"><span data-stu-id="24744-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24744-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24744-139">Example</span></span>  
 <span data-ttu-id="24744-140">O exemplo a seguir contém uma instrução `yield return` dentro de um loop `for`.</span><span class="sxs-lookup"><span data-stu-id="24744-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="24744-141">Cada iteração do corpo da instrução `foreach` no método `Main` cria uma chamada à função iteradora `Power`.</span><span class="sxs-lookup"><span data-stu-id="24744-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="24744-142">Cada chamada à função iteradora prossegue para a próxima execução da instrução `yield return` que ocorre durante a próxima iteração do loop `for`.</span><span class="sxs-lookup"><span data-stu-id="24744-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="24744-143">O tipo de retorno do método iterador é <xref:System.Collections.IEnumerable> que é um tipo de interface de iterador.</span><span class="sxs-lookup"><span data-stu-id="24744-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="24744-144">Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.</span><span class="sxs-lookup"><span data-stu-id="24744-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="24744-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24744-145">Example</span></span>  
 <span data-ttu-id="24744-146">O exemplo a seguir demonstra um acessador `get` que é um iterador.</span><span class="sxs-lookup"><span data-stu-id="24744-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="24744-147">No exemplo, cada instrução `yield return` retorna uma instância de uma classe definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="24744-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="24744-148">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="24744-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24744-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24744-149">See Also</span></span>

- [<span data-ttu-id="24744-150">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="24744-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="24744-151">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="24744-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="24744-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="24744-152">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="24744-153">Iteradores</span><span class="sxs-lookup"><span data-stu-id="24744-153">Iterators</span></span>](../../iterators.md)
