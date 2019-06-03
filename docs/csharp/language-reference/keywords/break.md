---
title: Instrução break – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 15b193d9f294c01826b6b60587678ad76248e976
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422069"
---
# <a name="break-c-reference"></a><span data-ttu-id="d3ba7-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d3ba7-102">break (C# Reference)</span></span>

<span data-ttu-id="d3ba7-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](../../../csharp/language-reference/keywords/switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="d3ba7-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="d3ba7-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3ba7-105">Example</span></span>

<span data-ttu-id="d3ba7-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="d3ba7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3ba7-107">Example</span></span>

<span data-ttu-id="d3ba7-108">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="d3ba7-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="d3ba7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3ba7-109">Example</span></span>

<span data-ttu-id="d3ba7-110">Este exemplo demonstra o uso de `break` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="d3ba7-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="d3ba7-111">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="d3ba7-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="d3ba7-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d3ba7-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d3ba7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3ba7-113">See also</span></span>

- [<span data-ttu-id="d3ba7-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d3ba7-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d3ba7-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d3ba7-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d3ba7-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d3ba7-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="d3ba7-117">switch</span><span class="sxs-lookup"><span data-stu-id="d3ba7-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
