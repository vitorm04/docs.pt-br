---
title: Operador \ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604231"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="edb7e-102">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edb7e-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="edb7e-103">Divide dois números e retorna um resultado inteiro.</span><span class="sxs-lookup"><span data-stu-id="edb7e-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edb7e-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="edb7e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="edb7e-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="edb7e-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="edb7e-106">Required.</span></span> <span data-ttu-id="edb7e-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="edb7e-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="edb7e-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="edb7e-108">Required.</span></span> <span data-ttu-id="edb7e-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="edb7e-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="edb7e-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="edb7e-110">Supported Types</span></span>  
 <span data-ttu-id="edb7e-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="edb7e-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="edb7e-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="edb7e-112">Result</span></span>  
 <span data-ttu-id="edb7e-113">O resultado é o quociente de inteiro de `expression1` dividido por `expression2`, que descarta qualquer resto e retém apenas a parte inteira.</span><span class="sxs-lookup"><span data-stu-id="edb7e-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="edb7e-114">Isso é conhecido como *truncamento*.</span><span class="sxs-lookup"><span data-stu-id="edb7e-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="edb7e-115">O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="edb7e-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="edb7e-116">Consulte as tabelas de "Aritmética de inteiros" em [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="edb7e-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="edb7e-117">O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, que retém o resto da parte fracionária.</span><span class="sxs-lookup"><span data-stu-id="edb7e-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edb7e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="edb7e-118">Remarks</span></span>  
 <span data-ttu-id="edb7e-119">Antes de executar a divisão, Visual Basic tenta converter qualquer expressão numérica de ponto flutuante para `Long`.</span><span class="sxs-lookup"><span data-stu-id="edb7e-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="edb7e-120">Se `Option Strict` é `On`, ocorre um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="edb7e-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="edb7e-121">Se `Option Strict` é `Off`, uma <xref:System.OverflowException> é possível se o valor está fora do intervalo da [tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="edb7e-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="edb7e-122">A conversão em `Long` também está sujeito à *do arredondamento bancário*.</span><span class="sxs-lookup"><span data-stu-id="edb7e-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="edb7e-123">Para obter mais informações, veja "Partes fracionários" em [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="edb7e-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="edb7e-124">Se `expression1` ou `expression2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="edb7e-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="edb7e-125">Tentativa de divisão por Zero</span><span class="sxs-lookup"><span data-stu-id="edb7e-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="edb7e-126">Se `expression2` for avaliada como zero, o `\` operador gerará um <xref:System.DivideByZeroException> exceção.</span><span class="sxs-lookup"><span data-stu-id="edb7e-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="edb7e-127">Isso é verdadeiro para todos os tipos de dados numéricos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="edb7e-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edb7e-128">O `\` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="edb7e-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="edb7e-129">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="edb7e-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="edb7e-130">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="edb7e-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb7e-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="edb7e-131">Example</span></span>  
 <span data-ttu-id="edb7e-132">O exemplo a seguir usa o `\` operador para executar uma divisão de inteiro.</span><span class="sxs-lookup"><span data-stu-id="edb7e-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="edb7e-133">O resultado é um inteiro que representa o quociente de inteiro dos dois operandos com o resto descartado.</span><span class="sxs-lookup"><span data-stu-id="edb7e-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 <span data-ttu-id="edb7e-134">As expressões no exemplo anterior retornam valores de 2, 3, 33 e -22, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="edb7e-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb7e-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edb7e-135">See Also</span></span>  
 [<span data-ttu-id="edb7e-136">\\= Operador</span><span class="sxs-lookup"><span data-stu-id="edb7e-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="edb7e-137">/ Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edb7e-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="edb7e-138">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="edb7e-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="edb7e-139">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="edb7e-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="edb7e-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edb7e-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="edb7e-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="edb7e-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="edb7e-142">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edb7e-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
