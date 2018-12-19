---
title: Operador () – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 57c23dbd6ee95597514dba92e7217bdcc3e38f24
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236447"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="125f6-102">Operador () (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="125f6-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="125f6-103">Além de serem usados para especificar a ordem das operações em uma expressão, os parênteses são usados para realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="125f6-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="125f6-104">Especificar conversões ou conversões de tipo.</span><span class="sxs-lookup"><span data-stu-id="125f6-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="125f6-105">Invocar métodos ou delegados.</span><span class="sxs-lookup"><span data-stu-id="125f6-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="125f6-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="125f6-106">Remarks</span></span>  
 <span data-ttu-id="125f6-107">Uma conversão invoca explicitamente o operador de conversão de um tipo para outro. A conversão falhará se nenhum operador de conversão desse tipo estiver definido.</span><span class="sxs-lookup"><span data-stu-id="125f6-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="125f6-108">Para definir um operador de conversão, consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="125f6-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="125f6-109">O operador `()` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="125f6-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="125f6-110">Para obter mais informações, consulte [Conversões e conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="125f6-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="125f6-111">Para obter mais informações sobre a invocação de método, consulte [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="125f6-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="125f6-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="125f6-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="125f6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="125f6-113">See Also</span></span>

- [<span data-ttu-id="125f6-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="125f6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="125f6-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="125f6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="125f6-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="125f6-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
