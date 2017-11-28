---
title: "Operador &amp;&amp; (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="94065-102">Operador &amp;&amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="94065-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="94065-103">O operador AND condicional (`&&`) realiza uma AND lógica de seu operandos `bool`, mas só avalia seu segundo operando se for necessário.</span><span class="sxs-lookup"><span data-stu-id="94065-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94065-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="94065-104">Remarks</span></span>  
 <span data-ttu-id="94065-105">A operação</span><span class="sxs-lookup"><span data-stu-id="94065-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="94065-106">corresponde à operação</span><span class="sxs-lookup"><span data-stu-id="94065-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="94065-107">exceto se `x` for `false`, `y` não será avaliado, porque o resultado da operação AND será `false`, independentemente do valor de `y`.</span><span class="sxs-lookup"><span data-stu-id="94065-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="94065-108">Isso é conhecido como avaliação de "curto-circuito".</span><span class="sxs-lookup"><span data-stu-id="94065-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="94065-109">O operador AND condicional não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), também são consideradas sobrecargas dos operadores lógicos condicionais, com algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="94065-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94065-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94065-110">Example</span></span>  
 <span data-ttu-id="94065-111">No exemplo a seguir, a expressão condicional na segunda instrução `if` avalia apenas o primeiro operando, porque o operando retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="94065-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="94065-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="94065-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94065-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94065-113">See Also</span></span>  
 [<span data-ttu-id="94065-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="94065-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="94065-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="94065-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="94065-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="94065-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
