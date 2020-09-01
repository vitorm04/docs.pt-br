---
description: Palavra-chave unchecked – Referência do C#
title: Palavra-chave unchecked – Referência do C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141979"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="6b721-103">unchecked (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6b721-103">unchecked (C# Reference)</span></span>

<span data-ttu-id="6b721-104">A palavra-chave `unchecked` é usada para suprimir a verificação estouro para conversões e operações aritméticas de tipo integral.</span><span class="sxs-lookup"><span data-stu-id="6b721-104">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="6b721-105">Em um contexto não verificado, se uma expressão produzir um valor que está fora do intervalo do tipo de destino, o estouro não será sinalizado.</span><span class="sxs-lookup"><span data-stu-id="6b721-105">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="6b721-106">Por exemplo, como o cálculo no exemplo a seguir é realizado em uma expressão ou bloco `unchecked`, o fato de o resultado ser muito grande para um inteiro é ignorado e `int1` recebe a atribuição do valor -2.147.483.639.</span><span class="sxs-lookup"><span data-stu-id="6b721-106">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="6b721-107">Se o ambiente `unchecked` for removido, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="6b721-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="6b721-108">O estouro pode ser detectado em tempo de compilação porque todos os termos da expressão são constantes.</span><span class="sxs-lookup"><span data-stu-id="6b721-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="6b721-109">Expressões que contêm termos não constantes não são verificadas por padrão em tempo de compilação e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6b721-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="6b721-110">Consulte [checked](checked.md) para obter informações sobre como habilitar um ambiente verificado.</span><span class="sxs-lookup"><span data-stu-id="6b721-110">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="6b721-111">Como a verificação de estouro leva tempo, o uso de código não verificado em situações em que não há nenhum risco de estouro pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6b721-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="6b721-112">No entanto, se o estouro for uma possibilidade, um ambiente verificado deverá ser usado.</span><span class="sxs-lookup"><span data-stu-id="6b721-112">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="6b721-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b721-113">Example</span></span>

<span data-ttu-id="6b721-114">Esse exemplo mostra como usar a palavra-chave `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="6b721-114">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="6b721-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6b721-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6b721-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b721-116">See also</span></span>

- [<span data-ttu-id="6b721-117">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="6b721-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b721-118">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="6b721-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b721-119">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="6b721-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6b721-120">Contexto verificado e não verificado</span><span class="sxs-lookup"><span data-stu-id="6b721-120">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="6b721-121">check</span><span class="sxs-lookup"><span data-stu-id="6b721-121">checked</span></span>](checked.md)
