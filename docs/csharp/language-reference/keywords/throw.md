---
description: throw – Referência de C#
title: throw – Referência de C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142031"
---
# <a name="throw-c-reference"></a><span data-ttu-id="66e99-103">throw (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="66e99-103">throw (C# Reference)</span></span>

<span data-ttu-id="66e99-104">Indica a ocorrência de uma exceção durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="66e99-104">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66e99-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="66e99-105">Remarks</span></span>

<span data-ttu-id="66e99-106">A sintaxe de `throw` é:</span><span class="sxs-lookup"><span data-stu-id="66e99-106">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="66e99-107">em que `e` é uma instância de uma classe derivada de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66e99-107">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66e99-108">O exemplo a seguir usará a instrução `throw` para gerar um <xref:System.IndexOutOfRangeException> se o argumento passado para um método chamado `GetNumber` não corresponder a um índice válido de uma matriz interna.</span><span class="sxs-lookup"><span data-stu-id="66e99-108">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="66e99-109">Os chamadores do método, então, usam um bloco `try-catch` ou `try-catch-finally` para tratar a exceção gerada.</span><span class="sxs-lookup"><span data-stu-id="66e99-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="66e99-110">O exemplo a seguir trata a exceção gerada pelo método `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="66e99-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="66e99-111">Como gerar novamente uma exceção</span><span class="sxs-lookup"><span data-stu-id="66e99-111">Re-throwing an exception</span></span>

<span data-ttu-id="66e99-112">`throw` também pode ser usado em um bloco `catch` para gerar novamente uma exceção tratada em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="66e99-112">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="66e99-113">Nesse caso, `throw` não usa um operando de exceção.</span><span class="sxs-lookup"><span data-stu-id="66e99-113">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="66e99-114">Ele é mais útil quando um método passa um argumento de um chamador para algum outro método de biblioteca e o método de biblioteca gera uma exceção que deve ser passada para o chamador.</span><span class="sxs-lookup"><span data-stu-id="66e99-114">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="66e99-115">O exemplo a seguir gera novamente um <xref:System.NullReferenceException> que é gerado ao tentar recuperar o primeiro caractere de uma cadeia de caracteres não inicializada.</span><span class="sxs-lookup"><span data-stu-id="66e99-115">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="66e99-116">Também é possível usar a sintaxe `throw e` em um bloco `catch` para instanciar uma nova exceção que você passa para o chamador.</span><span class="sxs-lookup"><span data-stu-id="66e99-116">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="66e99-117">Nesse caso, o rastreamento de pilha da exceção original, que fica disponível na propriedade <xref:System.Exception.StackTrace>, não é preservado.</span><span class="sxs-lookup"><span data-stu-id="66e99-117">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="66e99-118">A expressão `throw`</span><span class="sxs-lookup"><span data-stu-id="66e99-118">The `throw` expression</span></span>

<span data-ttu-id="66e99-119">Começando com o C# 7.0, o `throw` pode ser usado como uma expressão, bem como uma instrução.</span><span class="sxs-lookup"><span data-stu-id="66e99-119">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="66e99-120">Isso permite que uma exceção seja gerada em contextos que não tinham suporte anteriormente.</span><span class="sxs-lookup"><span data-stu-id="66e99-120">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="66e99-121">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="66e99-121">These include:</span></span>

- <span data-ttu-id="66e99-122">[o operador condicional](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-122">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="66e99-123">O exemplo a seguir usará uma expressão `throw` para gerar um <xref:System.ArgumentException> se uma matriz de cadeia de caracteres vazia for passada para um método.</span><span class="sxs-lookup"><span data-stu-id="66e99-123">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="66e99-124">Antes do C# 7.0, essa lógica precisava aparecer em uma instrução `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="66e99-124">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="66e99-125">[o operador de união nula](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-125">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="66e99-126">No exemplo a seguir, uma expressão `throw` será usada com um operador de união nula para gerar uma exceção se a cadeia de caracteres atribuída a uma propriedade `Name` for `null`.</span><span class="sxs-lookup"><span data-stu-id="66e99-126">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="66e99-127">um método ou [lambda](../operators/lambda-expressions.md) com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="66e99-127">an expression-bodied [lambda](../operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="66e99-128">O exemplo a seguir ilustra um método com corpo de expressão que gera um <xref:System.InvalidCastException> porque uma conversão para um valor <xref:System.DateTime> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="66e99-128">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="66e99-129">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="66e99-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="66e99-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="66e99-130">See also</span></span>

- [<span data-ttu-id="66e99-131">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="66e99-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="66e99-132">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="66e99-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="66e99-133">try-catch</span><span class="sxs-lookup"><span data-stu-id="66e99-133">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="66e99-134">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="66e99-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="66e99-135">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="66e99-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
