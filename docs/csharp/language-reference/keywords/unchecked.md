---
title: Palavra-chave unchecked – Referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 44301333f7a36e6b0baa6ea9e089d930bb485a45
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238449"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="7dce6-102">unchecked (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7dce6-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="7dce6-103">A palavra-chave `unchecked` é usada para suprimir a verificação estouro para conversões e operações aritméticas de tipo integral.</span><span class="sxs-lookup"><span data-stu-id="7dce6-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="7dce6-104">Em um contexto não verificado, se uma expressão produzir um valor que está fora do intervalo do tipo de destino, o estouro não será sinalizado.</span><span class="sxs-lookup"><span data-stu-id="7dce6-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="7dce6-105">Por exemplo, como o cálculo no exemplo a seguir é realizado em uma expressão ou bloco `unchecked`, o fato de o resultado ser muito grande para um inteiro é ignorado e `int1` recebe a atribuição do valor -2.147.483.639.</span><span class="sxs-lookup"><span data-stu-id="7dce6-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="7dce6-106">Se o ambiente `unchecked` for removido, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="7dce6-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="7dce6-107">O estouro pode ser detectado em tempo de compilação porque todos os termos da expressão são constantes.</span><span class="sxs-lookup"><span data-stu-id="7dce6-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="7dce6-108">Expressões que contêm termos não constantes não são verificadas por padrão em tempo de compilação e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7dce6-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="7dce6-109">Consulte [checked](checked.md) para obter informações sobre como habilitar um ambiente verificado.</span><span class="sxs-lookup"><span data-stu-id="7dce6-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="7dce6-110">Como a verificação de estouro leva tempo, o uso de código não verificado em situações em que não há nenhum risco de estouro pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7dce6-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="7dce6-111">No entanto, se o estouro for uma possibilidade, um ambiente verificado deverá ser usado.</span><span class="sxs-lookup"><span data-stu-id="7dce6-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="7dce6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7dce6-112">Example</span></span>

<span data-ttu-id="7dce6-113">Esse exemplo mostra como usar a palavra-chave `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="7dce6-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="7dce6-114">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7dce6-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7dce6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dce6-115">See also</span></span>

- [<span data-ttu-id="7dce6-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7dce6-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7dce6-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7dce6-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7dce6-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7dce6-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7dce6-119">Checked e Unchecked</span><span class="sxs-lookup"><span data-stu-id="7dce6-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="7dce6-120">checked</span><span class="sxs-lookup"><span data-stu-id="7dce6-120">checked</span></span>](checked.md)