---
title: "Como: calcular valores numéricos (Visual Basic) | Documentos do Microsoft"
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
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
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
ms.openlocfilehash: fe781cca8f716c792d3af153b2004c716bc87f90
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="1d5b6-102">Como calcular valores numéricos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d5b6-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="1d5b6-103">Você pode calcular valores numéricos com o uso de expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="1d5b6-104">A *expressão numérica* é uma expressão que contém variáveis que representam valores numéricos, literais e constantes e operadores que atuam sobre esses valores.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="1d5b6-105">Calculando valores numéricos</span><span class="sxs-lookup"><span data-stu-id="1d5b6-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="1d5b6-106">Para calcular um valor numérico</span><span class="sxs-lookup"><span data-stu-id="1d5b6-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="1d5b6-107">Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="1d5b6-108">O exemplo a seguir mostra algumas expressões numéricas válidas.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="1d5b6-109">As três primeiras linhas mostram um literal, uma constante e uma variável.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="1d5b6-110">Cada um deles faz uma expressão numérica válida por si só.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="1d5b6-111">A linha final mostra uma combinação de uma variável com dois literais.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="1d5b6-112">Observe que uma expressão numérica não formam uma completa [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instrução por si só.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statement by itself.</span></span> <span data-ttu-id="1d5b6-113">Você deve usar a expressão como parte de uma instrução completa.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="1d5b6-114">Para armazenar um valor numérico</span><span class="sxs-lookup"><span data-stu-id="1d5b6-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="1d5b6-115">Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     <span data-ttu-id="1d5b6-116">[!code-vb[VbVbalrOperators&#82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d5b6-116">[!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span></span>  
  
     <span data-ttu-id="1d5b6-117">No exemplo anterior, o valor da expressão no lado direito do operador igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto `j` avalia 276.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="1d5b6-118">Para obter mais informações, consulte [instruções](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b6-118">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="1d5b6-119">Vários operadores</span><span class="sxs-lookup"><span data-stu-id="1d5b6-119">Multiple Operators</span></span>  
 <span data-ttu-id="1d5b6-120">Se a expressão numérica contiver mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="1d5b6-121">Para substituir as regras de precedência de operador, você colocar expressões entre parênteses, como no exemplo acima; as expressões incluídas são avaliadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="1d5b6-122">Para substituir a precedência do operador normal</span><span class="sxs-lookup"><span data-stu-id="1d5b6-122">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="1d5b6-123">Use parênteses para delimitar as operações a serem executadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="1d5b6-124">O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.</span><span class="sxs-lookup"><span data-stu-id="1d5b6-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     <span data-ttu-id="1d5b6-125">[!code-vb[VbVbalrOperators&#83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1d5b6-125">[!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span></span>  
  
     <span data-ttu-id="1d5b6-126">No exemplo anterior, o cálculo de `j` executa o operador de adição (`+`) primeiro porque os parênteses `(67 + i)` substituir a precedência normal e o valor atribuído a `j` é 276 (69 4 vezes).</span><span class="sxs-lookup"><span data-stu-id="1d5b6-126">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="1d5b6-127">O cálculo de `k` executa os operadores na sua prioridade normal (`*` antes de `+`) e o valor atribuído a `k` é 270 (268 mais 2).</span><span class="sxs-lookup"><span data-stu-id="1d5b6-127">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="1d5b6-128">Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b6-128">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5b6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d5b6-129">See Also</span></span>  
 <span data-ttu-id="1d5b6-130">[Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="1d5b6-130">[Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="1d5b6-131"> [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="1d5b6-131"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="1d5b6-132"> [Instruções](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="1d5b6-132"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="1d5b6-133"> [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="1d5b6-133"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="1d5b6-134"> [Operadores aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="1d5b6-134"> [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="1d5b6-135"> [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="1d5b6-135"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
