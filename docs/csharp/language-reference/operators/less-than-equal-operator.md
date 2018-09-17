---
title: '&lt;Operador = (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: afbb932c1be010790236bec73a36acf0f01b97f4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45595049"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="2bfad-102">&lt;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2bfad-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="2bfad-103">Todos os tipos numéricos e de enumeração definem um operador relacional "menor ou igual" (`<=`) que retorna `true` se o primeiro operando é menor ou igual ao segundo, `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="2bfad-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bfad-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bfad-104">Remarks</span></span>  
 <span data-ttu-id="2bfad-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `<=`.</span><span class="sxs-lookup"><span data-stu-id="2bfad-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="2bfad-106">Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="2bfad-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="2bfad-107">Se `<=` estiver sobrecarregado, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="2bfad-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="2bfad-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="2bfad-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bfad-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bfad-109">Example</span></span>  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2bfad-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bfad-110">See Also</span></span>

- [<span data-ttu-id="2bfad-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2bfad-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2bfad-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2bfad-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2bfad-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="2bfad-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="2bfad-114">explicit</span><span class="sxs-lookup"><span data-stu-id="2bfad-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
