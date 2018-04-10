---
title: Operador || (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1ba82-102">Operador || (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1ba82-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="1ba82-103">O operador condicional OR (`||`) executa um OR lógico de seus operandos `bool`.</span><span class="sxs-lookup"><span data-stu-id="1ba82-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="1ba82-104">Se o primeiro operando for avaliado como `true`, o segundo operando não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="1ba82-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="1ba82-105">Se o primeiro operando for avaliado como `false`, o segundo operador determinará se a expressão OR como um todo será avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="1ba82-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ba82-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ba82-106">Remarks</span></span>  
 <span data-ttu-id="1ba82-107">A operação</span><span class="sxs-lookup"><span data-stu-id="1ba82-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="1ba82-108">corresponde à operação</span><span class="sxs-lookup"><span data-stu-id="1ba82-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="1ba82-109">exceto se `x` for `true`, `y` não será avaliado, porque a operação OR será `true`, independentemente do valor de `y`.</span><span class="sxs-lookup"><span data-stu-id="1ba82-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="1ba82-110">Esse conceito é conhecido como avaliação de “curto-circuito”.</span><span class="sxs-lookup"><span data-stu-id="1ba82-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="1ba82-111">O operador condicional OR não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), com algumas restrições, também são consideradas sobrecargas dos operadores lógicos condicionais.</span><span class="sxs-lookup"><span data-stu-id="1ba82-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ba82-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ba82-112">Example</span></span>  
 <span data-ttu-id="1ba82-113">Nos exemplos a seguir, a expressão que usa `||` avalia apenas o primeiro operando.</span><span class="sxs-lookup"><span data-stu-id="1ba82-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="1ba82-114">A expressão que usa `|` avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="1ba82-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="1ba82-115">No segundo exemplo, uma exceção de tempo de execução ocorrerá se ambos os operandos forem avaliados.</span><span class="sxs-lookup"><span data-stu-id="1ba82-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1ba82-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ba82-116">See Also</span></span>  
 [<span data-ttu-id="1ba82-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1ba82-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1ba82-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1ba82-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1ba82-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="1ba82-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
