---
title: Operadores e expressões no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 9d63a458ed747db0a63d2c648460a1a21f7cfbc8
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738988"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="67da7-102">Operadores e expressões no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67da7-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="67da7-103">Um *operador* é um elemento de código que executa uma operação em um ou mais elementos de código que retêm valores.</span><span class="sxs-lookup"><span data-stu-id="67da7-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="67da7-104">Os elementos de valor incluem variáveis, constantes, literais, propriedades, valores retornados dos procedimentos `Function` e `Operator`, bem como expressões.</span><span class="sxs-lookup"><span data-stu-id="67da7-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="67da7-105">Uma *expressão* é uma série de elementos de valor combinada com operadores, que gera um novo valor.</span><span class="sxs-lookup"><span data-stu-id="67da7-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="67da7-106">Os operadores agem em elementos de valor executando cálculos, comparações ou outras operações.</span><span class="sxs-lookup"><span data-stu-id="67da7-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="67da7-107">Tipos de operadores</span><span class="sxs-lookup"><span data-stu-id="67da7-107">Types of Operators</span></span>  
 <span data-ttu-id="67da7-108">Visual Basic oferece os seguintes tipos de operadores:</span><span class="sxs-lookup"><span data-stu-id="67da7-108">Visual Basic provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="67da7-109">Os [operadores aritméticos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) executam cálculos familiares em valores numéricos, incluindo a mudança dos padrões de bit.</span><span class="sxs-lookup"><span data-stu-id="67da7-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="67da7-110">Os [operadores de comparação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) comparam duas expressões e retornam um valor `Boolean` que representa o resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="67da7-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="67da7-111">Os [operadores de concatenação](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) unem várias cadeias de caracteres em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="67da7-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="67da7-112">Os [operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combinam valores numéricos ou `Boolean` e retornam um resultado do mesmo tipo de dados que os valores.</span><span class="sxs-lookup"><span data-stu-id="67da7-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="67da7-113">Os elementos de valor combinados com um operador são chamados *operandos* desse operador.</span><span class="sxs-lookup"><span data-stu-id="67da7-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="67da7-114">Os operadores combinados com elementos de valor formam expressões, exceto para o operador de atribuição, que forma uma *instrução*.</span><span class="sxs-lookup"><span data-stu-id="67da7-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="67da7-115">Para obter mais informações, consulte [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="67da7-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="67da7-116">Avaliação de expressões</span><span class="sxs-lookup"><span data-stu-id="67da7-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="67da7-117">O resultado final de uma expressão representa um valor, que normalmente é um tipo de dados familiar, como `Boolean`, `String` ou um tipo numérico.</span><span class="sxs-lookup"><span data-stu-id="67da7-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="67da7-118">Veja a seguir dois exemplos de expressões.</span><span class="sxs-lookup"><span data-stu-id="67da7-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="67da7-119">Vários operadores podem executar ações em uma única expressão ou instrução, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="67da7-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 <span data-ttu-id="67da7-120">No exemplo anterior, o Visual Basic que executa as operações na expressão no lado direito do operador de atribuição (`=`), em seguida, atribui o valor resultante à variável `x` à esquerda.</span><span class="sxs-lookup"><span data-stu-id="67da7-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="67da7-121">Não há nenhum limite prático para o número de operadores que podem ser combinados em uma expressão, mas é necessário entender a [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) para assegurar que você obtenha os resultados esperados.</span><span class="sxs-lookup"><span data-stu-id="67da7-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="67da7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67da7-122">See also</span></span>
- [<span data-ttu-id="67da7-123">Operadores</span><span class="sxs-lookup"><span data-stu-id="67da7-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="67da7-124">Combinação Eficiente de Operadores</span><span class="sxs-lookup"><span data-stu-id="67da7-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="67da7-125">Instruções</span><span class="sxs-lookup"><span data-stu-id="67da7-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
