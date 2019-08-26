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
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602252"
---
# <a name="break-c-reference"></a><span data-ttu-id="0f5f6-102">break (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-102">break (C# Reference)</span></span>

<span data-ttu-id="0f5f6-103">A instrução `break` termina o loop delimitador mais próximo ou a instrução [switch](./switch.md) na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="0f5f6-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="0f5f6-104">Controle é passado para a instrução que segue a instrução encerrada, se houver.</span><span class="sxs-lookup"><span data-stu-id="0f5f6-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="0f5f6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f5f6-105">Example</span></span>

<span data-ttu-id="0f5f6-106">Neste exemplo, a instrução condicional tem um contador que deveria contar de 1 a 100. No entanto, a instrução `break` encerra o loop após 4 contagens.</span><span class="sxs-lookup"><span data-stu-id="0f5f6-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="0f5f6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f5f6-107">Example</span></span>

<span data-ttu-id="0f5f6-108">Neste exemplo, a instrução `break` é usada para interromper um loop aninhado interno e retornar o controle para o loop externo.</span><span class="sxs-lookup"><span data-stu-id="0f5f6-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="0f5f6-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f5f6-109">Example</span></span>

<span data-ttu-id="0f5f6-110">Este exemplo demonstra o uso de `break` em uma instrução [switch](./switch.md).</span><span class="sxs-lookup"><span data-stu-id="0f5f6-110">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="0f5f6-111">Se você digitou `4`, a saída seria:</span><span class="sxs-lookup"><span data-stu-id="0f5f6-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="0f5f6-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0f5f6-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0f5f6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f5f6-113">See also</span></span>

- [<span data-ttu-id="0f5f6-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0f5f6-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0f5f6-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0f5f6-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0f5f6-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0f5f6-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0f5f6-117">switch</span><span class="sxs-lookup"><span data-stu-id="0f5f6-117">switch</span></span>](./switch.md)
