---
title: "Operador &gt;&gt;= (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="d9676-102">Operador &gt;&gt;= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d9676-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="d9676-103">O operador de atribuição de deslocamento para a direita.</span><span class="sxs-lookup"><span data-stu-id="d9676-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9676-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9676-104">Remarks</span></span>  
 <span data-ttu-id="d9676-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="d9676-105">An expression of the form</span></span>  
  
```  
x >>= y  
```  
  
 <span data-ttu-id="d9676-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="d9676-106">is evaluated as</span></span>  
  
```  
x = x >> y  
```  
  
 <span data-ttu-id="d9676-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d9676-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d9676-108">O [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="d9676-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="d9676-109">O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d9676-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9676-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9676-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d9676-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9676-111">See Also</span></span>  
 [<span data-ttu-id="d9676-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d9676-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9676-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d9676-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9676-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d9676-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
