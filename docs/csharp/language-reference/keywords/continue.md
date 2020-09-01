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
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128433"
---
# <a name="continue-c-reference"></a><span data-ttu-id="05324-103">continue (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="05324-103">continue (C# Reference)</span></span>

<span data-ttu-id="05324-104">A instrução `continue` passa o controle para a próxima iteração da instrução de circunscrição [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) na qual ela aparece.</span><span class="sxs-lookup"><span data-stu-id="05324-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="05324-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05324-105">Example</span></span>

<span data-ttu-id="05324-106">Neste exemplo, um contador é inicializado para a contagem de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="05324-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="05324-107">Ao usar a instrução `continue` junto com a expressão `(i < 9)`, as instruções entre `continue` e o término do corpo `for` serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="05324-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="05324-108">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="05324-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="05324-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="05324-109">See also</span></span>

- [<span data-ttu-id="05324-110">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="05324-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05324-111">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="05324-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05324-112">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="05324-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="05324-113">Instrução break</span><span class="sxs-lookup"><span data-stu-id="05324-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
