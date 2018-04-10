---
title: Restrição new (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="e86be-102">Restrição new (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e86be-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="e86be-103">A restrição `new` especifica que qualquer argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e86be-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="e86be-104">Para usar a restrição new, o tipo não pode ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="e86be-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e86be-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e86be-105">Example</span></span>  
 <span data-ttu-id="e86be-106">Aplique a restrição `new` a um parâmetro de tipo quando a classe genérica cria novas instâncias do tipo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e86be-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e86be-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e86be-107">Example</span></span>  
 <span data-ttu-id="e86be-108">Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:</span><span class="sxs-lookup"><span data-stu-id="e86be-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="e86be-109">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e86be-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e86be-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e86be-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e86be-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e86be-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="e86be-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e86be-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e86be-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e86be-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e86be-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e86be-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e86be-115">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="e86be-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="e86be-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="e86be-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
