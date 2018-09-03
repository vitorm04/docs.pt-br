---
title: unchecked (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415770"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="ad890-102">unchecked (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ad890-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="ad890-103">A palavra-chave `unchecked` é usada para suprimir a verificação estouro para conversões e operações aritméticas de tipo integral.</span><span class="sxs-lookup"><span data-stu-id="ad890-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="ad890-104">Em um contexto não verificado, se uma expressão produzir um valor que está fora do intervalo do tipo de destino, o estouro não será sinalizado.</span><span class="sxs-lookup"><span data-stu-id="ad890-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="ad890-105">Por exemplo, como o cálculo no exemplo a seguir é realizado em uma expressão ou bloco `unchecked`, o fato de o resultado ser muito grande para um inteiro é ignorado e `int1` recebe a atribuição do valor -2.147.483.639.</span><span class="sxs-lookup"><span data-stu-id="ad890-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="ad890-106">Se o ambiente `unchecked` for removido, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="ad890-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="ad890-107">O estouro pode ser detectado em tempo de compilação porque todos os termos da expressão são constantes.</span><span class="sxs-lookup"><span data-stu-id="ad890-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="ad890-108">Expressões que contêm termos não constantes não são verificadas por padrão em tempo de compilação e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ad890-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="ad890-109">Consulte [checked](../../../csharp/language-reference/keywords/checked.md) para obter informações sobre como habilitar um ambiente verificado.</span><span class="sxs-lookup"><span data-stu-id="ad890-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="ad890-110">Como a verificação de estouro leva tempo, o uso de código não verificado em situações em que não há nenhum risco de estouro pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="ad890-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="ad890-111">No entanto, se o estouro for uma possibilidade, um ambiente verificado deverá ser usado.</span><span class="sxs-lookup"><span data-stu-id="ad890-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad890-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad890-112">Example</span></span>  
 <span data-ttu-id="ad890-113">Esse exemplo mostra como usar a palavra-chave `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="ad890-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ad890-114">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ad890-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad890-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad890-115">See Also</span></span>

- [<span data-ttu-id="ad890-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ad890-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ad890-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ad890-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ad890-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="ad890-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="ad890-119">Checked e Unchecked</span><span class="sxs-lookup"><span data-stu-id="ad890-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [<span data-ttu-id="ad890-120">checked</span><span class="sxs-lookup"><span data-stu-id="ad890-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
