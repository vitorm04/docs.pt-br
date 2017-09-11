---
title: "Operadores de comparação em Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a958481fa04cb1a9abde69c5215dccd6dbbe4a14
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="4558e-102">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4558e-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="4558e-103">Operadores de comparação comparam duas expressões e retornam um `Boolean` valor que representa a relação entre seus valores.</span><span class="sxs-lookup"><span data-stu-id="4558e-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="4558e-104">Há operadores para comparar valores numéricos, operadores para comparar cadeias de caracteres e operadores para comparar objetos.</span><span class="sxs-lookup"><span data-stu-id="4558e-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="4558e-105">Todos os três tipos de operadores serão discutidos aqui.</span><span class="sxs-lookup"><span data-stu-id="4558e-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="4558e-106">Comparando valores numéricos</span><span class="sxs-lookup"><span data-stu-id="4558e-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4558e-107">compara valores numéricos usando seis operadores de comparação numérica.</span><span class="sxs-lookup"><span data-stu-id="4558e-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="4558e-108">Cada operador toma como operandos duas expressões que retornam valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="4558e-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="4558e-109">A tabela a seguir lista os operadores e mostra exemplos de cada um.</span><span class="sxs-lookup"><span data-stu-id="4558e-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="4558e-110">Operador</span><span class="sxs-lookup"><span data-stu-id="4558e-110">Operator</span></span>|<span data-ttu-id="4558e-111">Condição testada</span><span class="sxs-lookup"><span data-stu-id="4558e-111">Condition tested</span></span>|<span data-ttu-id="4558e-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4558e-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="4558e-113">`=`(Igualdade)</span><span class="sxs-lookup"><span data-stu-id="4558e-113">`=` (Equality)</span></span>|<span data-ttu-id="4558e-114">É o valor da primeira expressão é igual ao valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="4558e-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="4558e-118">`<>`(Desigualdade)</span><span class="sxs-lookup"><span data-stu-id="4558e-118">`<>` (Inequality)</span></span>|<span data-ttu-id="4558e-119">O valor da primeira expressão é diferente do valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="4558e-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="4558e-123">`<`(Menor que)</span><span class="sxs-lookup"><span data-stu-id="4558e-123">`<` (Less than)</span></span>|<span data-ttu-id="4558e-124">É o valor da primeira expressão menor que o valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="4558e-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="4558e-128">`>`(Maior que)</span><span class="sxs-lookup"><span data-stu-id="4558e-128">`>` (Greater than)</span></span>|<span data-ttu-id="4558e-129">O valor da primeira expressão é maior que o valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="4558e-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="4558e-133">`<=`(Menor que ou igual a)</span><span class="sxs-lookup"><span data-stu-id="4558e-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="4558e-134">O valor da primeira expressão é menor ou igual ao valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="4558e-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="4558e-138">`>=`(Maior que ou igual a)</span><span class="sxs-lookup"><span data-stu-id="4558e-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="4558e-139">É o valor da primeira expressão maior que ou igual ao valor da segunda?</span><span class="sxs-lookup"><span data-stu-id="4558e-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="4558e-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="4558e-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="4558e-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="4558e-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="4558e-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="4558e-143">Comparando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4558e-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4558e-144">compara cadeias de caracteres usando o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md) , bem como os operadores de comparação numérica.</span><span class="sxs-lookup"><span data-stu-id="4558e-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="4558e-145">O `Like` operador permite que você especifique um padrão.</span><span class="sxs-lookup"><span data-stu-id="4558e-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="4558e-146">A cadeia de caracteres é comparada com o padrão e se há correspondência, o resultado é `True`.</span><span class="sxs-lookup"><span data-stu-id="4558e-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="4558e-147">Caso contrário, o resultado será `False`.</span><span class="sxs-lookup"><span data-stu-id="4558e-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="4558e-148">Os operadores numéricos permitem que você compare `String` valores com base em sua ordem de classificação, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4558e-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="4558e-149">O resultado no exemplo anterior é `True` porque o primeiro caractere na primeira cadeia de caracteres classifica-se antes do primeiro caractere na segunda cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4558e-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="4558e-150">Se os primeiros caracteres fossem iguais, a comparação seria continuar com o próximo caractere em ambas as cadeias de caracteres e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4558e-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="4558e-151">Você também pode testar a igualdade de cadeias de caracteres usando o operador de igualdade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4558e-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="4558e-152">Se uma cadeia de caracteres é um prefixo de outra, como "aa" e "aaa", a cadeia de caracteres mais longa será considerada para ser maior do que a cadeia de caracteres mais curta.</span><span class="sxs-lookup"><span data-stu-id="4558e-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="4558e-153">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="4558e-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="4558e-154">A ordem de classificação se baseia em uma comparação binária ou uma comparação textual, dependendo da configuração do `Option Compare`.</span><span class="sxs-lookup"><span data-stu-id="4558e-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="4558e-155">Para obter mais informações, consulte [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4558e-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="4558e-156">Comparando objetos</span><span class="sxs-lookup"><span data-stu-id="4558e-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4558e-157">compara dois objetos referenciando variáveis com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) e [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4558e-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="4558e-158">Você pode usar qualquer um desses operadores para determinar se duas variáveis de referência se referem à mesma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="4558e-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="4558e-159">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="4558e-159">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="4558e-160">[!code-vb[VbVbalrOperators&#65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4558e-160">[!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="4558e-161">No exemplo anterior, `x Is y` é avaliada como `True`, porque ambas as variáveis referem-se à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="4558e-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="4558e-162">Compare este resultado com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4558e-162">Contrast this result with the following example.</span></span>  
  
 <span data-ttu-id="4558e-163">[!code-vb[VbVbalrOperators&#66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4558e-163">[!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="4558e-164">No exemplo anterior, `x Is y` é avaliada como `False`, porque apesar das variáveis se referirem a objetos do mesmo tipo, elas se referem a diferentes instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="4558e-164">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="4558e-165">Quando você quiser testar se dois objetos não apontam para a mesma instância, o `IsNot` operador permite que você evite a gramaticalmente infeliz combinação de `Not` e `Is`.</span><span class="sxs-lookup"><span data-stu-id="4558e-165">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="4558e-166">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="4558e-166">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="4558e-167">[!code-vb[VbVbalrOperators&#67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4558e-167">[!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="4558e-168">No exemplo anterior, `If a IsNot b` é equivalente a `If Not a Is b`.</span><span class="sxs-lookup"><span data-stu-id="4558e-168">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="4558e-169">Comparando o tipo de objeto</span><span class="sxs-lookup"><span data-stu-id="4558e-169">Comparing Object Type</span></span>  
 <span data-ttu-id="4558e-170">Você pode testar se um objeto for de um tipo específico com o `TypeOf`... `Is` expressão.</span><span class="sxs-lookup"><span data-stu-id="4558e-170">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="4558e-171">A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="4558e-171">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="4558e-172">Quando `typename` Especifica um tipo de interface, então o `TypeOf`... `Is` retorna `True` se o objeto implementa o tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="4558e-172">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="4558e-173">Quando `typename` é um tipo de classe, então a expressão retorna `True` se o objeto for uma instância da classe especificada ou de uma classe que deriva da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="4558e-173">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="4558e-174">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="4558e-174">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="4558e-175">[!code-vb[VbVbalrOperators&#68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4558e-175">[!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="4558e-176">No exemplo anterior, o `TypeOf x Is Control` expressão é avaliada como `True` porque o tipo de `x` é `Button`, que herda do `Control`.</span><span class="sxs-lookup"><span data-stu-id="4558e-176">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="4558e-177">Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4558e-177">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4558e-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4558e-178">See Also</span></span>  
 <span data-ttu-id="4558e-179">[Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="4558e-179">[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="4558e-180"> [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4558e-180"> [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="4558e-181"> [Operadores](../../../../visual-basic/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="4558e-181"> [Operators](../../../../visual-basic/language-reference/operators/index.md) </span></span>  
<span data-ttu-id="4558e-182"> [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4558e-182"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="4558e-183"> [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4558e-183"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="4558e-184"> [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="4558e-184"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
