---
description: Instrução goto – Referência em C#
title: Instrução goto – Referência em C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128420"
---
# <a name="goto-c-reference"></a><span data-ttu-id="bf2c0-103">goto (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bf2c0-103">goto (C# Reference)</span></span>

<span data-ttu-id="bf2c0-104">A declaração `goto` transfere o controle do programa diretamente para uma instrução rotulada.</span><span class="sxs-lookup"><span data-stu-id="bf2c0-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="bf2c0-105">Um uso comum de `goto` é a transferência do controle para um rótulo de caso de opção específico ou para o rótulo padrão em uma instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="bf2c0-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="bf2c0-106">A instrução `goto` também é útil para sair de loops profundamente aninhados.</span><span class="sxs-lookup"><span data-stu-id="bf2c0-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="bf2c0-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf2c0-107">Example</span></span>

<span data-ttu-id="bf2c0-108">O exemplo a seguir demonstra o uso de `goto` em uma instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="bf2c0-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="bf2c0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf2c0-109">Example</span></span>

<span data-ttu-id="bf2c0-110">O exemplo a seguir demonstra o uso de `goto` para sair de loops aninhados.</span><span class="sxs-lookup"><span data-stu-id="bf2c0-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="bf2c0-111">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bf2c0-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bf2c0-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf2c0-112">See also</span></span>

- [<span data-ttu-id="bf2c0-113">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="bf2c0-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bf2c0-114">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="bf2c0-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bf2c0-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bf2c0-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bf2c0-116">Instrução goto (C++)</span><span class="sxs-lookup"><span data-stu-id="bf2c0-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
