---
title: Restrição new (Referência em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087005"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="bba01-102">Restrição new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="bba01-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="bba01-103">A restrição `new` especifica que qualquer argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bba01-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="bba01-104">Para usar a restrição new, o tipo não pode ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="bba01-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="bba01-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bba01-105">Example</span></span>

<span data-ttu-id="bba01-106">Aplique a restrição `new` a um parâmetro de tipo quando a classe genérica cria novas instâncias do tipo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bba01-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="bba01-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bba01-107">Example</span></span>

<span data-ttu-id="bba01-108">Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:</span><span class="sxs-lookup"><span data-stu-id="bba01-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="bba01-109">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="bba01-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bba01-110">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bba01-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bba01-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bba01-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="bba01-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bba01-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="bba01-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bba01-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bba01-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bba01-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bba01-115">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="bba01-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="bba01-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="bba01-116">Generics</span></span>](../../programming-guide/generics/index.md)