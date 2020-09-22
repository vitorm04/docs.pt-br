---
title: + Operador
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: bc31e4c66c64d891e3fffd809b7ae99b9c9a0520
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873454"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c325e-102">Operador + (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c325e-102">+ Operator (Visual Basic)</span></span>

<span data-ttu-id="c325e-103">Adiciona dois números ou retorna o valor positivo de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="c325e-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="c325e-104">Também pode ser usado para concatenar duas expressões de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c325e-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c325e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c325e-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="c325e-106">ou</span><span class="sxs-lookup"><span data-stu-id="c325e-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="c325e-107">Partes</span><span class="sxs-lookup"><span data-stu-id="c325e-107">Parts</span></span>  
  
|<span data-ttu-id="c325e-108">Termo</span><span class="sxs-lookup"><span data-stu-id="c325e-108">Term</span></span>|<span data-ttu-id="c325e-109">Definição</span><span class="sxs-lookup"><span data-stu-id="c325e-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="c325e-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c325e-110">Required.</span></span> <span data-ttu-id="c325e-111">Qualquer expressão numérica ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c325e-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="c325e-112">Necessário, a menos que o `+` operador esteja calculando um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="c325e-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="c325e-113">Qualquer expressão numérica ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c325e-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="c325e-114">Resultado</span><span class="sxs-lookup"><span data-stu-id="c325e-114">Result</span></span>  

 <span data-ttu-id="c325e-115">Se `expression1` e `expression2` forem ambos numéricos, o resultado será sua soma aritmética.</span><span class="sxs-lookup"><span data-stu-id="c325e-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="c325e-116">Se `expression2` estiver ausente, o `+` operador será o operador de identidade *unário* para o valor inalterado de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c325e-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="c325e-117">Nesse sentido, a operação consiste em reter o sinal de `expression1` , portanto, o resultado será negativo se `expression1` for negativo.</span><span class="sxs-lookup"><span data-stu-id="c325e-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="c325e-118">Se `expression1` e `expression2` forem as duas cadeias de caracteres, o resultado será a concatenação de seus valores.</span><span class="sxs-lookup"><span data-stu-id="c325e-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="c325e-119">Se `expression1` e `expression2` forem de tipos mistos, a ação executada dependerá de seus tipos, do seu conteúdo e da configuração da [instrução Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c325e-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="c325e-120">Para obter mais informações, consulte as tabelas em "Comentários".</span><span class="sxs-lookup"><span data-stu-id="c325e-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c325e-121">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="c325e-121">Supported Types</span></span>  

 <span data-ttu-id="c325e-122">Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinado e e `Decimal` `String` .</span><span class="sxs-lookup"><span data-stu-id="c325e-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c325e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c325e-123">Remarks</span></span>  

 <span data-ttu-id="c325e-124">Em geral, `+` o executa a adição aritmética quando possível e concatena somente quando ambas as expressões são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c325e-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="c325e-125">Se nenhuma expressão for uma `Object` , Visual Basic executará as seguintes ações.</span><span class="sxs-lookup"><span data-stu-id="c325e-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="c325e-126">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="c325e-126">Data types of expressions</span></span>|<span data-ttu-id="c325e-127">Ação por compilador</span><span class="sxs-lookup"><span data-stu-id="c325e-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c325e-128">As duas expressões são tipos de dados numéricos (,,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` , `Decimal` , `Single` ou `Double` )</span><span class="sxs-lookup"><span data-stu-id="c325e-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="c325e-129">Adicionar.</span><span class="sxs-lookup"><span data-stu-id="c325e-129">Add.</span></span> <span data-ttu-id="c325e-130">O tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2` .</span><span class="sxs-lookup"><span data-stu-id="c325e-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="c325e-131">Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="c325e-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="c325e-132">Ambas as expressões são do tipo `String`</span><span class="sxs-lookup"><span data-stu-id="c325e-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="c325e-133">Concatenar.</span><span class="sxs-lookup"><span data-stu-id="c325e-133">Concatenate.</span></span>|  
|<span data-ttu-id="c325e-134">Uma expressão é um tipo de dados numérico e a outra é uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c325e-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="c325e-135">Se `Option Strict` for `On` , gere um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c325e-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c325e-136">Se `Option Strict` for `Off` , converta implicitamente o `String` para `Double` e adicione.</span><span class="sxs-lookup"><span data-stu-id="c325e-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c325e-137">Se o `String` não puder ser convertido em `Double` , lance uma <xref:System.InvalidCastException> exceção.</span><span class="sxs-lookup"><span data-stu-id="c325e-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c325e-138">Uma expressão é um tipo de dados numérico e a outra é [Nothing](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="c325e-138">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="c325e-139">Adicionar, com `Nothing` valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="c325e-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="c325e-140">Uma expressão é uma cadeia de caracteres e a outra é `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c325e-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="c325e-141">Concatenar, com `Nothing` valor "".</span><span class="sxs-lookup"><span data-stu-id="c325e-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="c325e-142">Se uma expressão for uma `Object` expressão, Visual Basic executará as seguintes ações.</span><span class="sxs-lookup"><span data-stu-id="c325e-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="c325e-143">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="c325e-143">Data types of expressions</span></span>|<span data-ttu-id="c325e-144">Ação por compilador</span><span class="sxs-lookup"><span data-stu-id="c325e-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c325e-145">`Object` a expressão contém um valor numérico e o outro é um tipo de dados numérico</span><span class="sxs-lookup"><span data-stu-id="c325e-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="c325e-146">Se `Option Strict` for `On` , gere um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c325e-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c325e-147">Se `Option Strict` for `Off` , adicione.</span><span class="sxs-lookup"><span data-stu-id="c325e-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="c325e-148">`Object` a expressão contém um valor numérico e o outro é do tipo `String`</span><span class="sxs-lookup"><span data-stu-id="c325e-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="c325e-149">Se `Option Strict` for `On` , gere um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c325e-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c325e-150">Se `Option Strict` for `Off` , converta implicitamente o `String` para `Double` e adicione.</span><span class="sxs-lookup"><span data-stu-id="c325e-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c325e-151">Se o `String` não puder ser convertido em `Double` , lance uma <xref:System.InvalidCastException> exceção.</span><span class="sxs-lookup"><span data-stu-id="c325e-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c325e-152">`Object` a expressão contém uma cadeia de caracteres e a outra é um tipo de dados numérico</span><span class="sxs-lookup"><span data-stu-id="c325e-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="c325e-153">Se `Option Strict` for `On` , gere um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c325e-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c325e-154">Se `Option Strict` for `Off` , converta implicitamente a cadeia de caracteres `Object` para `Double` e adicione.</span><span class="sxs-lookup"><span data-stu-id="c325e-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c325e-155">Se a cadeia de caracteres `Object` não puder ser convertida em `Double` , lance uma <xref:System.InvalidCastException> exceção.</span><span class="sxs-lookup"><span data-stu-id="c325e-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c325e-156">`Object` a expressão contém uma cadeia de caracteres e a outra é do tipo `String`</span><span class="sxs-lookup"><span data-stu-id="c325e-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="c325e-157">Se `Option Strict` for `On` , gere um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c325e-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c325e-158">Se `Option Strict` for `Off` , então converta implicitamente `Object` `String` e concatene.</span><span class="sxs-lookup"><span data-stu-id="c325e-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="c325e-159">Se ambas as expressões forem `Object` expressões, Visual Basic executará as seguintes ações ( `Option Strict Off` somente).</span><span class="sxs-lookup"><span data-stu-id="c325e-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="c325e-160">Tipos de dados de expressões</span><span class="sxs-lookup"><span data-stu-id="c325e-160">Data types of expressions</span></span>|<span data-ttu-id="c325e-161">Ação por compilador</span><span class="sxs-lookup"><span data-stu-id="c325e-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c325e-162">Ambas as `Object` expressões contêm valores numéricos</span><span class="sxs-lookup"><span data-stu-id="c325e-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="c325e-163">Adicionar.</span><span class="sxs-lookup"><span data-stu-id="c325e-163">Add.</span></span>|  
|<span data-ttu-id="c325e-164">Ambas as `Object` expressões são do tipo `String`</span><span class="sxs-lookup"><span data-stu-id="c325e-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="c325e-165">Concatenar.</span><span class="sxs-lookup"><span data-stu-id="c325e-165">Concatenate.</span></span>|  
|<span data-ttu-id="c325e-166">Uma `Object` expressão contém um valor numérico e a outra contém uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c325e-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="c325e-167">Converta implicitamente a cadeia de caracteres `Object` para `Double` e adicione.</span><span class="sxs-lookup"><span data-stu-id="c325e-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c325e-168">Se a cadeia de caracteres `Object` não puder ser convertida em um valor numérico, lance uma <xref:System.InvalidCastException> exceção.</span><span class="sxs-lookup"><span data-stu-id="c325e-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="c325e-169">Se qualquer `Object` expressão for avaliada como [Nothing](../nothing.md) ou <xref:System.DBNull> , o `+` operador a tratará como um `String` com um valor de "".</span><span class="sxs-lookup"><span data-stu-id="c325e-169">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c325e-170">Ao usar o `+` operador, talvez você não consiga determinar se a adição ou a concatenação de cadeia de caracteres ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="c325e-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="c325e-171">Use o `&` operador para concatenação para eliminar ambigüidade e fornecer código de autodocumentação.</span><span class="sxs-lookup"><span data-stu-id="c325e-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c325e-172">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="c325e-172">Overloading</span></span>  

 <span data-ttu-id="c325e-173">O `+` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c325e-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c325e-174">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="c325e-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c325e-175">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c325e-175">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c325e-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c325e-176">Example</span></span>  

 <span data-ttu-id="c325e-177">O exemplo a seguir usa o `+` operador para adicionar números.</span><span class="sxs-lookup"><span data-stu-id="c325e-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="c325e-178">Se os operandos forem numéricos, Visual Basic calculará o resultado aritmético.</span><span class="sxs-lookup"><span data-stu-id="c325e-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="c325e-179">O resultado aritmético representa a soma dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="c325e-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="c325e-180">Você também pode usar o `+` operador para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c325e-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="c325e-181">Se os operandos forem as duas cadeias de caracteres, Visual Basic as concatena.</span><span class="sxs-lookup"><span data-stu-id="c325e-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="c325e-182">O resultado da concatenação representa uma única cadeia de caracteres que consiste no conteúdo dos dois operandos um após o outro.</span><span class="sxs-lookup"><span data-stu-id="c325e-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="c325e-183">Se os operandos forem de tipos mistos, o resultado dependerá da configuração da [instrução Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c325e-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="c325e-184">O exemplo a seguir ilustra o resultado quando `Option Strict` é `On` .</span><span class="sxs-lookup"><span data-stu-id="c325e-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="c325e-185">O exemplo a seguir ilustra o resultado quando `Option Strict` é `Off` .</span><span class="sxs-lookup"><span data-stu-id="c325e-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="c325e-186">Para eliminar a ambiguidade, você deve usar o `&` operador em vez de `+` para concatenação.</span><span class="sxs-lookup"><span data-stu-id="c325e-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c325e-187">Confira também</span><span class="sxs-lookup"><span data-stu-id="c325e-187">See also</span></span>

- [<span data-ttu-id="c325e-188"> Operador de&</span><span class="sxs-lookup"><span data-stu-id="c325e-188">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="c325e-189">Operadores de concatenação</span><span class="sxs-lookup"><span data-stu-id="c325e-189">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="c325e-190">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="c325e-190">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c325e-191">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c325e-191">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c325e-192">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c325e-192">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c325e-193">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c325e-193">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="c325e-194">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="c325e-194">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
