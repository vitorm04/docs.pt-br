---
title: Funções de conversão do tipo (Visual Basic)
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
ms.openlocfilehash: 56dad921b2900061dbe2db0d8f1faaf759641f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148129"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="3be69-102">Funções de conversão do tipo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3be69-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="3be69-103">Essas funções são compilado embutido, o que significa que o código de conversão faz parte do código que avalia a expressão.</span><span class="sxs-lookup"><span data-stu-id="3be69-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="3be69-104">Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="3be69-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="3be69-105">Cada função impõe uma expressão para um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="3be69-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be69-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3be69-106">Syntax</span></span>  
  
```  
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
  
## <a name="part"></a><span data-ttu-id="3be69-107">Parte</span><span class="sxs-lookup"><span data-stu-id="3be69-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="3be69-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3be69-108">Required.</span></span> <span data-ttu-id="3be69-109">Qualquer expressão do tipo de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="3be69-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="3be69-110">Tipo de dados do valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3be69-110">Return Value Data Type</span></span>  
 <span data-ttu-id="3be69-111">O nome da função determina o tipo de dados do valor retornado por ele, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3be69-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="3be69-112">Nome da função</span><span class="sxs-lookup"><span data-stu-id="3be69-112">Function name</span></span>|<span data-ttu-id="3be69-113">Tipo de dados de retorno</span><span class="sxs-lookup"><span data-stu-id="3be69-113">Return data type</span></span>|<span data-ttu-id="3be69-114">Intervalo para `expression` argumento</span><span class="sxs-lookup"><span data-stu-id="3be69-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="3be69-115">Tipo de dados booliano</span><span class="sxs-lookup"><span data-stu-id="3be69-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="3be69-116">Qualquer `Char` ou `String` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="3be69-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="3be69-117">Tipo de dados Byte</span><span class="sxs-lookup"><span data-stu-id="3be69-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-118">(0) por meio <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-118">(0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-119">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de bytes com o `CByte` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-120">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="3be69-121">Tipo de dados Char</span><span class="sxs-lookup"><span data-stu-id="3be69-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="3be69-122">Qualquer `Char` ou `String` expressão; apenas primeiro caractere de um `String` é convertido; valor pode ser de 0 a 65535 (não assinado).</span><span class="sxs-lookup"><span data-stu-id="3be69-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="3be69-123">Tipo de dados Data</span><span class="sxs-lookup"><span data-stu-id="3be69-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="3be69-124">Qualquer representação válida de uma data e hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="3be69-125">Tipo de dados double</span><span class="sxs-lookup"><span data-stu-id="3be69-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="3be69-126">-1, 79769313486231570E + 308 a - 4.94065645841246544-324 para valores negativos; 4.94065645841246544-324 1.79769313486231570 + 308 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="3be69-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="3be69-127">Tipo de dados decimal</span><span class="sxs-lookup"><span data-stu-id="3be69-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="3be69-128">+ /-79.228.162.514.264.337.593.543.950.335 para números de escala de zero, ou seja, os números sem casas decimais.</span><span class="sxs-lookup"><span data-stu-id="3be69-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="3be69-129">Para números com 28 casas decimais, o intervalo é + /-7,9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="3be69-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="3be69-130">O menor número possível de diferente de zero é 0,0000000000000000000000000001 (+ /-1E-28).</span><span class="sxs-lookup"><span data-stu-id="3be69-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="3be69-131">Tipo de dados inteiro</span><span class="sxs-lookup"><span data-stu-id="3be69-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-132">(-2.147.483.648) por meio <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-132">(-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="3be69-133">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de número inteiro com o `CInt` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-134">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="3be69-135">Tipo de dados Long</span><span class="sxs-lookup"><span data-stu-id="3be69-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-136">(-9.223.372.036.854.775.808) por meio <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-136">(-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-137">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro de 64 bits com o `CLng` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-138">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="3be69-139">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="3be69-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="3be69-140">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="3be69-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="3be69-141">Tipo de dados SByte</span><span class="sxs-lookup"><span data-stu-id="3be69-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-142">(de -128) por meio <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-142">(-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-143">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de byte assinado com o `CSByte` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-144">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="3be69-145">Tipo de dados curto</span><span class="sxs-lookup"><span data-stu-id="3be69-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-146">(-32.768) por meio <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-146">(-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-147">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro de 16 bits com o `CShort` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-148">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="3be69-149">Tipo de dados único</span><span class="sxs-lookup"><span data-stu-id="3be69-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="3be69-150">-3,402823e+38 - 1,401298E-45 para valores negativos; 1,401298E-45 a 3,402823e+38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="3be69-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="3be69-151">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3be69-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="3be69-152">Retorna para `CStr` dependem do `expression` argumento.</span><span class="sxs-lookup"><span data-stu-id="3be69-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="3be69-153">Ver [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="3be69-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="3be69-154">Tipo de dados UInteger</span><span class="sxs-lookup"><span data-stu-id="3be69-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-155">(0) por meio <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-155">(0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-156">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro sem sinal com o `CUInt` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-157">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="3be69-158">Tipo de dados ULong</span><span class="sxs-lookup"><span data-stu-id="3be69-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-159">(0) por meio <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18.446.744.073.709.551.615) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-159">(0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-160">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro longo sem sinal com o `CULng` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-161">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="3be69-162">Tipo de dados UShort</span><span class="sxs-lookup"><span data-stu-id="3be69-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> <span data-ttu-id="3be69-163">(0) por meio <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="3be69-163">(0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="3be69-164">Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro sem sinal de 16 bits com o `CUShort` função; consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="3be69-165">Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3be69-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="3be69-166"><sup>1</sup> partes fracionárias podem estar sujeitos a um tipo especial de chamado de arredondamento *arredondamento bancário*.</span><span class="sxs-lookup"><span data-stu-id="3be69-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="3be69-167">Consulte "Comentários" para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3be69-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3be69-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="3be69-168">Remarks</span></span>  
 <span data-ttu-id="3be69-169">Como regra, você deve usar as funções de conversão de tipo de Visual Basic em preferência as métodos do .NET Framework, como `ToString()`, seja no <xref:System.Convert> classe ou em uma classe ou estrutura de tipo individual.</span><span class="sxs-lookup"><span data-stu-id="3be69-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="3be69-170">Funções do Visual Basic são projetadas para interação ideal com o código do Visual Basic, e elas também tornam o código-fonte mais curto e fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="3be69-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="3be69-171">Além disso, os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as funções do Visual Basic, por exemplo, ao converter `Boolean` para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3be69-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="3be69-172">Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3be69-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  

<span data-ttu-id="3be69-173">Começando com o Visual Basic 15,8, o desempenho da conversão flutuante-ponto para inteiro é otimizado quando você passa o <xref:System.Single> ou <xref:System.Double> valor retornado por métodos a seguir com uma das funções de conversão de número inteiro (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="3be69-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="3be69-174">Essa otimização permite que o código que faz um grande número de conversões de inteiro para ser executado até duas vezes mais rápido.</span><span class="sxs-lookup"><span data-stu-id="3be69-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="3be69-175">O exemplo a seguir ilustra essas conversões flutuante-ponto-a-inteiro otimizadas:</span><span class="sxs-lookup"><span data-stu-id="3be69-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="3be69-176">Comportamento</span><span class="sxs-lookup"><span data-stu-id="3be69-176">Behavior</span></span>  
  
-   **<span data-ttu-id="3be69-177">Coerção.</span><span class="sxs-lookup"><span data-stu-id="3be69-177">Coercion.</span></span>** <span data-ttu-id="3be69-178">Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um determinado tipo de dados em vez de um tipo de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="3be69-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="3be69-179">Por exemplo, use `CDec` para forçar a aritmética decimal em casos onde precisão simples, precisão dupla ou aritmética de inteiros normalmente aconteceria.</span><span class="sxs-lookup"><span data-stu-id="3be69-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   **<span data-ttu-id="3be69-180">Conversões com falha.</span><span class="sxs-lookup"><span data-stu-id="3be69-180">Failed Conversions.</span></span>** <span data-ttu-id="3be69-181">Se o `expression` passado para a função está fora do intervalo do tipo de dados para o qual ele deve ser convertido, um <xref:System.OverflowException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="3be69-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   **<span data-ttu-id="3be69-182">Partes fracionárias.</span><span class="sxs-lookup"><span data-stu-id="3be69-182">Fractional Parts.</span></span>** <span data-ttu-id="3be69-183">Quando você converter um valor não integral para integral tipo, as funções de conversão de número inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, e `CUShort`) remover o fracionários parte e arredondar o valor para o inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="3be69-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="3be69-184">Se a parte fracionária é exatamente 0,5, as funções de conversão de número inteiro de ida e volta para o inteiro par mais próximo.</span><span class="sxs-lookup"><span data-stu-id="3be69-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="3be69-185">Por exemplo, 0,5 é arredondado para 0 e 1.5 e 2.5 que sejam arredondados para 2.</span><span class="sxs-lookup"><span data-stu-id="3be69-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="3be69-186">Isso às vezes é chamado *arredondamento bancário*, e sua finalidade é compensar uma tendência que poderia criar acúmulos ao somar muitos esses números.</span><span class="sxs-lookup"><span data-stu-id="3be69-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     `CInt` <span data-ttu-id="3be69-187">e `CLng` difere de <xref:Microsoft.VisualBasic.Conversion.Int%2A> e <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funções, que truncam, ao invés de ida e volta, a parte fracionária de um número.</span><span class="sxs-lookup"><span data-stu-id="3be69-187">and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="3be69-188">Além disso, `Fix` e `Int` sempre retornam um valor do mesmo tipo de dados conforme você passa no.</span><span class="sxs-lookup"><span data-stu-id="3be69-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   **<span data-ttu-id="3be69-189">Conversões de data/hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-189">Date/Time Conversions.</span></span>** <span data-ttu-id="3be69-190">Use o <xref:Microsoft.VisualBasic.Information.IsDate%2A> função para determinar se um valor pode ser convertido em uma data e hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> `CDate` <span data-ttu-id="3be69-191">reconhece os literais de data e hora literais, mas valores não numéricos.</span><span class="sxs-lookup"><span data-stu-id="3be69-191">recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="3be69-192">Para converter um Visual Basic 6.0 `Date` de valor para um `Date` valor no Visual Basic 2005 ou versões posteriores, você pode usar o <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="3be69-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   **<span data-ttu-id="3be69-193">Neutro valores de data/hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-193">Neutral Date/Time Values.</span></span>** <span data-ttu-id="3be69-194">O [tipo de dados Date](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="3be69-195">Para fins de conversão de tipo, o Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) ser um valor neutro para a hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="3be69-196">Se você converter um `Date` valor em uma cadeia de caracteres `CStr` não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="3be69-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="3be69-197">Por exemplo, se você converter `#January 1, 0001 9:30:00#` como uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="3be69-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="3be69-198">No entanto, as informações de data ainda estão presentes no original `Date` de valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> função.</span><span class="sxs-lookup"><span data-stu-id="3be69-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   **<span data-ttu-id="3be69-199">Diferenciação de cultura.</span><span class="sxs-lookup"><span data-stu-id="3be69-199">Culture Sensitivity.</span></span>** <span data-ttu-id="3be69-200">As funções de conversão de tipo envolvendo cadeias de caracteres executam conversões com base nas configurações de cultura atual para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3be69-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="3be69-201">Por exemplo, `CDate` reconhece os formatos de data de acordo com a configuração de localidade do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="3be69-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="3be69-202">Você deve fornecer o dia, mês e ano na ordem correta para sua localidade ou a data não pode ser interpretada corretamente.</span><span class="sxs-lookup"><span data-stu-id="3be69-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="3be69-203">Um formato de data por extenso não é reconhecido se ele contiver uma cadeia de caracteres de dia da semana, como "Quarta-feira".</span><span class="sxs-lookup"><span data-stu-id="3be69-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="3be69-204">Se você precisar converter de ou para uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado pela sua localidade, será possível usar as funções de conversão de tipo de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3be69-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="3be69-205">Para fazer isso, use o `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` métodos de tipo desse valor.</span><span class="sxs-lookup"><span data-stu-id="3be69-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="3be69-206">Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> ao converter uma cadeia de caracteres para um `Double`e use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3be69-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="3be69-207">Função CType</span><span class="sxs-lookup"><span data-stu-id="3be69-207">CType Function</span></span>  
 <span data-ttu-id="3be69-208">O [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) leva um segundo argumento, `typename`e impõe `expression` para `typename`, onde `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual existe uma conversão válida.</span><span class="sxs-lookup"><span data-stu-id="3be69-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="3be69-209">Para obter uma comparação `CType` com o outro tipo conversão palavras-chave, consulte [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3be69-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="3be69-210">Exemplo de CBool</span><span class="sxs-lookup"><span data-stu-id="3be69-210">CBool Example</span></span>  
 <span data-ttu-id="3be69-211">O exemplo a seguir usa o `CBool` função para converter expressões para `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="3be69-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="3be69-212">Se uma expressão é avaliada como um valor diferente de zero, `CBool` retorna `True`; caso contrário, ele retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="3be69-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="3be69-213">Exemplo de CByte</span><span class="sxs-lookup"><span data-stu-id="3be69-213">CByte Example</span></span>  
 <span data-ttu-id="3be69-214">O exemplo a seguir usa o `CByte` função para converter uma expressão para um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="3be69-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a><span data-ttu-id="3be69-215">Exemplo de CChar</span><span class="sxs-lookup"><span data-stu-id="3be69-215">CChar Example</span></span>  
 <span data-ttu-id="3be69-216">O exemplo a seguir usa o `CChar` função para converter o primeiro caractere de um `String` expressão para um `Char` tipo.</span><span class="sxs-lookup"><span data-stu-id="3be69-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 <span data-ttu-id="3be69-217">O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`.</span><span class="sxs-lookup"><span data-stu-id="3be69-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="3be69-218">Não é possível usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar o tipo de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="3be69-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="3be69-219">O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte em caractere correspondente.</span><span class="sxs-lookup"><span data-stu-id="3be69-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="3be69-220">Ele usa o <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> função para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`, e `ChrW` converter o número para o tipo `Char`.</span><span class="sxs-lookup"><span data-stu-id="3be69-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a><span data-ttu-id="3be69-221">Exemplo de CDate</span><span class="sxs-lookup"><span data-stu-id="3be69-221">CDate Example</span></span>  
 <span data-ttu-id="3be69-222">O exemplo a seguir usa o `CDate` função para converter cadeias de caracteres para `Date` valores.</span><span class="sxs-lookup"><span data-stu-id="3be69-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="3be69-223">Em geral, embutir datas e horas como cadeias de caracteres (como mostrado neste exemplo) não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="3be69-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="3be69-224">Use literais de data e hora literais, como #Feb 12, 1969 # e # 4:45:23 PM #, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3be69-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="3be69-225">Exemplo de CDbl</span><span class="sxs-lookup"><span data-stu-id="3be69-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a><span data-ttu-id="3be69-226">Exemplo de CDec</span><span class="sxs-lookup"><span data-stu-id="3be69-226">CDec Example</span></span>  
 <span data-ttu-id="3be69-227">O exemplo a seguir usa o `CDec` função para converter um valor numérico para `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="3be69-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a><span data-ttu-id="3be69-228">Exemplo de CInt</span><span class="sxs-lookup"><span data-stu-id="3be69-228">CInt Example</span></span>  
 <span data-ttu-id="3be69-229">O exemplo a seguir usa o `CInt` função para converter um valor de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3be69-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a><span data-ttu-id="3be69-230">Exemplo de CLng</span><span class="sxs-lookup"><span data-stu-id="3be69-230">CLng Example</span></span>
 <span data-ttu-id="3be69-231">O exemplo a seguir usa o `CLng` função para converter valores para `Long`.</span><span class="sxs-lookup"><span data-stu-id="3be69-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a><span data-ttu-id="3be69-232">Exemplo de CObj</span><span class="sxs-lookup"><span data-stu-id="3be69-232">CObj Example</span></span>  
 <span data-ttu-id="3be69-233">O exemplo a seguir usa o `CObj` função para converter um valor numérico para `Object`.</span><span class="sxs-lookup"><span data-stu-id="3be69-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="3be69-234">O `Object` própria variável contém apenas um ponteiro de quatro bytes, que aponta para o `Double` valor atribuído a ele.</span><span class="sxs-lookup"><span data-stu-id="3be69-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="3be69-235">Exemplo de CSByte</span><span class="sxs-lookup"><span data-stu-id="3be69-235">CSByte Example</span></span>  
 <span data-ttu-id="3be69-236">O exemplo a seguir usa o `CSByte` função para converter um valor numérico para `SByte`.</span><span class="sxs-lookup"><span data-stu-id="3be69-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a><span data-ttu-id="3be69-237">Exemplo de CShort</span><span class="sxs-lookup"><span data-stu-id="3be69-237">CShort Example</span></span>  
 <span data-ttu-id="3be69-238">O exemplo a seguir usa o `CShort` função para converter um valor numérico para `Short`.</span><span class="sxs-lookup"><span data-stu-id="3be69-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a><span data-ttu-id="3be69-239">Exemplo de CSng</span><span class="sxs-lookup"><span data-stu-id="3be69-239">CSng Example</span></span>  
 <span data-ttu-id="3be69-240">O exemplo a seguir usa o `CSng` função para converter valores para `Single`.</span><span class="sxs-lookup"><span data-stu-id="3be69-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a><span data-ttu-id="3be69-241">Exemplo de CStr</span><span class="sxs-lookup"><span data-stu-id="3be69-241">CStr Example</span></span>  
 <span data-ttu-id="3be69-242">O exemplo a seguir usa o `CStr` função para converter um valor numérico para `String`.</span><span class="sxs-lookup"><span data-stu-id="3be69-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 <span data-ttu-id="3be69-243">O exemplo a seguir usa o `CStr` função para converter `Date` valores `String` valores.</span><span class="sxs-lookup"><span data-stu-id="3be69-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` <span data-ttu-id="3be69-244">sempre renderiza um `Date` valor no formato padrão curto para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="3be69-244">always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="3be69-245">No entanto, `CStr` suprime a *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.</span><span class="sxs-lookup"><span data-stu-id="3be69-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="3be69-246">Para obter mais detalhes sobre os valores retornados pelo `CStr`, consulte [retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="3be69-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="3be69-247">Exemplo de CUInt</span><span class="sxs-lookup"><span data-stu-id="3be69-247">CUInt Example</span></span>  
 <span data-ttu-id="3be69-248">O exemplo a seguir usa o `CUInt` função para converter um valor numérico para `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="3be69-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a><span data-ttu-id="3be69-249">Exemplo de CULng</span><span class="sxs-lookup"><span data-stu-id="3be69-249">CULng Example</span></span>  
 <span data-ttu-id="3be69-250">O exemplo a seguir usa o `CULng` função para converter um valor numérico para `ULong`.</span><span class="sxs-lookup"><span data-stu-id="3be69-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a><span data-ttu-id="3be69-251">Exemplo de CUShort</span><span class="sxs-lookup"><span data-stu-id="3be69-251">CUShort Example</span></span>  
 <span data-ttu-id="3be69-252">O exemplo a seguir usa o `CUShort` função para converter um valor numérico para `UShort`.</span><span class="sxs-lookup"><span data-stu-id="3be69-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="3be69-253">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3be69-253">See also</span></span>

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
- [<span data-ttu-id="3be69-254">Funções de conversão</span><span class="sxs-lookup"><span data-stu-id="3be69-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="3be69-255">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3be69-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
