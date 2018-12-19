---
title: try-catch-finally – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 3419ad46d5bbe13bb4308ad15b7819d615cdbe86
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244720"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="cc6f7-102">try-catch-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cc6f7-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="cc6f7-103">Um uso comum de `catch` e `finally` juntos é obter e usar recursos em um bloco `try`, lidar com circunstâncias excepcionais em um bloco `catch` e liberar os recursos no bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="cc6f7-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="cc6f7-104">Para obter mais informações e exemplos sobre como lançar exceções, consulte [try-catch](try-catch.md) e [Lançando exceções](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc6f7-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="cc6f7-105">Para obter mais informações sobre o bloco `finally`, consulte [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="cc6f7-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="cc6f7-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc6f7-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="cc6f7-107">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cc6f7-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cc6f7-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc6f7-108">See also</span></span>

- [<span data-ttu-id="cc6f7-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cc6f7-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc6f7-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cc6f7-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc6f7-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="cc6f7-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cc6f7-112">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="cc6f7-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="cc6f7-113">Instruções para manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="cc6f7-113">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="cc6f7-114">throw</span><span class="sxs-lookup"><span data-stu-id="cc6f7-114">throw</span></span>](throw.md)
- [<span data-ttu-id="cc6f7-115">Como: Gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="cc6f7-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="cc6f7-116">Instrução using</span><span class="sxs-lookup"><span data-stu-id="cc6f7-116">using Statement</span></span>](using-statement.md)