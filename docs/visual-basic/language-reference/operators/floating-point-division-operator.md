---
title: Operador / (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
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
ms.openlocfilehash: d30d871d48bc87e050a072cd01a38065be20616c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933266"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e60cb-102">Operador / (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e60cb-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="e60cb-103">Divide dois números e retorna um resultado de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="e60cb-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e60cb-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e60cb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e60cb-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="e60cb-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e60cb-106">Required.</span></span> <span data-ttu-id="e60cb-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e60cb-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e60cb-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e60cb-108">Required.</span></span> <span data-ttu-id="e60cb-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e60cb-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e60cb-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="e60cb-110">Supported Types</span></span>  
 <span data-ttu-id="e60cb-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e60cb-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e60cb-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="e60cb-112">Result</span></span>  
 <span data-ttu-id="e60cb-113">O resultado é o quociente completo de `expression1` dividido por `expression2`, incluindo qualquer restante.</span><span class="sxs-lookup"><span data-stu-id="e60cb-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="e60cb-114">O [operador \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente inteiro, que remove o resto.</span><span class="sxs-lookup"><span data-stu-id="e60cb-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e60cb-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e60cb-115">Remarks</span></span>  
 <span data-ttu-id="e60cb-116">O tipo de dados do resultado depende dos tipos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="e60cb-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="e60cb-117">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="e60cb-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="e60cb-118">Tipos de dados do operando</span><span class="sxs-lookup"><span data-stu-id="e60cb-118">Operand data types</span></span>|<span data-ttu-id="e60cb-119">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="e60cb-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="e60cb-120">Ambas as expressões são tipos de dados integral ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="e60cb-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="e60cb-121">Uma expressão é um tipo de dados [único](../../../visual-basic/language-reference/data-types/single-data-type.md) e a outra não é uma [dupla](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="e60cb-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="e60cb-122">Uma expressão é um tipo de dados [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) e a outra não é uma [única](../../../visual-basic/language-reference/data-types/single-data-type.md) ou uma [dupla](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="e60cb-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="e60cb-123">Uma das expressões é um tipo de dados [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="e60cb-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="e60cb-124">Antes da divisão ser executada, todas as expressões numéricas integrais `Double`são ampliadas para.</span><span class="sxs-lookup"><span data-stu-id="e60cb-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="e60cb-125">Se você atribuir o resultado a um tipo de dados integral, Visual Basic tentará converter o resultado `Double` de para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="e60cb-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="e60cb-126">Isso pode gerar uma exceção se o resultado não couber nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="e60cb-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="e60cb-127">Em particular, consulte "tentativa de divisão por zero" nesta página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="e60cb-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="e60cb-128">Se `expression1` ou`expression2` for avaliado como [Nothing](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="e60cb-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="e60cb-129">Tentativa de divisão por zero</span><span class="sxs-lookup"><span data-stu-id="e60cb-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="e60cb-130">Se `expression2` for avaliada como zero, `/` o operador se comporta de forma diferente para diferentes tipos de dados de operando.</span><span class="sxs-lookup"><span data-stu-id="e60cb-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="e60cb-131">A tabela a seguir mostra os possíveis comportamentos.</span><span class="sxs-lookup"><span data-stu-id="e60cb-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="e60cb-132">Tipos de dados do operando</span><span class="sxs-lookup"><span data-stu-id="e60cb-132">Operand data types</span></span>|<span data-ttu-id="e60cb-133">Comportamento se `expression2` for zero</span><span class="sxs-lookup"><span data-stu-id="e60cb-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="e60cb-134">Ponto flutuante (`Single` ou `Double`)</span><span class="sxs-lookup"><span data-stu-id="e60cb-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="e60cb-135">Retorna infinito (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>) ou <xref:System.Double.NaN> (não é um número) se `expression1` também for zero</span><span class="sxs-lookup"><span data-stu-id="e60cb-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="e60cb-136">Emite<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="e60cb-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="e60cb-137">Integral (assinada ou não assinada)</span><span class="sxs-lookup"><span data-stu-id="e60cb-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="e60cb-138">Tentativa de conversão de volta para tipo integral <xref:System.OverflowException> gera porque tipos integrais <xref:System.Double.PositiveInfinity>não <xref:System.Double.NegativeInfinity>podem aceitar,, ou<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="e60cb-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e60cb-139">O `/` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e60cb-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e60cb-140">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="e60cb-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e60cb-141">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e60cb-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e60cb-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e60cb-142">Example</span></span>  
 <span data-ttu-id="e60cb-143">Este exemplo usa o `/` operador para executar a divisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="e60cb-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="e60cb-144">O resultado é o quociente dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="e60cb-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="e60cb-145">As expressões no exemplo anterior retornam valores de 2,5 e 3,333333.</span><span class="sxs-lookup"><span data-stu-id="e60cb-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="e60cb-146">Observe que o resultado é sempre ponto flutuante (`Double`), embora ambos os operandos sejam constantes de inteiro.</span><span class="sxs-lookup"><span data-stu-id="e60cb-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60cb-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e60cb-147">See also</span></span>

- [<span data-ttu-id="e60cb-148">Operador/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e60cb-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="e60cb-149">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e60cb-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="e60cb-150">Tipos de Dados de Resultados do Operador</span><span class="sxs-lookup"><span data-stu-id="e60cb-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [<span data-ttu-id="e60cb-151">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="e60cb-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="e60cb-152">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e60cb-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e60cb-153">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e60cb-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e60cb-154">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e60cb-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
