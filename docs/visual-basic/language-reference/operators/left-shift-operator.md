---
title: '&lt;&lt;Operador (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="bb51f-102">&lt;&lt;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb51f-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="bb51f-103">Executa um deslocamento aritmético à esquerda em um padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="bb51f-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb51f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb51f-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="bb51f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="bb51f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="bb51f-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bb51f-106">Required.</span></span> <span data-ttu-id="bb51f-107">Valor numérico inteiro.</span><span class="sxs-lookup"><span data-stu-id="bb51f-107">Integral numeric value.</span></span> <span data-ttu-id="bb51f-108">O resultado do deslocamento o padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="bb51f-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="bb51f-109">O tipo de dados é o mesmo de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="bb51f-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="bb51f-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bb51f-110">Required.</span></span> <span data-ttu-id="bb51f-111">Expressão numérica integral.</span><span class="sxs-lookup"><span data-stu-id="bb51f-111">Integral numeric expression.</span></span> <span data-ttu-id="bb51f-112">O padrão de bits a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="bb51f-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="bb51f-113">O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="bb51f-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="bb51f-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bb51f-114">Required.</span></span> <span data-ttu-id="bb51f-115">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="bb51f-115">Numeric expression.</span></span> <span data-ttu-id="bb51f-116">O número de bits para deslocar o padrão de bits.</span><span class="sxs-lookup"><span data-stu-id="bb51f-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="bb51f-117">O tipo de dados deve ser `Integer` ou ampliar a `Integer`.</span><span class="sxs-lookup"><span data-stu-id="bb51f-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb51f-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb51f-118">Remarks</span></span>  
 <span data-ttu-id="bb51f-119">Deslocamentos aritméticos não são circulares, que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="bb51f-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="bb51f-120">Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo do tipo de dados de resultado são descartados e as posições de bits vagas à direita são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="bb51f-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="bb51f-121">Para evitar um deslocamento de bits maior do que o resultado pode comportar, Visual Basic mascara o valor de `amount` com uma máscara de tamanho que corresponde ao tipo de dados de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="bb51f-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="bb51f-122">O binário AND desses valores é usado para o valor de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="bb51f-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="bb51f-123">As máscaras de tamanho são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bb51f-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="bb51f-124">Tipo de dados`pattern`</span><span class="sxs-lookup"><span data-stu-id="bb51f-124">Data type of `pattern`</span></span>|<span data-ttu-id="bb51f-125">Máscara de tamanho (decimal)</span><span class="sxs-lookup"><span data-stu-id="bb51f-125">Size mask (decimal)</span></span>|<span data-ttu-id="bb51f-126">Máscara de tamanho (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="bb51f-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="bb51f-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="bb51f-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="bb51f-128">7</span><span class="sxs-lookup"><span data-stu-id="bb51f-128">7</span></span>|<span data-ttu-id="bb51f-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="bb51f-129">&H00000007</span></span>|  
|<span data-ttu-id="bb51f-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="bb51f-130">`Short`, `UShort`</span></span>|<span data-ttu-id="bb51f-131">15</span><span class="sxs-lookup"><span data-stu-id="bb51f-131">15</span></span>|<span data-ttu-id="bb51f-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="bb51f-132">&H0000000F</span></span>|  
|<span data-ttu-id="bb51f-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="bb51f-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="bb51f-134">31</span><span class="sxs-lookup"><span data-stu-id="bb51f-134">31</span></span>|<span data-ttu-id="bb51f-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="bb51f-135">&H0000001F</span></span>|  
|<span data-ttu-id="bb51f-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="bb51f-136">`Long`, `ULong`</span></span>|<span data-ttu-id="bb51f-137">63</span><span class="sxs-lookup"><span data-stu-id="bb51f-137">63</span></span>|<span data-ttu-id="bb51f-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="bb51f-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="bb51f-139">Se `amount` for zero, o valor de `result` é idêntico ao valor de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="bb51f-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="bb51f-140">Se `amount` for negativo, ele é interpretado como um valor não assinado e mascarado com a máscara de tamanho apropriado.</span><span class="sxs-lookup"><span data-stu-id="bb51f-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="bb51f-141">Deslocamentos aritméticos nunca geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="bb51f-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb51f-142">O `<<` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bb51f-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bb51f-143">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="bb51f-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="bb51f-144">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bb51f-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb51f-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb51f-145">Example</span></span>  
 <span data-ttu-id="bb51f-146">O exemplo a seguir usa o `<<` operador para executar cálculos aritméticos deixado turnos em valores integral.</span><span class="sxs-lookup"><span data-stu-id="bb51f-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="bb51f-147">O resultado sempre tem os mesmos dados de tipo da expressão que está sendo alterado.</span><span class="sxs-lookup"><span data-stu-id="bb51f-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="bb51f-148">Os resultados do exemplo anterior são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="bb51f-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="bb51f-149">`result1`é 192 (0000 0000 0000 de 1100).</span><span class="sxs-lookup"><span data-stu-id="bb51f-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="bb51f-150">`result2`é 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="bb51f-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="bb51f-151">`result3`é -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="bb51f-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="bb51f-152">`result4`é 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="bb51f-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="bb51f-153">`result5`é 0 (deslocadas 15 casas à esquerda).</span><span class="sxs-lookup"><span data-stu-id="bb51f-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="bb51f-154">O valor de deslocamento para `result4` é calculado como 17 e 15, que é igual a 1.</span><span class="sxs-lookup"><span data-stu-id="bb51f-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb51f-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb51f-155">See Also</span></span>  
 [<span data-ttu-id="bb51f-156">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="bb51f-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="bb51f-157">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="bb51f-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="bb51f-158">Operador <<=</span><span class="sxs-lookup"><span data-stu-id="bb51f-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="bb51f-159">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb51f-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="bb51f-160">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="bb51f-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="bb51f-161">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb51f-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
