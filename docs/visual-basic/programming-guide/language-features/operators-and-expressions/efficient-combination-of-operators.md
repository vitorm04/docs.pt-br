---
title: Combinação eficiente de operadores (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648912"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="1fba3-102">Combinação eficiente de operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fba3-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="1fba3-103">Expressões complexas podem conter muitos operadores diferentes.</span><span class="sxs-lookup"><span data-stu-id="1fba3-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="1fba3-104">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="1fba3-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="1fba3-105">Criar expressões complexas, como mostrado no exemplo anterior requer uma compreensão completa das regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="1fba3-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="1fba3-106">Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="1fba3-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="1fba3-107">Expressões entre parênteses</span><span class="sxs-lookup"><span data-stu-id="1fba3-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="1fba3-108">Geralmente, você deseja operações continuem em uma ordem diferente daquela que determinado pela precedência do operador.</span><span class="sxs-lookup"><span data-stu-id="1fba3-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="1fba3-109">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1fba3-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="1fba3-110">Multiplica o exemplo anterior `z` por `y`, em seguida, adiciona o resultado para `4`.</span><span class="sxs-lookup"><span data-stu-id="1fba3-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="1fba3-111">Porém, se você deseja adicionar `y` e `4` antes de multiplicar o resultado pelo `z`, você pode substituir a precedência do operador normal usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="1fba3-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="1fba3-112">Colocando uma expressão entre parênteses, você deve forçar essa expressão seja avaliada primeiro, independentemente de precedência do operador.</span><span class="sxs-lookup"><span data-stu-id="1fba3-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="1fba3-113">Para forçar o exemplo anterior para fazer a adição primeiro, você poderia reescrever como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1fba3-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="1fba3-114">O exemplo anterior adiciona `y` e `4`, em seguida, multiplica essa soma pelo `z`.</span><span class="sxs-lookup"><span data-stu-id="1fba3-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="1fba3-115">Expressões entre parênteses aninhadas</span><span class="sxs-lookup"><span data-stu-id="1fba3-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="1fba3-116">Você pode aninhar expressões em vários níveis de parênteses para substituir a precedência ainda mais.</span><span class="sxs-lookup"><span data-stu-id="1fba3-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="1fba3-117">As expressões mais profundamente aninhadas entre parênteses são avaliadas primeiro, seguida da próxima mais profundamente aninhada, de e assim por diante para menos profundamente aninhadas e, finalmente, as expressões fora parênteses.</span><span class="sxs-lookup"><span data-stu-id="1fba3-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="1fba3-118">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="1fba3-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="1fba3-119">No exemplo anterior, `z + 2` é avaliado primeiro, depois em seguida outras expressões entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="1fba3-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="1fba3-120">Exponenciação, que normalmente tem precedência maior do que a adição ou multiplicação, é avaliada pela última neste exemplo porque outras expressões são colocados entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="1fba3-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fba3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fba3-121">See Also</span></span>  
 [<span data-ttu-id="1fba3-122">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fba3-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="1fba3-123">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fba3-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="1fba3-124">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fba3-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="1fba3-125">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fba3-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="1fba3-126">Expressões Boolianas</span><span class="sxs-lookup"><span data-stu-id="1fba3-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="1fba3-127">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="1fba3-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="1fba3-128">Como calcular valores numéricos</span><span class="sxs-lookup"><span data-stu-id="1fba3-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="1fba3-129">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fba3-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
