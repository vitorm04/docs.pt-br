---
title: Operador &gt;= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 9bea9034d2998a589fefca19f41444c9aced6e13
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237708"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="ff85a-102">&gt;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ff85a-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="ff85a-103">Todos os tipos numéricos e de enumeração definem um operador relacional "maior ou igual a", `>=`, que retorna `true` se o primeiro operando é maior ou igual ao segundo, `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="ff85a-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff85a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff85a-104">Remarks</span></span>  
 <span data-ttu-id="ff85a-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `>=`.</span><span class="sxs-lookup"><span data-stu-id="ff85a-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="ff85a-106">Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="ff85a-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="ff85a-107">Se `>=` estiver sobrecarregado, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="ff85a-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="ff85a-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="ff85a-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff85a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff85a-109">Example</span></span>  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ff85a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff85a-110">See Also</span></span>

- [<span data-ttu-id="ff85a-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ff85a-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ff85a-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ff85a-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ff85a-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="ff85a-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
