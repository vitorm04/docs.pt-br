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
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071832"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="7bf8b-102">Tipos incorporados para primitivos comuns da linguagem XAML</span><span class="sxs-lookup"><span data-stu-id="7bf8b-102">Built-in types for common XAML language primitives</span></span>

<span data-ttu-id="7bf8b-103">XAML 2009 introduz suporte em nível de linguagem XAML para vários tipos de dados que são frequentemente usados primitivos no tempo de execução da linguagem comum (CLR) e em outras linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="7bf8b-104">XAML 2009 adiciona suporte a `x:Object` `x:Boolean`estes primitivos: `x:Int16` `x:Int32`, `x:Int64` `x:TimeSpan`, `x:Uri` `x:Char`, `x:String` `x:Decimal`, `x:Single`, `x:Double`, , , , , , , , `x:Byte`, , e`x:Array`</span><span class="sxs-lookup"><span data-stu-id="7bf8b-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="7bf8b-105">Técnicas anteriores para primitivos linguísticos na marcação XAML</span><span class="sxs-lookup"><span data-stu-id="7bf8b-105">Previous Techniques for Language Primitives in XAML Markup</span></span>

 <span data-ttu-id="7bf8b-106">Em XAML para versões Anteriores do WPF, você pode referenciar os primitivos da linguagem CLR mapeando o conjunto e o namespace que continha uma classe de definição primitiva CLR para o Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="7bf8b-107">A maioria deles está na montagem <xref:System> mscorlib e namespace.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="7bf8b-108">Por exemplo, <xref:System.Int32>para usar, você pode declarar o seguinte mapeamento (com um uso de exemplo mostrado posteriormente):</span><span class="sxs-lookup"><span data-stu-id="7bf8b-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="7bf8b-109">XAML 2009 Língua primitiva</span><span class="sxs-lookup"><span data-stu-id="7bf8b-109">XAML 2009 Language Primitives</span></span>

<span data-ttu-id="7bf8b-110">Por convenção, os primitivos da linguagem para XAML e todos `x:` os outros elementos da linguagem XAML são mostrados, incluindo o prefixo.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="7bf8b-111">É assim que os elementos da linguagem XAML são normalmente usados em situações reais de marcação.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="7bf8b-112">Esta convenção é seguida na documentação conceitual para XAML na WPF e também na especificação XAML.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>

### <a name="xobject"></a><span data-ttu-id="7bf8b-113">x:Objeto</span><span class="sxs-lookup"><span data-stu-id="7bf8b-113">x:Object</span></span>

<span data-ttu-id="7bf8b-114">Para o apoio `x:Object` da CLR, o primitivo corresponde a <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>

<span data-ttu-id="7bf8b-115">Este primitivo não é normalmente usado na marcação de aplicativos, mas pode ser útil para alguns cenários, como verificar a atribuibilidade em um sistema tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>

### <a name="xboolean"></a><span data-ttu-id="7bf8b-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="7bf8b-116">x:Boolean</span></span>

<span data-ttu-id="7bf8b-117">Para o apoio `x:Boolean` da CLR, o primitivo corresponde a <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>

<span data-ttu-id="7bf8b-118">XAML analisa valores `x:Boolean` como caso insensível.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="7bf8b-119">Note `x:Bool` que não é uma alternativa aceita.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="7bf8b-120">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.17 e 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xchar"></a><span data-ttu-id="7bf8b-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="7bf8b-121">x:Char</span></span>

<span data-ttu-id="7bf8b-122">Para o apoio `x:Char` da CLR, o primitivo corresponde a <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>

<span data-ttu-id="7bf8b-123">Os tipos de string e char têm interação com a codificação geral do arquivo no nível XML.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="7bf8b-124">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.7 e 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xstring"></a><span data-ttu-id="7bf8b-125">x:String</span><span class="sxs-lookup"><span data-stu-id="7bf8b-125">x:String</span></span>

<span data-ttu-id="7bf8b-126">Para o apoio `x:String` da CLR, o primitivo corresponde a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>

<span data-ttu-id="7bf8b-127">Os tipos de string e char têm interação com a codificação geral do arquivo no nível XML.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="7bf8b-128">Para obter a definição de especificação do idioma XAML, consulte [ \[As seções MS-XAML\] 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdecimal"></a><span data-ttu-id="7bf8b-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="7bf8b-129">x:Decimal</span></span>

<span data-ttu-id="7bf8b-130">Para o apoio `x:Decimal` da CLR, o primitivo corresponde a <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>

<span data-ttu-id="7bf8b-131">O parsing XAML é `en-US` inerentemente feito sob a cultura.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-131">XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="7bf8b-132">Segundo `en-US` a cultura, o separador correto para os componentes`.`de uma decimal é sempre um período ( ) independentemente das configurações de cultura do ambiente de desenvolvimento, ou do eventual alvo do cliente onde o XAML é carregado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>

<span data-ttu-id="7bf8b-133">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.14 e 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xsingle"></a><span data-ttu-id="7bf8b-134">x:Único</span><span class="sxs-lookup"><span data-stu-id="7bf8b-134">x:Single</span></span>

<span data-ttu-id="7bf8b-135">Para o apoio `x:Single` da CLR, o primitivo corresponde a <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>

<span data-ttu-id="7bf8b-136">Além dos valores numéricos, a `x:Single` sintaxe `Infinity`de `-Infinity`texto `NaN`para também permite os tokens, e .</span><span class="sxs-lookup"><span data-stu-id="7bf8b-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="7bf8b-137">Esses tokens são tratados como sensíveis ao caso.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-137">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="7bf8b-138">`x:Single`pode apoiar valores na forma de notação científica, `e` se `E`o primeiro caractere na sintaxe de texto for ou .</span><span class="sxs-lookup"><span data-stu-id="7bf8b-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>

<span data-ttu-id="7bf8b-139">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.8 e 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xdouble"></a><span data-ttu-id="7bf8b-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="7bf8b-140">x:Double</span></span>

<span data-ttu-id="7bf8b-141">Para o apoio `x:Double` da CLR, o primitivo corresponde a <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>

<span data-ttu-id="7bf8b-142">Além dos valores numéricos, a `x:Double` sintaxe `Infinity` `-Infinity`de `NaN`texto para permitir os tokens, e .</span><span class="sxs-lookup"><span data-stu-id="7bf8b-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="7bf8b-143">Esses tokens são tratados como sensíveis ao caso.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-143">These tokens are treated as case sensitive.</span></span>

<span data-ttu-id="7bf8b-144">`x:Double`pode apoiar valores na forma de notação científica.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="7bf8b-145">Use o `e` `E` caractere ou para introduzir a parte expoente.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>

<span data-ttu-id="7bf8b-146">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.9 e 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint16"></a><span data-ttu-id="7bf8b-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="7bf8b-147">x:Int16</span></span>

<span data-ttu-id="7bf8b-148">Para o apoio `x:Int16` da CLR, o primitivo corresponde <xref:System.Int16> e `x:Int16` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="7bf8b-149">No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="7bf8b-150">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.11 e 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint32"></a><span data-ttu-id="7bf8b-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="7bf8b-151">x:Int32</span></span>

<span data-ttu-id="7bf8b-152">Para o apoio `x:Int32` da CLR, o primitivo corresponde a <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="7bf8b-153">`x:Int32`é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="7bf8b-154">No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="7bf8b-155">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.12 e 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xint64"></a><span data-ttu-id="7bf8b-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="7bf8b-156">x:Int64</span></span>

<span data-ttu-id="7bf8b-157">Para o apoio `x:Int64` da CLR, o primitivo corresponde a <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="7bf8b-158">`x:Int64`é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="7bf8b-159">No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>

<span data-ttu-id="7bf8b-160">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.13 e 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xtimespan"></a><span data-ttu-id="7bf8b-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="7bf8b-161">x:TimeSpan</span></span>

<span data-ttu-id="7bf8b-162">Para o apoio `x:TimeSpan` da CLR, o primitivo corresponde a <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>

<span data-ttu-id="7bf8b-163">O parsing XAML para o formato `en-US` de data-hora é inerentemente feito sob a cultura.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-163">XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>

<span data-ttu-id="7bf8b-164">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.16 e 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xuri"></a><span data-ttu-id="7bf8b-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="7bf8b-165">x:Uri</span></span>

<span data-ttu-id="7bf8b-166">Para o apoio `x:Uri` da CLR, o primitivo corresponde a <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>

<span data-ttu-id="7bf8b-167">Verificar os protocolos não faz parte da `x:Uri`definição XAML para .</span><span class="sxs-lookup"><span data-stu-id="7bf8b-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>

<span data-ttu-id="7bf8b-168">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.15 e 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xbyte"></a><span data-ttu-id="7bf8b-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="7bf8b-169">x:Byte</span></span>

<span data-ttu-id="7bf8b-170">Para o apoio `x:Byte` da CLR, o primitivo corresponde a <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="7bf8b-171"><xref:System.Byte>  /  A `x:Byte` é tratado como não assinado.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>

<span data-ttu-id="7bf8b-172">Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.10 e 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

### <a name="xarray"></a><span data-ttu-id="7bf8b-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="7bf8b-173">x:Array</span></span>

<span data-ttu-id="7bf8b-174">Para o apoio `x:Array` da CLR, o primitivo corresponde a <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>

<span data-ttu-id="7bf8b-175">Você pode definir uma matriz no XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido pela linguagem que não requer acesso a uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="7bf8b-176">Para obter mais informações sobre o suporte ao XAML 2006, consulte [x:Array Markup Extension](xarray-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-176">For more information about XAML 2006 support, see [x:Array Markup Extension](xarray-markup-extension.md).</span></span>

<span data-ttu-id="7bf8b-177">Para obter a definição de especificação do idioma XAML, consulte [ \[As seções MS-XAML\] 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7bf8b-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="wpf-support"></a><span data-ttu-id="7bf8b-178">Suporte wpf</span><span class="sxs-lookup"><span data-stu-id="7bf8b-178">WPF Support</span></span>

<span data-ttu-id="7bf8b-179">No WPF, você pode usar recursos XAML 2009, mas apenas para XAML que não é compilado por marcação.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="7bf8b-180">O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>

<span data-ttu-id="7bf8b-181">Um cenário onde você pode usar os recursos do XAML 2009 juntamente com o WPF é se você escrever <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>XAML solto e, em seguida, carregar esse XAML em um gráfico de tempo de execução wpf e objeto com .</span><span class="sxs-lookup"><span data-stu-id="7bf8b-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7bf8b-182">O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlReader.Load%2A> e seus podem processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de gráfico de objeto válida.</span><span class="sxs-lookup"><span data-stu-id="7bf8b-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
