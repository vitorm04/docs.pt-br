---
title: '&amp;Operador = (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 092f46ddd8ca52e2d705200768c93a3473f1520f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="a253a-102">&amp;Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a253a-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="a253a-103">O operador de atribuição AND.</span><span class="sxs-lookup"><span data-stu-id="a253a-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a253a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a253a-104">Remarks</span></span>  
 <span data-ttu-id="a253a-105">Uma expressão que usa o operador de atribuição `&=`, como</span><span class="sxs-lookup"><span data-stu-id="a253a-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="a253a-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="a253a-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="a253a-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="a253a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a253a-108">O [operador &](../../../csharp/language-reference/operators/and-operator.md) executa uma operação AND lógica bit a bit em operandos integrais e AND lógica em operandos `bool`.</span><span class="sxs-lookup"><span data-stu-id="a253a-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="a253a-109">O operador `&=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &](../../../csharp/language-reference/operators/and-operator.md) binário (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a253a-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a253a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a253a-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a253a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a253a-111">See Also</span></span>  
 [<span data-ttu-id="a253a-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a253a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a253a-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a253a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a253a-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a253a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
