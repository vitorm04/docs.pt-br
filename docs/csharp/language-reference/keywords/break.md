---
description: Instrução break – Referência de C#
title: Instrução break – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134738"
---
# <a name="break-c-reference"></a><span data-ttu-id="fa9b4-103">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fa9b4-103">break (C# Reference)</span></span>

<span data-ttu-id="fa9b4-104">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](./switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="fa9b4-105">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="fa9b4-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa9b4-106">Example</span></span>

<span data-ttu-id="fa9b4-107">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="fa9b4-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa9b4-108">Example</span></span>

<span data-ttu-id="fa9b4-109">Este exemplo demonstra o uso de `break` em uma instrução [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="fa9b4-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="fa9b4-110">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="fa9b4-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="fa9b4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa9b4-111">Example</span></span>

<span data-ttu-id="fa9b4-112">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="fa9b4-113">O controle _só_ retornou um nível acima nos loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="fa9b4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa9b4-114">Example</span></span>

<span data-ttu-id="fa9b4-115">Neste exemplo, a `break` instrução é usada apenas para interromper a ramificação atual durante cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="fa9b4-116">O loop em si não é afetado pelas instâncias do `break` que pertencem à instrução [switch](./switch.md) aninhada.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="fa9b4-117">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fa9b4-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fa9b4-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="fa9b4-118">See also</span></span>

- [<span data-ttu-id="fa9b4-119">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="fa9b4-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fa9b4-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="fa9b4-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fa9b4-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fa9b4-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="fa9b4-122">switch</span><span class="sxs-lookup"><span data-stu-id="fa9b4-122">switch</span></span>](./switch.md)
