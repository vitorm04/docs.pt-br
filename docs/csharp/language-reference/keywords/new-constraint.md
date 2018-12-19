---
title: Restrição new – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: de0798319d91032143cb806d6d39338c4f51ac8f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237838"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="83811-102">Restrição new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="83811-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="83811-103">A restrição `new` especifica que qualquer argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="83811-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="83811-104">Para usar a restrição new, o tipo não pode ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="83811-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="83811-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83811-105">Example</span></span>

<span data-ttu-id="83811-106">Aplique a restrição `new` a um parâmetro de tipo quando a classe genérica cria novas instâncias do tipo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="83811-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="83811-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83811-107">Example</span></span>

<span data-ttu-id="83811-108">Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:</span><span class="sxs-lookup"><span data-stu-id="83811-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="83811-109">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="83811-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83811-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="83811-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="83811-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83811-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="83811-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="83811-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="83811-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="83811-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83811-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="83811-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="83811-115">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="83811-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="83811-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="83811-116">Generics</span></span>](../../programming-guide/generics/index.md)