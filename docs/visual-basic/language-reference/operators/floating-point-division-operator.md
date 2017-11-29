---
title: Operador / (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f221e863725b9aeb0b3fa3219b3a881541e2be0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1d427-102">Operador / (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d427-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="1d427-103">Divide dois números e retorna um resultado de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="1d427-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d427-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d427-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1d427-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1d427-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="1d427-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1d427-106">Required.</span></span> <span data-ttu-id="1d427-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="1d427-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1d427-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1d427-108">Required.</span></span> <span data-ttu-id="1d427-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="1d427-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1d427-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="1d427-110">Supported Types</span></span>  
 <span data-ttu-id="1d427-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1d427-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="1d427-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="1d427-112">Result</span></span>  
 <span data-ttu-id="1d427-113">O resultado é o quociente total de `expression1` dividido por `expression2`, incluindo qualquer restante.</span><span class="sxs-lookup"><span data-stu-id="1d427-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="1d427-114">O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro, que ignora o resto.</span><span class="sxs-lookup"><span data-stu-id="1d427-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d427-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d427-115">Remarks</span></span>  
 <span data-ttu-id="1d427-116">O tipo de dados do resultado depende dos tipos de operandos.</span><span class="sxs-lookup"><span data-stu-id="1d427-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="1d427-117">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="1d427-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="1d427-118">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="1d427-118">Operand data types</span></span>|<span data-ttu-id="1d427-119">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="1d427-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="1d427-120">As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="1d427-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="1d427-121">Uma expressão é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) tipo de dados e o outro não é um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="1d427-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="1d427-122">Uma expressão é um [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) tipo de dados e o outro não é um [único](../../../visual-basic/language-reference/data-types/single-data-type.md) ou um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="1d427-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="1d427-123">Qualquer expressão for um [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) tipo de dados</span><span class="sxs-lookup"><span data-stu-id="1d427-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="1d427-124">Antes de divisão, qualquer integrante expressões numéricas são ampliados para `Double`.</span><span class="sxs-lookup"><span data-stu-id="1d427-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="1d427-125">Se você atribuir o resultado a um tipo de dados inteiros, Visual Basic tenta converter o resultado da `Double` a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="1d427-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="1d427-126">Isso pode gerar uma exceção se o resultado não couber nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="1d427-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="1d427-127">Em particular, consulte "Tentativa de divisão por Zero" nesta página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="1d427-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="1d427-128">Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="1d427-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="1d427-129">Tentativa de divisão por Zero</span><span class="sxs-lookup"><span data-stu-id="1d427-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="1d427-130">Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para operando diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="1d427-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="1d427-131">A tabela a seguir mostra os comportamentos possíveis.</span><span class="sxs-lookup"><span data-stu-id="1d427-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="1d427-132">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="1d427-132">Operand data types</span></span>|<span data-ttu-id="1d427-133">Comportamento se `expression2` é zero</span><span class="sxs-lookup"><span data-stu-id="1d427-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="1d427-134">Ponto flutuante (`Single` ou `Double`)</span><span class="sxs-lookup"><span data-stu-id="1d427-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="1d427-135">Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN> (não um número) se `expression1` também é zero</span><span class="sxs-lookup"><span data-stu-id="1d427-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="1d427-136">Lança<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="1d427-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="1d427-137">Integral (assinados ou não assinados)</span><span class="sxs-lookup"><span data-stu-id="1d427-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="1d427-138">Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="1d427-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1d427-139">O `/` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="1d427-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1d427-140">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="1d427-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1d427-141">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1d427-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d427-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d427-142">Example</span></span>  
 <span data-ttu-id="1d427-143">Este exemplo usa o `/` operador para executar a divisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="1d427-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="1d427-144">O resultado é o quociente de dois operandos.</span><span class="sxs-lookup"><span data-stu-id="1d427-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="1d427-145">As expressões no exemplo anterior retornam valores de 2.5 and 3.333333.</span><span class="sxs-lookup"><span data-stu-id="1d427-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="1d427-146">Observe que o resultado é sempre ponto flutuante (`Double`), embora ambos os operandos são constantes de inteiro.</span><span class="sxs-lookup"><span data-stu-id="1d427-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d427-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d427-147">See Also</span></span>  
 [<span data-ttu-id="1d427-148">Operador / = (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d427-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="1d427-149">\ Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d427-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="1d427-150">Tipos de Dados de Resultados do Operador</span><span class="sxs-lookup"><span data-stu-id="1d427-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [<span data-ttu-id="1d427-151">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="1d427-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="1d427-152">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d427-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1d427-153">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="1d427-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1d427-154">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d427-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
