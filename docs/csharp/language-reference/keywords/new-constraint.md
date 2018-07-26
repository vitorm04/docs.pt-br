---
title: Restrição new (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199451"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="e2167-102">Restrição new (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e2167-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="e2167-103">A restrição `new` especifica que qualquer argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e2167-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="e2167-104">Para usar a restrição new, o tipo não pode ser abstrato.</span><span class="sxs-lookup"><span data-stu-id="e2167-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2167-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2167-105">Example</span></span>  
 <span data-ttu-id="e2167-106">Aplique a restrição `new` a um parâmetro de tipo quando a classe genérica cria novas instâncias do tipo, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2167-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e2167-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2167-107">Example</span></span>  
 <span data-ttu-id="e2167-108">Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:</span><span class="sxs-lookup"><span data-stu-id="e2167-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="e2167-109">Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e2167-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e2167-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e2167-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e2167-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2167-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="e2167-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e2167-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e2167-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e2167-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e2167-114">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e2167-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e2167-115">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="e2167-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="e2167-116">Genéricos</span><span class="sxs-lookup"><span data-stu-id="e2167-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
