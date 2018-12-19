---
title: Operador &gt;&gt;= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239440"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="e2da5-102">Operador &gt;&gt;= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e2da5-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="e2da5-103">O operador de atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="e2da5-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2da5-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2da5-104">Remarks</span></span>  
 <span data-ttu-id="e2da5-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="e2da5-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="e2da5-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="e2da5-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="e2da5-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="e2da5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e2da5-108">O [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="e2da5-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="e2da5-109">O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e2da5-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2da5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2da5-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e2da5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2da5-111">See Also</span></span>

- [<span data-ttu-id="e2da5-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e2da5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e2da5-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e2da5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e2da5-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e2da5-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
