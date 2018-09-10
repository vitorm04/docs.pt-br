---
title: Instrução break (Referência do C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 9dc71cce3cc0ca4035df483d2b3a3ab9a3bab9c5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44216286"
---
# <a name="break-c-reference"></a><span data-ttu-id="3d231-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3d231-102">break (C# Reference)</span></span>

<span data-ttu-id="3d231-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](../../../csharp/language-reference/keywords/switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="3d231-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="3d231-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="3d231-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="3d231-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d231-105">Example</span></span>

<span data-ttu-id="3d231-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="3d231-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="3d231-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d231-107">Example</span></span>

<span data-ttu-id="3d231-108">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="3d231-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="3d231-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d231-109">Example</span></span>

<span data-ttu-id="3d231-110">Este exemplo demonstra o uso de `break` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="3d231-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="3d231-111">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="3d231-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="3d231-112">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3d231-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3d231-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d231-113">See Also</span></span>

- [<span data-ttu-id="3d231-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3d231-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3d231-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3d231-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3d231-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3d231-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="3d231-117">switch</span><span class="sxs-lookup"><span data-stu-id="3d231-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
- [<span data-ttu-id="3d231-118">Instruções de atalho</span><span class="sxs-lookup"><span data-stu-id="3d231-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
- [<span data-ttu-id="3d231-119">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="3d231-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
