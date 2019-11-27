---
title: Combinação eficiente de operadores
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
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348990"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="f25ae-102">Combinação eficiente de operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f25ae-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="f25ae-103">Expressões complexas podem conter muitos operadores diferentes.</span><span class="sxs-lookup"><span data-stu-id="f25ae-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="f25ae-104">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="f25ae-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="f25ae-105">A criação de expressões complexas, como a do exemplo anterior, requer uma compreensão completa das regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="f25ae-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="f25ae-106">Para obter mais informações, consulte [precedência de operador em Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="f25ae-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="f25ae-107">Expressões entre parênteses</span><span class="sxs-lookup"><span data-stu-id="f25ae-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="f25ae-108">Muitas vezes você deseja que as operações continuem em uma ordem diferente da determinada por precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="f25ae-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="f25ae-109">Considere o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f25ae-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="f25ae-110">O exemplo anterior multiplica `z` por `y`, em seguida, adiciona o resultado a `4`.</span><span class="sxs-lookup"><span data-stu-id="f25ae-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="f25ae-111">Mas se você quiser adicionar `y` e `4` antes de multiplicar o resultado por `z`, poderá substituir a precedência de operador normal usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="f25ae-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="f25ae-112">Ao colocar uma expressão entre parênteses, você força essa expressão a ser avaliada primeiro, independentemente da precedência do operador.</span><span class="sxs-lookup"><span data-stu-id="f25ae-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="f25ae-113">Para forçar o exemplo anterior a fazer a adição primeiro, você pode reescrevê-lo como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f25ae-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="f25ae-114">O exemplo anterior adiciona `y` e `4`e, em seguida, multiplica essa soma por `z`.</span><span class="sxs-lookup"><span data-stu-id="f25ae-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="f25ae-115">Expressões de parênteses aninhadas</span><span class="sxs-lookup"><span data-stu-id="f25ae-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="f25ae-116">Você pode aninhar expressões em vários níveis de parênteses para substituir a precedência ainda mais.</span><span class="sxs-lookup"><span data-stu-id="f25ae-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="f25ae-117">As expressões que mais profundamente são aninhadas em parênteses são avaliadas primeiro, seguidas pelo próximo aninhado mais profundamente e assim por diante para o menos aninhado e finalmente as expressões fora dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="f25ae-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="f25ae-118">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="f25ae-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="f25ae-119">No exemplo anterior, `z + 2` é avaliado primeiro e, em seguida, as outras expressões entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="f25ae-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="f25ae-120">A exponenciação, que normalmente tem maior precedência do que adição ou multiplicação, é avaliada por último neste exemplo porque as outras expressões são colocadas entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="f25ae-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25ae-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f25ae-121">See also</span></span>

- [<span data-ttu-id="f25ae-122">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25ae-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="f25ae-123">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25ae-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="f25ae-124">Operadores lógicos e de bits bit a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25ae-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="f25ae-125">Operadores lógicos/bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f25ae-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="f25ae-126">Expressões Boolianas</span><span class="sxs-lookup"><span data-stu-id="f25ae-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="f25ae-127">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="f25ae-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="f25ae-128">Como calcular valores numéricos</span><span class="sxs-lookup"><span data-stu-id="f25ae-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="f25ae-129">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25ae-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
