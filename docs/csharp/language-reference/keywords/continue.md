---
title: Instrução continue – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713670"
---
# <a name="continue-c-reference"></a><span data-ttu-id="3ae13-102">continue (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3ae13-102">continue (C# Reference)</span></span>

<span data-ttu-id="3ae13-103">A instrução `continue` passa o controle para a próxima iteração da instrução de circunscrição [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) na qual ela aparece.</span><span class="sxs-lookup"><span data-stu-id="3ae13-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="3ae13-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ae13-104">Example</span></span>

<span data-ttu-id="3ae13-105">Neste exemplo, um contador é inicializado para a contagem de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="3ae13-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="3ae13-106">Ao usar a instrução `continue` junto com a expressão `(i < 9)`, as instruções entre `continue` e o término do corpo `for` serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="3ae13-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="3ae13-107">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3ae13-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3ae13-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ae13-108">See also</span></span>

- [<span data-ttu-id="3ae13-109">C# Referência</span><span class="sxs-lookup"><span data-stu-id="3ae13-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3ae13-110">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="3ae13-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ae13-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3ae13-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3ae13-112">Instrução Break</span><span class="sxs-lookup"><span data-stu-id="3ae13-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
