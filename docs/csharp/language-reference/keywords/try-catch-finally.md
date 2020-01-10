---
title: try-catch-finally – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713034"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="99305-102">try-catch-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="99305-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="99305-103">Um uso comum de `catch` e `finally` juntos é obter e usar recursos em um bloco `try`, lidar com circunstâncias excepcionais em um bloco `catch` e liberar os recursos no bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="99305-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="99305-104">Para obter mais informações e exemplos sobre como lançar exceções, consulte [try-catch](try-catch.md) e [Lançando exceções](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="99305-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="99305-105">Para obter mais informações sobre o bloco `finally`, consulte [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="99305-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="99305-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99305-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="99305-107">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="99305-107">C# language specification</span></span>

<span data-ttu-id="99305-108">Para obter mais informações, confira a seção [A instrução try](~/_csharplang/spec/statements.md#the-try-statement) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="99305-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99305-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="99305-109">See also</span></span>

- [<span data-ttu-id="99305-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="99305-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99305-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="99305-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="99305-112">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="99305-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="99305-113">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="99305-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="99305-114">throw</span><span class="sxs-lookup"><span data-stu-id="99305-114">throw</span></span>](throw.md)
- [<span data-ttu-id="99305-115">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="99305-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="99305-116">Instrução using</span><span class="sxs-lookup"><span data-stu-id="99305-116">using Statement</span></span>](using-statement.md)
