---
title: Restrição new – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401490"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="18409-102">Restrição new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="18409-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="18409-103">A restrição `new` especifica que um argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18409-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="18409-104">Para usar a restrição `new`, o tipo não pode ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="18409-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="18409-105">Aplique a restrição `new` a um parâmetro de tipo quando uma classe genérica criar novas instâncias do tipo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="18409-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="18409-106">Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:</span><span class="sxs-lookup"><span data-stu-id="18409-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="18409-107">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="18409-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="18409-108">Você também pode usar a palavra-chave `new` para [criar uma instância de um tipo](../operators/new-operator.md) ou como um [modificador de declaração de membro](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="18409-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="18409-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="18409-109">C# language specification</span></span>

<span data-ttu-id="18409-110">Para obter mais informações, confira a seção [Restrições de parâmetro de tipo](~/_csharplang/spec/classes.md#type-parameter-constraints) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="18409-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18409-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18409-111">See also</span></span>

- [<span data-ttu-id="18409-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="18409-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="18409-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="18409-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18409-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="18409-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="18409-115">Genéricos</span><span class="sxs-lookup"><span data-stu-id="18409-115">Generics</span></span>](../../programming-guide/generics/index.md)
