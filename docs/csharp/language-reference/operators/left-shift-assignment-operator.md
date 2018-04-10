---
title: Operador &lt;&lt;= (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5c2a177182561075442afc3f1b76603c6646bd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="f18cd-102">Operador &lt;&lt;= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f18cd-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="f18cd-103">O operador de atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="f18cd-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f18cd-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f18cd-104">Remarks</span></span>  
 <span data-ttu-id="f18cd-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="f18cd-105">An expression of the form</span></span>  
  
```  
x <<= y  
```  
  
 <span data-ttu-id="f18cd-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="f18cd-106">is evaluated as</span></span>  
  
```  
x = x << y  
```  
  
 <span data-ttu-id="f18cd-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f18cd-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f18cd-108">O [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="f18cd-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="f18cd-109">O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f18cd-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18cd-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f18cd-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f18cd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f18cd-111">See Also</span></span>  
 [<span data-ttu-id="f18cd-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f18cd-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f18cd-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f18cd-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f18cd-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f18cd-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
