---
title: Operador %= (Referência de C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998650"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="346d8-102">Operador %= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="346d8-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="346d8-103">Operador de atribuição restante.</span><span class="sxs-lookup"><span data-stu-id="346d8-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="346d8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="346d8-104">Remarks</span></span>  
 <span data-ttu-id="346d8-105">Uma expressão que usa o operador de atribuição `%=`, como</span><span class="sxs-lookup"><span data-stu-id="346d8-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```csharp  
x %= y  
```  
  
 <span data-ttu-id="346d8-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="346d8-106">is equivalent to</span></span>  
  
```csharp  
x = x % y  
```  
  
 <span data-ttu-id="346d8-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="346d8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="346d8-108">O [operador %](../../../csharp/language-reference/operators/remainder-operator.md) é predefinido para tipos numéricos a fim de calcular o restante após a divisão.</span><span class="sxs-lookup"><span data-stu-id="346d8-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="346d8-109">O operador `%=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador %](../../../csharp/language-reference/operators/remainder-operator.md) (consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="346d8-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="346d8-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="346d8-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="346d8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="346d8-111">See Also</span></span>

- [<span data-ttu-id="346d8-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="346d8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="346d8-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="346d8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="346d8-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="346d8-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
