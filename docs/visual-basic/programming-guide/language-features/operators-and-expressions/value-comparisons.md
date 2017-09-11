---
title: "Valor comparações (Visual Basic) | Documentos do Microsoft"
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
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators, comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: 9
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
ms.openlocfilehash: 32a2e1693b4092bad251af67a68ad0ec2ae726a1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="b6a6c-102">Comparações de valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6a6c-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="b6a6c-103">Operadores de comparação podem ser usados para construir expressões que comparam valores de variáveis numéricas.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="b6a6c-104">Essas expressões retornam um `Boolean` valor com base em se a comparação é true ou false.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="b6a6c-105">Estes são exemplos de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="b6a6c-106">A primeira expressão é avaliada como `True`, porque 45 é maior que 26.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="b6a6c-107">O segundo exemplo avalia `False`, porque 26 não é maior do que 45.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="b6a6c-108">Você também pode comparar expressões numéricas dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="b6a6c-109">Expressões que você compara podem estar expressões complexas, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="b6a6c-110">A expressão complexa anterior inclui literais, variáveis e chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="b6a6c-111">As expressões em ambos os lados do operador de comparação são avaliadas, e os valores resultantes são então comparados usando o `>=` operador de comparação.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="b6a6c-112">Se o valor da expressão no lado esquerdo for maior que ou igual ao valor da expressão no lado direito, toda a expressão é avaliada como `True`; caso contrário, ele será avaliado como `False`.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="b6a6c-113">Expressões que comparam valores são mais comumente usadas em `If...Then` construções, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 <span data-ttu-id="b6a6c-114">[!code-vb[VbVbalrOperators&#84;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6a6c-114">[!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]</span></span>  
  
 <span data-ttu-id="b6a6c-115">O `=` sinal é um operador de comparação, bem como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-115">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="b6a6c-116">Quando usado como um operador de comparação, ele avalia se o valor à esquerda é igual ao valor à direita, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-116">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 <span data-ttu-id="b6a6c-117">[!code-vb[VbVbalrOperators&#85;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6a6c-117">[!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]</span></span>  
  
 <span data-ttu-id="b6a6c-118">Você também pode usar uma expressão de comparação em qualquer lugar uma `Boolean` valor é necessário, como em uma `If`, `While`, `Loop`, ou `ElseIf` instrução, ou quando atribuir ou passar um valor para um `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-118">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="b6a6c-119">No exemplo a seguir, o valor retornado pela expressão de comparação é atribuído a um `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="b6a6c-119">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 <span data-ttu-id="b6a6c-120">[!code-vb[VbVbalrOperators&#86;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6a6c-120">[!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a6c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6a6c-121">See Also</span></span>  
 <span data-ttu-id="b6a6c-122">[Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b6a6c-122">[Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="b6a6c-123"> [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6a6c-123"> [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="b6a6c-124"> [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b6a6c-124"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="b6a6c-125"> [Como: calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md) </span><span class="sxs-lookup"><span data-stu-id="b6a6c-125"> [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md) </span></span>  
<span data-ttu-id="b6a6c-126"> [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)</span><span class="sxs-lookup"><span data-stu-id="b6a6c-126"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)</span></span>
