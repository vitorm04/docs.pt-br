---
title: Operador ^ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 2fb52a57a9d96f93c31ab1419e81e7f05967f831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659696"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="06d4a-102">Operador ^ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06d4a-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="06d4a-103">Eleva um número à potência de outro número.</span><span class="sxs-lookup"><span data-stu-id="06d4a-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06d4a-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="06d4a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="06d4a-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="06d4a-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="06d4a-106">Required.</span></span> <span data-ttu-id="06d4a-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="06d4a-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="06d4a-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="06d4a-108">Required.</span></span> <span data-ttu-id="06d4a-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="06d4a-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="06d4a-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="06d4a-110">Result</span></span>  
 <span data-ttu-id="06d4a-111">O resultado será `number` elevado à potência de `exponent`, sempre como um `Double` valor.</span><span class="sxs-lookup"><span data-stu-id="06d4a-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="06d4a-112">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="06d4a-112">Supported Types</span></span>  
 <span data-ttu-id="06d4a-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="06d4a-113">`Double`.</span></span> <span data-ttu-id="06d4a-114">Operandos de qualquer outro tipo são convertidos em `Double`.</span><span class="sxs-lookup"><span data-stu-id="06d4a-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06d4a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="06d4a-115">Remarks</span></span>  
 <span data-ttu-id="06d4a-116">Visual Basic sempre executa exponenciação na [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="06d4a-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="06d4a-117">O valor de `exponent` pode ser fracionário, negativo, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="06d4a-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="06d4a-118">Quando mais de um expoente é executada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="06d4a-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06d4a-119">O `^` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="06d4a-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="06d4a-120">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="06d4a-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="06d4a-121">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="06d4a-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d4a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06d4a-122">Example</span></span>  
 <span data-ttu-id="06d4a-123">O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente.</span><span class="sxs-lookup"><span data-stu-id="06d4a-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="06d4a-124">O resultado é o primeiro operando elevado à potência do segundo.</span><span class="sxs-lookup"><span data-stu-id="06d4a-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="06d4a-125">O exemplo anterior produz os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="06d4a-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="06d4a-126">`exp1` é definido como 4 (2 ao quadrado).</span><span class="sxs-lookup"><span data-stu-id="06d4a-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="06d4a-127">`exp2` é definido como 19683 (3 ao cubo, em seguida, esse valor ao cubo).</span><span class="sxs-lookup"><span data-stu-id="06d4a-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="06d4a-128">`exp3` é definido como -125 (-5 cúbico).</span><span class="sxs-lookup"><span data-stu-id="06d4a-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="06d4a-129">`exp4` é definido como 625 (-5 à quarta potência).</span><span class="sxs-lookup"><span data-stu-id="06d4a-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="06d4a-130">`exp5` é definido como 2 (raiz cúbica de 8).</span><span class="sxs-lookup"><span data-stu-id="06d4a-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="06d4a-131">`exp6` é definido como 0,5 (1.0 dividido pela raiz cúbica de 8).</span><span class="sxs-lookup"><span data-stu-id="06d4a-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="06d4a-132">Observe a importância dos parênteses nas expressões no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="06d4a-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="06d4a-133">Por causa da *precedência do operador*, Visual Basic normalmente executa o `^` operador antes de qualquer outro, até mesmo o operador unário `–` operador.</span><span class="sxs-lookup"><span data-stu-id="06d4a-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="06d4a-134">Se `exp4` e `exp6` tinha sido calculada sem parênteses, deve ter produzido os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="06d4a-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="06d4a-135">`exp4 = -5 ^ 4` será calculado como – (5 à quarta potência), que resultaria em-625.</span><span class="sxs-lookup"><span data-stu-id="06d4a-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="06d4a-136">`exp6 = 8 ^ -1.0 / 3.0` será calculado como (8 para a potência de-1 ou 0,125) dividido por 3.0, o que resultaria em 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="06d4a-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d4a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06d4a-137">See also</span></span>
- [<span data-ttu-id="06d4a-138">Operador ^=</span><span class="sxs-lookup"><span data-stu-id="06d4a-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="06d4a-139">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="06d4a-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="06d4a-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06d4a-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="06d4a-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="06d4a-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="06d4a-142">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06d4a-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
