---
title: / Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
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
ms.openlocfilehash: 82255339c3bdab7f6e760de9bef073f463260877
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="098d3-102">Operador / (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="098d3-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="098d3-103">Divide dois números e retorna um resultado de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="098d3-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="098d3-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="098d3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="098d3-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="098d3-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="098d3-106">Required.</span></span> <span data-ttu-id="098d3-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="098d3-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="098d3-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="098d3-108">Required.</span></span> <span data-ttu-id="098d3-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="098d3-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="098d3-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="098d3-110">Supported Types</span></span>  
 <span data-ttu-id="098d3-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="098d3-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="098d3-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="098d3-112">Result</span></span>  
 <span data-ttu-id="098d3-113">O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer restante.</span><span class="sxs-lookup"><span data-stu-id="098d3-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="098d3-114">O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro, que ignora o resto.</span><span class="sxs-lookup"><span data-stu-id="098d3-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="098d3-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="098d3-115">Remarks</span></span>  
 <span data-ttu-id="098d3-116">O tipo de dados do resultado depende do tipo dos operandos.</span><span class="sxs-lookup"><span data-stu-id="098d3-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="098d3-117">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="098d3-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="098d3-118">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="098d3-118">Operand data types</span></span>|<span data-ttu-id="098d3-119">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="098d3-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="098d3-120">As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="098d3-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="098d3-121">Uma expressão é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="098d3-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="098d3-122">Uma expressão é um [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="098d3-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="098d3-123">Uma das expressões é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados</span><span class="sxs-lookup"><span data-stu-id="098d3-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="098d3-124">Antes de divisão, qualquer integrante expressões numéricas são ampliados para `Double`.</span><span class="sxs-lookup"><span data-stu-id="098d3-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="098d3-125">Se você atribuir o resultado a um tipo de dados inteiros, Visual Basic tenta converter o resultado da `Double` para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="098d3-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="098d3-126">Isso pode gerar uma exceção se o resultado não couber nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="098d3-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="098d3-127">Em particular, consulte "Tentativa de divisão por Zero" nesta página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="098d3-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="098d3-128">Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="098d3-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="098d3-129">Tentativa de divisão por Zero</span><span class="sxs-lookup"><span data-stu-id="098d3-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="098d3-130">Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para operando diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="098d3-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="098d3-131">A tabela a seguir mostra os comportamentos possíveis.</span><span class="sxs-lookup"><span data-stu-id="098d3-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="098d3-132">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="098d3-132">Operand data types</span></span>|<span data-ttu-id="098d3-133">Comportamento se `expression2` é zero</span><span class="sxs-lookup"><span data-stu-id="098d3-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="098d3-134">Ponto flutuante (`Single` ou `Double`)</span><span class="sxs-lookup"><span data-stu-id="098d3-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="098d3-135">Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN>(não um número) se `expression1` também é zero</xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity></span><span class="sxs-lookup"><span data-stu-id="098d3-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="098d3-136">Lança<xref:System.DivideByZeroException></xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="098d3-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="098d3-137">Integral (assinados ou não assinados)</span><span class="sxs-lookup"><span data-stu-id="098d3-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="098d3-138">Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException>porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN></xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="098d3-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="098d3-139">O `/` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="098d3-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="098d3-140">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="098d3-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="098d3-141">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="098d3-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="098d3-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="098d3-142">Example</span></span>  
 <span data-ttu-id="098d3-143">Este exemplo usa o `/` operador para realizar a divisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="098d3-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="098d3-144">O resultado é o quociente de dois operandos.</span><span class="sxs-lookup"><span data-stu-id="098d3-144">The result is the quotient of the two operands.</span></span>  
  
 <span data-ttu-id="098d3-145">[!code-vb[VbVbalrOperators n º&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="098d3-145">[!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="098d3-146">As expressões no exemplo anterior retornam valores de 2.5 and 3.333333.</span><span class="sxs-lookup"><span data-stu-id="098d3-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="098d3-147">Observe que o resultado é sempre um ponto flutuante (`Double`), embora ambos os operandos são constantes de inteiro.</span><span class="sxs-lookup"><span data-stu-id="098d3-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098d3-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="098d3-148">See Also</span></span>  
 <span data-ttu-id="098d3-149">[Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-149">[/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="098d3-150"> [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-150"> [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span></span>  
<span data-ttu-id="098d3-151"> [Tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-151"> [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span></span>  
<span data-ttu-id="098d3-152"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-152"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="098d3-153"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-153"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="098d3-154"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="098d3-154"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="098d3-155"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="098d3-155"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

