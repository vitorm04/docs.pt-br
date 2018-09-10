---
title: throw (Referência de C#)
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 831c4cce14e902697d84129e54cc54f07d26b9f3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865030"
---
# <a name="throw-c-reference"></a><span data-ttu-id="92f81-102">throw (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="92f81-102">throw (C# Reference)</span></span>
<span data-ttu-id="92f81-103">Indica a ocorrência de uma exceção durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="92f81-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92f81-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="92f81-104">Remarks</span></span>

<span data-ttu-id="92f81-105">A sintaxe de `throw` é:</span><span class="sxs-lookup"><span data-stu-id="92f81-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="92f81-106">em que `e` é uma instância de uma classe derivada de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92f81-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="92f81-107">O exemplo a seguir usará a instrução `throw` para gerar um <xref:System.IndexOutOfRangeException> se o argumento passado para um método chamado `GetNumber` não corresponder a um índice válido de uma matriz interna.</span><span class="sxs-lookup"><span data-stu-id="92f81-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="92f81-108">Os chamadores do método, então, usam um bloco `try-catch` ou `try-catch-finally` para tratar a exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="92f81-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="92f81-109">O exemplo a seguir trata a exceção gerada pelo método `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="92f81-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="92f81-110">Gerando uma exceção novamente</span><span class="sxs-lookup"><span data-stu-id="92f81-110">Re-throwing an exception</span></span>

<span data-ttu-id="92f81-111">`throw` também pode ser usado em um bloco `catch` para gerar novamente uma exceção tratada em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="92f81-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="92f81-112">Nesse caso, `throw` não usa um operando de exceção.</span><span class="sxs-lookup"><span data-stu-id="92f81-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="92f81-113">Ele é mais útil quando um método passa um argumento de um chamador para algum outro método de biblioteca e o método de biblioteca gera uma exceção que deve ser passada para o chamador.</span><span class="sxs-lookup"><span data-stu-id="92f81-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="92f81-114">O exemplo a seguir gera novamente um <xref:System.NullReferenceException> que é gerado ao tentar recuperar o primeiro caractere de uma cadeia de caracteres não inicializada.</span><span class="sxs-lookup"><span data-stu-id="92f81-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="92f81-115">Também é possível usar a sintaxe `throw e` em um bloco `catch` para instanciar uma nova exceção que você passa para o chamador.</span><span class="sxs-lookup"><span data-stu-id="92f81-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="92f81-116">Nesse caso, o rastreamento de pilha da exceção original, que fica disponível na propriedade <xref:System.Exception.StackTrace>, não é preservado.</span><span class="sxs-lookup"><span data-stu-id="92f81-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="92f81-117">A expressão `throw`</span><span class="sxs-lookup"><span data-stu-id="92f81-117">The `throw` expression</span></span>

<span data-ttu-id="92f81-118">Começando com o C# 7.0, o `throw` pode ser usado como uma expressão, bem como uma instrução.</span><span class="sxs-lookup"><span data-stu-id="92f81-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="92f81-119">Isso permite que uma exceção seja gerada em contextos que não tinham suporte anteriormente.</span><span class="sxs-lookup"><span data-stu-id="92f81-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="92f81-120">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="92f81-120">These include:</span></span>

- <span data-ttu-id="92f81-121">[o operador condicional](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="92f81-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="92f81-122">O exemplo a seguir usará uma expressão `throw` para gerar um <xref:System.ArgumentException> se uma matriz de cadeia de caracteres vazia for passada para um método.</span><span class="sxs-lookup"><span data-stu-id="92f81-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="92f81-123">Antes do C# 7.0, essa lógica precisava aparecer em uma instrução `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="92f81-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="92f81-124">[o operador de união nula](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="92f81-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="92f81-125">No exemplo a seguir, uma expressão `throw` será usada com um operador de união nula para gerar uma exceção se a cadeia de caracteres atribuída a uma propriedade `Name` for `null`.</span><span class="sxs-lookup"><span data-stu-id="92f81-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="92f81-126">um método ou [lambda](../../lambda-expressions.md) com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="92f81-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="92f81-127">O exemplo a seguir ilustra um método com corpo de expressão que gera um <xref:System.InvalidCastException> porque uma conversão para um valor <xref:System.DateTime> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="92f81-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="92f81-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="92f81-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92f81-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92f81-129">See Also</span></span>

- [<span data-ttu-id="92f81-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="92f81-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="92f81-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="92f81-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="92f81-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="92f81-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="92f81-133">As instruções try, catch e throw em C++</span><span class="sxs-lookup"><span data-stu-id="92f81-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="92f81-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="92f81-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="92f81-135">Instruções para manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="92f81-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="92f81-136">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="92f81-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
