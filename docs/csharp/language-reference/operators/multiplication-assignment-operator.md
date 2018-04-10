---
title: Operador *= (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3c1b6-102">Operador \*= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3c1b6-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="3c1b6-103">O operador de atribuição de multiplicação binária.</span><span class="sxs-lookup"><span data-stu-id="3c1b6-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c1b6-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c1b6-104">Remarks</span></span>  
 <span data-ttu-id="3c1b6-105">Uma expressão que usa o operador de atribuição `*=`, como</span><span class="sxs-lookup"><span data-stu-id="3c1b6-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="3c1b6-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="3c1b6-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="3c1b6-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="3c1b6-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="3c1b6-108">O [\* operador](../../../csharp/language-reference/operators/multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.</span><span class="sxs-lookup"><span data-stu-id="3c1b6-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="3c1b6-109">O operador `*=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador *](../../../csharp/language-reference/operators/multiplication-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3c1b6-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1b6-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c1b6-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3c1b6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c1b6-111">See Also</span></span>  
 [<span data-ttu-id="3c1b6-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3c1b6-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3c1b6-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3c1b6-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c1b6-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3c1b6-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
