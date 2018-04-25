---
title: Operador %= (Referência de C#)
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 864b96dcf16e4756cd0e74a6e02297660e72357e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d0e48-102">Operador %= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d0e48-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="d0e48-103">Operador de atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="d0e48-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0e48-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0e48-104">Remarks</span></span>  
 <span data-ttu-id="d0e48-105">Uma expressão que usa o operador de atribuição `%=`, como</span><span class="sxs-lookup"><span data-stu-id="d0e48-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="d0e48-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="d0e48-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="d0e48-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d0e48-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d0e48-108">O [operador %](../../../csharp/language-reference/operators/remainder-operator.md) é predefinido para tipos numéricos a fim de calcular o restante após a divisão.</span><span class="sxs-lookup"><span data-stu-id="d0e48-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="d0e48-109">O operador `%=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador %](../../../csharp/language-reference/operators/remainder-operator.md) (consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d0e48-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0e48-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0e48-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d0e48-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0e48-111">See Also</span></span>  
 [<span data-ttu-id="d0e48-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d0e48-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d0e48-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d0e48-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d0e48-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d0e48-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
