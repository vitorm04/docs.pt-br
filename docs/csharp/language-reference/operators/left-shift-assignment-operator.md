---
title: Operador &lt;&lt;= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43406968"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="09b7d-102">Operador &lt;&lt;= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="09b7d-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="09b7d-103">O operador de atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="09b7d-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b7d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="09b7d-104">Remarks</span></span>  
 <span data-ttu-id="09b7d-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="09b7d-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="09b7d-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="09b7d-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="09b7d-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="09b7d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="09b7d-108">O [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="09b7d-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="09b7d-109">O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="09b7d-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b7d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09b7d-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="09b7d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b7d-111">See Also</span></span>

- [<span data-ttu-id="09b7d-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="09b7d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="09b7d-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="09b7d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="09b7d-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="09b7d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
