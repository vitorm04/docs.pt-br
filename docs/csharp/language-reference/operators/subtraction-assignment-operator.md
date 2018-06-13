---
title: Operador -= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 2f37bfa303fb523840b15e896ee3b4a967eb5b2b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171449"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="13f26-102">Operador -= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="13f26-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="13f26-103">O operador de atribuição de subtração.</span><span class="sxs-lookup"><span data-stu-id="13f26-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f26-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="13f26-104">Remarks</span></span>  
 <span data-ttu-id="13f26-105">Uma expressão que usa o operador de atribuição `-=`, como</span><span class="sxs-lookup"><span data-stu-id="13f26-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="13f26-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="13f26-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="13f26-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="13f26-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="13f26-108">O significado do [operador –](../../../csharp/language-reference/operators/subtraction-operator.md) depende dos tipos do `x` e `y` (subtração para operandos numéricos, remoção de delegado para operandos de delegado e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="13f26-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="13f26-109">O operador `-=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [- operador](../../../csharp/language-reference/operators/subtraction-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="13f26-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="13f26-110">O operador -= também é usado em C# para cancelar a assinatura de um evento.</span><span class="sxs-lookup"><span data-stu-id="13f26-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="13f26-111">Para obter mais informações, consulte [Como Realizar e Cancelar a Assinatura de Eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="13f26-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f26-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13f26-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="13f26-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13f26-113">See Also</span></span>  
 [<span data-ttu-id="13f26-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="13f26-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="13f26-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="13f26-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="13f26-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="13f26-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
