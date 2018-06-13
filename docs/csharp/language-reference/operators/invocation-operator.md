---
title: Operador () (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275019"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b7b35-102">Operador () (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b7b35-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="b7b35-103">Além de serem usados para especificar a ordem das operações em uma expressão, os parênteses são usados para realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b7b35-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="b7b35-104">Especificar conversões ou conversões de tipo.</span><span class="sxs-lookup"><span data-stu-id="b7b35-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="b7b35-105">Invocar métodos ou delegados.</span><span class="sxs-lookup"><span data-stu-id="b7b35-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="b7b35-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7b35-106">Remarks</span></span>  
 <span data-ttu-id="b7b35-107">Uma conversão invoca explicitamente o operador de conversão de um tipo para outro. A conversão falhará se nenhum operador de conversão desse tipo estiver definido.</span><span class="sxs-lookup"><span data-stu-id="b7b35-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="b7b35-108">Para definir um operador de conversão, consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="b7b35-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="b7b35-109">O operador `()` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="b7b35-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="b7b35-110">Para obter mais informações, consulte [Conversões Cast e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b7b35-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="b7b35-111">Uma expressão de conversão pode levar a uma sintaxe ambígua.</span><span class="sxs-lookup"><span data-stu-id="b7b35-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="b7b35-112">Por exemplo, a expressão `(x)–y` poderia ser interpretada como uma expressão de conversão (uma conversão de –y para tipo x) ou como uma expressão aditiva combinada com uma expressão entre parênteses, que calcula o valor de x – y.</span><span class="sxs-lookup"><span data-stu-id="b7b35-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="b7b35-113">Para obter mais informações sobre a invocação de método, consulte [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="b7b35-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b7b35-114">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b7b35-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7b35-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7b35-115">See Also</span></span>  
 [<span data-ttu-id="b7b35-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b7b35-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b7b35-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b7b35-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7b35-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="b7b35-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
