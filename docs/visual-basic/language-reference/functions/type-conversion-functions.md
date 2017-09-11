---
title: "Funções de conversão (Visual Basic) de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
dev_langs:
- VB
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type, converting
- string conversion, conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type, converting
- type conversion, functions for
- Single data type, converting
- numbers, rounding
- rounding numbers, type conversion
- CUShort function
- Long data type, converting
- return values, data types
- single-precision numbers, converting
- data type conversion, functions for
- CStr function
- times, converting
- CSng function
- conversions, type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type, conversion functions
- numbers, converting
- Double data type, converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type, converting
- Boolean data type, converting
- integers, type conversion functions
- dates, converting
- CULng function
- CInt function
- Date data type, converting
- Byte data type, converting
- String data type, converting
- CChar function
- banker's rounding
- Short data type, converting
- rounding numbers, banker's rounding
- type conversion, Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
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
ms.openlocfilehash: 70ffbbaac8e19102a935df5d77ce3632a2c89a09
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="d7d0d-102">Funções de conversão do tipo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7d0d-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="d7d0d-103">Essas funções são compilados em linha, que significa que o código de conversão faz parte do código que avalia a expressão.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="d7d0d-104">Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="d7d0d-105">Cada função impõe uma expressão para um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d0d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7d0d-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="d7d0d-107">Parte</span><span class="sxs-lookup"><span data-stu-id="d7d0d-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="d7d0d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-108">Required.</span></span> <span data-ttu-id="d7d0d-109">Qualquer expressão do tipo de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="d7d0d-110">Tipo de dados do valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d7d0d-110">Return Value Data Type</span></span>  
 <span data-ttu-id="d7d0d-111">O nome da função determina o tipo de dados do valor que ele retorna, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d7d0d-112">Nome da função</span><span class="sxs-lookup"><span data-stu-id="d7d0d-112">Function name</span></span>|<span data-ttu-id="d7d0d-113">Tipo de dados de retorno</span><span class="sxs-lookup"><span data-stu-id="d7d0d-113">Return data type</span></span>|<span data-ttu-id="d7d0d-114">Intervalo para `expression` argumento</span><span class="sxs-lookup"><span data-stu-id="d7d0d-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="d7d0d-115">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="d7d0d-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="d7d0d-116">Qualquer `Char` ou `String` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="d7d0d-117">Tipo de Dados Byte</span><span class="sxs-lookup"><span data-stu-id="d7d0d-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="d7d0d-118">0 a 255 (não assinado); partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="d7d0d-119">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="d7d0d-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="d7d0d-120">Qualquer `Char` ou `String` expressão; apenas primeiro caractere de um `String` é convertido; valor pode ser de 0 a 65535 (não assinado).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="d7d0d-121">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="d7d0d-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="d7d0d-122">Qualquer representação válida de uma data e hora.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="d7d0d-123">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="d7d0d-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="d7d0d-124">-1, 79769313486231570E + 308 até - 4.94065645841246544 e-324 para valores negativos; 4.94065645841246544 e-324 1.79769313486231570 e + 308 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="d7d0d-125">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="d7d0d-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="d7d0d-126">+ /-79.228.162.514.264.337.593.543.950.335 para números com escala de zero, ou seja, números sem casas decimais.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="d7d0d-127">Para números com 28 casas decimais, o intervalo é + /-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="d7d0d-128">O menor número possível diferente de zero é 0,0000000000000000000000000001 (+ /-1E-28).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="d7d0d-129">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="d7d0d-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="d7d0d-130">-2.147.483.648 a 2.147.483.647; partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="d7d0d-131">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="d7d0d-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="d7d0d-132">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807; partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="d7d0d-133">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="d7d0d-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="d7d0d-134">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="d7d0d-135">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="d7d0d-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="d7d0d-136">-128 a 127; partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="d7d0d-137">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="d7d0d-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="d7d0d-138">-32.768 a 32.767; partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="d7d0d-139">Tipo de Dados Simples</span><span class="sxs-lookup"><span data-stu-id="d7d0d-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="d7d0d-140">-3.402823E + 38 a - 1, 401298E-45 para valores negativos; 1, 401298E-45 a 3.402823E + 38 para valores positivos.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="d7d0d-141">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="d7d0d-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="d7d0d-142">Retorna para `CStr` dependem de `expression` argumento.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="d7d0d-143">Consulte [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="d7d0d-144">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="d7d0d-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="d7d0d-145">0 a 4.294.967.295 (não assinado); partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="d7d0d-146">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="d7d0d-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="d7d0d-147">0 e 18.446.744.073.709.551.615 (não assinado); partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="d7d0d-148">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="d7d0d-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="d7d0d-149">0 a 65.535 (não assinado); partes fracionários são arredondados. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d7d0d-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="d7d0d-150"><sup>1</sup> partes fracionárias podem estar sujeitos a um tipo especial de arredondamento chamado *arredondamento bancário*.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="d7d0d-151">Consulte "Comentários" para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d0d-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7d0d-152">Remarks</span></span>  
 <span data-ttu-id="d7d0d-153">Como regra, você deve usar as funções de conversão de tipo do Visual Basic em vez de métodos do .NET Framework como `ToString()`, no <xref:System.Convert>classe ou em uma estrutura de tipo individual ou a classe</xref:System.Convert></span><span class="sxs-lookup"><span data-stu-id="d7d0d-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="d7d0d-154">As funções do Visual Basic são projetadas para interação ideal com código do Visual Basic, e elas também tornam o código-fonte mais curto e fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="d7d0d-155">Além disso, os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as funções do Visual Basic, por exemplo, ao converter `Boolean` para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="d7d0d-156">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d7d0d-157">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d7d0d-157">Behavior</span></span>  
  
-   <span data-ttu-id="d7d0d-158">**Coerção.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-158">**Coercion.**</span></span> <span data-ttu-id="d7d0d-159">Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um determinado tipo de dados em vez de um tipo de dados padrão.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="d7d0d-160">Por exemplo, use `CDec` para forçar aritmética decimal em casos onde precisão simples, precisão dupla ou aritmética de inteiros seria normalmente ocorrem.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="d7d0d-161">**Conversões com falha.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-161">**Failed Conversions.**</span></span> <span data-ttu-id="d7d0d-162">Se o `expression` passado para a função está fora do intervalo do tipo de dados para o qual ele deve ser convertido, um <xref:System.OverflowException>ocorre.</xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="d7d0d-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="d7d0d-163">**Partes fracionárias.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-163">**Fractional Parts.**</span></span> <span data-ttu-id="d7d0d-164">Quando você converter um valor não integral integral tipo, as funções de conversão de inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, e `CUShort`) removem a parte fracionária e arredondar o valor para o inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="d7d0d-165">Se a parte fracionária é exatamente 0,5, as funções de conversão de inteiro de ida e volta para o inteiro par mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="d7d0d-166">Por exemplo, 0,5 é arredondado para 0 e 1.5 e 2.5 que sejam arredondados para 2.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="d7d0d-167">Isso às vezes é chamado *arredondamento bancário*, e sua finalidade é compensar uma tendência que pode se acumular ao somar muitos desses números.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="d7d0d-168">`CInt`e `CLng` difere do <xref:Microsoft.VisualBasic.Conversion.Int%2A>e <xref:Microsoft.VisualBasic.Conversion.Fix%2A>funções, que truncam, ao invés de arredondar, a parte fracionária de um número.</xref:Microsoft.VisualBasic.Conversion.Fix%2A> </xref:Microsoft.VisualBasic.Conversion.Int%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="d7d0d-169">Além disso, `Fix` e `Int` você passar sempre retornam um valor do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="d7d0d-170">**Conversões de data/hora.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="d7d0d-171">Use o <xref:Microsoft.VisualBasic.Information.IsDate%2A>função para determinar se um valor pode ser convertido em uma data e hora.</xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="d7d0d-172">`CDate`reconhece literais de data e hora literais, mas valores não numéricos.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="d7d0d-173">Para converter um Visual Basic 6.0 `Date` valor para um `Date` valor no Visual Basic 2005 ou versões posteriores, você pode usar o <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>método.</xref:System.DateTime.FromOADate%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d7d0d-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> method.</span></span>  
  
-   <span data-ttu-id="d7d0d-174">**Neutralidade de valores de data/hora.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="d7d0d-175">O [tipo de dados data](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="d7d0d-176">Para fins de conversão de tipos, Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como sendo um *valor neutro* para a data e 00:00:00 (meia-noite) como sendo um valor neutro para a hora.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="d7d0d-177">Se você converter um `Date` valor para uma cadeia de caracteres `CStr` não inclui valores neutros na cadeia de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="d7d0d-178">Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="d7d0d-179">No entanto, as informações de data ainda estão presentes no original `Date` valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>função.</xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="d7d0d-180">**Diferenciação de cultura.**</span><span class="sxs-lookup"><span data-stu-id="d7d0d-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="d7d0d-181">As funções de conversão de tipo que envolvem sequências de caracteres executam conversões com base nas configurações de cultura atual do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="d7d0d-182">Por exemplo, `CDate` reconhece formatos de data de acordo com a configuração de localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="d7d0d-183">Você deve fornecer o dia, mês e ano na ordem correta para sua localidade, ou a data não pode ser interpretada corretamente.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="d7d0d-184">Um formato de data por extenso não é reconhecido se ele contém uma cadeia de caracteres de dia da semana, como "Quarta-feira".</span><span class="sxs-lookup"><span data-stu-id="d7d0d-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="d7d0d-185">Se você precisar converter para ou de uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado pela sua localidade, você não pode usar as funções de conversão de tipo do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="d7d0d-186">Para fazer isso, use o `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` métodos de tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="d7d0d-187">Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=fullName>ao converter uma cadeia de caracteres para um `Double`e usar <xref:System.Double.ToString%2A?displayProperty=fullName>ao converter um valor do tipo `Double` para uma cadeia de caracteres.</xref:System.Double.ToString%2A?displayProperty=fullName> </xref:System.Double.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d7d0d-187">For example, use <xref:System.Double.Parse%2A?displayProperty=fullName> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=fullName> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="d7d0d-188">Função CType</span><span class="sxs-lookup"><span data-stu-id="d7d0d-188">CType Function</span></span>  
 <span data-ttu-id="d7d0d-189">O [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) leva um segundo argumento, `typename`e impõe `expression` para `typename`, onde `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual há uma conversão válida.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="d7d0d-190">Para obter uma comparação de `CType` com as outras keywords de conversão de tipo, consulte [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="d7d0d-191">Exemplo de CBool</span><span class="sxs-lookup"><span data-stu-id="d7d0d-191">CBool Example</span></span>  
 <span data-ttu-id="d7d0d-192">O exemplo a seguir usa o `CBool` função converter expressões para `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="d7d0d-193">Se uma expressão é avaliada como um valor diferente de zero, `CBool` retorna `True`; caso contrário, retornará `False`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 <span data-ttu-id="d7d0d-194">[!code-vb[VbVbalrFunctions n º&1;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-194">[!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]</span></span>  
  
## <a name="cbyte-example"></a><span data-ttu-id="d7d0d-195">Exemplo de CByte</span><span class="sxs-lookup"><span data-stu-id="d7d0d-195">CByte Example</span></span>  
 <span data-ttu-id="d7d0d-196">O exemplo a seguir usa o `CByte` função para converter uma expressão para um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-196">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 <span data-ttu-id="d7d0d-197">[!code-vb[VbVbalrFunctions n º&2;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-197">[!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]</span></span>  
  
## <a name="cchar-example"></a><span data-ttu-id="d7d0d-198">Exemplo de CChar</span><span class="sxs-lookup"><span data-stu-id="d7d0d-198">CChar Example</span></span>  
 <span data-ttu-id="d7d0d-199">O exemplo a seguir usa o `CChar` função para converter o primeiro caractere de um `String` expressão para um `Char` tipo.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-199">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 <span data-ttu-id="d7d0d-200">[!code-vb[VbVbalrFunctions n º&3;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-200">[!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]</span></span>  
  
 <span data-ttu-id="d7d0d-201">O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-201">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="d7d0d-202">Não é possível usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar um tipo de dados numérico.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-202">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="d7d0d-203">O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte em caractere correspondente.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-203">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="d7d0d-204">Ele usa o <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>função para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`, e `ChrW` para converter o número para o tipo `Char`.</xref:Microsoft.VisualBasic.Interaction.InputBox%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-204">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 <span data-ttu-id="d7d0d-205">[!code-vb[VbVbalrFunctions n º&4;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-205">[!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]</span></span>  
  
## <a name="cdate-example"></a><span data-ttu-id="d7d0d-206">Exemplo de CDate</span><span class="sxs-lookup"><span data-stu-id="d7d0d-206">CDate Example</span></span>  
 <span data-ttu-id="d7d0d-207">O exemplo a seguir usa o `CDate` função para converter cadeias de caracteres para `Date` valores.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-207">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="d7d0d-208">Em geral, embutir datas e horas como cadeias de caracteres (como mostrado neste exemplo) não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-208">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="d7d0d-209">Usar literais de data e hora, como #Feb 12, &#1969; e # 4:45:23 PM #, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-209">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 <span data-ttu-id="d7d0d-210">[!code-vb[VbVbalrFunctions n º&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-210">[!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]</span></span>  
  
## <a name="cdbl-example"></a><span data-ttu-id="d7d0d-211">Exemplo de CDbl</span><span class="sxs-lookup"><span data-stu-id="d7d0d-211">CDbl Example</span></span>  
 <span data-ttu-id="d7d0d-212">[!code-vb[VbVbalrFunctions n º&6;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-212">[!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]</span></span>  
  
## <a name="cdec-example"></a><span data-ttu-id="d7d0d-213">Exemplo de CDec</span><span class="sxs-lookup"><span data-stu-id="d7d0d-213">CDec Example</span></span>  
 <span data-ttu-id="d7d0d-214">O exemplo a seguir usa o `CDec` função para converter um valor numérico para `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-214">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 <span data-ttu-id="d7d0d-215">[!code-vb[VbVbalrFunctions&#7;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-215">[!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]</span></span>  
  
## <a name="cint-example"></a><span data-ttu-id="d7d0d-216">Exemplo de CInt</span><span class="sxs-lookup"><span data-stu-id="d7d0d-216">CInt Example</span></span>  
 <span data-ttu-id="d7d0d-217">O exemplo a seguir usa o `CInt` função para converter um valor de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-217">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 <span data-ttu-id="d7d0d-218">[!code-vb[VbVbalrFunctions n º&8;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-218">[!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]</span></span>  
  
## <a name="clng-example"></a><span data-ttu-id="d7d0d-219">Exemplo de CLng</span><span class="sxs-lookup"><span data-stu-id="d7d0d-219">CLng Example</span></span>  
 <span data-ttu-id="d7d0d-220">O exemplo a seguir usa o `CLng` função para converter valores para `Long`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-220">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 <span data-ttu-id="d7d0d-221">[!code-vb[VbVbalrFunctions n º&9;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-221">[!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]</span></span>  
  
## <a name="cobj-example"></a><span data-ttu-id="d7d0d-222">Exemplo de CObj</span><span class="sxs-lookup"><span data-stu-id="d7d0d-222">CObj Example</span></span>  
 <span data-ttu-id="d7d0d-223">O exemplo a seguir usa o `CObj` função para converter um valor numérico para `Object`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-223">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="d7d0d-224">O `Object` variável contém apenas um ponteiro de quatro bytes, que aponta para o `Double` valor atribuído a ele.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-224">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 <span data-ttu-id="d7d0d-225">[!code-vb[VbVbalrFunctions n º&10;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-225">[!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]</span></span>  
  
## <a name="csbyte-example"></a><span data-ttu-id="d7d0d-226">Exemplo de CSByte</span><span class="sxs-lookup"><span data-stu-id="d7d0d-226">CSByte Example</span></span>  
 <span data-ttu-id="d7d0d-227">O exemplo a seguir usa o `CSByte` função para converter um valor numérico para `SByte`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-227">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 <span data-ttu-id="d7d0d-228">[!code-vb[VbVbalrFunctions n º&11;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-228">[!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]</span></span>  
  
## <a name="cshort-example"></a><span data-ttu-id="d7d0d-229">Exemplo de CShort</span><span class="sxs-lookup"><span data-stu-id="d7d0d-229">CShort Example</span></span>  
 <span data-ttu-id="d7d0d-230">O exemplo a seguir usa o `CShort` função para converter um valor numérico para `Short`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-230">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 <span data-ttu-id="d7d0d-231">[!code-vb[VbVbalrFunctions&#12;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-231">[!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]</span></span>  
  
## <a name="csng-example"></a><span data-ttu-id="d7d0d-232">Exemplo de CSng</span><span class="sxs-lookup"><span data-stu-id="d7d0d-232">CSng Example</span></span>  
 <span data-ttu-id="d7d0d-233">O exemplo a seguir usa o `CSng` função para converter valores para `Single`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-233">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 <span data-ttu-id="d7d0d-234">[!code-vb[VbVbalrFunctions&13;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-234">[!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]</span></span>  
  
## <a name="cstr-example"></a><span data-ttu-id="d7d0d-235">Exemplo de CStr</span><span class="sxs-lookup"><span data-stu-id="d7d0d-235">CStr Example</span></span>  
 <span data-ttu-id="d7d0d-236">O exemplo a seguir usa o `CStr` função para converter um valor numérico para `String`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-236">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 <span data-ttu-id="d7d0d-237">[!code-vb[VbVbalrFunctions&#14;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-237">[!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]</span></span>  
  
 <span data-ttu-id="d7d0d-238">O exemplo a seguir usa o `CStr` função para converter `Date` valores `String` valores.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-238">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 <span data-ttu-id="d7d0d-239">[!code-vb[VbVbalrFunctions&#15;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-239">[!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]</span></span>  
  
 <span data-ttu-id="d7d0d-240">`CStr`sempre processa uma `Date` valor no formato curto padrão para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="d7d0d-240">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="d7d0d-241">No entanto, `CStr` suprime o *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-241">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="d7d0d-242">Para obter mais detalhes sobre os valores retornados por `CStr`, consulte [retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="d7d0d-242">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="d7d0d-243">Exemplo de CUInt</span><span class="sxs-lookup"><span data-stu-id="d7d0d-243">CUInt Example</span></span>  
 <span data-ttu-id="d7d0d-244">O exemplo a seguir usa o `CUInt` função para converter um valor numérico para `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-244">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 <span data-ttu-id="d7d0d-245">[!code-vb[VbVbalrFunctions n º&16;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-245">[!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]</span></span>  
  
## <a name="culng-example"></a><span data-ttu-id="d7d0d-246">Exemplo de CULng</span><span class="sxs-lookup"><span data-stu-id="d7d0d-246">CULng Example</span></span>  
 <span data-ttu-id="d7d0d-247">O exemplo a seguir usa o `CULng` função para converter um valor numérico para `ULong`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-247">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 <span data-ttu-id="d7d0d-248">[!code-vb[17 VbVbalrFunctions](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-248">[!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]</span></span>  
  
## <a name="cushort-example"></a><span data-ttu-id="d7d0d-249">Exemplo de CUShort</span><span class="sxs-lookup"><span data-stu-id="d7d0d-249">CUShort Example</span></span>  
 <span data-ttu-id="d7d0d-250">O exemplo a seguir usa o `CUShort` função para converter um valor numérico para `UShort`.</span><span class="sxs-lookup"><span data-stu-id="d7d0d-250">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 <span data-ttu-id="d7d0d-251">[!code-vb[VbVbalrFunctions n º&18;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7d0d-251">[!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d0d-252">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7d0d-252">See Also</span></span>  
 <span data-ttu-id="d7d0d-253"><xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-253"><xref:Microsoft.VisualBasic.Strings.Asc%2A></span></span>   
 <span data-ttu-id="d7d0d-254"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-254"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
 <span data-ttu-id="d7d0d-255"><xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-255"><xref:Microsoft.VisualBasic.Strings.Chr%2A></span></span>   
 <span data-ttu-id="d7d0d-256"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-256"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>   
 <span data-ttu-id="d7d0d-257"><xref:Microsoft.VisualBasic.Conversion.Int%2A></xref:Microsoft.VisualBasic.Conversion.Int%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-257"><xref:Microsoft.VisualBasic.Conversion.Int%2A></span></span>   
 <span data-ttu-id="d7d0d-258"><xref:Microsoft.VisualBasic.Conversion.Fix%2A></xref:Microsoft.VisualBasic.Conversion.Fix%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-258"><xref:Microsoft.VisualBasic.Conversion.Fix%2A></span></span>   
 <span data-ttu-id="d7d0d-259"><xref:Microsoft.VisualBasic.Strings.Format%2A></xref:Microsoft.VisualBasic.Strings.Format%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-259"><xref:Microsoft.VisualBasic.Strings.Format%2A></span></span>   
 <span data-ttu-id="d7d0d-260"><xref:Microsoft.VisualBasic.Conversion.Hex%2A></xref:Microsoft.VisualBasic.Conversion.Hex%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-260"><xref:Microsoft.VisualBasic.Conversion.Hex%2A></span></span>   
 <span data-ttu-id="d7d0d-261"><xref:Microsoft.VisualBasic.Conversion.Oct%2A></xref:Microsoft.VisualBasic.Conversion.Oct%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-261"><xref:Microsoft.VisualBasic.Conversion.Oct%2A></span></span>   
 <span data-ttu-id="d7d0d-262"><xref:Microsoft.VisualBasic.Conversion.Str%2A></xref:Microsoft.VisualBasic.Conversion.Str%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-262"><xref:Microsoft.VisualBasic.Conversion.Str%2A></span></span>   
 <span data-ttu-id="d7d0d-263"><xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Conversion.Val%2A></span><span class="sxs-lookup"><span data-stu-id="d7d0d-263"><xref:Microsoft.VisualBasic.Conversion.Val%2A></span></span>   
<span data-ttu-id="d7d0d-264"> [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="d7d0d-264"> [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md) </span></span>  
<span data-ttu-id="d7d0d-265"> [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="d7d0d-265"> [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)</span></span>
