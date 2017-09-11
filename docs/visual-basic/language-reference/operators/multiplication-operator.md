---
title: '* Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator, syntax
- math operators
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
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
ms.openlocfilehash: 66f414e01779cf1c91d10e2d93b1274384d008f8
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f799b-102">Operador * (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f799b-102">* Operator (Visual Basic)</span></span>
<span data-ttu-id="f799b-103">Multiplica dois números.</span><span class="sxs-lookup"><span data-stu-id="f799b-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f799b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f799b-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="f799b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f799b-105">Parts</span></span>  
  
|<span data-ttu-id="f799b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="f799b-106">Term</span></span>|<span data-ttu-id="f799b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="f799b-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="f799b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f799b-108">Required.</span></span> <span data-ttu-id="f799b-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="f799b-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="f799b-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f799b-110">Required.</span></span> <span data-ttu-id="f799b-111">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="f799b-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="f799b-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="f799b-112">Result</span></span>  
 <span data-ttu-id="f799b-113">O resultado é o produto de `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="f799b-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="f799b-114">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="f799b-114">Supported Types</span></span>  
 <span data-ttu-id="f799b-115">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f799b-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f799b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f799b-116">Remarks</span></span>  
 <span data-ttu-id="f799b-117">O tipo de dados do resultado depende do tipo dos operandos.</span><span class="sxs-lookup"><span data-stu-id="f799b-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="f799b-118">A tabela a seguir mostra como o tipo de dados do resultado é determinado.</span><span class="sxs-lookup"><span data-stu-id="f799b-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="f799b-119">Tipos de dados de operando</span><span class="sxs-lookup"><span data-stu-id="f799b-119">Operand data types</span></span>|<span data-ttu-id="f799b-120">Tipo de dados de resultado</span><span class="sxs-lookup"><span data-stu-id="f799b-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="f799b-121">As duas expressões são tipos de dados integrais ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bytes](../../../visual-basic/language-reference/data-types/byte-data-type.md), [curto](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [longo](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="f799b-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="f799b-122">Um tipo de dados numérico apropriado para os tipos de dados de `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="f799b-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="f799b-123">Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f799b-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="f799b-124">Ambas as expressões forem [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="f799b-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="f799b-125">Ambas as expressões forem [único](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="f799b-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="f799b-126">Qualquer expressão é um tipo de dados de ponto flutuante (`Single` ou [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)), mas não ambos `Single` (Observação `Decimal` não é um tipo de dados de ponto flutuante)</span><span class="sxs-lookup"><span data-stu-id="f799b-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="f799b-127">Se uma expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="f799b-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f799b-128">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="f799b-128">Overloading</span></span>  
 <span data-ttu-id="f799b-129">O `*` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f799b-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f799b-130">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="f799b-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f799b-131">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f799b-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f799b-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f799b-132">Example</span></span>  
 <span data-ttu-id="f799b-133">Este exemplo usa o `*` operador para multiplicar dois números.</span><span class="sxs-lookup"><span data-stu-id="f799b-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="f799b-134">O resultado é o produto dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="f799b-134">The result is the product of the two operands.</span></span>  
  
 <span data-ttu-id="f799b-135">[!code-vb[VbVbalrOperators n º&4;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f799b-135">[!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f799b-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f799b-136">See Also</span></span>  
 <span data-ttu-id="f799b-137">[* O operador =](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f799b-137">[*= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span></span>  
<span data-ttu-id="f799b-138"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="f799b-138"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="f799b-139"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="f799b-139"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="f799b-140"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="f799b-140"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="f799b-141"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f799b-141"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

