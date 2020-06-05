---
title: Operador /
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
ms.openlocfilehash: e9400b50a84522f87a9a2ea4cd05b479d7a4538e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371162"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="32d91-102">Operador / (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d91-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="32d91-103">Divide dois números e retorna um resultado de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="32d91-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32d91-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="32d91-105">Partes</span><span class="sxs-lookup"><span data-stu-id="32d91-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="32d91-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="32d91-106">Required.</span></span> <span data-ttu-id="32d91-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="32d91-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="32d91-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="32d91-108">Required.</span></span> <span data-ttu-id="32d91-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="32d91-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="32d91-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="32d91-110">Supported Types</span></span>  
 <span data-ttu-id="32d91-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinados e `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="32d91-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="32d91-112">Result</span><span class="sxs-lookup"><span data-stu-id="32d91-112">Result</span></span>  
 <span data-ttu-id="32d91-113">O resultado é o quociente completo de `expression1` dividido por `expression2` , incluindo qualquer restante.</span><span class="sxs-lookup"><span data-stu-id="32d91-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="32d91-114">O [operador \ (Visual Basic)](integer-division-operator.md) retorna o quociente inteiro, que remove o resto.</span><span class="sxs-lookup"><span data-stu-id="32d91-114">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32d91-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="32d91-115">Remarks</span></span>  
 <span data-ttu-id="32d91-116">O tipo de dados do resultado depende dos tipos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="32d91-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="32d91-117">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="32d91-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="32d91-118">Tipos de dados do operando</span><span class="sxs-lookup"><span data-stu-id="32d91-118">Operand data types</span></span>|<span data-ttu-id="32d91-119">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="32d91-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="32d91-120">Ambas as expressões são tipos de dados integral ([SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULONG](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="32d91-120">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="32d91-121">Uma expressão é um tipo de dados [único](../data-types/single-data-type.md) e a outra não é uma [dupla](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="32d91-121">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="32d91-122">Uma expressão é um tipo de dados [decimal](../data-types/decimal-data-type.md) e a outra não é uma [única](../data-types/single-data-type.md) ou uma [dupla](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="32d91-122">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="32d91-123">Uma das expressões é um tipo de dados [duplo](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="32d91-123">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="32d91-124">Antes da divisão ser executada, todas as expressões numéricas integrais são ampliadas para `Double` .</span><span class="sxs-lookup"><span data-stu-id="32d91-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="32d91-125">Se você atribuir o resultado a um tipo de dados integral, Visual Basic tentará converter o resultado de `Double` para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="32d91-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="32d91-126">Isso pode gerar uma exceção se o resultado não couber nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="32d91-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="32d91-127">Em particular, consulte "tentativa de divisão por zero" nesta página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="32d91-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="32d91-128">Se `expression1` ou `expression2` for avaliado como [Nothing](../nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="32d91-128">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="32d91-129">Tentativa de divisão por zero</span><span class="sxs-lookup"><span data-stu-id="32d91-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="32d91-130">Se `expression2` for avaliada como zero, o `/` operador se comporta de forma diferente para diferentes tipos de dados de operando.</span><span class="sxs-lookup"><span data-stu-id="32d91-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="32d91-131">A tabela a seguir mostra os possíveis comportamentos.</span><span class="sxs-lookup"><span data-stu-id="32d91-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="32d91-132">Tipos de dados do operando</span><span class="sxs-lookup"><span data-stu-id="32d91-132">Operand data types</span></span>|<span data-ttu-id="32d91-133">Comportamento se `expression2` for zero</span><span class="sxs-lookup"><span data-stu-id="32d91-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="32d91-134">Ponto flutuante ( `Single` ou `Double` )</span><span class="sxs-lookup"><span data-stu-id="32d91-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="32d91-135">Retorna infinito ( <xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity> ) ou <xref:System.Double.NaN> (não é um número) se `expression1` também for zero</span><span class="sxs-lookup"><span data-stu-id="32d91-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="32d91-136">Emite<xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="32d91-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="32d91-137">Integral (assinada ou não assinada)</span><span class="sxs-lookup"><span data-stu-id="32d91-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="32d91-138">Tentativa de conversão de volta para tipo integral gera <xref:System.OverflowException> porque tipos integrais não podem aceitar <xref:System.Double.PositiveInfinity> , <xref:System.Double.NegativeInfinity> , ou<xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="32d91-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="32d91-139">O `/` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="32d91-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="32d91-140">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="32d91-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="32d91-141">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="32d91-141">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32d91-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32d91-142">Example</span></span>  
 <span data-ttu-id="32d91-143">Este exemplo usa o `/` operador para executar a divisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="32d91-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="32d91-144">O resultado é o quociente dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="32d91-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="32d91-145">As expressões no exemplo anterior retornam valores de 2,5 e 3,333333.</span><span class="sxs-lookup"><span data-stu-id="32d91-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="32d91-146">Observe que o resultado é sempre ponto flutuante ( `Double` ), embora ambos os operandos sejam constantes de inteiro.</span><span class="sxs-lookup"><span data-stu-id="32d91-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d91-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="32d91-147">See also</span></span>

- [<span data-ttu-id="32d91-148">Operador/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d91-148">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="32d91-149">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d91-149">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="32d91-150">Tipos de Dados de Resultados do Operador</span><span class="sxs-lookup"><span data-stu-id="32d91-150">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="32d91-151">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="32d91-151">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="32d91-152">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32d91-152">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="32d91-153">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="32d91-153">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="32d91-154">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32d91-154">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
