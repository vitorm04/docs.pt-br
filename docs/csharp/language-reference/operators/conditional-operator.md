---
title: "Operador ?: (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbd434e02ece4843bab4ffded6877f81f622950c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="33d50-102">Operador ?: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="33d50-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="33d50-103">O operador condicional (`?:`), comumente conhecido como o operador condicional ternário, retorna um de dois valores dependendo do valor de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="33d50-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="33d50-104">Esta é a sintaxe do operador condicional.</span><span class="sxs-lookup"><span data-stu-id="33d50-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="33d50-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="33d50-105">Remarks</span></span>  
 <span data-ttu-id="33d50-106">A `condition` deve ser avaliada como `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="33d50-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="33d50-107">Se `condition` for `true`, `first_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="33d50-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="33d50-108">Se `condition` for `false`, `second_expression` será avaliada e se tornará o resultado.</span><span class="sxs-lookup"><span data-stu-id="33d50-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="33d50-109">Somente uma das duas expressões será avaliada.</span><span class="sxs-lookup"><span data-stu-id="33d50-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="33d50-110">O tipo da `first_expression` e `second_expression` devem ser iguais ou uma conversão implícita deve existir de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="33d50-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="33d50-111">Você pode expressar cálculos que podem, de outra forma, exigir uma construção `if-else` mais concisamente ao usar o operador condicional.</span><span class="sxs-lookup"><span data-stu-id="33d50-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="33d50-112">Por exemplo, o código a seguir usa primeiro uma instrução `if` e, em seguida, um operador condicional para classificar um inteiro como positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="33d50-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="33d50-113">O operador condicional é associativo direito.</span><span class="sxs-lookup"><span data-stu-id="33d50-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="33d50-114">A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="33d50-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="33d50-115">O operador condicional não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="33d50-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33d50-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33d50-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="33d50-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33d50-117">See Also</span></span>  
 [<span data-ttu-id="33d50-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="33d50-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="33d50-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="33d50-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33d50-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="33d50-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="33d50-121">if-else</span><span class="sxs-lookup"><span data-stu-id="33d50-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 [<span data-ttu-id="33d50-122">Operadores ?. e ?</span><span class="sxs-lookup"><span data-stu-id="33d50-122">?. and ?Operators</span></span>](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [<span data-ttu-id="33d50-123">Operador ??</span><span class="sxs-lookup"><span data-stu-id="33d50-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
