---
title: "Tabela de formatação de resultados numéricos (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="ce0da-102">Tabela de formatação de resultados numéricos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="ce0da-102">Formatting Numeric Results Table (C# Reference)</span></span>
<span data-ttu-id="ce0da-103">Você pode formatar resultados numéricos usando o método <xref:System.String.Format%2A?displayProperty=fullName>, ou pelo método <xref:System.Console.Write%2A?displayProperty=fullName> ou <xref:System.Console.WriteLine%2A?displayProperty=fullName>, que chama `String.Format`.</span><span class="sxs-lookup"><span data-stu-id="ce0da-103">You can format numeric results by using the <xref:System.String.Format%2A?displayProperty=fullName> method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> or <xref:System.Console.WriteLine%2A?displayProperty=fullName> method, which calls `String.Format`.</span></span> <span data-ttu-id="ce0da-104">O formato é especificado usando cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="ce0da-104">The format is specified by using format strings.</span></span> <span data-ttu-id="ce0da-105">A tabela a seguir contém as cadeias de caracteres de formato padrão com suporte.</span><span class="sxs-lookup"><span data-stu-id="ce0da-105">The following table contains the supported standard format strings.</span></span> <span data-ttu-id="ce0da-106">A cadeia de caracteres de formato usa o seguinte formato: `Axx`, em que `A` é o especificador de formato e `xx` é o especificador de precisão.</span><span class="sxs-lookup"><span data-stu-id="ce0da-106">The format string takes the following form: `Axx`, where `A` is the format specifier and `xx` is the precision specifier.</span></span> <span data-ttu-id="ce0da-107">O especificador de formato controla o tipo de formatação aplicada ao valor numérico e o especificador de precisão controla o número de dígitos significativos ou casas decimais do resultado formatado.</span><span class="sxs-lookup"><span data-stu-id="ce0da-107">The format specifier controls the type of formatting applied to the numeric value, and the precision specifier controls the number of significant digits or decimal places of the formatted output.</span></span> <span data-ttu-id="ce0da-108">O valor do especificador de precisão varia de 0 a 99.</span><span class="sxs-lookup"><span data-stu-id="ce0da-108">The value of the precision specifier ranges from 0 to 99.</span></span>  
  
 <span data-ttu-id="ce0da-109">Para obter mais informações sobre cadeias de caracteres de formatação padrão e personalizadas, consulte [Tipos de Formatação](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ce0da-109">For more information about standard and custom formatting strings, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="ce0da-110">Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ce0da-110">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
|<span data-ttu-id="ce0da-111">Especificador de Formato</span><span class="sxs-lookup"><span data-stu-id="ce0da-111">Format Specifier</span></span>|<span data-ttu-id="ce0da-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce0da-112">Description</span></span>|<span data-ttu-id="ce0da-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ce0da-113">Examples</span></span>|<span data-ttu-id="ce0da-114">Saída</span><span class="sxs-lookup"><span data-stu-id="ce0da-114">Output</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="ce0da-115">“C” ou “c”</span><span class="sxs-lookup"><span data-stu-id="ce0da-115">C or c</span></span>|<span data-ttu-id="ce0da-116">Moeda</span><span class="sxs-lookup"><span data-stu-id="ce0da-116">Currency</span></span>|<span data-ttu-id="ce0da-117">Console.Write("{0:C}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="ce0da-117">Console.Write("{0:C}", 2.5);</span></span><br /><br /> <span data-ttu-id="ce0da-118">Console.Write("{0:C}", -2.5);</span><span class="sxs-lookup"><span data-stu-id="ce0da-118">Console.Write("{0:C}", -2.5);</span></span>|<span data-ttu-id="ce0da-119">$2.50</span><span class="sxs-lookup"><span data-stu-id="ce0da-119">$2.50</span></span><br /><br /> <span data-ttu-id="ce0da-120">($2,50)</span><span class="sxs-lookup"><span data-stu-id="ce0da-120">($2.50)</span></span>|  
|<span data-ttu-id="ce0da-121">D ou d</span><span class="sxs-lookup"><span data-stu-id="ce0da-121">D or d</span></span>|<span data-ttu-id="ce0da-122">Decimal</span><span class="sxs-lookup"><span data-stu-id="ce0da-122">Decimal</span></span>|<span data-ttu-id="ce0da-123">Console.Write("{0:D5}", 25);</span><span class="sxs-lookup"><span data-stu-id="ce0da-123">Console.Write("{0:D5}", 25);</span></span>|<span data-ttu-id="ce0da-124">00025</span><span class="sxs-lookup"><span data-stu-id="ce0da-124">00025</span></span>|  
|<span data-ttu-id="ce0da-125">"E" ou "e"</span><span class="sxs-lookup"><span data-stu-id="ce0da-125">E or e</span></span>|<span data-ttu-id="ce0da-126">Científico</span><span class="sxs-lookup"><span data-stu-id="ce0da-126">Scientific</span></span>|<span data-ttu-id="ce0da-127">Console.Write("{0:E}", 250000);</span><span class="sxs-lookup"><span data-stu-id="ce0da-127">Console.Write("{0:E}", 250000);</span></span>|<span data-ttu-id="ce0da-128">2,500000E+005</span><span class="sxs-lookup"><span data-stu-id="ce0da-128">2.500000E+005</span></span>|  
|<span data-ttu-id="ce0da-129">F ou f</span><span class="sxs-lookup"><span data-stu-id="ce0da-129">F or f</span></span>|<span data-ttu-id="ce0da-130">Ponto fixo</span><span class="sxs-lookup"><span data-stu-id="ce0da-130">Fixed-point</span></span>|<span data-ttu-id="ce0da-131">Console.Write("{0:F2}", 25);</span><span class="sxs-lookup"><span data-stu-id="ce0da-131">Console.Write("{0:F2}", 25);</span></span><br /><br /> <span data-ttu-id="ce0da-132">Console.Write("{0:F0}", 25);</span><span class="sxs-lookup"><span data-stu-id="ce0da-132">Console.Write("{0:F0}", 25);</span></span>|<span data-ttu-id="ce0da-133">25,00</span><span class="sxs-lookup"><span data-stu-id="ce0da-133">25.00</span></span><br /><br /> <span data-ttu-id="ce0da-134">25</span><span class="sxs-lookup"><span data-stu-id="ce0da-134">25</span></span>|  
|<span data-ttu-id="ce0da-135">"G" ou "g"</span><span class="sxs-lookup"><span data-stu-id="ce0da-135">G or g</span></span>|<span data-ttu-id="ce0da-136">Geral</span><span class="sxs-lookup"><span data-stu-id="ce0da-136">General</span></span>|<span data-ttu-id="ce0da-137">Console.Write("{0:G}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="ce0da-137">Console.Write("{0:G}", 2.5);</span></span>|<span data-ttu-id="ce0da-138">2.5</span><span class="sxs-lookup"><span data-stu-id="ce0da-138">2.5</span></span>|  
|<span data-ttu-id="ce0da-139">"N" ou "n"</span><span class="sxs-lookup"><span data-stu-id="ce0da-139">N or n</span></span>|<span data-ttu-id="ce0da-140">Número</span><span class="sxs-lookup"><span data-stu-id="ce0da-140">Number</span></span>|<span data-ttu-id="ce0da-141">Console.Write("{0:N}", 2500000);</span><span class="sxs-lookup"><span data-stu-id="ce0da-141">Console.Write("{0:N}", 2500000);</span></span>|<span data-ttu-id="ce0da-142">2.500.000,00</span><span class="sxs-lookup"><span data-stu-id="ce0da-142">2,500,000.00</span></span>|  
|<span data-ttu-id="ce0da-143">"X" ou "x"</span><span class="sxs-lookup"><span data-stu-id="ce0da-143">X or x</span></span>|<span data-ttu-id="ce0da-144">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="ce0da-144">Hexadecimal</span></span>|<span data-ttu-id="ce0da-145">Console.Write("{0:X}", 250);</span><span class="sxs-lookup"><span data-stu-id="ce0da-145">Console.Write("{0:X}", 250);</span></span><br /><br /> <span data-ttu-id="ce0da-146">Console.Write("{0:X}", 0xffff);</span><span class="sxs-lookup"><span data-stu-id="ce0da-146">Console.Write("{0:X}", 0xffff);</span></span>|<span data-ttu-id="ce0da-147">FA</span><span class="sxs-lookup"><span data-stu-id="ce0da-147">FA</span></span><br /><br /> <span data-ttu-id="ce0da-148">FFFF</span><span class="sxs-lookup"><span data-stu-id="ce0da-148">FFFF</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce0da-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce0da-149">See Also</span></span>  
 <span data-ttu-id="ce0da-150">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ce0da-150">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ce0da-151">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ce0da-151">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ce0da-152">[Cadeias de Caracteres de Formato Numérico Padrão](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="ce0da-152">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="ce0da-153">[Tabelas de Referência de Tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="ce0da-153">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 [<span data-ttu-id="ce0da-154">string</span><span class="sxs-lookup"><span data-stu-id="ce0da-154">string</span></span>](../../../csharp/language-reference/keywords/string.md)

