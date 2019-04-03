---
title: Operadores de comparação (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821030"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="73cf7-102">Operadores de comparação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73cf7-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="73cf7-103">A seguir estão os operadores de comparação definidos no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73cf7-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="73cf7-104">`<` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-104">`<` operator</span></span>  
  
 <span data-ttu-id="73cf7-105">`<=` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-105">`<=` operator</span></span>  
  
 <span data-ttu-id="73cf7-106">`>` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-106">`>` operator</span></span>  
  
 <span data-ttu-id="73cf7-107">`>=` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-107">`>=` operator</span></span>  
  
 <span data-ttu-id="73cf7-108">`=` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-108">`=` operator</span></span>  
  
 <span data-ttu-id="73cf7-109">`<>` operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="73cf7-110">Operador Is</span><span class="sxs-lookup"><span data-stu-id="73cf7-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="73cf7-111">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="73cf7-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="73cf7-112">Operador Like</span><span class="sxs-lookup"><span data-stu-id="73cf7-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="73cf7-113">Esses operadores comparam duas expressões para determinar se eles forem iguais e se não estiver, como eles diferem.</span><span class="sxs-lookup"><span data-stu-id="73cf7-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="73cf7-114">`Is`, `IsNot`, e `Like` são discutidos em detalhes nas páginas de Ajuda separadas.</span><span class="sxs-lookup"><span data-stu-id="73cf7-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="73cf7-115">Os operadores de comparação relacional são discutidos em detalhes nesta página.</span><span class="sxs-lookup"><span data-stu-id="73cf7-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cf7-116">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73cf7-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="73cf7-117">Partes</span><span class="sxs-lookup"><span data-stu-id="73cf7-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="73cf7-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-118">Required.</span></span> <span data-ttu-id="73cf7-119">Um `Boolean` que representa o resultado da comparação de valor.</span><span class="sxs-lookup"><span data-stu-id="73cf7-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="73cf7-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-120">Required.</span></span> <span data-ttu-id="73cf7-121">Qualquer expressão.</span><span class="sxs-lookup"><span data-stu-id="73cf7-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="73cf7-122">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-122">Required.</span></span> <span data-ttu-id="73cf7-123">Qualquer operador de comparação relacional.</span><span class="sxs-lookup"><span data-stu-id="73cf7-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="73cf7-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="73cf7-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="73cf7-125">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-125">Required.</span></span> <span data-ttu-id="73cf7-126">Qualquer referência a nomes de objeto.</span><span class="sxs-lookup"><span data-stu-id="73cf7-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="73cf7-127">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-127">Required.</span></span> <span data-ttu-id="73cf7-128">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="73cf7-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="73cf7-129">Necessário.</span><span class="sxs-lookup"><span data-stu-id="73cf7-129">Required.</span></span> <span data-ttu-id="73cf7-130">Qualquer `String` expressão ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="73cf7-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73cf7-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="73cf7-131">Remarks</span></span>  
 <span data-ttu-id="73cf7-132">A tabela a seguir contém uma lista de operadores de comparação relacional e as condições que determinam se `result` está `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="73cf7-133">Operador</span><span class="sxs-lookup"><span data-stu-id="73cf7-133">Operator</span></span>|<span data-ttu-id="73cf7-134">`True` se</span><span class="sxs-lookup"><span data-stu-id="73cf7-134">`True` if</span></span>|<span data-ttu-id="73cf7-135">`False` se</span><span class="sxs-lookup"><span data-stu-id="73cf7-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="73cf7-136">`<` (Menor que)</span><span class="sxs-lookup"><span data-stu-id="73cf7-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="73cf7-137">`<=` (Menor que ou igual a)</span><span class="sxs-lookup"><span data-stu-id="73cf7-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="73cf7-138">`>` (Maior que)</span><span class="sxs-lookup"><span data-stu-id="73cf7-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="73cf7-139">`>=` (Maior que ou igual a)</span><span class="sxs-lookup"><span data-stu-id="73cf7-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="73cf7-140">`=` (Igual a)</span><span class="sxs-lookup"><span data-stu-id="73cf7-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="73cf7-141">`<>` (Não igual a)</span><span class="sxs-lookup"><span data-stu-id="73cf7-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="73cf7-142">O [operador =](../../../visual-basic/language-reference/operators/assignment-operator.md) também é usado como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="73cf7-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="73cf7-143">O `Is` operador, o `IsNot` operador e o `Like` operador ter funcionalidades de comparação específicas que são diferentes dos operadores na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="73cf7-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="73cf7-144">Comparação de números</span><span class="sxs-lookup"><span data-stu-id="73cf7-144">Comparing Numbers</span></span>  
 <span data-ttu-id="73cf7-145">Se você comparar uma expressão do tipo `Single` a um do tipo `Double`, o `Single` expressão é convertida em `Double`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="73cf7-146">Esse comportamento é o oposto o comportamento encontrado no Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="73cf7-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="73cf7-147">Da mesma forma, se você comparar uma expressão do tipo `Decimal` em uma expressão de tipo `Single` ou `Double`, o `Decimal` converter a expressão `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="73cf7-148">Para `Decimal` expressões, qualquer valor fracionário menor que 1E-28 pode ser perdido.</span><span class="sxs-lookup"><span data-stu-id="73cf7-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="73cf7-149">Essa perda do valor fracionário pode causar dois valores sejam comparados como iguais quando eles não são.</span><span class="sxs-lookup"><span data-stu-id="73cf7-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="73cf7-150">Por esse motivo, você deve ter cuidado ao usar a igualdade (`=`) para comparar duas variáveis de ponto flutuantes.</span><span class="sxs-lookup"><span data-stu-id="73cf7-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="73cf7-151">É mais seguro testar se o valor absoluto da diferença entre os dois números é menor que um pequeno tolerância aceitável.</span><span class="sxs-lookup"><span data-stu-id="73cf7-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="73cf7-152">Ponto flutuante imprecisão</span><span class="sxs-lookup"><span data-stu-id="73cf7-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="73cf7-153">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="73cf7-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="73cf7-154">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o [operador Mod](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="73cf7-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="73cf7-155">Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="73cf7-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="73cf7-156">Comparando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="73cf7-156">Comparing Strings</span></span>  
 <span data-ttu-id="73cf7-157">Ao comparar cadeias de caracteres, as expressões de cadeia de caracteres são avaliadas com base em sua ordem de classificação em ordem alfabética, que depende de `Option Compare` configuração.</span><span class="sxs-lookup"><span data-stu-id="73cf7-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="73cf7-158">`Option Compare Binary` bases de comparações em uma ordem de classificação derivada de representações binárias internas dos caracteres da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="73cf7-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="73cf7-159">A ordem de classificação é determinada pela página de código.</span><span class="sxs-lookup"><span data-stu-id="73cf7-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="73cf7-160">O exemplo a seguir mostra uma ordem de classificação binária típica.</span><span class="sxs-lookup"><span data-stu-id="73cf7-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="73cf7-161">`Option Compare Text` bases de cadeia de caracteres comparações em uma ordem de classificação textual diferencia maiusculas de minúsculas determinada pela localidade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73cf7-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="73cf7-162">Quando você define `Option Compare Text` e classificar os caracteres no exemplo anterior, a ordem de classificação seguinte se aplica:</span><span class="sxs-lookup"><span data-stu-id="73cf7-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="73cf7-163">Dependência de localidade</span><span class="sxs-lookup"><span data-stu-id="73cf7-163">Locale Dependence</span></span>  
 <span data-ttu-id="73cf7-164">Quando você define `Option Compare Text`, o resultado de uma comparação de cadeia de caracteres pode depender de localidade no qual o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="73cf7-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="73cf7-165">Dois caracteres podem ser comparados como iguais em uma localidade, mas não em outro.</span><span class="sxs-lookup"><span data-stu-id="73cf7-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="73cf7-166">Se você estiver usando uma comparação de cadeia de caracteres para tomar decisões importantes, como se deseja aceitar uma tentativa de fazer logon, você deve estar alerta a distinção de localidade.</span><span class="sxs-lookup"><span data-stu-id="73cf7-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="73cf7-167">Considere uma das configurações `Option Compare Binary` ou chamando o <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, que usa a localidade em consideração.</span><span class="sxs-lookup"><span data-stu-id="73cf7-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="73cf7-168">Programação sem tipo com operadores de comparação relacional</span><span class="sxs-lookup"><span data-stu-id="73cf7-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="73cf7-169">O uso de operadores de comparação relacional `Object` expressões não é permitido em `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="73cf7-170">Quando `Option Strict` está `Off`e qualquer `expression1` ou `expression2` é um `Object` expressão, os tipos de tempo de execução determinam como são comparados.</span><span class="sxs-lookup"><span data-stu-id="73cf7-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="73cf7-171">A tabela a seguir mostra como as expressões são comparadas e o resultado da comparação, dependendo do tipo de tempo de execução dos operandos.</span><span class="sxs-lookup"><span data-stu-id="73cf7-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="73cf7-172">Se os operandos forem</span><span class="sxs-lookup"><span data-stu-id="73cf7-172">If operands are</span></span>|<span data-ttu-id="73cf7-173">A comparação é</span><span class="sxs-lookup"><span data-stu-id="73cf7-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="73cf7-174">Ambos `String`</span><span class="sxs-lookup"><span data-stu-id="73cf7-174">Both `String`</span></span>|<span data-ttu-id="73cf7-175">Comparação com base em características de classificação de cadeia de caracteres de classificação.</span><span class="sxs-lookup"><span data-stu-id="73cf7-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="73cf7-176">Ambas numéricas</span><span class="sxs-lookup"><span data-stu-id="73cf7-176">Both numeric</span></span>|<span data-ttu-id="73cf7-177">Os objetos convertidos `Double`, comparação numérica.</span><span class="sxs-lookup"><span data-stu-id="73cf7-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="73cf7-178">Um numérico e uma `String`</span><span class="sxs-lookup"><span data-stu-id="73cf7-178">One numeric and one `String`</span></span>|<span data-ttu-id="73cf7-179">O `String` é convertido em um `Double` e comparação numérica é executada.</span><span class="sxs-lookup"><span data-stu-id="73cf7-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="73cf7-180">Se o `String` não pode ser convertido em `Double`, um <xref:System.InvalidCastException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="73cf7-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="73cf7-181">Um ou ambos são tipos de referência diferente de `String`</span><span class="sxs-lookup"><span data-stu-id="73cf7-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="73cf7-182"><xref:System.InvalidCastException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="73cf7-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="73cf7-183">Tratam comparações numéricas `Nothing` como 0.</span><span class="sxs-lookup"><span data-stu-id="73cf7-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="73cf7-184">Comparações de cadeia de caracteres tratam `Nothing` como `""` (uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="73cf7-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="73cf7-185">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="73cf7-185">Overloading</span></span>  
 <span data-ttu-id="73cf7-186">Os operadores de comparação relacional (`<`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="73cf7-187">`<=``>`, `>=`, `=`, `<>`) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="73cf7-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="73cf7-188">Se seu código usa qualquer um destes operadores em uma classe ou estrutura, certifique-se de que você entende o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="73cf7-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="73cf7-189">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="73cf7-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="73cf7-190">Observe que o [operador =](../../../visual-basic/language-reference/operators/assignment-operator.md) podem ser sobrecarregadas apenas como um operador de comparação relacional, e não como um operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="73cf7-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73cf7-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73cf7-191">Example</span></span>  
 <span data-ttu-id="73cf7-192">O exemplo a seguir mostra vários usos de operadores de comparação relacional, que você usa para comparar expressões.</span><span class="sxs-lookup"><span data-stu-id="73cf7-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="73cf7-193">Operadores de comparação relacional retornam um `Boolean` que representa se a expressão declarada é avaliada como resultado `True`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="73cf7-194">Quando você aplica a `>` e `<` operadores em cadeias de caracteres, a comparação é feita usando a ordem de classificação alfabética normal das cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="73cf7-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="73cf7-195">Essa ordem pode ser dependente de configuração de localidade.</span><span class="sxs-lookup"><span data-stu-id="73cf7-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="73cf7-196">Se a classificação é diferencia maiusculas de minúsculas ou não depende de [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) configuração.</span><span class="sxs-lookup"><span data-stu-id="73cf7-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 <span data-ttu-id="73cf7-197">No exemplo anterior, a primeira comparação retorna `False` e as demais comparações retornam `True`.</span><span class="sxs-lookup"><span data-stu-id="73cf7-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cf7-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73cf7-198">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="73cf7-199">Operador =</span><span class="sxs-lookup"><span data-stu-id="73cf7-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="73cf7-200">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73cf7-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="73cf7-201">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="73cf7-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="73cf7-202">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="73cf7-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="73cf7-203">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73cf7-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
