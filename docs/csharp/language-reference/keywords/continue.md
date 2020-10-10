---
description: Instrução continue – Referência de C#
title: Instrução continue – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877646"
---
# <a name="continue-c-reference"></a><span data-ttu-id="9d18a-103">continue (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9d18a-103">continue (C# Reference)</span></span>

<span data-ttu-id="9d18a-104">A instrução `continue` passa o controle para a próxima iteração da instrução de circunscrição [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) na qual ela aparece.</span><span class="sxs-lookup"><span data-stu-id="9d18a-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="9d18a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d18a-105">Example</span></span>

<span data-ttu-id="9d18a-106">Neste exemplo, um contador é inicializado para a contagem de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="9d18a-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="9d18a-107">Usando a `continue` instrução em conjunto com a expressão `(i < 9)` , as instruções entre `continue` e o final do `for` corpo são ignoradas nas iterações em que `i` é menor que 9.</span><span class="sxs-lookup"><span data-stu-id="9d18a-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped in the iterations where `i` is less than 9.</span></span> <span data-ttu-id="9d18a-108">Nas duas últimas iterações do `for` loop (onde i = = 9 e i = = 10), a `continue` instrução não é executada e o valor de `i` é impresso no console.</span><span class="sxs-lookup"><span data-stu-id="9d18a-108">In the last two iterations of the `for` loop (where i == 9 and i == 10), the `continue` statement is not executed and the value of `i` is printed to the console.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9d18a-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9d18a-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9d18a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d18a-110">See also</span></span>

- [<span data-ttu-id="9d18a-111">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="9d18a-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9d18a-112">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9d18a-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9d18a-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9d18a-113">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9d18a-114">Instrução break</span><span class="sxs-lookup"><span data-stu-id="9d18a-114">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
