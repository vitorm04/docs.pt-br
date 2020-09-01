---
description: try-catch-finally – Referência de C#
title: try-catch-finally – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 6e85330e12c53e0728ef671530709748090ebe02
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142005"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="f1893-103">try-catch-finally (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f1893-103">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="f1893-104">Um uso comum de `catch` e `finally` juntos é obter e usar recursos em um bloco `try`, lidar com circunstâncias excepcionais em um bloco `catch` e liberar os recursos no bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="f1893-104">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="f1893-105">Para obter mais informações e exemplos sobre como lançar exceções, consulte [try-catch](try-catch.md) e [Lançando exceções](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1893-105">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="f1893-106">Para obter mais informações sobre o bloco `finally`, consulte [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="f1893-106">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="f1893-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1893-107">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="f1893-108">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f1893-108">C# language specification</span></span>

<span data-ttu-id="f1893-109">Para obter mais informações, confira a seção [A instrução try](~/_csharplang/spec/statements.md#the-try-statement) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f1893-109">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1893-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1893-110">See also</span></span>

- [<span data-ttu-id="f1893-111">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="f1893-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f1893-112">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="f1893-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f1893-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f1893-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f1893-114">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="f1893-114">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="f1893-115">throw</span><span class="sxs-lookup"><span data-stu-id="f1893-115">throw</span></span>](throw.md)
- [<span data-ttu-id="f1893-116">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="f1893-116">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="f1893-117">Instrução using</span><span class="sxs-lookup"><span data-stu-id="f1893-117">using Statement</span></span>](using-statement.md)
