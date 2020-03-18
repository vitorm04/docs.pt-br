---
title: try-finally – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713008"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="7e3e4-102">try-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7e3e4-102">try-finally (C# Reference)</span></span>

<span data-ttu-id="7e3e4-103">Usando um bloco `finally`, você pode limpar todos os recursos alocados em um bloco [try](try-catch.md) e pode executar código mesmo se uma exceção ocorrer no bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="7e3e4-104">Normalmente, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="7e3e4-105">A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma instrução `break`, `continue`, `goto` ou `return`, ou da propagação de uma exceção para fora da instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="7e3e4-106">Dentro de uma exceção tratada, é garantido que o bloco `finally` será executado.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="7e3e4-107">No entanto, se a exceção não for tratada, a execução do bloco `finally` depende de como a operação de desenrolamento da exceção é disparada.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="7e3e4-108">Isso, por sua vez, depende da configuração do seu computador.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-108">That, in turn, is dependent on how your computer is set up.</span></span>

<span data-ttu-id="7e3e4-109">Normalmente, quando uma exceção sem tratamento encerra um aplicativo, não é importante se o bloco `finally` é executado.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="7e3e4-110">No entanto, se você tiver instruções em um bloco `finally` que devem ser executadas mesmo nesse caso, uma solução é adicionar um bloco `catch` à instrução `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="7e3e4-111">Como alternativa, você pode detectar a exceção que pode ser gerada no bloco `try` de uma instrução `try`-`finally` em posição superior na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="7e3e4-112">Ou seja, você pode detectar a exceção no método que chama o método que contém a instrução `try`-`finally` ou no método que chama esse método ou em qualquer método na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="7e3e4-113">Se a exceção não for detectada, a execução do bloco `finally` dependerá do sistema operacional escolher disparar uma operação de desenrolamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="7e3e4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e3e4-114">Example</span></span>

<span data-ttu-id="7e3e4-115">No exemplo a seguir, uma instrução de conversão inválida causa uma exceção `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="7e3e4-116">A exceção não é tratada.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-116">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="7e3e4-117">No exemplo a seguir, uma exceção do método `TryCast` ocorre em um método mais para cima na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="7e3e4-118">Para obter mais informações sobre `finally`, consulte [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e4-118">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="7e3e4-119">C# também contém a [instrução using](using-statement.md), que fornece uma funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.</span><span class="sxs-lookup"><span data-stu-id="7e3e4-119">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7e3e4-120">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7e3e4-120">C# language specification</span></span>

<span data-ttu-id="7e3e4-121">Para obter mais informações, confira a seção [A instrução try](~/_csharplang/spec/statements.md#the-try-statement) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e4-121">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e3e4-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e3e4-122">See also</span></span>

- [<span data-ttu-id="7e3e4-123">C# Referência</span><span class="sxs-lookup"><span data-stu-id="7e3e4-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7e3e4-124">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="7e3e4-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7e3e4-125">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7e3e4-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7e3e4-126">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="7e3e4-126">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="7e3e4-127">Jogar</span><span class="sxs-lookup"><span data-stu-id="7e3e4-127">throw</span></span>](throw.md)
- [<span data-ttu-id="7e3e4-128">tentar pegar</span><span class="sxs-lookup"><span data-stu-id="7e3e4-128">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="7e3e4-129">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="7e3e4-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
