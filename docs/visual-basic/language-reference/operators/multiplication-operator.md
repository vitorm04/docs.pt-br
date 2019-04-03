---
title: '* Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828947"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="90590-102">Operador \* (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90590-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="90590-103">Multiplica dois números.</span><span class="sxs-lookup"><span data-stu-id="90590-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90590-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90590-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="90590-105">Partes</span><span class="sxs-lookup"><span data-stu-id="90590-105">Parts</span></span>  
  
|<span data-ttu-id="90590-106">Termo</span><span class="sxs-lookup"><span data-stu-id="90590-106">Term</span></span>|<span data-ttu-id="90590-107">Definição</span><span class="sxs-lookup"><span data-stu-id="90590-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="90590-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="90590-108">Required.</span></span> <span data-ttu-id="90590-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="90590-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="90590-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="90590-110">Required.</span></span> <span data-ttu-id="90590-111">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="90590-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="90590-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="90590-112">Result</span></span>  
 <span data-ttu-id="90590-113">O resultado é o produto dos `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="90590-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="90590-114">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="90590-114">Supported Types</span></span>  
 <span data-ttu-id="90590-115">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="90590-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90590-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="90590-116">Remarks</span></span>  
 <span data-ttu-id="90590-117">O tipo de dados do resultado depende dos tipos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="90590-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="90590-118">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="90590-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="90590-119">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="90590-119">Operand data types</span></span>|<span data-ttu-id="90590-120">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="90590-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="90590-121">Ambas as expressões forem de tipos de dados inteiros ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="90590-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="90590-122">Um tipo de dados numérico apropriado para os tipos de dados do `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="90590-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="90590-123">Consulte as tabelas "Aritmética de inteiros" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="90590-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="90590-124">Ambas as expressões forem [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="90590-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="90590-125">Ambas as expressões forem [único](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="90590-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="90590-126">Qualquer expressão é um tipo de dados de ponto flutuante (`Single` ou [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)), mas não ambos `Single` (Observação `Decimal` não é um tipo de dados de ponto flutuante)</span><span class="sxs-lookup"><span data-stu-id="90590-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="90590-127">Se uma expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="90590-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="90590-128">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="90590-128">Overloading</span></span>  
 <span data-ttu-id="90590-129">O `*` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="90590-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="90590-130">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="90590-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="90590-131">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="90590-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90590-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90590-132">Example</span></span>  
 <span data-ttu-id="90590-133">Este exemplo usa o `*` operador para multiplicar dois números.</span><span class="sxs-lookup"><span data-stu-id="90590-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="90590-134">O resultado é o produto dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="90590-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="90590-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90590-135">See also</span></span>

- [<span data-ttu-id="90590-136">Operador \*=</span><span class="sxs-lookup"><span data-stu-id="90590-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="90590-137">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="90590-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="90590-138">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90590-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="90590-139">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="90590-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="90590-140">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90590-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
