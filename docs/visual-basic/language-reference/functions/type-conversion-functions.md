---
title: Funções de conversão do tipo
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 3924da6ccbfea00668370f2fbcf4baf289be80db
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349963"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="6fe50-102">Funções de conversão do tipo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fe50-102">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="6fe50-103">Essas funções são compiladas em linha, o que significa que o código de conversão faz parte do código que avalia a expressão.</span><span class="sxs-lookup"><span data-stu-id="6fe50-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="6fe50-104">Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6fe50-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="6fe50-105">Cada função impõe uma expressão para um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="6fe50-105">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fe50-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fe50-106">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="6fe50-107">Parte</span><span class="sxs-lookup"><span data-stu-id="6fe50-107">Part</span></span>

`expression`  
<span data-ttu-id="6fe50-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6fe50-108">Required.</span></span> <span data-ttu-id="6fe50-109">Qualquer expressão do tipo de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="6fe50-109">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="6fe50-110">Tipo de dados de valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6fe50-110">Return Value Data Type</span></span>

<span data-ttu-id="6fe50-111">O nome da função determina o tipo de dados do valor que ele retorna, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6fe50-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="6fe50-112">Nome da função</span><span class="sxs-lookup"><span data-stu-id="6fe50-112">Function name</span></span>|<span data-ttu-id="6fe50-113">Tipo de dados de retorno</span><span class="sxs-lookup"><span data-stu-id="6fe50-113">Return data type</span></span>|<span data-ttu-id="6fe50-114">Intervalo para `expression` argumento</span><span class="sxs-lookup"><span data-stu-id="6fe50-114">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="6fe50-115">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="6fe50-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="6fe50-116">Qualquer `Char` ou expressão numérica ou `String` válida.</span><span class="sxs-lookup"><span data-stu-id="6fe50-116">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="6fe50-117">Tipo de Dados Byte</span><span class="sxs-lookup"><span data-stu-id="6fe50-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="6fe50-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-119">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho da conversão de ponto flutuante para byte com a função `CByte`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-120">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-120">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="6fe50-121">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="6fe50-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="6fe50-122">Qualquer expressão de `Char` ou `String` válida; somente o primeiro caractere de um `String` é convertido; o valor pode ser de 0 a 65535 (não assinado).</span><span class="sxs-lookup"><span data-stu-id="6fe50-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="6fe50-123">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="6fe50-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="6fe50-124">Qualquer representação válida de uma data e hora.</span><span class="sxs-lookup"><span data-stu-id="6fe50-124">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="6fe50-125">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="6fe50-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="6fe50-126">-1.79769313486231570 e + 308 a-4.94065645841246544 E-324 para valores negativos; 4.94065645841246544 e-324 a 1.79769313486231570 E + 308 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="6fe50-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="6fe50-127">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="6fe50-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="6fe50-128">+/-79228162514264337593543950335 para números com escala zero, ou seja, números sem casas decimais.</span><span class="sxs-lookup"><span data-stu-id="6fe50-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="6fe50-129">Para números com 28 casas decimais, o intervalo é +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="6fe50-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="6fe50-130">O menor número não zero possível é 0, 1 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="6fe50-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="6fe50-131">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="6fe50-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="6fe50-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) por meio de <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="6fe50-133">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho da conversão de ponto flutuante para inteiro com a função `CInt`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-134">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-134">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="6fe50-135">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="6fe50-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="6fe50-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9.223.372.036.854.775.808) por meio de <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-137">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiros de 64 bits com a função `CLng`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-138">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-138">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="6fe50-139">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="6fe50-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="6fe50-140">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="6fe50-140">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="6fe50-141">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="6fe50-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="6fe50-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) por meio de <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-143">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de bytes assinados com a função `CSByte`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-144">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-144">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="6fe50-145">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="6fe50-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="6fe50-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) por meio de <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-147">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiros de 16 bits com a função `CShort`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-148">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-148">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="6fe50-149">Tipo de Dados Simples</span><span class="sxs-lookup"><span data-stu-id="6fe50-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="6fe50-150">-3.402823 e + 38 a-1.401298 E-45 para valores negativos; 1.401298 e-45 a 3.402823 E + 38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="6fe50-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="6fe50-151">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="6fe50-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="6fe50-152">Retorna para `CStr` dependem do argumento `expression`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="6fe50-153">Confira [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="6fe50-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="6fe50-154">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="6fe50-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="6fe50-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-156">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de inteiros sem sinal com a função `CUInt`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-157">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-157">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="6fe50-158">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="6fe50-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="6fe50-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) a <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-160">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro longo sem sinal com a função `CULng`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-161">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-161">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="6fe50-162">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="6fe50-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="6fe50-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6fe50-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="6fe50-164">A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de inteiros de 16 bits sem sinal com a função `CUShort`; consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="6fe50-165">Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-165">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="6fe50-166"><sup>1</sup> partes fracionárias podem estar sujeitas a um tipo especial de arredondamento chamado de *arredondamento do Banker*.</span><span class="sxs-lookup"><span data-stu-id="6fe50-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="6fe50-167">Consulte "Comentários" para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fe50-167">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fe50-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fe50-168">Remarks</span></span>

<span data-ttu-id="6fe50-169">Como regra, você deve usar as funções de conversão de tipo Visual Basic em preferência aos métodos .NET Framework como `ToString()`, seja na classe <xref:System.Convert> ou em uma estrutura ou classe de tipo individual.</span><span class="sxs-lookup"><span data-stu-id="6fe50-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="6fe50-170">As funções de Visual Basic são projetadas para uma interação ideal com código de Visual Basic e também tornam seu código-fonte mais curto e mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="6fe50-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="6fe50-171">Além disso, os métodos de conversão de .NET Framework nem sempre produzem os mesmos resultados que as funções de Visual Basic, por exemplo, ao converter `Boolean` em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="6fe50-172">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="6fe50-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="6fe50-173">A partir do Visual Basic 15,8, o desempenho da conversão de ponto-a-inteiro flutuante é otimizado quando você passa o <xref:System.Single> ou <xref:System.Double> valor retornado pelos métodos a seguir para uma das funções de conversão de inteiro (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="6fe50-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="6fe50-174">Essa otimização permite que um código que faz um grande número de conversões de inteiros seja executado até duas vezes mais rápido.</span><span class="sxs-lookup"><span data-stu-id="6fe50-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="6fe50-175">O exemplo a seguir ilustra essas conversões otimizadas de ponto flutuante para inteiro:</span><span class="sxs-lookup"><span data-stu-id="6fe50-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="6fe50-176">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6fe50-176">Behavior</span></span>

- <span data-ttu-id="6fe50-177">**Coerção.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-177">**Coercion.**</span></span> <span data-ttu-id="6fe50-178">Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um tipo de dados específico em vez do tipo de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="6fe50-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="6fe50-179">Por exemplo, use `CDec` para forçar aritmética decimal nos casos em que a precisão única, a precisão dupla ou a aritmética de inteiro normalmente ocorreria.</span><span class="sxs-lookup"><span data-stu-id="6fe50-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="6fe50-180">**Conversões com falha.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-180">**Failed Conversions.**</span></span> <span data-ttu-id="6fe50-181">Se o `expression` passado para a função estiver fora do intervalo do tipo de dados para o qual será convertido, ocorrerá uma <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="6fe50-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="6fe50-182">**Partes fracionárias.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-182">**Fractional Parts.**</span></span> <span data-ttu-id="6fe50-183">Quando você converte um valor não integral em um tipo integral, as funções de conversão de inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`e `CUShort`) removem a parte fracionária e arredondam o valor para o número inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="6fe50-184">Se a parte fracionária for exatamente 0,5, as funções de conversão de inteiros o arredondarão para o inteiro par mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="6fe50-185">Por exemplo, 0,5 arredonda para 0 e 1,5 e 2,5 são arredondados para 2.</span><span class="sxs-lookup"><span data-stu-id="6fe50-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="6fe50-186">Isso às vezes é chamado de *arredondamento do Banker*, e sua finalidade é compensar uma tendência que poderia se acumular ao adicionar muitos desses números juntos.</span><span class="sxs-lookup"><span data-stu-id="6fe50-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="6fe50-187">`CInt` e `CLng` diferem das funções <xref:Microsoft.VisualBasic.Conversion.Int%2A> e <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, que truncam, em vez de arredondar, a parte fracionária de um número.</span><span class="sxs-lookup"><span data-stu-id="6fe50-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="6fe50-188">Além disso, `Fix` e `Int` sempre retornam um valor do mesmo tipo de dados que você passa.</span><span class="sxs-lookup"><span data-stu-id="6fe50-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="6fe50-189">**Conversões de data/hora.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="6fe50-190">Use a função <xref:Microsoft.VisualBasic.Information.IsDate%2A> para determinar se um valor pode ser convertido em uma data e hora.</span><span class="sxs-lookup"><span data-stu-id="6fe50-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="6fe50-191">`CDate` reconhece literais de data e literais de tempo, mas não valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="6fe50-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="6fe50-192">Para converter um valor de `Date` Visual Basic 6,0 em um valor `Date` no Visual Basic 2005 ou em versões posteriores, você pode usar o método <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fe50-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="6fe50-193">**Valores de data/hora neutros.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="6fe50-194">O [tipo de dados Date](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="6fe50-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="6fe50-195">Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1º de Janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) para ser um valor neutro para o tempo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="6fe50-196">Se você converter um valor de `Date` em uma cadeia de caracteres, `CStr` não incluirá valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="6fe50-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="6fe50-197">Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="6fe50-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="6fe50-198">No entanto, as informações de data ainda estão presentes no valor de `Date` original e podem ser recuperadas com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> função.</span><span class="sxs-lookup"><span data-stu-id="6fe50-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="6fe50-199">**Sensibilidade de cultura.**</span><span class="sxs-lookup"><span data-stu-id="6fe50-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="6fe50-200">As funções de conversão de tipo que envolvem cadeias de caracteres executam conversões com base nas configurações de cultura atuais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="6fe50-201">Por exemplo, `CDate` reconhece formatos de data de acordo com a configuração de localidade do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="6fe50-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="6fe50-202">Você deve fornecer o dia, o mês e o ano na ordem correta para sua localidade, ou a data pode não ser interpretada corretamente.</span><span class="sxs-lookup"><span data-stu-id="6fe50-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="6fe50-203">Um formato de data por extenso não será reconhecido se ele contiver uma cadeia de caracteres de dia da semana, como "quarta-feira".</span><span class="sxs-lookup"><span data-stu-id="6fe50-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="6fe50-204">Se você precisar converter de ou para uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado por sua localidade, não será possível usar as funções de conversão de tipo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6fe50-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="6fe50-205">Para fazer isso, use os métodos `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` do tipo desse valor.</span><span class="sxs-lookup"><span data-stu-id="6fe50-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="6fe50-206">Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> ao converter uma cadeia de caracteres em um `Double`e use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6fe50-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="6fe50-207">Função CType</span><span class="sxs-lookup"><span data-stu-id="6fe50-207">CType Function</span></span>

<span data-ttu-id="6fe50-208">A [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) usa um segundo argumento, `typename`e impõe `expression` para `typename`, em que `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual exista uma conversão válida.</span><span class="sxs-lookup"><span data-stu-id="6fe50-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="6fe50-209">Para obter uma comparação de `CType` com as outras palavras-chave de conversão de tipo, consulte operador [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6fe50-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="6fe50-210">Exemplo de CBool</span><span class="sxs-lookup"><span data-stu-id="6fe50-210">CBool Example</span></span>

<span data-ttu-id="6fe50-211">O exemplo a seguir usa a função `CBool` para converter expressões em valores `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="6fe50-212">Se uma expressão for avaliada como um valor diferente de zero, `CBool` retornará `True`; caso contrário, ele retornará `False`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="6fe50-213">Exemplo de CByte</span><span class="sxs-lookup"><span data-stu-id="6fe50-213">CByte Example</span></span>

<span data-ttu-id="6fe50-214">O exemplo a seguir usa a função `CByte` para converter uma expressão em um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="6fe50-215">Exemplo de CChar</span><span class="sxs-lookup"><span data-stu-id="6fe50-215">CChar Example</span></span>

<span data-ttu-id="6fe50-216">O exemplo a seguir usa a função `CChar` para converter o primeiro caractere de uma expressão de `String` para um tipo de `Char`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="6fe50-217">O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="6fe50-218">Você não pode usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar um tipo de dados numérico.</span><span class="sxs-lookup"><span data-stu-id="6fe50-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="6fe50-219">O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte no caractere correspondente.</span><span class="sxs-lookup"><span data-stu-id="6fe50-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="6fe50-220">Ele usa a função <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`e `ChrW` para converter o número em `Char`de tipo.</span><span class="sxs-lookup"><span data-stu-id="6fe50-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="6fe50-221">Exemplo de CDate</span><span class="sxs-lookup"><span data-stu-id="6fe50-221">CDate Example</span></span>

<span data-ttu-id="6fe50-222">O exemplo a seguir usa a função `CDate` para converter cadeias de caracteres em valores `Date`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="6fe50-223">Em geral, as datas e as horas de codificação rígida como cadeias de caracteres (como mostrado neste exemplo) não são recomendadas.</span><span class="sxs-lookup"><span data-stu-id="6fe50-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="6fe50-224">Use literais de data e literais de tempo, como #Feb 12, 1969 # e #4:45:23 PM #, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6fe50-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="6fe50-225">Exemplo de CDbl</span><span class="sxs-lookup"><span data-stu-id="6fe50-225">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="6fe50-226">Exemplo de CDec</span><span class="sxs-lookup"><span data-stu-id="6fe50-226">CDec Example</span></span>

<span data-ttu-id="6fe50-227">O exemplo a seguir usa a função `CDec` para converter um valor numérico em `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="6fe50-228">Exemplo de CInt</span><span class="sxs-lookup"><span data-stu-id="6fe50-228">CInt Example</span></span>

<span data-ttu-id="6fe50-229">O exemplo a seguir usa a função `CInt` para converter um valor em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="6fe50-230">Exemplo de CLng</span><span class="sxs-lookup"><span data-stu-id="6fe50-230">CLng Example</span></span>

<span data-ttu-id="6fe50-231">O exemplo a seguir usa a função `CLng` para converter valores em `Long`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="6fe50-232">Exemplo de CObj</span><span class="sxs-lookup"><span data-stu-id="6fe50-232">CObj Example</span></span>

<span data-ttu-id="6fe50-233">O exemplo a seguir usa a função `CObj` para converter um valor numérico em `Object`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="6fe50-234">A variável `Object` em si contém apenas um ponteiro de quatro bytes, que aponta para o valor `Double` atribuído a ela.</span><span class="sxs-lookup"><span data-stu-id="6fe50-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="6fe50-235">Exemplo de CSByte</span><span class="sxs-lookup"><span data-stu-id="6fe50-235">CSByte Example</span></span>

<span data-ttu-id="6fe50-236">O exemplo a seguir usa a função `CSByte` para converter um valor numérico em `SByte`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="6fe50-237">Exemplo de CShort</span><span class="sxs-lookup"><span data-stu-id="6fe50-237">CShort Example</span></span>

<span data-ttu-id="6fe50-238">O exemplo a seguir usa a função `CShort` para converter um valor numérico em `Short`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="6fe50-239">Exemplo de CSng</span><span class="sxs-lookup"><span data-stu-id="6fe50-239">CSng Example</span></span>

<span data-ttu-id="6fe50-240">O exemplo a seguir usa a função `CSng` para converter valores em `Single`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="6fe50-241">Exemplo de CStr</span><span class="sxs-lookup"><span data-stu-id="6fe50-241">CStr Example</span></span>

<span data-ttu-id="6fe50-242">O exemplo a seguir usa a função `CStr` para converter um valor numérico em `String`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="6fe50-243">O exemplo a seguir usa a função `CStr` para converter valores de `Date` em valores `String`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="6fe50-244">`CStr` sempre renderiza um valor de `Date` no formato curto padrão para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="6fe50-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="6fe50-245">No entanto, `CStr` suprime os *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.</span><span class="sxs-lookup"><span data-stu-id="6fe50-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="6fe50-246">Para obter mais detalhes sobre os valores retornados por `CStr`, consulte [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="6fe50-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="6fe50-247">Exemplo de CUInt</span><span class="sxs-lookup"><span data-stu-id="6fe50-247">CUInt Example</span></span>

<span data-ttu-id="6fe50-248">O exemplo a seguir usa a função `CUInt` para converter um valor numérico em `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="6fe50-249">Exemplo de CULng</span><span class="sxs-lookup"><span data-stu-id="6fe50-249">CULng Example</span></span>

<span data-ttu-id="6fe50-250">O exemplo a seguir usa a função `CULng` para converter um valor numérico em `ULong`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="6fe50-251">Exemplo de CUShort</span><span class="sxs-lookup"><span data-stu-id="6fe50-251">CUShort Example</span></span>

<span data-ttu-id="6fe50-252">O exemplo a seguir usa a função `CUShort` para converter um valor numérico em `UShort`.</span><span class="sxs-lookup"><span data-stu-id="6fe50-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="6fe50-253">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fe50-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="6fe50-254">Funções de Conversão</span><span class="sxs-lookup"><span data-stu-id="6fe50-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="6fe50-255">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fe50-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
