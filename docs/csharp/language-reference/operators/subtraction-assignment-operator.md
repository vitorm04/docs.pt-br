---
title: Operador -= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239573"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="80d60-102">Operador -= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="80d60-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="80d60-103">O operador de atribuição de subtração.</span><span class="sxs-lookup"><span data-stu-id="80d60-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80d60-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="80d60-104">Remarks</span></span>  
 <span data-ttu-id="80d60-105">Uma expressão que usa o operador de atribuição `-=`, como</span><span class="sxs-lookup"><span data-stu-id="80d60-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="80d60-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="80d60-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="80d60-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="80d60-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="80d60-108">O significado do [operador –](../../../csharp/language-reference/operators/subtraction-operator.md) depende dos tipos do `x` e `y` (subtração para operandos numéricos, remoção de delegado para operandos de delegado e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="80d60-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="80d60-109">O operador `-=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [- operador](../../../csharp/language-reference/operators/subtraction-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="80d60-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="80d60-110">O operador -= também é usado em C# para cancelar a assinatura de um evento.</span><span class="sxs-lookup"><span data-stu-id="80d60-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="80d60-111">Confira mais informações em [Como: realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="80d60-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d60-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80d60-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="80d60-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d60-113">See Also</span></span>

- [<span data-ttu-id="80d60-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="80d60-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="80d60-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="80d60-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="80d60-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="80d60-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
