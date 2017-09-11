---
title: + Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, addition
- + operator
- concatenation operators, syntax
- strings [Visual Basic], concatenating
- sum operator
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
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
ms.openlocfilehash: 03cb7e73c47f196cf8d2832c4d4881d9bf09e72b
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="68fec-102">Operador + (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68fec-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="68fec-103">Adiciona dois números ou retorna o valor positivo de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="68fec-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="68fec-104">Também pode ser usado para concatenar duas expressões de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68fec-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68fec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68fec-105">Syntax</span></span>  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="68fec-106">Partes</span><span class="sxs-lookup"><span data-stu-id="68fec-106">Parts</span></span>  
  
|<span data-ttu-id="68fec-107">Termo</span><span class="sxs-lookup"><span data-stu-id="68fec-107">Term</span></span>|<span data-ttu-id="68fec-108">Definição</span><span class="sxs-lookup"><span data-stu-id="68fec-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="68fec-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="68fec-109">Required.</span></span> <span data-ttu-id="68fec-110">Qualquer expressão numérica ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68fec-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="68fec-111">Necessário a menos que o `+` operador está calculando um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="68fec-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="68fec-112">Qualquer expressão numérica ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68fec-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="68fec-113">Resultado</span><span class="sxs-lookup"><span data-stu-id="68fec-113">Result</span></span>  
 <span data-ttu-id="68fec-114">Se `expression1` e `expression2` forem numéricos, o resultado é sua soma aritmética.</span><span class="sxs-lookup"><span data-stu-id="68fec-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="68fec-115">Se `expression2` estiver ausente, o `+` operador é a *unário* operador de identidade para o valor inalterado de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="68fec-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="68fec-116">Nesse sentido, a operação consiste em manter o sinal de `expression1`, portanto, o resultado é negativo se `expression1` for negativo.</span><span class="sxs-lookup"><span data-stu-id="68fec-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="68fec-117">Se `expression1` e `expression2` são as duas cadeias de caracteres, o resultado é a concatenação de seus valores.</span><span class="sxs-lookup"><span data-stu-id="68fec-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="68fec-118">Se `expression1` e `expression2` são de tipos mistos, a ação tomada depende seus tipos, seu conteúdo e a configuração do [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68fec-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="68fec-119">Para obter mais informações, consulte as tabelas em "Comentários".</span><span class="sxs-lookup"><span data-stu-id="68fec-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="68fec-120">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="68fec-120">Supported Types</span></span>  
 <span data-ttu-id="68fec-121">Todos os tipos numéricos, incluindo os tipos de ponto flutuantes e não assinados e `Decimal`, e `String`.</span><span class="sxs-lookup"><span data-stu-id="68fec-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68fec-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="68fec-122">Remarks</span></span>  
 <span data-ttu-id="68fec-123">Em geral, `+` executa adição aritmética quando possível e concatena somente quando as duas expressões são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68fec-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="68fec-124">Se nenhuma expressão for um `Object`, Visual Basic toma as seguintes medidas.</span><span class="sxs-lookup"><span data-stu-id="68fec-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="68fec-125">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="68fec-125">Data types of expressions</span></span>|<span data-ttu-id="68fec-126">Ação pelo compilador</span><span class="sxs-lookup"><span data-stu-id="68fec-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="68fec-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span><span class="sxs-lookup"><span data-stu-id="68fec-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="68fec-128">Adicione.</span><span class="sxs-lookup"><span data-stu-id="68fec-128">Add.</span></span> <span data-ttu-id="68fec-129">O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="68fec-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="68fec-130">Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="68fec-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="68fec-131">Ambas as expressões forem do tipo`String`</span><span class="sxs-lookup"><span data-stu-id="68fec-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="68fec-132">Concatene.</span><span class="sxs-lookup"><span data-stu-id="68fec-132">Concatenate.</span></span>|  
|<span data-ttu-id="68fec-133">Uma expressão é um tipo de dados numéricos e a outra é uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="68fec-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="68fec-134">Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="68fec-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="68fec-135">Se `Option Strict` é `Off`, em seguida, converter implicitamente o `String` para `Double` e adicionar.</span><span class="sxs-lookup"><span data-stu-id="68fec-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="68fec-136">Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="68fec-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="68fec-137">Uma expressão é um tipo de dados numéricos e a outra é [nada](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="68fec-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="68fec-138">Adicionar, com `Nothing` com valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="68fec-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="68fec-139">Uma expressão é uma cadeia de caracteres e a outra é`Nothing`</span><span class="sxs-lookup"><span data-stu-id="68fec-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="68fec-140">Concatenar com `Nothing` valores como "".</span><span class="sxs-lookup"><span data-stu-id="68fec-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="68fec-141">Se uma expressão for um `Object` expressão, Visual Basic toma as seguintes medidas.</span><span class="sxs-lookup"><span data-stu-id="68fec-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="68fec-142">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="68fec-142">Data types of expressions</span></span>|<span data-ttu-id="68fec-143">Ação pelo compilador</span><span class="sxs-lookup"><span data-stu-id="68fec-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="68fec-144">`Object`a expressão contém um valor numérico e a outra é um tipo de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="68fec-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="68fec-145">Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="68fec-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="68fec-146">Se `Option Strict` é `Off`, em seguida, adicione.</span><span class="sxs-lookup"><span data-stu-id="68fec-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="68fec-147">`Object`a expressão contém um valor numérico e a outra é do tipo`String`</span><span class="sxs-lookup"><span data-stu-id="68fec-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="68fec-148">Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="68fec-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="68fec-149">Se `Option Strict` é `Off`, em seguida, converter implicitamente o `String` para `Double` e adicionar.</span><span class="sxs-lookup"><span data-stu-id="68fec-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="68fec-150">Se o `String` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="68fec-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="68fec-151">`Object`a expressão contém uma cadeia de caracteres e a outra é um tipo de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="68fec-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="68fec-152">Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="68fec-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="68fec-153">Se `Option Strict` é `Off`, em seguida, converter implicitamente a cadeia de caracteres `Object` para `Double` e adicionar.</span><span class="sxs-lookup"><span data-stu-id="68fec-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="68fec-154">Se a cadeia de caracteres `Object` não pode ser convertido em `Double`, em seguida, gerar um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="68fec-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="68fec-155">`Object`a expressão contém uma cadeia de caracteres e a outra é do tipo`String`</span><span class="sxs-lookup"><span data-stu-id="68fec-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="68fec-156">Se `Option Strict` é `On`, em seguida, gerar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="68fec-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="68fec-157">Se `Option Strict` é `Off`, em seguida, converter implicitamente `Object` para `String` e concatenar.</span><span class="sxs-lookup"><span data-stu-id="68fec-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="68fec-158">Se ambas as expressões forem `Object` expressões, Visual Basic toma as seguintes medidas (`Option Strict Off` somente).</span><span class="sxs-lookup"><span data-stu-id="68fec-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="68fec-159">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="68fec-159">Data types of expressions</span></span>|<span data-ttu-id="68fec-160">Ação pelo compilador</span><span class="sxs-lookup"><span data-stu-id="68fec-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="68fec-161">Ambos `Object` expressões contém valores numéricos</span><span class="sxs-lookup"><span data-stu-id="68fec-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="68fec-162">Adicione.</span><span class="sxs-lookup"><span data-stu-id="68fec-162">Add.</span></span>|  
|<span data-ttu-id="68fec-163">Ambos `Object` expressões forem do tipo`String`</span><span class="sxs-lookup"><span data-stu-id="68fec-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="68fec-164">Concatene.</span><span class="sxs-lookup"><span data-stu-id="68fec-164">Concatenate.</span></span>|  
|<span data-ttu-id="68fec-165">Um `Object` expressão contém um valor numérico e a outra contém uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="68fec-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="68fec-166">Converter implicitamente a cadeia de caracteres `Object` para `Double` e adicionar.</span><span class="sxs-lookup"><span data-stu-id="68fec-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="68fec-167">Se a cadeia de caracteres `Object` não pode ser convertido em um valor numérico, em seguida, gere um <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="68fec-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="68fec-168">Se qualquer um dos `Object` expressão é avaliada como [nada](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, o `+` operador tratá-la como um `String` com um valor de "".</xref:System.DBNull></span><span class="sxs-lookup"><span data-stu-id="68fec-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68fec-169">Quando você usa o `+` operador, você não poderá determinar se a concatenação de cadeia de caracteres ou adição ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="68fec-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="68fec-170">Use o `&` operador de concatenação para eliminar ambiguidade e fornecer código de documentação própria.</span><span class="sxs-lookup"><span data-stu-id="68fec-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="68fec-171">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="68fec-171">Overloading</span></span>  
 <span data-ttu-id="68fec-172">O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="68fec-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="68fec-173">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="68fec-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="68fec-174">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="68fec-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fec-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68fec-175">Example</span></span>  
 <span data-ttu-id="68fec-176">O exemplo a seguir usa o `+` para adicionar números.</span><span class="sxs-lookup"><span data-stu-id="68fec-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="68fec-177">Se os operandos forem numéricos, o Visual Basic calcula o resultado aritmético.</span><span class="sxs-lookup"><span data-stu-id="68fec-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="68fec-178">O resultado aritmético representa a soma de dois operandos.</span><span class="sxs-lookup"><span data-stu-id="68fec-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 <span data-ttu-id="68fec-179">[!code-vb[VbVbalrOperators n º&6;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-179">[!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="68fec-180">Você também pode usar o `+` operador concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="68fec-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="68fec-181">Se os operandos forem ambos cadeias de caracteres, o Visual Basic os concatena.</span><span class="sxs-lookup"><span data-stu-id="68fec-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="68fec-182">O resultado da concatenação representa uma única cadeia de caracteres consistindo no conteúdo de dois operandos um após o outro.</span><span class="sxs-lookup"><span data-stu-id="68fec-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="68fec-183">Se os operandos forem de tipos mistos, o resultado depende da configuração do [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68fec-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="68fec-184">O exemplo a seguir ilustra o resultado quando `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="68fec-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="68fec-185">[!code-vb[VbVbalrOperators&#53;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-185">[!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="68fec-186">[!code-vb[VbVbalrOperators&#50;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-186">[!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]</span></span>  
<span data-ttu-id="68fec-187">[!code-vb[VbVbalrOperators&#51;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-187">[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]</span></span>  
  
 <span data-ttu-id="68fec-188">O exemplo a seguir ilustra o resultado quando `Option Strict` é `Off`.</span><span class="sxs-lookup"><span data-stu-id="68fec-188">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 <span data-ttu-id="68fec-189">[!code-vb[VbVbalrOperators&#54;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-189">[!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]</span></span>  
  
 <span data-ttu-id="68fec-190">[!code-vb[VbVbalrOperators&#50;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-190">[!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]</span></span>  
<span data-ttu-id="68fec-191">[!code-vb[VbVbalrOperators&#52;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="68fec-191">[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]</span></span>  
  
 <span data-ttu-id="68fec-192">Para eliminar a ambiguidade, você deve usar o `&` em vez do operador `+` para concatenação.</span><span class="sxs-lookup"><span data-stu-id="68fec-192">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fec-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68fec-193">See Also</span></span>  
 <span data-ttu-id="68fec-194">[< / Operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-194">[& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) </span></span>  
<span data-ttu-id="68fec-195"> [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-195"> [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span></span>  
<span data-ttu-id="68fec-196"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-196"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="68fec-197"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-197"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="68fec-198"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-198"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="68fec-199"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="68fec-199"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="68fec-200"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="68fec-200"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>

