---
title: '&gt;&gt;Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
dev_langs:
- VB
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators
- operator >>
- right shift operators
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
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
ms.openlocfilehash: e693e04ea1a52a70f8e8c6c0bd1651c84aee34f3
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="b81e7-102">&gt;&gt;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b81e7-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="b81e7-103">Executa um deslocamento aritmético à direita em um padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="b81e7-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b81e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b81e7-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b81e7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b81e7-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b81e7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b81e7-106">Required.</span></span> <span data-ttu-id="b81e7-107">Valor numérico inteiro.</span><span class="sxs-lookup"><span data-stu-id="b81e7-107">Integral numeric value.</span></span> <span data-ttu-id="b81e7-108">O resultado do deslocamento do padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="b81e7-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="b81e7-109">O tipo de dados é o mesmo que `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b81e7-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="b81e7-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b81e7-110">Required.</span></span> <span data-ttu-id="b81e7-111">Expressão numérica integral.</span><span class="sxs-lookup"><span data-stu-id="b81e7-111">Integral numeric expression.</span></span> <span data-ttu-id="b81e7-112">O padrão de bits a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="b81e7-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="b81e7-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b81e7-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b81e7-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b81e7-114">Required.</span></span> <span data-ttu-id="b81e7-115">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="b81e7-115">Numeric expression.</span></span> <span data-ttu-id="b81e7-116">O número de bits para deslocar o padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="b81e7-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="b81e7-117">O tipo de dados deve ser `Integer` ou ampliar a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b81e7-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b81e7-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b81e7-118">Remarks</span></span>  
 <span data-ttu-id="b81e7-119">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="b81e7-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b81e7-120">Em um deslocamento aritmético à direita, os bits deslocados além da posição mais à direita de bits são descartados, e o bit mais à esquerda (entrada) é propagado para as posições de bits vagas à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b81e7-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="b81e7-121">Isso significa que se `pattern` tem um valor negativo, as posições vagas são definidas como um; caso contrário, eles são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="b81e7-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="b81e7-122">Observe que os tipos de dados `Byte`, `UShort`, `UInteger`, e `ULong` são assinados e, portanto, não há nenhum bit de sinal para se propagar.</span><span class="sxs-lookup"><span data-stu-id="b81e7-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="b81e7-123">Se `pattern` for de qualquer tipo não assinado, as posições vazias são sempre definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="b81e7-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="b81e7-124">Para evitar um deslocamento de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho correspondente ao tipo de dados de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b81e7-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="b81e7-125">O binário AND desses valores é usado para o valor de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="b81e7-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="b81e7-126">As máscaras de tamanho são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b81e7-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="b81e7-127">Tipo de dados`pattern`</span><span class="sxs-lookup"><span data-stu-id="b81e7-127">Data type of `pattern`</span></span>|<span data-ttu-id="b81e7-128">Máscara de tamanho (decimal)</span><span class="sxs-lookup"><span data-stu-id="b81e7-128">Size mask (decimal)</span></span>|<span data-ttu-id="b81e7-129">Máscara de tamanho (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="b81e7-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="b81e7-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="b81e7-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="b81e7-131">7</span><span class="sxs-lookup"><span data-stu-id="b81e7-131">7</span></span>|<span data-ttu-id="b81e7-132">&LT; / H00000007</span><span class="sxs-lookup"><span data-stu-id="b81e7-132">&H00000007</span></span>|  
|<span data-ttu-id="b81e7-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="b81e7-133">`Short`, `UShort`</span></span>|<span data-ttu-id="b81e7-134">15</span><span class="sxs-lookup"><span data-stu-id="b81e7-134">15</span></span>|<span data-ttu-id="b81e7-135">&LT; / H0000000F</span><span class="sxs-lookup"><span data-stu-id="b81e7-135">&H0000000F</span></span>|  
|<span data-ttu-id="b81e7-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="b81e7-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="b81e7-137">31</span><span class="sxs-lookup"><span data-stu-id="b81e7-137">31</span></span>|<span data-ttu-id="b81e7-138">&LT; / H0000001F</span><span class="sxs-lookup"><span data-stu-id="b81e7-138">&H0000001F</span></span>|  
|<span data-ttu-id="b81e7-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="b81e7-139">`Long`, `ULong`</span></span>|<span data-ttu-id="b81e7-140">63</span><span class="sxs-lookup"><span data-stu-id="b81e7-140">63</span></span>|<span data-ttu-id="b81e7-141">&LT; / H0000003F</span><span class="sxs-lookup"><span data-stu-id="b81e7-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="b81e7-142">Se `amount` for zero, o valor de `result` é idêntico ao valor de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b81e7-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="b81e7-143">Se `amount` for negativo, ele é interpretado como um valor não assinado e mascarado com a máscara de tamanho apropriado.</span><span class="sxs-lookup"><span data-stu-id="b81e7-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="b81e7-144">Deslocamentos aritméticos nunca geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="b81e7-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b81e7-145">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="b81e7-145">Overloading</span></span>  
 <span data-ttu-id="b81e7-146">O `>>` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="b81e7-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b81e7-147">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="b81e7-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b81e7-148">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b81e7-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b81e7-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b81e7-149">Example</span></span>  
 <span data-ttu-id="b81e7-150">O exemplo a seguir usa o `>>` operador para executar deslocamentos aritméticos para a direita em valores integral.</span><span class="sxs-lookup"><span data-stu-id="b81e7-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="b81e7-151">O resultado sempre tem os mesmos dados de tipo da expressão está sendo deslocada.</span><span class="sxs-lookup"><span data-stu-id="b81e7-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 <span data-ttu-id="b81e7-152">[!code-vb[VbVbalrOperators&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b81e7-152">[!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="b81e7-153">Os resultados do exemplo anterior são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="b81e7-153">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="b81e7-154">`result1`é 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b81e7-154">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="b81e7-155">`result2`é de 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="b81e7-155">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="b81e7-156">`result3`é 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="b81e7-156">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="b81e7-157">`result4`é 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="b81e7-157">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="b81e7-158">`result5`é 0 (deslocadas 15 locais para a direita).</span><span class="sxs-lookup"><span data-stu-id="b81e7-158">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="b81e7-159">O valor de deslocamento para `result4` é calculado como 18 AND 15, que é igual a 2.</span><span class="sxs-lookup"><span data-stu-id="b81e7-159">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="b81e7-160">O exemplo a seguir mostra deslocamentos aritméticos em um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="b81e7-160">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 <span data-ttu-id="b81e7-161">[!code-vb[VbVbalrOperators&#55;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b81e7-161">[!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="b81e7-162">Os resultados do exemplo anterior são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="b81e7-162">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="b81e7-163">`negresult1`é -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b81e7-163">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="b81e7-164">`negresult2`é -1 (o bit de sinal é propagado).</span><span class="sxs-lookup"><span data-stu-id="b81e7-164">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81e7-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b81e7-165">See Also</span></span>  
 <span data-ttu-id="b81e7-166">[Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b81e7-166">[Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span></span>  
<span data-ttu-id="b81e7-167"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b81e7-167"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="b81e7-168"> [>> = Operador](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b81e7-168"> [>>= Operator](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md) </span></span>  
<span data-ttu-id="b81e7-169"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="b81e7-169"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="b81e7-170"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="b81e7-170"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="b81e7-171"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="b81e7-171"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

