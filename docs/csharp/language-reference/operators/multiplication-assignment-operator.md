---
title: Operador *= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171544"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a90b4-102">Operador \*= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a90b4-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="a90b4-103">O operador de atribuição de multiplicação binária.</span><span class="sxs-lookup"><span data-stu-id="a90b4-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a90b4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a90b4-104">Remarks</span></span>  
 <span data-ttu-id="a90b4-105">Uma expressão que usa o operador de atribuição `*=`, como</span><span class="sxs-lookup"><span data-stu-id="a90b4-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="a90b4-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="a90b4-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="a90b4-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="a90b4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a90b4-108">O [\* operador](../../../csharp/language-reference/operators/multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.</span><span class="sxs-lookup"><span data-stu-id="a90b4-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="a90b4-109">O operador `*=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador *](../../../csharp/language-reference/operators/multiplication-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a90b4-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a90b4-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a90b4-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a90b4-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a90b4-111">See Also</span></span>  
 [<span data-ttu-id="a90b4-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a90b4-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a90b4-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a90b4-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a90b4-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a90b4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
