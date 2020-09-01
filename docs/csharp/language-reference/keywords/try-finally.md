---
description: try-finally – Referência de C#
title: try-finally – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141966"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="bc971-103">try-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bc971-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="bc971-104">Usando um bloco `finally`, você pode limpar todos os recursos alocados em um bloco [try](try-catch.md) e pode executar código mesmo se uma exceção ocorrer no bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="bc971-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="bc971-105">Normalmente, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="bc971-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="bc971-106">A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma instrução `break`, `continue`, `goto` ou `return`, ou da propagação de uma exceção para fora da instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="bc971-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="bc971-107">Dentro de uma exceção tratada, é garantido que o bloco `finally` será executado.</span><span class="sxs-lookup"><span data-stu-id="bc971-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="bc971-108">No entanto, se a exceção não for tratada, a execução do bloco `finally` depende de como a operação de desenrolamento da exceção é disparada.</span><span class="sxs-lookup"><span data-stu-id="bc971-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="bc971-109">Isso, por sua vez, depende da configuração do seu computador.</span><span class="sxs-lookup"><span data-stu-id="bc971-109">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="bc971-110">Normalmente, quando uma exceção sem tratamento encerra um aplicativo, não é importante se o bloco `finally` é executado.</span><span class="sxs-lookup"><span data-stu-id="bc971-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="bc971-111">No entanto, se você tiver instruções em um bloco `finally` que devem ser executadas mesmo nesse caso, uma solução é adicionar um bloco `catch` à instrução `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="bc971-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="bc971-112">Como alternativa, você pode detectar a exceção que pode ser gerada no bloco `try` de uma instrução `try`-`finally` em posição superior na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="bc971-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="bc971-113">Ou seja, você pode detectar a exceção no método que chama o método que contém a instrução `try`-`finally` ou no método que chama esse método ou em qualquer método na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="bc971-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="bc971-114">Se a exceção não for detectada, a execução do bloco `finally` dependerá do sistema operacional escolher disparar uma operação de desenrolamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="bc971-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="bc971-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc971-115">Example</span></span>

<span data-ttu-id="bc971-116">No exemplo a seguir, uma instrução de conversão inválida causa uma exceção `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="bc971-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="bc971-117">A exceção não é tratada.</span><span class="sxs-lookup"><span data-stu-id="bc971-117">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="bc971-118">No exemplo a seguir, uma exceção do método `TryCast` ocorre em um método mais para cima na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="bc971-118">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="bc971-119">Para obter mais informações sobre `finally`, consulte [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="bc971-119">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="bc971-120">C# também contém a [instrução using](using-statement.md), que fornece uma funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.</span><span class="sxs-lookup"><span data-stu-id="bc971-120">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bc971-121">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bc971-121">C# language specification</span></span>

<span data-ttu-id="bc971-122">Para obter mais informações, confira a seção [A instrução try](~/_csharplang/spec/statements.md#the-try-statement) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="bc971-122">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc971-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc971-123">See also</span></span>

- [<span data-ttu-id="bc971-124">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="bc971-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc971-125">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="bc971-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc971-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bc971-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bc971-127">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="bc971-127">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="bc971-128">throw</span><span class="sxs-lookup"><span data-stu-id="bc971-128">throw</span></span>](throw.md)
- [<span data-ttu-id="bc971-129">try-catch</span><span class="sxs-lookup"><span data-stu-id="bc971-129">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="bc971-130">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="bc971-130">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
