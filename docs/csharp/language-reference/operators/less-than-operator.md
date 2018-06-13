---
title: Operador &lt; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: eceb6214e4e625aa71e12788d5dd5e8324c75443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270225"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="1a4a5-102">Operador &lt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1a4a5-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="1a4a5-103">Todos os tipos numéricos e de enumeração definem um operador relacional "menor que" (`<`) que retornará `true` se o primeiro operando for menor que o segundo, `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="1a4a5-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a4a5-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a4a5-104">Remarks</span></span>  
 <span data-ttu-id="1a4a5-105">Os tipos definidos pelo usuário podem sobrecarregar o operador `<` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1a4a5-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1a4a5-106">Se `<` estiver sobrecarregado, [>](../../../csharp/language-reference/operators/greater-than-operator.md) também deverá estar sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="1a4a5-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="1a4a5-107">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="1a4a5-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a4a5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a4a5-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1a4a5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a4a5-109">See Also</span></span>  
 [<span data-ttu-id="1a4a5-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1a4a5-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1a4a5-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1a4a5-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1a4a5-112">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="1a4a5-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
