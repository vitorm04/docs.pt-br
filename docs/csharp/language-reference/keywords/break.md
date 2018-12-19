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
ms.openlocfilehash: 02d12ef92e1361bc8d46603d803a1b8b7c06a0a0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243186"
---
# <a name="break-c-reference"></a><span data-ttu-id="7990f-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7990f-102">break (C# Reference)</span></span>

<span data-ttu-id="7990f-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](../../../csharp/language-reference/keywords/switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="7990f-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="7990f-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="7990f-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="7990f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7990f-105">Example</span></span>

<span data-ttu-id="7990f-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="7990f-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="7990f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7990f-107">Example</span></span>

<span data-ttu-id="7990f-108">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="7990f-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="7990f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7990f-109">Example</span></span>

<span data-ttu-id="7990f-110">Este exemplo demonstra o uso de `break` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="7990f-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="7990f-111">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="7990f-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="7990f-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7990f-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7990f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7990f-113">See Also</span></span>

- [<span data-ttu-id="7990f-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7990f-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7990f-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7990f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7990f-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7990f-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="7990f-117">switch</span><span class="sxs-lookup"><span data-stu-id="7990f-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
- [<span data-ttu-id="7990f-118">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="7990f-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
- [<span data-ttu-id="7990f-119">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="7990f-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
