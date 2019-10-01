---
title: Operador de < de < (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701120"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a73ec-102">\<\<Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a73ec-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="a73ec-103">Executa um deslocamento aritmético para a esquerda em um padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="a73ec-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a73ec-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="a73ec-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a73ec-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a73ec-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a73ec-106">Required.</span></span> <span data-ttu-id="a73ec-107">Valor numérico integral.</span><span class="sxs-lookup"><span data-stu-id="a73ec-107">Integral numeric value.</span></span> <span data-ttu-id="a73ec-108">O resultado do deslocamento do padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="a73ec-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="a73ec-109">O tipo de dados é o mesmo que o de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="a73ec-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="a73ec-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a73ec-110">Required.</span></span> <span data-ttu-id="a73ec-111">Expressão numérica integral.</span><span class="sxs-lookup"><span data-stu-id="a73ec-111">Integral numeric expression.</span></span> <span data-ttu-id="a73ec-112">O padrão de bit a ser deslocado.</span><span class="sxs-lookup"><span data-stu-id="a73ec-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="a73ec-113">O tipo de dados deve ser um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="a73ec-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="a73ec-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a73ec-114">Required.</span></span> <span data-ttu-id="a73ec-115">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="a73ec-115">Numeric expression.</span></span> <span data-ttu-id="a73ec-116">O número de bits para deslocar o padrão de bit.</span><span class="sxs-lookup"><span data-stu-id="a73ec-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="a73ec-117">O tipo de dados deve ser `Integer` ou ampliado para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a73ec-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a73ec-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a73ec-118">Remarks</span></span>  
 <span data-ttu-id="a73ec-119">Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="a73ec-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="a73ec-120">Em um deslocamento aritmético à esquerda, os bits deslocados além do intervalo do tipo de dados de resultado são descartados e as posições de bits vagadas à direita são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="a73ec-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="a73ec-121">Para evitar uma mudança de mais bits do que o resultado pode conter, Visual Basic mascara o valor de `amount` com uma máscara de tamanho que corresponde ao tipo de dados de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="a73ec-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="a73ec-122">O binário e desses valores é usado para o valor de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="a73ec-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="a73ec-123">As máscaras de tamanho são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="a73ec-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="a73ec-124">Tipo de dados de `pattern`</span><span class="sxs-lookup"><span data-stu-id="a73ec-124">Data type of `pattern`</span></span>|<span data-ttu-id="a73ec-125">Máscara de tamanho (Decimal)</span><span class="sxs-lookup"><span data-stu-id="a73ec-125">Size mask (decimal)</span></span>|<span data-ttu-id="a73ec-126">Máscara de tamanho (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="a73ec-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="a73ec-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="a73ec-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="a73ec-128">7</span><span class="sxs-lookup"><span data-stu-id="a73ec-128">7</span></span>|<span data-ttu-id="a73ec-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="a73ec-129">&H00000007</span></span>|  
|<span data-ttu-id="a73ec-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="a73ec-130">`Short`, `UShort`</span></span>|<span data-ttu-id="a73ec-131">15</span><span class="sxs-lookup"><span data-stu-id="a73ec-131">15</span></span>|<span data-ttu-id="a73ec-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="a73ec-132">&H0000000F</span></span>|  
|<span data-ttu-id="a73ec-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="a73ec-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="a73ec-134">31</span><span class="sxs-lookup"><span data-stu-id="a73ec-134">31</span></span>|<span data-ttu-id="a73ec-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="a73ec-135">&H0000001F</span></span>|  
|<span data-ttu-id="a73ec-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="a73ec-136">`Long`, `ULong`</span></span>|<span data-ttu-id="a73ec-137">63</span><span class="sxs-lookup"><span data-stu-id="a73ec-137">63</span></span>|<span data-ttu-id="a73ec-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="a73ec-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="a73ec-139">Se `amount` for zero, o valor de `result` será idêntico ao valor de `pattern`.</span><span class="sxs-lookup"><span data-stu-id="a73ec-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="a73ec-140">Se `amount` for negativo, ele será usado como um valor não assinado e mascarado com a máscara de tamanho apropriada.</span><span class="sxs-lookup"><span data-stu-id="a73ec-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="a73ec-141">As turnos aritméticos nunca geram exceções de estouro.</span><span class="sxs-lookup"><span data-stu-id="a73ec-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a73ec-142">O operador `<<` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a73ec-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a73ec-143">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de que você entendeu seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="a73ec-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="a73ec-144">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a73ec-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73ec-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a73ec-145">Example</span></span>  
 <span data-ttu-id="a73ec-146">O exemplo a seguir usa o operador `<<` para executar deslocamentos à esquerda aritméticos em valores integrais.</span><span class="sxs-lookup"><span data-stu-id="a73ec-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="a73ec-147">O resultado sempre tem o mesmo tipo de dados que a expressão que está sendo deslocada.</span><span class="sxs-lookup"><span data-stu-id="a73ec-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a73ec-148">Os resultados do exemplo anterior são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="a73ec-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="a73ec-149">`result1` é 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="a73ec-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="a73ec-150">`result2` é 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="a73ec-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="a73ec-151">`result3` é-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="a73ec-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="a73ec-152">`result4` é 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="a73ec-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="a73ec-153">`result5` é 0 (deslocada 15 locais para a esquerda).</span><span class="sxs-lookup"><span data-stu-id="a73ec-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="a73ec-154">O valor de deslocamento para `result4` é calculado como 17 e 15, que é igual a 1.</span><span class="sxs-lookup"><span data-stu-id="a73ec-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73ec-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a73ec-155">See also</span></span>

- [<span data-ttu-id="a73ec-156">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="a73ec-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="a73ec-157">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="a73ec-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="a73ec-158">Operador <<=</span><span class="sxs-lookup"><span data-stu-id="a73ec-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="a73ec-159">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a73ec-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a73ec-160">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="a73ec-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a73ec-161">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a73ec-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
