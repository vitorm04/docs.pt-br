---
title: 'Como: Calcular valores numéricos (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 036985a7b60afedc1e8ef0854c619ea8515e5ffe
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974296"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="4af0c-102">Como: Calcular valores numéricos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4af0c-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="4af0c-103">Você pode calcular valores numéricos com o uso de expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="4af0c-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="4af0c-104">Um *expressão numérica* é uma expressão que contém os literais, constantes e variáveis que representam valores numéricos e operadores que atuam nesses valores.</span><span class="sxs-lookup"><span data-stu-id="4af0c-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="4af0c-105">Calculando valores numéricos</span><span class="sxs-lookup"><span data-stu-id="4af0c-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="4af0c-106">Para calcular um valor numérico</span><span class="sxs-lookup"><span data-stu-id="4af0c-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="4af0c-107">Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4af0c-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="4af0c-108">O exemplo a seguir mostra algumas expressões de numéricos válidos.</span><span class="sxs-lookup"><span data-stu-id="4af0c-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="4af0c-109">As três primeiras linhas mostram um literal, uma constante e uma variável.</span><span class="sxs-lookup"><span data-stu-id="4af0c-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="4af0c-110">Cada uma forma de uma expressão numérica válida por si só.</span><span class="sxs-lookup"><span data-stu-id="4af0c-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="4af0c-111">A linha final mostra uma combinação de uma variável com dois literais.</span><span class="sxs-lookup"><span data-stu-id="4af0c-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="4af0c-112">Observe que uma expressão numérica não formam uma instrução completa do Visual Basic, por si só.</span><span class="sxs-lookup"><span data-stu-id="4af0c-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="4af0c-113">Você deve usar a expressão como parte de uma instrução completa.</span><span class="sxs-lookup"><span data-stu-id="4af0c-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="4af0c-114">Para armazenar um valor numérico</span><span class="sxs-lookup"><span data-stu-id="4af0c-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="4af0c-115">Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4af0c-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="4af0c-116">No exemplo anterior, o valor da expressão no lado direito do operador de igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto, `j` é avaliada como 276.</span><span class="sxs-lookup"><span data-stu-id="4af0c-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="4af0c-117">Para obter mais informações, consulte [Instruções](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="4af0c-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="4af0c-118">Vários operadores</span><span class="sxs-lookup"><span data-stu-id="4af0c-118">Multiple Operators</span></span>  
 <span data-ttu-id="4af0c-119">Se a expressão numérica contiver mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência do operador.</span><span class="sxs-lookup"><span data-stu-id="4af0c-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="4af0c-120">Para substituir as regras de precedência de operador, você deve colocar expressões entre parênteses, como no exemplo acima; as expressões entre são avaliadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="4af0c-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="4af0c-121">Para substituir a precedência do operador normal</span><span class="sxs-lookup"><span data-stu-id="4af0c-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="4af0c-122">Use parênteses para delimitar as operações que devem ser executadas pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="4af0c-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="4af0c-123">O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.</span><span class="sxs-lookup"><span data-stu-id="4af0c-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="4af0c-124">No exemplo anterior, o cálculo da `j` executa o operador de adição (`+`) primeiro porque os parênteses que delimitam `(67 + i)` substituir a precedência normal e o valor atribuído a `j` é 276 (4 vezes 69).</span><span class="sxs-lookup"><span data-stu-id="4af0c-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="4af0c-125">O cálculo da `k` executa os operadores na respectiva precedência normal (`*` antes de `+`) e o valor atribuído a `k` é 270 (268 mais 2).</span><span class="sxs-lookup"><span data-stu-id="4af0c-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="4af0c-126">Para obter mais informações, consulte [precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="4af0c-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af0c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4af0c-127">See also</span></span>
- [<span data-ttu-id="4af0c-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="4af0c-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4af0c-129">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="4af0c-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="4af0c-130">Instruções</span><span class="sxs-lookup"><span data-stu-id="4af0c-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="4af0c-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4af0c-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4af0c-132">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="4af0c-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="4af0c-133">Combinação Eficiente de Operadores</span><span class="sxs-lookup"><span data-stu-id="4af0c-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
