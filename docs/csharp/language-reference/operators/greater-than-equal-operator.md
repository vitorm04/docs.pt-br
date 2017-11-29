---
title: "&gt;Operador = (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f020c2bd8756899908681ab72cac7aa2a203c6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="81b82-102">&gt;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="81b82-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="81b82-103">Todos os tipos numéricos e de enumeração definem um operador relacional "maior ou igual a", `>=`, que retorna `true` se o primeiro operando é maior ou igual ao segundo, `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="81b82-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81b82-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="81b82-104">Remarks</span></span>  
 <span data-ttu-id="81b82-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `>=`.</span><span class="sxs-lookup"><span data-stu-id="81b82-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="81b82-106">Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="81b82-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="81b82-107">Se `>=` estiver sobrecarregado, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="81b82-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="81b82-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="81b82-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81b82-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81b82-109">Example</span></span>  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="81b82-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81b82-110">See Also</span></span>  
 [<span data-ttu-id="81b82-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="81b82-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="81b82-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="81b82-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="81b82-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="81b82-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
