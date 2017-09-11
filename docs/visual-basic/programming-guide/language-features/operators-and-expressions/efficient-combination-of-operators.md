---
title: "Combinação eficiente de operadores (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses, complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bc00d47fcbbee415d152f5e449d542f909ec4ba8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="888da-102">Combinação eficiente de operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="888da-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="888da-103">Expressões complexas podem conter muitos operadores diferentes.</span><span class="sxs-lookup"><span data-stu-id="888da-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="888da-104">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="888da-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="888da-105">Criar expressões complexas, como no exemplo anterior requer uma compreensão completa das regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="888da-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="888da-106">Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="888da-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="888da-107">Expressões entre parênteses</span><span class="sxs-lookup"><span data-stu-id="888da-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="888da-108">Com frequência você deseja operações em uma ordem diferente daquela determinada pela precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="888da-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="888da-109">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="888da-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="888da-110">Multiplica o exemplo anterior `z` por `y`, em seguida, adiciona o resultado para `4`.</span><span class="sxs-lookup"><span data-stu-id="888da-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="888da-111">Mas se você quiser adicionar `y` e `4` antes de multiplicar o resultado por `z`, você pode substituir a precedência do operador normal usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="888da-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="888da-112">Colocando uma expressão entre parênteses, você forçar essa expressão seja avaliada primeiro, independentemente de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="888da-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="888da-113">Para forçar o exemplo anterior para fazer a adição primeiro, você poderia reescrever como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="888da-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="888da-114">O exemplo anterior adiciona `y` e `4`, em seguida, multiplica essa soma pelo `z`.</span><span class="sxs-lookup"><span data-stu-id="888da-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="888da-115">Expressões entre parênteses aninhadas</span><span class="sxs-lookup"><span data-stu-id="888da-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="888da-116">Você pode aninhar expressões em vários níveis de parênteses para substituir a precedência ainda mais.</span><span class="sxs-lookup"><span data-stu-id="888da-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="888da-117">As expressões mais profundamente aninhadas em parênteses são avaliadas primeiro, seguido pelo próximo aninhado mais profundamente, e assim por diante para menos profundamente aninhados e, finalmente, as expressões fora parênteses.</span><span class="sxs-lookup"><span data-stu-id="888da-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="888da-118">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="888da-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="888da-119">No exemplo anterior, `z + 2` é avaliado primeiro e, em seguida, outras expressões entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="888da-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="888da-120">Expoente, que normalmente tem precedência maior do que a adição ou multiplicação, é avaliada por último neste exemplo porque outras expressões estão entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="888da-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888da-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="888da-121">See Also</span></span>  
 <span data-ttu-id="888da-122">[Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="888da-122">[Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="888da-123"> [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="888da-123"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="888da-124"> [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="888da-124"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span></span>  
<span data-ttu-id="888da-125"> [Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="888da-125"> [Logical/Bitwise Operators (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="888da-126"> [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="888da-126"> [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="888da-127"> [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="888da-127"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="888da-128"> [Como: calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md) </span><span class="sxs-lookup"><span data-stu-id="888da-128"> [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md) </span></span>  
<span data-ttu-id="888da-129"> [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)</span><span class="sxs-lookup"><span data-stu-id="888da-129"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)</span></span>
