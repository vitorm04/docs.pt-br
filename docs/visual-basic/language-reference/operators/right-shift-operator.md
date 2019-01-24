---
title: '&gt;&gt; Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: e1d2b6569e2bcb3c1516dbc8c78adca0855481e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668490"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="c8003-102">&gt;&gt; Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8003-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="c8003-103">Executa um deslocamento aritmético à direita em um padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="c8003-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8003-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8003-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="c8003-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c8003-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="c8003-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c8003-106">Required.</span></span> <span data-ttu-id="c8003-107">Valor numérico integral.</span><span class="sxs-lookup"><span data-stu-id="c8003-107">Integral numeric value.</span></span> <span data-ttu-id="c8003-108">O resultado do deslocamento do padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="c8003-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="c8003-109">O tipo de dados é o mesmo que o de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="c8003-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="c8003-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c8003-110">Required.</span></span> <span data-ttu-id="c8003-111">Expressão numérica integral.</span><span class="sxs-lookup"><span data-stu-id="c8003-111">Integral numeric expression.</span></span> <span data-ttu-id="c8003-112">O padrão de bit a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="c8003-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="c8003-113">O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="c8003-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="c8003-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c8003-114">Required.</span></span> <span data-ttu-id="c8003-115">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="c8003-115">Numeric expression.</span></span> <span data-ttu-id="c8003-116">O número de bits para deslocar o padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="c8003-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="c8003-117">O tipo de dados deve ser `Integer` ou ampliado para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="c8003-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8003-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8003-118">Remarks</span></span>  
 <span data-ttu-id="c8003-119">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados em uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="c8003-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="c8003-120">Em um deslocamento aritmético à direita, os bits deslocados além da posição do bit mais à direita são descartados e o bit mais à esquerda (entrada) é propagado para as posições de bits vagas à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c8003-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="c8003-121">Isso significa que se `pattern` tem um valor negativo, as posições vagas são definidas como um; caso contrário, eles são definidos como zero.</span><span class="sxs-lookup"><span data-stu-id="c8003-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="c8003-122">Observe que os tipos de dados `Byte`, `UShort`, `UInteger`, e `ULong` são assinados e, portanto, não há nenhum bit de sinal para propagar.</span><span class="sxs-lookup"><span data-stu-id="c8003-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="c8003-123">Se `pattern` é de qualquer tipo não assinado, as posições vazias são sempre definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="c8003-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="c8003-124">Para impedir que o deslocamento de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho correspondente ao tipo de dados de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="c8003-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="c8003-125">O binário AND desses valores é usado para o valor de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="c8003-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="c8003-126">As máscaras de tamanho são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c8003-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="c8003-127">Tipo de dados do `pattern`</span><span class="sxs-lookup"><span data-stu-id="c8003-127">Data type of `pattern`</span></span>|<span data-ttu-id="c8003-128">Máscara de tamanho (decimal)</span><span class="sxs-lookup"><span data-stu-id="c8003-128">Size mask (decimal)</span></span>|<span data-ttu-id="c8003-129">Máscara de tamanho (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="c8003-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="c8003-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="c8003-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="c8003-131">7</span><span class="sxs-lookup"><span data-stu-id="c8003-131">7</span></span>|<span data-ttu-id="c8003-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="c8003-132">&H00000007</span></span>|  
|<span data-ttu-id="c8003-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="c8003-133">`Short`, `UShort`</span></span>|<span data-ttu-id="c8003-134">15</span><span class="sxs-lookup"><span data-stu-id="c8003-134">15</span></span>|<span data-ttu-id="c8003-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="c8003-135">&H0000000F</span></span>|  
|<span data-ttu-id="c8003-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="c8003-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="c8003-137">31</span><span class="sxs-lookup"><span data-stu-id="c8003-137">31</span></span>|<span data-ttu-id="c8003-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="c8003-138">&H0000001F</span></span>|  
|<span data-ttu-id="c8003-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="c8003-139">`Long`, `ULong`</span></span>|<span data-ttu-id="c8003-140">63</span><span class="sxs-lookup"><span data-stu-id="c8003-140">63</span></span>|<span data-ttu-id="c8003-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="c8003-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="c8003-142">Se `amount` for zero, o valor da `result` é idêntico ao valor de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="c8003-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="c8003-143">Se `amount` é negativo, ele é interpretado como um valor sem sinal e mascarado com a máscara de tamanho apropriado.</span><span class="sxs-lookup"><span data-stu-id="c8003-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="c8003-144">Deslocamentos aritméticos nunca geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="c8003-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c8003-145">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="c8003-145">Overloading</span></span>  
 <span data-ttu-id="c8003-146">O `>>` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c8003-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c8003-147">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="c8003-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c8003-148">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c8003-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8003-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8003-149">Example</span></span>  
 <span data-ttu-id="c8003-150">O exemplo a seguir usa o `>>` operador para executar aritméticos deslocamentos para a direito em valores integrais.</span><span class="sxs-lookup"><span data-stu-id="c8003-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="c8003-151">O resultado sempre tem os mesmos dados de tipo da expressão a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="c8003-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="c8003-152">Os resultados do exemplo anterior são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c8003-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="c8003-153">`result1` é 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="c8003-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="c8003-154">`result2` é de 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="c8003-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="c8003-155">`result3` é 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="c8003-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="c8003-156">`result4` é 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="c8003-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="c8003-157">`result5` é 0 (deslocadas 15 locais para a direita).</span><span class="sxs-lookup"><span data-stu-id="c8003-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="c8003-158">O valor de deslocamento para `result4` é calculado como 18 AND 15, que é igual a 2.</span><span class="sxs-lookup"><span data-stu-id="c8003-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="c8003-159">O exemplo a seguir mostra os deslocamentos aritméticos em um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="c8003-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="c8003-160">Os resultados do exemplo anterior são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c8003-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="c8003-161">`negresult1` é -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="c8003-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="c8003-162">`negresult2` é -1 (o bit de sinal é propagado).</span><span class="sxs-lookup"><span data-stu-id="c8003-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8003-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8003-163">See also</span></span>
- [<span data-ttu-id="c8003-164">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="c8003-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="c8003-165">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="c8003-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="c8003-166">Operador >>=</span><span class="sxs-lookup"><span data-stu-id="c8003-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="c8003-167">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8003-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c8003-168">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c8003-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c8003-169">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8003-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
