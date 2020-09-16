---
title: Tipos inseridos para primitivos de linguagem XML comuns
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: ec0e2a29a191d5057ce66a5f3272d00e92b01bd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540023"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="27d31-102">Tipos internos para primitivos comuns de linguagem XAML</span><span class="sxs-lookup"><span data-stu-id="27d31-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="27d31-103">O XAML 2009 apresenta suporte no nível da linguagem XAML para vários tipos de dados que são primitivos usados com frequência no Common Language Runtime (CLR) e em outras linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="27d31-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="27d31-104">O XAML 2009 adiciona suporte para esses primitivos:,,,,,,, `x:Object` `x:Boolean` ,,,, `x:Char` `x:String` `x:Decimal` `x:Single` `x:Double` `x:Int16` `x:Int32` `x:Int64` `x:TimeSpan` `x:Uri` `x:Byte` e `x:Array`</span><span class="sxs-lookup"><span data-stu-id="27d31-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="27d31-105">Técnicas anteriores para primitivas de idioma na marcação XAML</span><span class="sxs-lookup"><span data-stu-id="27d31-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="27d31-106">Em XAML para versões anteriores do WPF, você pode referenciar os primitivos de linguagem CLR mapeando o assembly e o namespace que continham uma classe de definição de CLR primitivo para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27d31-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="27d31-107">A maioria deles está no assembly e no <xref:System> namespace mscorlib.</span><span class="sxs-lookup"><span data-stu-id="27d31-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="27d31-108">Por exemplo, para usar <xref:System.Int32> o, você pode declarar o seguinte mapeamento (com um exemplo de uso mostrado em seguida):</span><span class="sxs-lookup"><span data-stu-id="27d31-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="27d31-109">Primitivos de linguagem XAML 2009</span><span class="sxs-lookup"><span data-stu-id="27d31-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="27d31-110">Por convenção, os primitivos de idioma para XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo.</span><span class="sxs-lookup"><span data-stu-id="27d31-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="27d31-111">É assim que os elementos da linguagem XAML são normalmente usados em situações reais de marcação.</span><span class="sxs-lookup"><span data-stu-id="27d31-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="27d31-112">Essa convenção é seguida da documentação conceitual para XAML no WPF e também na especificação XAML.</span><span class="sxs-lookup"><span data-stu-id="27d31-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="27d31-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="27d31-113">x:Object</span></span>

<span data-ttu-id="27d31-114">Para o backup do CLR, o `x:Object` primitivo corresponde a <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="27d31-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="27d31-115">Normalmente, esse primitivo não é usado na marcação do aplicativo, mas pode ser útil para alguns cenários, como a verificação da atribuição em um sistema de tipos XAML.</span><span class="sxs-lookup"><span data-stu-id="27d31-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="27d31-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="27d31-116">x:Boolean</span></span>

<span data-ttu-id="27d31-117">Para o backup do CLR, o `x:Boolean` primitivo corresponde a <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="27d31-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="27d31-118">O XAML analisa valores `x:Boolean` como não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="27d31-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="27d31-119">Observe que `x:Bool` não é uma alternativa aceita.</span><span class="sxs-lookup"><span data-stu-id="27d31-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="27d31-120">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.17 e 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="27d31-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="27d31-121">x:Char</span></span>

<span data-ttu-id="27d31-122">Para o backup do CLR, o `x:Char` primitivo corresponde a <xref:System.Char> .</span><span class="sxs-lookup"><span data-stu-id="27d31-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="27d31-123">Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML.</span><span class="sxs-lookup"><span data-stu-id="27d31-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="27d31-124">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.7 e 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="27d31-125">x:String</span><span class="sxs-lookup"><span data-stu-id="27d31-125">x:String</span></span>

<span data-ttu-id="27d31-126">Para o backup do CLR, o `x:String` primitivo corresponde a <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="27d31-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="27d31-127">Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML.</span><span class="sxs-lookup"><span data-stu-id="27d31-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="27d31-128">Para a definição de especificação da linguagem XAML, consulte as [ \[ seções do MS-XAML \] 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="27d31-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="27d31-129">x:Decimal</span></span>

<span data-ttu-id="27d31-130">Para o backup do CLR, o `x:Decimal` primitivo corresponde a <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="27d31-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="27d31-131">A análise de XAML é feita de forma inerente em `en-US` Culture.</span><span class="sxs-lookup"><span data-stu-id="27d31-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="27d31-132">Em `en-US` Culture, o separador correto para os componentes de um decimal é sempre um ponto ( `.` ), independentemente das configurações de cultura do ambiente de desenvolvimento, ou do destino de cliente eventual em que o XAML é carregado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="27d31-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="27d31-133">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.14 e 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="27d31-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="27d31-134">x:Single</span></span>

<span data-ttu-id="27d31-135">Para o backup do CLR, o `x:Single` primitivo corresponde a <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="27d31-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="27d31-136">Além dos valores numéricos, a sintaxe de texto para `x:Single` também permite os tokens `Infinity` , `-Infinity` e `NaN` .</span><span class="sxs-lookup"><span data-stu-id="27d31-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="27d31-137">Esses tokens são tratados como diferenciando maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="27d31-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="27d31-138">`x:Single` pode dar suporte a valores no formato de notação científica, se o primeiro caractere na sintaxe de texto for `e` ou `E` .</span><span class="sxs-lookup"><span data-stu-id="27d31-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="27d31-139">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.8 e tópico 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="27d31-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="27d31-140">x:Double</span></span>

<span data-ttu-id="27d31-141">Para o backup do CLR, o `x:Double` primitivo corresponde a <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="27d31-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="27d31-142">Além dos valores numéricos, a sintaxe de texto para `x:Double` permite os tokens `Infinity` , `-Infinity` e `NaN` .</span><span class="sxs-lookup"><span data-stu-id="27d31-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="27d31-143">Esses tokens são tratados como diferenciando maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="27d31-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="27d31-144">`x:Double` pode dar suporte a valores no formato de notação científica.</span><span class="sxs-lookup"><span data-stu-id="27d31-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="27d31-145">Use o caractere `e` ou `E` para introduzir a parte do expoente.</span><span class="sxs-lookup"><span data-stu-id="27d31-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="27d31-146">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.9 e 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="27d31-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="27d31-147">x:Int16</span></span>

<span data-ttu-id="27d31-148">Para o backup do CLR, o `x:Int16` primitivo corresponde a <xref:System.Int16> e `x:Int16` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="27d31-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="27d31-149">Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="27d31-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="27d31-150">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.11 e 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="27d31-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="27d31-151">x:Int32</span></span>

<span data-ttu-id="27d31-152">Para o backup do CLR, o `x:Int32` primitivo corresponde a <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="27d31-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="27d31-153">`x:Int32` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="27d31-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="27d31-154">Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="27d31-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="27d31-155">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.12 e 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="27d31-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="27d31-156">x:Int64</span></span>

<span data-ttu-id="27d31-157">Para o backup do CLR, o `x:Int64` primitivo corresponde a <xref:System.Int64> .</span><span class="sxs-lookup"><span data-stu-id="27d31-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="27d31-158">`x:Int64` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="27d31-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="27d31-159">Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="27d31-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="27d31-160">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.13 e 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="27d31-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="27d31-161">x:TimeSpan</span></span>

<span data-ttu-id="27d31-162">Para o backup do CLR, o `x:TimeSpan` primitivo corresponde a <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="27d31-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="27d31-163">A análise XAML para o formato de data e hora é inerentemente feita em `en-US` cultura.</span><span class="sxs-lookup"><span data-stu-id="27d31-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="27d31-164">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.16 e 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="27d31-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="27d31-165">x:Uri</span></span>

<span data-ttu-id="27d31-166">Para o backup do CLR, o `x:Uri` primitivo corresponde a <xref:System.Uri> .</span><span class="sxs-lookup"><span data-stu-id="27d31-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="27d31-167">A verificação de protocolos não faz parte da definição XAML para `x:Uri` .</span><span class="sxs-lookup"><span data-stu-id="27d31-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="27d31-168">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.15 e 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="27d31-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="27d31-169">x:Byte</span></span>

<span data-ttu-id="27d31-170">Para o backup do CLR, o `x:Byte` primitivo corresponde a <xref:System.Byte> .</span><span class="sxs-lookup"><span data-stu-id="27d31-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="27d31-171">Um <xref:System.Byte>  /  `x:Byte` é tratado como não assinado.</span><span class="sxs-lookup"><span data-stu-id="27d31-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="27d31-172">Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.10 e 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="27d31-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="27d31-173">x:Array</span></span>

<span data-ttu-id="27d31-174">Para o backup do CLR, o `x:Array` primitivo corresponde a <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="27d31-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="27d31-175">Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido por linguagem que não requer acesso a uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="27d31-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="27d31-176">Para obter mais informações sobre o suporte a XAML 2006, consulte [extensão de marcação x:array](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="27d31-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="27d31-177">Para a definição de especificação da linguagem XAML, consulte as [ \[ seções do MS-XAML \] 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="27d31-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="27d31-178">Suporte do WPF</span><span class="sxs-lookup"><span data-stu-id="27d31-178">WPF Support</span></span>

<span data-ttu-id="27d31-179">No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação.</span><span class="sxs-lookup"><span data-stu-id="27d31-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="27d31-180">O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="27d31-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="27d31-181">Um cenário em que você pode usar recursos XAML 2009 junto com o WPF é se você criar um XAML livre e, em seguida, carregar esse XAML em um grafo de tempo de execução e de objeto do WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="27d31-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="27d31-182">O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e seu <xref:System.Windows.Markup.XamlReader.Load%2A> pode processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de grafo de objeto válido.</span><span class="sxs-lookup"><span data-stu-id="27d31-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
