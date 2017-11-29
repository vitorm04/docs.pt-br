---
title: "Como calcular valores numéricos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="cfdcb-102">Como calcular valores numéricos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfdcb-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="cfdcb-103">Você pode calcular valores numéricos com o uso de expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="cfdcb-104">Um *expressão numérica* é uma expressão que contém literais, constantes e variáveis que representam valores numéricos e operadores que atuam sobre esses valores.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="cfdcb-105">Calculando valores numéricos</span><span class="sxs-lookup"><span data-stu-id="cfdcb-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="cfdcb-106">Para calcular um valor numérico</span><span class="sxs-lookup"><span data-stu-id="cfdcb-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="cfdcb-107">Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="cfdcb-108">O exemplo a seguir mostra algumas expressões numéricas válidos.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="cfdcb-109">As três primeiras linhas mostram um literal, uma constante e uma variável.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="cfdcb-110">Cada uma forma de uma expressão numérica válida por si só.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="cfdcb-111">A linha final exibe uma combinação de uma variável com dois literais.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="cfdcb-112">Observe que uma expressão numérica não formam uma completa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instrução por si só.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statement by itself.</span></span> <span data-ttu-id="cfdcb-113">Você deve usar a expressão como parte de uma instrução completa.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="cfdcb-114">Para armazenar um valor numérico</span><span class="sxs-lookup"><span data-stu-id="cfdcb-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="cfdcb-115">Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="cfdcb-116">No exemplo anterior, o valor da expressão no lado direito do operador igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto `j` é avaliada como 276.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="cfdcb-117">Para obter mais informações, consulte [Instruções](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="cfdcb-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="cfdcb-118">Vários operadores</span><span class="sxs-lookup"><span data-stu-id="cfdcb-118">Multiple Operators</span></span>  
 <span data-ttu-id="cfdcb-119">Se a expressão numérica contém mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="cfdcb-120">Para substituir as regras de precedência de operador, você deve colocar expressões entre parênteses, como no exemplo acima; as expressões entre são avaliadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="cfdcb-121">Para substituir a precedência do operador normal</span><span class="sxs-lookup"><span data-stu-id="cfdcb-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="cfdcb-122">Use parênteses para incluir as operações que você deseja que seja executada primeiro.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="cfdcb-123">O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.</span><span class="sxs-lookup"><span data-stu-id="cfdcb-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="cfdcb-124">No exemplo anterior, o cálculo de `j` executa o operador de adição (`+`) primeiro porque os parênteses que delimitam `(67 + i)` substituir prioridade normal e o valor atribuído à `j` é 276 (69 4 vezes).</span><span class="sxs-lookup"><span data-stu-id="cfdcb-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="cfdcb-125">O cálculo de `k` executa os operadores na sua prioridade normal (`*` antes de `+`) e o valor atribuído à `k` é 270 (268 + 2).</span><span class="sxs-lookup"><span data-stu-id="cfdcb-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="cfdcb-126">Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="cfdcb-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdcb-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfdcb-127">See Also</span></span>  
 [<span data-ttu-id="cfdcb-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="cfdcb-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="cfdcb-129">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="cfdcb-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="cfdcb-130">Instruções</span><span class="sxs-lookup"><span data-stu-id="cfdcb-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="cfdcb-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfdcb-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="cfdcb-132">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="cfdcb-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="cfdcb-133">Combinação Eficiente de Operadores</span><span class="sxs-lookup"><span data-stu-id="cfdcb-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
