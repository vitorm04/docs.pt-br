---
title: throw – Referência de C#
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: f274802c84ff8f3dd2588db8b83a0d0de36d2d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101769"
---
# <a name="throw-c-reference"></a><span data-ttu-id="2c3e0-102">throw (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2c3e0-102">throw (C# Reference)</span></span>

<span data-ttu-id="2c3e0-103">Indica a ocorrência de uma exceção durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c3e0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c3e0-104">Remarks</span></span>

<span data-ttu-id="2c3e0-105">A sintaxe de `throw` é:</span><span class="sxs-lookup"><span data-stu-id="2c3e0-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="2c3e0-106">em que `e` é uma instância de uma classe derivada de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c3e0-107">O exemplo a seguir usará a instrução `throw` para gerar um <xref:System.IndexOutOfRangeException> se o argumento passado para um método chamado `GetNumber` não corresponder a um índice válido de uma matriz interna.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="2c3e0-108">Os chamadores do método, então, usam um bloco `try-catch` ou `try-catch-finally` para tratar a exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="2c3e0-109">O exemplo a seguir trata a exceção gerada pelo método `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="2c3e0-110">Gerando uma exceção novamente</span><span class="sxs-lookup"><span data-stu-id="2c3e0-110">Re-throwing an exception</span></span>

<span data-ttu-id="2c3e0-111">`throw` também pode ser usado em um bloco `catch` para gerar novamente uma exceção tratada em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="2c3e0-112">Nesse caso, `throw` não usa um operando de exceção.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="2c3e0-113">Ele é mais útil quando um método passa um argumento de um chamador para algum outro método de biblioteca e o método de biblioteca gera uma exceção que deve ser passada para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="2c3e0-114">O exemplo a seguir gera novamente um <xref:System.NullReferenceException> que é gerado ao tentar recuperar o primeiro caractere de uma cadeia de caracteres não inicializada.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="2c3e0-115">Também é possível usar a sintaxe `throw e` em um bloco `catch` para instanciar uma nova exceção que você passa para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="2c3e0-116">Nesse caso, o rastreamento de pilha da exceção original, que fica disponível na propriedade <xref:System.Exception.StackTrace>, não é preservado.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="2c3e0-117">A expressão `throw`</span><span class="sxs-lookup"><span data-stu-id="2c3e0-117">The `throw` expression</span></span>

<span data-ttu-id="2c3e0-118">Começando com o C# 7.0, o `throw` pode ser usado como uma expressão, bem como uma instrução.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="2c3e0-119">Isso permite que uma exceção seja gerada em contextos que não tinham suporte anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="2c3e0-120">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="2c3e0-120">These include:</span></span>

- <span data-ttu-id="2c3e0-121">[o operador condicional](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2c3e0-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="2c3e0-122">O exemplo a seguir usará uma expressão `throw` para gerar um <xref:System.ArgumentException> se uma matriz de cadeia de caracteres vazia for passada para um método.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="2c3e0-123">Antes do C# 7.0, essa lógica precisava aparecer em uma instrução `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="2c3e0-124">[o operador de união nula](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2c3e0-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="2c3e0-125">No exemplo a seguir, uma expressão `throw` será usada com um operador de união nula para gerar uma exceção se a cadeia de caracteres atribuída a uma propriedade `Name` for `null`.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="2c3e0-126">um método ou [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="2c3e0-127">O exemplo a seguir ilustra um método com corpo de expressão que gera um <xref:System.InvalidCastException> porque uma conversão para um valor <xref:System.DateTime> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="2c3e0-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="2c3e0-128">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2c3e0-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2c3e0-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c3e0-129">See also</span></span>

- [<span data-ttu-id="2c3e0-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2c3e0-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2c3e0-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2c3e0-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2c3e0-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="2c3e0-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="2c3e0-133">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2c3e0-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2c3e0-134">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="2c3e0-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
