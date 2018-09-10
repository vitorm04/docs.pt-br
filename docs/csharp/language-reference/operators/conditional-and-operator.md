---
title: Operador &amp;&amp; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529229"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="6d04c-102">Operador &amp;&amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6d04c-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="6d04c-103">O operador AND condicional (`&&`) realiza uma AND lógica de seu operandos `bool`, mas só avalia seu segundo operando se for necessário.</span><span class="sxs-lookup"><span data-stu-id="6d04c-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d04c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d04c-104">Remarks</span></span>  
 <span data-ttu-id="6d04c-105">A operação</span><span class="sxs-lookup"><span data-stu-id="6d04c-105">The operation</span></span>  
  
```csharp  
x && y  
```  
  
 <span data-ttu-id="6d04c-106">corresponde à operação</span><span class="sxs-lookup"><span data-stu-id="6d04c-106">corresponds to the operation</span></span>  
  
```csharp  
x & y  
```  
  
 <span data-ttu-id="6d04c-107">exceto se `x` for `false`, `y` não será avaliado, porque o resultado da operação AND será `false`, independentemente do valor de `y`.</span><span class="sxs-lookup"><span data-stu-id="6d04c-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="6d04c-108">Isso é conhecido como avaliação de "curto-circuito".</span><span class="sxs-lookup"><span data-stu-id="6d04c-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="6d04c-109">O operador AND condicional não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), também são consideradas sobrecargas dos operadores lógicos condicionais, com algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="6d04c-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d04c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d04c-110">Example</span></span>  
 <span data-ttu-id="6d04c-111">No exemplo a seguir, a expressão condicional na segunda instrução `if` avalia apenas o primeiro operando, porque o operando retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="6d04c-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d04c-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6d04c-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d04c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d04c-113">See Also</span></span>

- [<span data-ttu-id="6d04c-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6d04c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6d04c-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6d04c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6d04c-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6d04c-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
