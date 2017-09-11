---
title: '&lt;&lt;Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<
dev_langs:
- VB
helpviewer_keywords:
- bit shift operators
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
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
ms.openlocfilehash: df28114438a8d241fad88446580ac0633adc0b2d
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="d4b81-102">&lt;&lt;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b81-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="d4b81-103">Executa um deslocamento aritmético para a esquerda em um padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="d4b81-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4b81-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="d4b81-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d4b81-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d4b81-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4b81-106">Required.</span></span> <span data-ttu-id="d4b81-107">Valor numérico inteiro.</span><span class="sxs-lookup"><span data-stu-id="d4b81-107">Integral numeric value.</span></span> <span data-ttu-id="d4b81-108">O resultado do deslocamento do padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="d4b81-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="d4b81-109">O tipo de dados é o mesmo que `pattern`.</span><span class="sxs-lookup"><span data-stu-id="d4b81-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="d4b81-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4b81-110">Required.</span></span> <span data-ttu-id="d4b81-111">Expressão numérica integral.</span><span class="sxs-lookup"><span data-stu-id="d4b81-111">Integral numeric expression.</span></span> <span data-ttu-id="d4b81-112">O padrão de bits a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="d4b81-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="d4b81-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="d4b81-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="d4b81-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4b81-114">Required.</span></span> <span data-ttu-id="d4b81-115">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="d4b81-115">Numeric expression.</span></span> <span data-ttu-id="d4b81-116">O número de bits para deslocar o padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="d4b81-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="d4b81-117">O tipo de dados deve ser `Integer` ou ampliar a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d4b81-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4b81-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4b81-118">Remarks</span></span>  
 <span data-ttu-id="d4b81-119">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados de uma extremidade do resultado não são reconectados na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="d4b81-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="d4b81-120">Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo do tipo de dados de resultado são descartados e as posições de bits vagas à direita são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="d4b81-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="d4b81-121">Para evitar um deslocamento de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho correspondente ao tipo de dados de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="d4b81-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="d4b81-122">O binário AND desses valores é usado para o valor de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="d4b81-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="d4b81-123">As máscaras de tamanho são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d4b81-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="d4b81-124">Tipo de dados`pattern`</span><span class="sxs-lookup"><span data-stu-id="d4b81-124">Data type of `pattern`</span></span>|<span data-ttu-id="d4b81-125">Máscara de tamanho (decimal)</span><span class="sxs-lookup"><span data-stu-id="d4b81-125">Size mask (decimal)</span></span>|<span data-ttu-id="d4b81-126">Máscara de tamanho (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="d4b81-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="d4b81-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="d4b81-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="d4b81-128">7</span><span class="sxs-lookup"><span data-stu-id="d4b81-128">7</span></span>|<span data-ttu-id="d4b81-129">&LT; / H00000007</span><span class="sxs-lookup"><span data-stu-id="d4b81-129">&H00000007</span></span>|  
|<span data-ttu-id="d4b81-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="d4b81-130">`Short`, `UShort`</span></span>|<span data-ttu-id="d4b81-131">15</span><span class="sxs-lookup"><span data-stu-id="d4b81-131">15</span></span>|<span data-ttu-id="d4b81-132">&LT; / H0000000F</span><span class="sxs-lookup"><span data-stu-id="d4b81-132">&H0000000F</span></span>|  
|<span data-ttu-id="d4b81-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="d4b81-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="d4b81-134">31</span><span class="sxs-lookup"><span data-stu-id="d4b81-134">31</span></span>|<span data-ttu-id="d4b81-135">&LT; / H0000001F</span><span class="sxs-lookup"><span data-stu-id="d4b81-135">&H0000001F</span></span>|  
|<span data-ttu-id="d4b81-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="d4b81-136">`Long`, `ULong`</span></span>|<span data-ttu-id="d4b81-137">63</span><span class="sxs-lookup"><span data-stu-id="d4b81-137">63</span></span>|<span data-ttu-id="d4b81-138">&LT; / H0000003F</span><span class="sxs-lookup"><span data-stu-id="d4b81-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="d4b81-139">Se `amount` for zero, o valor de `result` é idêntico ao valor de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="d4b81-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="d4b81-140">Se `amount` for negativo, ele é interpretado como um valor não assinado e mascarado com a máscara de tamanho apropriado.</span><span class="sxs-lookup"><span data-stu-id="d4b81-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="d4b81-141">Deslocamentos aritméticos nunca geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="d4b81-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4b81-142">O `<<` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="d4b81-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d4b81-143">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="d4b81-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="d4b81-144">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d4b81-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b81-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4b81-145">Example</span></span>  
 <span data-ttu-id="d4b81-146">O exemplo a seguir usa o `<<` operador para executar cálculos aritméticos ligado turnos valores integrais.</span><span class="sxs-lookup"><span data-stu-id="d4b81-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="d4b81-147">O resultado sempre tem os mesmos dados de tipo da expressão está sendo deslocada.</span><span class="sxs-lookup"><span data-stu-id="d4b81-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 <span data-ttu-id="d4b81-148">[!code-vb[VbVbalrOperators&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d4b81-148">[!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="d4b81-149">Os resultados do exemplo anterior são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d4b81-149">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="d4b81-150">`result1`é 192 (0000 0000 0000 de 1100).</span><span class="sxs-lookup"><span data-stu-id="d4b81-150">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="d4b81-151">`result2`é 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="d4b81-151">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="d4b81-152">`result3`é de -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="d4b81-152">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="d4b81-153">`result4`é 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="d4b81-153">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="d4b81-154">`result5`é 0 (deslocadas 15 locais para a esquerda).</span><span class="sxs-lookup"><span data-stu-id="d4b81-154">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="d4b81-155">O valor de deslocamento para `result4` é calculado como 17 e 15, que é igual a 1.</span><span class="sxs-lookup"><span data-stu-id="d4b81-155">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b81-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4b81-156">See Also</span></span>  
 <span data-ttu-id="d4b81-157">[Operadores bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span><span class="sxs-lookup"><span data-stu-id="d4b81-157">[Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span></span>  
<span data-ttu-id="d4b81-158"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="d4b81-158"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="d4b81-159"> [<=></=>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="d4b81-159"> [<<= Operator](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md) </span></span>  
<span data-ttu-id="d4b81-160"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="d4b81-160"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="d4b81-161"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="d4b81-161"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="d4b81-162"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="d4b81-162"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

