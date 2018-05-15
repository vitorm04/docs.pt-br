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
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="c86a3-102">Tipos inseridos para primitivos de linguagem XML comuns</span><span class="sxs-lookup"><span data-stu-id="c86a3-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="c86a3-103">XAML 2009 introduz o suporte ao nível de linguagem XAML vários tipos de dados que são usados com frequência primitivos no common language runtime (CLR) e em outras linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="c86a3-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="c86a3-104">XAML 2009 adiciona suporte para esses primitivos: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, e `x:Array`</span><span class="sxs-lookup"><span data-stu-id="c86a3-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="c86a3-105">Técnicas anteriores para primitivos de linguagem de marcação XAML</span><span class="sxs-lookup"><span data-stu-id="c86a3-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="c86a3-106">Em XAML para versões anteriores do WPF, você pode referenciar os primitivos de linguagem CLR mapeando o assembly e o namespace que continha uma classe de definição primitivo do CLR para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c86a3-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="c86a3-107">A maioria deles está no assembly mscorlib e <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="c86a3-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="c86a3-108">Por exemplo, para usar <xref:System.Int32>, você pode declarar o seguinte mapeamento (com um uso de exemplo mostrado posteriormente):</span><span class="sxs-lookup"><span data-stu-id="c86a3-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="c86a3-109">Primitivos de linguagem XAML 2009</span><span class="sxs-lookup"><span data-stu-id="c86a3-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="c86a3-110">Por convenção, os primitivos de linguagem XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo.</span><span class="sxs-lookup"><span data-stu-id="c86a3-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="c86a3-111">Isso é como os elementos de linguagem XAML normalmente são usados na marcação do mundo real.</span><span class="sxs-lookup"><span data-stu-id="c86a3-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="c86a3-112">Essa convenção é seguida na documentação conceitual do XAML em WPF e também na especificação do XAML.</span><span class="sxs-lookup"><span data-stu-id="c86a3-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="c86a3-113">x: o objeto</span><span class="sxs-lookup"><span data-stu-id="c86a3-113">x:Object</span></span>  
 <span data-ttu-id="c86a3-114">Para backups de CLR, o `x:Object` primitivo corresponde ao <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="c86a3-115">Esse primitivo geralmente não é usado na marcação de aplicativo, mas pode ser útil para alguns cenários, como verificação de assignability em um sistema de tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="c86a3-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="c86a3-116">x: Boolean</span><span class="sxs-lookup"><span data-stu-id="c86a3-116">x:Boolean</span></span>  
 <span data-ttu-id="c86a3-117">Para backups de CLR, o `x:Boolean` primitivo corresponde ao <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="c86a3-118">XAML analisa os valores para `x:Boolean` como maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c86a3-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="c86a3-119">Observe que `x:Bool` não é uma alternativa aceita.</span><span class="sxs-lookup"><span data-stu-id="c86a3-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="c86a3-120">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.17 e 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="c86a3-121">x: Char</span><span class="sxs-lookup"><span data-stu-id="c86a3-121">x:Char</span></span>  
 <span data-ttu-id="c86a3-122">Para backups de CLR, o `x:Char` primitivo corresponde ao <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="c86a3-123">Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível do XML.</span><span class="sxs-lookup"><span data-stu-id="c86a3-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="c86a3-124">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.7 e 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="c86a3-125">x: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c86a3-125">x:String</span></span>  
 <span data-ttu-id="c86a3-126">Para backups de CLR, o `x:String` primitivo corresponde ao <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="c86a3-127">Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível do XML.</span><span class="sxs-lookup"><span data-stu-id="c86a3-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="c86a3-128">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="c86a3-129">x: Decimal</span><span class="sxs-lookup"><span data-stu-id="c86a3-129">x:Decimal</span></span>  
 <span data-ttu-id="c86a3-130">Para backups de CLR, o `x:Decimal` primitivo corresponde ao <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="c86a3-131">Observe que a análise de XAML inerentemente é feita em `en-US` cultura.</span><span class="sxs-lookup"><span data-stu-id="c86a3-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="c86a3-132">Em `en-US` cultura, o separador correto para os componentes de um decimal é sempre um período (`.`), independentemente das configurações de cultura do ambiente de desenvolvimento ou de destino eventual cliente onde o XAML é carregado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c86a3-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="c86a3-133">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.14 e 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="c86a3-134">x: único</span><span class="sxs-lookup"><span data-stu-id="c86a3-134">x:Single</span></span>  
 <span data-ttu-id="c86a3-135">Para backups de CLR, o `x:Single` primitivo corresponde ao <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="c86a3-136">Além de valores numéricos, sintaxe de texto para `x:Single` também permite que os tokens `Infinity`, `-Infinity`, e `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c86a3-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="c86a3-137">Esses tokens são tratados como maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c86a3-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="c86a3-138">`x:Single` pode dar suporte a valores no formulário de notação científica, se o primeiro caractere na sintaxe do texto é `e` ou `E`.</span><span class="sxs-lookup"><span data-stu-id="c86a3-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="c86a3-139">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.8 e 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="c86a3-140">x: duplo</span><span class="sxs-lookup"><span data-stu-id="c86a3-140">x:Double</span></span>  
 <span data-ttu-id="c86a3-141">Para backups de CLR, o `x:Double` primitivo corresponde ao <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="c86a3-142">Além de valores numéricos, sintaxe de texto para `x:Double` permite que os tokens `Infinity`, `-Infinity`, e `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c86a3-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="c86a3-143">Esses tokens são tratados como maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c86a3-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="c86a3-144">`x:Double` pode dar suporte a valores no formulário de notação científica.</span><span class="sxs-lookup"><span data-stu-id="c86a3-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="c86a3-145">Use o caractere `e` ou `E` para apresentar a parte expoente.</span><span class="sxs-lookup"><span data-stu-id="c86a3-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="c86a3-146">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.9 e 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="c86a3-147">x: Int16</span><span class="sxs-lookup"><span data-stu-id="c86a3-147">x:Int16</span></span>  
 <span data-ttu-id="c86a3-148">Para backups de CLR, o `x:Int16` primitivo corresponde à <xref:System.Int16> e `x:Int16` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="c86a3-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="c86a3-149">Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.</span><span class="sxs-lookup"><span data-stu-id="c86a3-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c86a3-150">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.11 e 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="c86a3-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="c86a3-151">x:Int32</span></span>  
 <span data-ttu-id="c86a3-152">Para backups de CLR, o `x:Int32` primitivo corresponde ao <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="c86a3-153">`x:Int32` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="c86a3-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="c86a3-154">Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.</span><span class="sxs-lookup"><span data-stu-id="c86a3-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c86a3-155">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.12 e 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="c86a3-156">x: Int64</span><span class="sxs-lookup"><span data-stu-id="c86a3-156">x:Int64</span></span>  
 <span data-ttu-id="c86a3-157">Para backups de CLR, o `x:Int64` primitivo corresponde ao <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="c86a3-158">`x:Int64` é tratado como assinado.</span><span class="sxs-lookup"><span data-stu-id="c86a3-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="c86a3-159">Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.</span><span class="sxs-lookup"><span data-stu-id="c86a3-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="c86a3-160">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.13 e 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="c86a3-161">X:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c86a3-161">x:TimeSpan</span></span>  
 <span data-ttu-id="c86a3-162">Para backups de CLR, o `x:TimeSpan` primitivo corresponde ao <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="c86a3-163">Observe que XAML análise para o formato de data / hora é feito inerentemente `en-US` cultura.</span><span class="sxs-lookup"><span data-stu-id="c86a3-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="c86a3-164">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.16 e 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="c86a3-165">x: Uri</span><span class="sxs-lookup"><span data-stu-id="c86a3-165">x:Uri</span></span>  
 <span data-ttu-id="c86a3-166">Para backups de CLR, o `x:Uri` primitivo corresponde ao <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="c86a3-167">A verificação de protocolos não é parte da definição de XAML para `x:Uri`.</span><span class="sxs-lookup"><span data-stu-id="c86a3-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="c86a3-168">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.15 e 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="c86a3-169">x: Byte</span><span class="sxs-lookup"><span data-stu-id="c86a3-169">x:Byte</span></span>  
 <span data-ttu-id="c86a3-170">Para backups de CLR, o `x:Byte` primitivo corresponde ao <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="c86a3-171">Um <xref:System.Byte>  /  `x:Byte` é tratado como não assinados.</span><span class="sxs-lookup"><span data-stu-id="c86a3-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="c86a3-172">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.10 e 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="c86a3-173">X:array</span><span class="sxs-lookup"><span data-stu-id="c86a3-173">x:Array</span></span>  
 <span data-ttu-id="c86a3-174">Para backups de CLR, o `x:Array` primitivo corresponde ao <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="c86a3-175">Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; No entanto, a sintaxe XAML 2009 é um primitivo de idioma definido que não requer acesso a uma extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="c86a3-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="c86a3-176">Para obter mais informações sobre o suporte de 2006 XAML, consulte [extensão de marcação X:array](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c86a3-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="c86a3-177">Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="c86a3-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="c86a3-178">Suporte a WPF</span><span class="sxs-lookup"><span data-stu-id="c86a3-178">WPF Support</span></span>  
 <span data-ttu-id="c86a3-179">No WPF, você pode usar recursos XAML 2009 mas somente para XAML não marcação-compilado.</span><span class="sxs-lookup"><span data-stu-id="c86a3-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="c86a3-180">Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="c86a3-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="c86a3-181">Um cenário onde você pode usar recursos XAML 2009 junto com WPF é se você criar XAML livre e você, em seguida, carregar esse XAML em um gráfico de tempo de execução e o objeto WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c86a3-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c86a3-182">O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e sua <xref:System.Windows.Markup.XamlReader.Load%2A> pode processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de gráfico de objeto válido.</span><span class="sxs-lookup"><span data-stu-id="c86a3-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
