---
title: ^ Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
dev_langs:
- VB
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers, rasing
- powers
- arithmetic operators, exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 9096f736007aa1908c8e72dfc8d4a457f12bb80a
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="79faf-102">Operador ^ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79faf-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="79faf-103">Eleva um número à potência de outro número.</span><span class="sxs-lookup"><span data-stu-id="79faf-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79faf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79faf-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="79faf-105">Partes</span><span class="sxs-lookup"><span data-stu-id="79faf-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="79faf-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="79faf-106">Required.</span></span> <span data-ttu-id="79faf-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="79faf-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="79faf-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="79faf-108">Required.</span></span> <span data-ttu-id="79faf-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="79faf-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="79faf-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="79faf-110">Result</span></span>  
 <span data-ttu-id="79faf-111">O resultado é `number` elevado à potência de `exponent`, sempre que um `Double` valor.</span><span class="sxs-lookup"><span data-stu-id="79faf-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="79faf-112">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="79faf-112">Supported Types</span></span>  
 <span data-ttu-id="79faf-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="79faf-113">`Double`.</span></span> <span data-ttu-id="79faf-114">Os operandos de qualquer outro tipo são convertidos em `Double`.</span><span class="sxs-lookup"><span data-stu-id="79faf-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79faf-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="79faf-115">Remarks</span></span>  
 <span data-ttu-id="79faf-116">Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="79faf-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="79faf-117">O valor de `exponent` pode ser fracionário, negativo, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="79faf-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="79faf-118">Quando mais de uma exponenciação for realizada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="79faf-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79faf-119">O `^` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="79faf-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="79faf-120">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="79faf-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="79faf-121">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="79faf-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79faf-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79faf-122">Example</span></span>  
 <span data-ttu-id="79faf-123">O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente.</span><span class="sxs-lookup"><span data-stu-id="79faf-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="79faf-124">O resultado é o primeiro operando elevado à potência da segunda.</span><span class="sxs-lookup"><span data-stu-id="79faf-124">The result is the first operand raised to the power of the second.</span></span>  
  
 <span data-ttu-id="79faf-125">[!code-vb[20 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="79faf-125">[!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="79faf-126">O exemplo anterior produz os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="79faf-126">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="79faf-127">`exp1`é definido como 4 (2 ao quadrado).</span><span class="sxs-lookup"><span data-stu-id="79faf-127">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="79faf-128">`exp2`é definido como 19683 (3 ao cubo, em seguida, esse valor ao cubo).</span><span class="sxs-lookup"><span data-stu-id="79faf-128">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="79faf-129">`exp3`é definido como -125 (-5 cúbico).</span><span class="sxs-lookup"><span data-stu-id="79faf-129">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="79faf-130">`exp4`é definido como 625 (-5 o quarto de energia).</span><span class="sxs-lookup"><span data-stu-id="79faf-130">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="79faf-131">`exp5`é definido como 2 (raiz cúbica de 8).</span><span class="sxs-lookup"><span data-stu-id="79faf-131">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="79faf-132">`exp6`é definido como 0,5 (1.0 dividido pela raiz cúbica de 8).</span><span class="sxs-lookup"><span data-stu-id="79faf-132">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="79faf-133">Observe a importância dos parênteses em expressões no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="79faf-133">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="79faf-134">Por causa da *precedência do operador*, Visual Basic normalmente executa o `^` operador antes de qualquer outro, mesmo que o operador unário `–` operador.</span><span class="sxs-lookup"><span data-stu-id="79faf-134">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="79faf-135">Se `exp4` e `exp6` tinha sido calculados sem parênteses, deve ter produzido os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="79faf-135">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="79faf-136">`exp4 = -5 ^ 4`será calculado como – (5 o quarto de energia), que resultaria em-625.</span><span class="sxs-lookup"><span data-stu-id="79faf-136">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="79faf-137">`exp6 = 8 ^ -1.0 / 3.0`será calculado como (8 a potência de-1 ou 0,125) dividido por 3.0, o que resultaria em 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="79faf-137">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79faf-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79faf-138">See Also</span></span>  
 <span data-ttu-id="79faf-139">[^ = Operador](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="79faf-139">[^= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span></span>  
<span data-ttu-id="79faf-140"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="79faf-140"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="79faf-141"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="79faf-141"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="79faf-142"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="79faf-142"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="79faf-143"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="79faf-143"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

