---
title: Operador true (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96ab7679862959f3c99e31beac0bd5514228bd8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="59c43-102">Operador true (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="59c43-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="59c43-103">Retorna o valor [bool](../../../csharp/language-reference/keywords/bool.md) `true` para indicar que um operando é true, caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="59c43-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="59c43-104">Antes do C# 2.0, os operadores `true` e `false` eram usados para criar tipos que permitem valor nulo definidos pelo usuário que eram compatíveis com tipos como `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="59c43-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="59c43-105">No entanto, a linguagem agora fornece suporte interno para tipos que permitem valor nulo e, sempre que possível, você deve usá-los em vez de sobrecarregar os operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="59c43-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="59c43-106">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="59c43-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="59c43-107">Com boolianos que permitem valor nulo, a expressão `a != b` não é necessariamente igual a `!(a == b)` porque um ou ambos os valores podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="59c43-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="59c43-108">Você precisa sobrecarregar os operadores `true` e `false` separadamente para identificar corretamente os valores nulos na expressão.</span><span class="sxs-lookup"><span data-stu-id="59c43-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="59c43-109">O exemplo a seguir mostra como sobrecarregar e usar os operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="59c43-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 <span data-ttu-id="59c43-110">Um tipo que sobrecarrega os operadores `true` e `false` pode ser usado para a expressão de controle nas instruções [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md) e [for](../../../csharp/language-reference/keywords/for.md), bem como em [expressões condicionais](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59c43-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="59c43-111">Se um tipo define o operador `true`, ele também deve definir o operador [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="59c43-111">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="59c43-112">Um tipo não pode sobrecarregar diretamente os operadores lógicos condicionais ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), mas um efeito equivalente poderá ser obtido ao sobrecarregar os operadores lógicos regulares e operadores `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="59c43-112">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="59c43-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="59c43-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59c43-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59c43-114">See Also</span></span>  
 [<span data-ttu-id="59c43-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="59c43-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="59c43-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="59c43-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="59c43-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="59c43-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="59c43-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="59c43-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="59c43-119">false</span><span class="sxs-lookup"><span data-stu-id="59c43-119">false</span></span>](../../../csharp/language-reference/keywords/false.md)
