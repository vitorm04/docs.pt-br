---
title: "&amp;Operador = (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="db545-102">&amp;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="db545-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="db545-103">O operador de atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="db545-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db545-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="db545-104">Remarks</span></span>  
 <span data-ttu-id="db545-105">Uma expressão que usa o operador de atribuição `&=`, como</span><span class="sxs-lookup"><span data-stu-id="db545-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="db545-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="db545-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="db545-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="db545-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="db545-108">O [operador &](../../../csharp/language-reference/operators/and-operator.md) executa uma operação AND lógica bit a bit em operandos integrais e AND lógica em operandos `bool`.</span><span class="sxs-lookup"><span data-stu-id="db545-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="db545-109">O operador `&=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &](../../../csharp/language-reference/operators/and-operator.md) binário (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="db545-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db545-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db545-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="db545-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db545-111">See Also</span></span>  
 [<span data-ttu-id="db545-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="db545-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="db545-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="db545-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db545-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="db545-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
