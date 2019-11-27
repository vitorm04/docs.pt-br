---
title: Operador ^
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: b9860b7b6e076fc9c0288818aa9e4f2c0fc4c356
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331102"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d9417-102">Operador ^ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9417-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="d9417-103">Eleva um número à potência de outro número.</span><span class="sxs-lookup"><span data-stu-id="d9417-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9417-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9417-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="d9417-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d9417-105">Parts</span></span>

`number`\
<span data-ttu-id="d9417-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d9417-106">Required.</span></span> <span data-ttu-id="d9417-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="d9417-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="d9417-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d9417-108">Required.</span></span> <span data-ttu-id="d9417-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="d9417-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="d9417-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="d9417-110">Result</span></span>

<span data-ttu-id="d9417-111">O resultado é `number` elevado à potência de `exponent`, sempre como um valor `Double`.</span><span class="sxs-lookup"><span data-stu-id="d9417-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="d9417-112">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="d9417-112">Supported Types</span></span>

<span data-ttu-id="d9417-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="d9417-113">`Double`.</span></span> <span data-ttu-id="d9417-114">Os operandos de qualquer tipo diferente são convertidos em `Double`.</span><span class="sxs-lookup"><span data-stu-id="d9417-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9417-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9417-115">Remarks</span></span>

<span data-ttu-id="d9417-116">Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d9417-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="d9417-117">O valor de `exponent` pode ser fracionário, negativo ou ambos.</span><span class="sxs-lookup"><span data-stu-id="d9417-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="d9417-118">Quando mais de uma exponenciação é executada em uma única expressão, o operador de `^` é avaliado como é encontrado da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="d9417-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="d9417-119">O operador `^` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="d9417-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d9417-120">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="d9417-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d9417-121">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d9417-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="d9417-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9417-122">Example</span></span>

<span data-ttu-id="d9417-123">O exemplo a seguir usa o operador `^` para elevar um número à potência de um expoente.</span><span class="sxs-lookup"><span data-stu-id="d9417-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="d9417-124">O resultado é o primeiro operando elevado à potência do segundo.</span><span class="sxs-lookup"><span data-stu-id="d9417-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="d9417-125">O exemplo anterior produz os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="d9417-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="d9417-126">`exp1` é definido como 4 (2 ao quadrado).</span><span class="sxs-lookup"><span data-stu-id="d9417-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="d9417-127">`exp2` é definido como 19683 (3 cúbico, então esse valor cúbico).</span><span class="sxs-lookup"><span data-stu-id="d9417-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="d9417-128">`exp3` é definido como-125 (-5 cúbico).</span><span class="sxs-lookup"><span data-stu-id="d9417-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="d9417-129">`exp4` é definido como 625 (-5 para a quarta potência).</span><span class="sxs-lookup"><span data-stu-id="d9417-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="d9417-130">`exp5` é definido como 2 (a raiz do cubo de 8).</span><span class="sxs-lookup"><span data-stu-id="d9417-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="d9417-131">`exp6` é definido como 0,5 (1,0 dividido pela raiz do cubo de 8).</span><span class="sxs-lookup"><span data-stu-id="d9417-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="d9417-132">Observe a importância dos parênteses nas expressões no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d9417-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="d9417-133">Devido à *precedência de operador*, Visual Basic normalmente executa o operador de `^` antes de qualquer outro, até mesmo o operador de `–` unário.</span><span class="sxs-lookup"><span data-stu-id="d9417-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="d9417-134">Se `exp4` e `exp6` tiverem sido calculadas sem parênteses, eles produziram os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="d9417-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="d9417-135">`exp4 = -5 ^ 4` seria calculado como – (5 à quarta potência), o que resultaria em-625.</span><span class="sxs-lookup"><span data-stu-id="d9417-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="d9417-136">`exp6 = 8 ^ -1.0 / 3.0` seria calculado como (8 para a potência – 1 ou 0,125) dividido por 3,0, o que resultaria em 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="d9417-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9417-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9417-137">See also</span></span>

- [<span data-ttu-id="d9417-138">Operador ^=</span><span class="sxs-lookup"><span data-stu-id="d9417-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="d9417-139">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="d9417-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="d9417-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9417-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d9417-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="d9417-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d9417-142">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9417-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
