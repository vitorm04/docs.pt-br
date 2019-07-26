---
title: Tipo de dados decimal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: bab5a0bd7e0a85d550362bc3c1166566f6dcb81b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512781"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="70e66-102">Tipo de dados decimal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70e66-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="70e66-103">Contém valores de 128 bits (16 bytes) assinados que representam os números de inteiro de 96 bits (12 bytes) dimensionados por uma potência variável de 10.</span><span class="sxs-lookup"><span data-stu-id="70e66-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="70e66-104">O fator de dimensionamento especifica o número de dígitos à direita do ponto decimal; Ele varia de 0 a 28.</span><span class="sxs-lookup"><span data-stu-id="70e66-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="70e66-105">Com uma escala de 0 (sem casas decimais), o maior valor possível é +/-79228162514264337593543950335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="70e66-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="70e66-106">Com 28 casas decimais, o maior valor é +/-7.9228162514264337593543950335 e o menor valor diferente de zero é +/-0, 1 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="70e66-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="70e66-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="70e66-107">Remarks</span></span>

<span data-ttu-id="70e66-108">O `Decimal` tipo de dados fornece o maior número de dígitos significativos para um número.</span><span class="sxs-lookup"><span data-stu-id="70e66-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="70e66-109">Ele dá suporte a até 29 dígitos significativos e pode representar valores acima de 7,9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="70e66-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="70e66-110">Ele é particularmente adequado para cálculos, como financeiro, que exigem um grande número de dígitos, mas não podem tolerar erros de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="70e66-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="70e66-111">O valor padrão de `Decimal` é 0.</span><span class="sxs-lookup"><span data-stu-id="70e66-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="70e66-112">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="70e66-112">Programming Tips</span></span>

- <span data-ttu-id="70e66-113">**Preciso.**</span><span class="sxs-lookup"><span data-stu-id="70e66-113">**Precision.**</span></span> <span data-ttu-id="70e66-114">`Decimal`Não é um tipo de dados de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="70e66-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="70e66-115">A `Decimal` estrutura contém um valor inteiro binário, junto com um bit de sinal e um fator de dimensionamento inteiro que especifica qual parte do valor é uma fração decimal.</span><span class="sxs-lookup"><span data-stu-id="70e66-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="70e66-116">Por isso, `Decimal` os números têm uma representação mais precisa na memória do que os tipos de ponto flutuante `Double`(`Single` e).</span><span class="sxs-lookup"><span data-stu-id="70e66-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="70e66-117">**Desempenho.**</span><span class="sxs-lookup"><span data-stu-id="70e66-117">**Performance.**</span></span> <span data-ttu-id="70e66-118">O `Decimal` tipo de dados é o mais lento de todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="70e66-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="70e66-119">Você deve avaliar a importância da precisão em relação ao desempenho antes de escolher um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="70e66-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="70e66-120">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="70e66-120">**Widening.**</span></span> <span data-ttu-id="70e66-121">O `Decimal` tipo de dados amplia para `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="70e66-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="70e66-122">Isso significa que você pode `Decimal` converter para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="70e66-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="70e66-123">**Zeros à direita.**</span><span class="sxs-lookup"><span data-stu-id="70e66-123">**Trailing Zeros.**</span></span> <span data-ttu-id="70e66-124">Visual Basic não armazena zeros à direita em um `Decimal` literal.</span><span class="sxs-lookup"><span data-stu-id="70e66-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="70e66-125">No entanto `Decimal` , uma variável preserva os zeros à direita adquiridos de computação.</span><span class="sxs-lookup"><span data-stu-id="70e66-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="70e66-126">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="70e66-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="70e66-127">A saída do `MsgBox` no exemplo anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="70e66-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="70e66-128">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="70e66-128">**Type Characters.**</span></span> <span data-ttu-id="70e66-129">Acrescentar o caractere de tipo literal `D` a um literal o força ao tipo de dados `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="70e66-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="70e66-130">Acrescentar o caractere de tipo identificador `@` a qualquer identificador o força ao tipo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="70e66-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="70e66-131">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="70e66-131">**Framework Type.**</span></span> <span data-ttu-id="70e66-132">O tipo correspondente no .NET Framework é a estrutura <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70e66-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="70e66-133">Intervalo</span><span class="sxs-lookup"><span data-stu-id="70e66-133">Range</span></span>
 <span data-ttu-id="70e66-134">Talvez seja necessário usar o caractere `D` de tipo para atribuir um valor grande a uma `Decimal` variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="70e66-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="70e66-135">Esse requisito é porque o compilador interpreta um literal como `Long` a menos que um caractere de tipo literal siga o literal, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="70e66-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="70e66-136">A declaração para `bigDec1` não produz um estouro porque o valor atribuído a ele está dentro do intervalo de. `Long`</span><span class="sxs-lookup"><span data-stu-id="70e66-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="70e66-137">O `Long` valor pode ser atribuído `Decimal` à variável.</span><span class="sxs-lookup"><span data-stu-id="70e66-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="70e66-138">A declaração para `bigDec2` gera um erro de estouro porque o valor atribuído a ele é muito grande para. `Long`</span><span class="sxs-lookup"><span data-stu-id="70e66-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="70e66-139">Como o literal numérico não pode ser interpretado `Long`primeiro como um, ele não pode `Decimal` ser atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="70e66-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="70e66-140">Para `bigDec3`, o caractere `D` de tipo literal resolve o problema forçando o compilador a interpretar o literal como um `Decimal` , em vez de `Long`como um.</span><span class="sxs-lookup"><span data-stu-id="70e66-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="70e66-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70e66-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="70e66-142">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70e66-142">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="70e66-143">Tipo de Dados Simples</span><span class="sxs-lookup"><span data-stu-id="70e66-143">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="70e66-144">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="70e66-144">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="70e66-145">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="70e66-145">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="70e66-146">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="70e66-146">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="70e66-147">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70e66-147">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
