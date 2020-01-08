---
title: Tabela de formatação de resultados numéricos – Referência de C#
ms.custom: seodec18
description: Saiba mais sobre cadeias de caracteres de formato numérico padrão do C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 853faf481e546f2980d799d5daf50a14c608c052
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345468"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="92443-103">Tabela de formatação de resultados numéricos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="92443-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="92443-104">A tabela a seguir mostra os especificadores de formato compatíveis para formatação de resultados numéricos.</span><span class="sxs-lookup"><span data-stu-id="92443-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="92443-105">O resultado formatado na última coluna corresponde ao "en-US" <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="92443-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="92443-106">Especificador de formato</span><span class="sxs-lookup"><span data-stu-id="92443-106">Format specifier</span></span>|<span data-ttu-id="92443-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="92443-107">Description</span></span>|<span data-ttu-id="92443-108">Exemplos</span><span class="sxs-lookup"><span data-stu-id="92443-108">Examples</span></span>|<span data-ttu-id="92443-109">Resultado</span><span class="sxs-lookup"><span data-stu-id="92443-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="92443-110">“C” ou “c”</span><span class="sxs-lookup"><span data-stu-id="92443-110">C or c</span></span>|<span data-ttu-id="92443-111">Moeda</span><span class="sxs-lookup"><span data-stu-id="92443-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="92443-112">\\$2.50</span><span class="sxs-lookup"><span data-stu-id="92443-112">\\$2.50</span></span><br /><br /> <span data-ttu-id="92443-113">(\\$2.50)</span><span class="sxs-lookup"><span data-stu-id="92443-113">(\\$2.50)</span></span>|  
|<span data-ttu-id="92443-114">D ou d</span><span class="sxs-lookup"><span data-stu-id="92443-114">D or d</span></span>|<span data-ttu-id="92443-115">Decimal</span><span class="sxs-lookup"><span data-stu-id="92443-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="92443-116">00025</span><span class="sxs-lookup"><span data-stu-id="92443-116">00025</span></span>|  
|<span data-ttu-id="92443-117">"E" ou "e"</span><span class="sxs-lookup"><span data-stu-id="92443-117">E or e</span></span>|<span data-ttu-id="92443-118">Exponencial</span><span class="sxs-lookup"><span data-stu-id="92443-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="92443-119">2.50E+005</span><span class="sxs-lookup"><span data-stu-id="92443-119">2.50E+005</span></span>|  
|<span data-ttu-id="92443-120">F ou f</span><span class="sxs-lookup"><span data-stu-id="92443-120">F or f</span></span>|<span data-ttu-id="92443-121">Ponto fixo</span><span class="sxs-lookup"><span data-stu-id="92443-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="92443-122">2,50</span><span class="sxs-lookup"><span data-stu-id="92443-122">2.50</span></span><br /><br /> <span data-ttu-id="92443-123">3</span><span class="sxs-lookup"><span data-stu-id="92443-123">3</span></span>|  
|<span data-ttu-id="92443-124">"G" ou "g"</span><span class="sxs-lookup"><span data-stu-id="92443-124">G or g</span></span>|<span data-ttu-id="92443-125">Geral</span><span class="sxs-lookup"><span data-stu-id="92443-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="92443-126">2.5</span><span class="sxs-lookup"><span data-stu-id="92443-126">2.5</span></span>|  
|<span data-ttu-id="92443-127">"N" ou "n"</span><span class="sxs-lookup"><span data-stu-id="92443-127">N or n</span></span>|<span data-ttu-id="92443-128">Numeric</span><span class="sxs-lookup"><span data-stu-id="92443-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="92443-129">2\.500.000,00</span><span class="sxs-lookup"><span data-stu-id="92443-129">2,500,000.00</span></span>|  
|<span data-ttu-id="92443-130">P ou p</span><span class="sxs-lookup"><span data-stu-id="92443-130">P or p</span></span>|<span data-ttu-id="92443-131">Porcentagem</span><span class="sxs-lookup"><span data-stu-id="92443-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="92443-132">25,00%</span><span class="sxs-lookup"><span data-stu-id="92443-132">25.00%</span></span>|  
|<span data-ttu-id="92443-133">R ou r</span><span class="sxs-lookup"><span data-stu-id="92443-133">R or r</span></span>|<span data-ttu-id="92443-134">Ida e volta</span><span class="sxs-lookup"><span data-stu-id="92443-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="92443-135">2.5</span><span class="sxs-lookup"><span data-stu-id="92443-135">2.5</span></span>|  
|<span data-ttu-id="92443-136">"X" ou "x"</span><span class="sxs-lookup"><span data-stu-id="92443-136">X or x</span></span>|<span data-ttu-id="92443-137">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="92443-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="92443-138">FA</span><span class="sxs-lookup"><span data-stu-id="92443-138">FA</span></span><br /><br /> <span data-ttu-id="92443-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="92443-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="92443-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="92443-140">Remarks</span></span>

<span data-ttu-id="92443-141">Você pode usar um especificador de formato para criar uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="92443-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="92443-142">A cadeia de caracteres de formato é da seguinte forma: `Axx`, em que</span><span class="sxs-lookup"><span data-stu-id="92443-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="92443-143">`A` é o especificador de formato, que controla o tipo de formatação aplicada ao valor numérico.</span><span class="sxs-lookup"><span data-stu-id="92443-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="92443-144">`xx` é o especificador de precisão, que afeta o número de dígitos na saída formatada.</span><span class="sxs-lookup"><span data-stu-id="92443-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="92443-145">O valor do especificador de precisão varia de 0 a 99.</span><span class="sxs-lookup"><span data-stu-id="92443-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="92443-146">Os especificadores de formato decimal ("D" ou "d") e hexadecimal ("X" ou "x") são compatíveis apenas com tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="92443-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="92443-147">O especificador de formato de ida e volta ("R" ou "r") é compatível apenas com tipos <xref:System.Single>, <xref:System.Double> e <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="92443-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="92443-148">As cadeias de caractere de formato numérico padrão têm suporte de:</span><span class="sxs-lookup"><span data-stu-id="92443-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="92443-149">Algumas sobrecargas do método `ToString` de todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="92443-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="92443-150">Por exemplo, você pode fornecer uma cadeia de caracteres de formato numérico para os métodos <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> e <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92443-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="92443-151">O [recurso de formatação composta](../../../standard/base-types/composite-formatting.md) do .NET, que é compatível com o método <xref:System.String.Format%2A?displayProperty=nameWithType>, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="92443-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="92443-152">[Cadeias de caracteres interpoladas](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="92443-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="92443-153">Para obter mais informações, confira [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="92443-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92443-154">Veja também</span><span class="sxs-lookup"><span data-stu-id="92443-154">See also</span></span>

- [<span data-ttu-id="92443-155">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="92443-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="92443-156">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="92443-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="92443-157">Formatando tipos</span><span class="sxs-lookup"><span data-stu-id="92443-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="92443-158">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="92443-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="92443-159">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="92443-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="92443-160">string</span><span class="sxs-lookup"><span data-stu-id="92443-160">string</span></span>](../builtin-types/reference-types.md)
