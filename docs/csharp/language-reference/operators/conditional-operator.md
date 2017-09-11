---
title: "Operador ?: (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 794ff53fe471ef23163503f59599b528df127e2e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="cac4f-102">Operador ?: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cac4f-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="cac4f-103">O operador condicional (`?:`) retorna um de dois valores dependendo do valor de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="cac4f-103">The conditional operator (`?:`) returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="cac4f-104">Esta é a sintaxe do operador condicional.</span><span class="sxs-lookup"><span data-stu-id="cac4f-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="cac4f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cac4f-105">Remarks</span></span>  
 <span data-ttu-id="cac4f-106">A `condition` deve ser avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="cac4f-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="cac4f-107">Se `condition` for `true`, `first_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="cac4f-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="cac4f-108">Se `condition` for `false`, `second_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="cac4f-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="cac4f-109">Somente uma das duas expressões será avaliada.</span><span class="sxs-lookup"><span data-stu-id="cac4f-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="cac4f-110">O tipo da `first_expression` e `second_expression` devem ser iguais ou uma conversão implícita deve existir de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="cac4f-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="cac4f-111">Você pode expressar cálculos que podem, de outra forma, exigir uma construção `if-else` mais concisamente ao usar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="cac4f-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="cac4f-112">Por exemplo, o código a seguir usa primeiro uma instrução `if` e, em seguida, um operador condicional para classificar um inteiro como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="cac4f-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="cac4f-113">O operador condicional é associativo direito.</span><span class="sxs-lookup"><span data-stu-id="cac4f-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="cac4f-114">A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="cac4f-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="cac4f-115">O operador condicional não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="cac4f-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac4f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cac4f-116">Example</span></span>  
 <span data-ttu-id="cac4f-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cac4f-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac4f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cac4f-118">See Also</span></span>  
 <span data-ttu-id="cac4f-119">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cac4f-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cac4f-120">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cac4f-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cac4f-121">[Operadores do C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="cac4f-121">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="cac4f-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="cac4f-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span></span>  
 <span data-ttu-id="cac4f-123">[Operadores ?. e ?](../../../csharp/language-reference/operators/null-conditional-operators.md) </span><span class="sxs-lookup"><span data-stu-id="cac4f-123">[?. and ?Operators](../../../csharp/language-reference/operators/null-conditional-operators.md) </span></span>  
 [<span data-ttu-id="cac4f-124">Operador ??</span><span class="sxs-lookup"><span data-stu-id="cac4f-124">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)

