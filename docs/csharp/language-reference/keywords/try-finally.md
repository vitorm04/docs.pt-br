---
title: try-finally (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001416"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="5a73c-102">try-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5a73c-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="5a73c-103">Usando um bloco `finally`, você pode limpar todos os recursos alocados em um bloco [try](../../../csharp/language-reference/keywords/try-catch.md) e pode executar código mesmo se uma exceção ocorrer no bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="5a73c-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="5a73c-104">Normalmente, as instruções de um bloco `finally` são executadas quando o controle deixa uma instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="5a73c-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="5a73c-105">A transferência de controle pode ocorrer como resultado da execução normal, da execução de uma instrução `break`, `continue`, `goto` ou `return`, ou da propagação de uma exceção para fora da instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="5a73c-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="5a73c-106">Dentro de uma exceção tratada, é garantido que o bloco `finally` será executado.</span><span class="sxs-lookup"><span data-stu-id="5a73c-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="5a73c-107">No entanto, se a exceção não for tratada, a execução do bloco `finally` depende de como a operação de desenrolamento da exceção é disparada.</span><span class="sxs-lookup"><span data-stu-id="5a73c-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="5a73c-108">Isso, por sua vez, depende da configuração do seu computador.</span><span class="sxs-lookup"><span data-stu-id="5a73c-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="5a73c-109">Normalmente, quando uma exceção sem tratamento encerra um aplicativo, não é importante se o bloco `finally` é executado.</span><span class="sxs-lookup"><span data-stu-id="5a73c-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="5a73c-110">No entanto, se você tiver instruções em um bloco `finally` que devem ser executadas mesmo nesse caso, uma solução é adicionar um bloco `catch` à instrução `try`-`finally`.</span><span class="sxs-lookup"><span data-stu-id="5a73c-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="5a73c-111">Como alternativa, você pode detectar a exceção que pode ser gerada no bloco `try` de uma instrução `try`-`finally` em posição superior na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="5a73c-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="5a73c-112">Ou seja, você pode detectar a exceção no método que chama o método que contém a instrução `try`-`finally` ou no método que chama esse método ou em qualquer método na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="5a73c-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="5a73c-113">Se a exceção não for detectada, a execução do bloco `finally` dependerá do sistema operacional escolher disparar uma operação de desenrolamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="5a73c-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a73c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a73c-114">Example</span></span>  
 <span data-ttu-id="5a73c-115">No exemplo a seguir, uma instrução de conversão inválida causa uma exceção `System.InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="5a73c-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="5a73c-116">A exceção não é tratada.</span><span class="sxs-lookup"><span data-stu-id="5a73c-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="5a73c-117">No exemplo a seguir, uma exceção do método `TryCast` ocorre em um método mais para cima na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="5a73c-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="5a73c-118">Para obter mais informações sobre `finally`, consulte [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="5a73c-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="5a73c-119">C# também contém a [instrução using](../../../csharp/language-reference/keywords/using-statement.md), que fornece uma funcionalidade semelhante para objetos <xref:System.IDisposable> em uma sintaxe conveniente.</span><span class="sxs-lookup"><span data-stu-id="5a73c-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a73c-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5a73c-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a73c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a73c-121">See Also</span></span>

- [<span data-ttu-id="5a73c-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5a73c-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5a73c-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5a73c-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5a73c-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="5a73c-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="5a73c-125">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="5a73c-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [<span data-ttu-id="5a73c-126">Instruções para manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="5a73c-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="5a73c-127">throw</span><span class="sxs-lookup"><span data-stu-id="5a73c-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
- [<span data-ttu-id="5a73c-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="5a73c-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="5a73c-129">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="5a73c-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
