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
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179928"
---
# <a name="break-c-reference"></a><span data-ttu-id="b7cad-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b7cad-102">break (C# Reference)</span></span>

<span data-ttu-id="b7cad-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](./switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="b7cad-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="b7cad-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="b7cad-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="b7cad-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7cad-105">Example</span></span>

<span data-ttu-id="b7cad-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="b7cad-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="b7cad-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7cad-107">Example</span></span>

<span data-ttu-id="b7cad-108">Este exemplo demonstra o uso de `break` em uma instrução [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="b7cad-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="b7cad-109">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="b7cad-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="b7cad-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7cad-110">Example</span></span>

<span data-ttu-id="b7cad-111">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="b7cad-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="b7cad-112">O controle _só_ retornou um nível acima nos loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="b7cad-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="b7cad-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7cad-113">Example</span></span>

<span data-ttu-id="b7cad-114">Neste exemplo, a instrução `break` é usada apenas para interromper a ramificação atual durante cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="b7cad-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="b7cad-115">O loop em si não é afetado pelas instâncias de `break` que pertencem à instrução [switch](./switch.md) aninhada.</span><span class="sxs-lookup"><span data-stu-id="b7cad-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="b7cad-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b7cad-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b7cad-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7cad-117">See also</span></span>

- [<span data-ttu-id="b7cad-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b7cad-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b7cad-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b7cad-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b7cad-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b7cad-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b7cad-121">switch</span><span class="sxs-lookup"><span data-stu-id="b7cad-121">switch</span></span>](./switch.md)
