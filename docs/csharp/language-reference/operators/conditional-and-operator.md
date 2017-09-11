---
title: "Operador &amp;&amp; (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1da61947cbc85e5b3045513e99e013d1e4fae4b3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="0c47f-102">Operador &amp;&amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0c47f-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="0c47f-103">O operador AND condicional (`&&`) realiza uma AND lógica de seu operandos `bool`, mas só avalia seu segundo operando se for necessário.</span><span class="sxs-lookup"><span data-stu-id="0c47f-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c47f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c47f-104">Remarks</span></span>  
 <span data-ttu-id="0c47f-105">A operação</span><span class="sxs-lookup"><span data-stu-id="0c47f-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="0c47f-106">corresponde à operação</span><span class="sxs-lookup"><span data-stu-id="0c47f-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="0c47f-107">exceto se `x` for `false`, `y` não será avaliado, porque o resultado da operação AND será `false`, independentemente do valor de `y`.</span><span class="sxs-lookup"><span data-stu-id="0c47f-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="0c47f-108">Isso é conhecido como avaliação de "curto-circuito".</span><span class="sxs-lookup"><span data-stu-id="0c47f-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="0c47f-109">O operador AND condicional não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), também são consideradas sobrecargas dos operadores lógicos condicionais, com algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="0c47f-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c47f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c47f-110">Example</span></span>  
 <span data-ttu-id="0c47f-111">No exemplo a seguir, a expressão condicional na segunda instrução `if` avalia apenas o primeiro operando, porque o operando retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="0c47f-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 <span data-ttu-id="0c47f-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0c47f-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0c47f-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0c47f-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c47f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c47f-114">See Also</span></span>  
 <span data-ttu-id="0c47f-115">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c47f-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0c47f-116">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c47f-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="0c47f-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0c47f-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

