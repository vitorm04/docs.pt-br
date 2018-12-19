---
title: Instrução continue – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: fbb5d170f10c0a4b6c6edeae6c3f4a549de65525
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243888"
---
# <a name="continue-c-reference"></a><span data-ttu-id="10c97-102">continue (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="10c97-102">continue (C# Reference)</span></span>

<span data-ttu-id="10c97-103">A instrução `continue` passa o controle para a próxima iteração da instrução de circunscrição [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md) ou [foreach](../../../csharp/language-reference/keywords/foreach-in.md) na qual ela aparece.</span><span class="sxs-lookup"><span data-stu-id="10c97-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="10c97-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10c97-104">Example</span></span>

<span data-ttu-id="10c97-105">Neste exemplo, um contador é inicializado para a contagem de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="10c97-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="10c97-106">Ao usar a instrução `continue` junto com a expressão `(i < 9)`, as instruções entre `continue` e o término do corpo `for` serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="10c97-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="10c97-107">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="10c97-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10c97-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10c97-108">See also</span></span>

- [<span data-ttu-id="10c97-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="10c97-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="10c97-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="10c97-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="10c97-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="10c97-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="10c97-112">Instrução Break</span><span class="sxs-lookup"><span data-stu-id="10c97-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
- [<span data-ttu-id="10c97-113">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="10c97-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)