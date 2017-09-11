---
title: "Analisando cadeias de caracteres numéricas no .NET"
description: "Analisando cadeias de caracteres numéricas no .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 85cd57d33b03f7a2105ee3f770b2f8bcc0a57ee4
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-numeric-strings-in-net"></a><span data-ttu-id="29840-104">Analisando cadeias de caracteres numéricas no .NET</span><span class="sxs-lookup"><span data-stu-id="29840-104">Parsing numeric strings in .NET</span></span>

<span data-ttu-id="29840-105">Todos os tipos numéricos têm dois métodos de análise estáticos, `Parse` e `TryParse`, que podem ser usados para converter a representação de cadeia de caracteres de um número em um tipo numérico.</span><span class="sxs-lookup"><span data-stu-id="29840-105">All numeric types have two static parsing methods, `Parse` and `TryParse`, that you can use to convert the string representation of a number into a numeric type.</span></span> <span data-ttu-id="29840-106">Esses métodos permitem analisar cadeias de caracteres que foram produzidas usando as cadeias de caracteres de formato documentadas em [Cadeias de caracteres de formato numérico padrão](standard-numeric.md) e [Cadeias de caracteres de formato numérico personalizadas](custom-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="29840-106">These methods enable you to parse strings that were produced by using the format strings documented in [Standard Numeric Format Strings](standard-numeric.md) and [Custom Numeric Format Strings](custom-numeric.md).</span></span> <span data-ttu-id="29840-107">Por padrão, os métodos `Parse` e `TryParse` conseguem converter cadeias de caracteres que contêm dígitos decimais integrais somente em valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="29840-107">By default, the `Parse` and `TryParse` methods can successfully convert strings that contain integral decimal digits only to integer values.</span></span> <span data-ttu-id="29840-108">Podem converter cadeias de caracteres que contêm dígitos decimais integrais e dígitos fracionários, separadores de grupo e um separador decimal em valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="29840-108">They can successfully convert strings that contain integral and fractional decimal digits, group separators, and a decimal separator to floating-point values.</span></span> <span data-ttu-id="29840-109">O método `Parse` lança uma exceção se a operação falhar, enquanto o método `TryParse` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="29840-109">The `Parse` method throws an exception if the operation fails, whereas the `TryParse` method returns `false`.</span></span>

## <a name="parsing-and-format-providers"></a><span data-ttu-id="29840-110">Provedores de análise e formato</span><span class="sxs-lookup"><span data-stu-id="29840-110">Parsing and format providers</span></span>

<span data-ttu-id="29840-111">Normalmente, as representações de cadeia de caracteres de valores numéricos diferem por cultura.</span><span class="sxs-lookup"><span data-stu-id="29840-111">Typically, the string representations of numeric values differ by culture.</span></span> <span data-ttu-id="29840-112">Elementos de separadores de cadeias de caracteres numéricas, como símbolos de moeda, separadores de grupo (ou milhares) e separadores decimais, variam por cultura.</span><span class="sxs-lookup"><span data-stu-id="29840-112">Elements of numeric strings such as currency symbols, group (or thousands) separators, and decimal separators all vary by culture.</span></span> <span data-ttu-id="29840-113">Os métodos de análise usam, implícita ou explicitamente, um provedor de formato que reconhece essas variações específicas da cultura.</span><span class="sxs-lookup"><span data-stu-id="29840-113">Parsing methods either implicitly or explicitly use a format provider that recognizes these culture-specific variations.</span></span> <span data-ttu-id="29840-114">Se nenhum provedor de formato for especificado em uma chamada para o método `Parse` ou `TryParse`, será usado o provedor de formato associado com a cultura do thread atual (o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) retornado pela propriedade [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo)).</span><span class="sxs-lookup"><span data-stu-id="29840-114">If no format provider is specified in a call to the `Parse` or `TryParse` method, the format provider associated with the current thread culture (the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object returned by the [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) property) is used.</span></span> 

<span data-ttu-id="29840-115">Um provedor de formato é representado por uma implementação [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo).</span><span class="sxs-lookup"><span data-stu-id="29840-115">A format provider is represented by an [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementation.</span></span> <span data-ttu-id="29840-116">Essa interface tem um único membro, o método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)), cujo único parâmetro é um objeto [Type](xref:System.Type) que representa o tipo a ser formatado.</span><span class="sxs-lookup"><span data-stu-id="29840-116">This interface has a single member, the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method, whose single parameter is a [Type](xref:System.Type) object that represents the type to be formatted.</span></span> <span data-ttu-id="29840-117">Esse método retorna um objeto que fornece informações de formatação.</span><span class="sxs-lookup"><span data-stu-id="29840-117">This method returns the object that provides formatting information.</span></span> <span data-ttu-id="29840-118">O .NET dá suporte às duas implementações [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) a seguir para analisar cadeias de caracteres numéricas:</span><span class="sxs-lookup"><span data-stu-id="29840-118">.NET supports the following two [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) implementations for parsing numeric strings:</span></span>

* <span data-ttu-id="29840-119">Um objeto [CultureInfo](xref:System.Globalization.CultureInfo) cujo método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que fornece informações de formatação específicas da cultura.</span><span class="sxs-lookup"><span data-stu-id="29840-119">A [CultureInfo](xref:System.Globalization.CultureInfo) object whose [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information.</span></span>

* <span data-ttu-id="29840-120">Um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) cujo método [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retorna ele próprio.</span><span class="sxs-lookup"><span data-stu-id="29840-120">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object whose [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns itself.</span></span>

<span data-ttu-id="29840-121">O exemplo a seguir tenta converter cada cadeia de caracteres em uma matriz para um valor [Double](xref:System.Double).</span><span class="sxs-lookup"><span data-stu-id="29840-121">The following example tries to convert each string in an array to a [Double](xref:System.Double) value.</span></span> <span data-ttu-id="29840-122">Em primeiro lugar, tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura do inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="29840-122">It first tries to parse the string by using a format provider that reflects the conventions of the English (United States) culture.</span></span> <span data-ttu-id="29840-123">Se essa operação lançar uma [FormatException](xref:System.FormatException), tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura francês (França).</span><span class="sxs-lookup"><span data-stu-id="29840-123">If this operation throws a [FormatException](xref:System.FormatException), it tries to parse the string by using a format provider that reflects the conventions of the French (France) culture.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a><span data-ttu-id="29840-124">Análise e valores NumberStyles</span><span class="sxs-lookup"><span data-stu-id="29840-124">Parsing and NumberStyles values</span></span>

<span data-ttu-id="29840-125">Os elementos de estilo (como espaço em branco, separadores de grupo e separador decimal) que a operação de análise pode manipular são definidos por um valor de enumeração [NumberStyles](xref:System.Globalization.NumberStyles).</span><span class="sxs-lookup"><span data-stu-id="29840-125">The style elements (such as white space, group separators, and decimal separator) that the parse operation can handle are defined by a [NumberStyles](xref:System.Globalization.NumberStyles) enumeration value.</span></span> <span data-ttu-id="29840-126">Por padrão, as cadeias de caracteres que representam valores inteiros são analisadas usando o valor [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer), que permite apenas dígitos numéricos, espaço em branco à esquerda e à direita e um sinal à esquerda.</span><span class="sxs-lookup"><span data-stu-id="29840-126">By default, strings that represent integer values are parsed by using the [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) value, which permits only numeric digits, leading and trailing white space, and a leading sign.</span></span> <span data-ttu-id="29840-127">Cadeias de caracteres que representam valores de ponto flutuante são analisadas usando uma combinação dos valores [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) e [AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands); esse estilo de composição permite dígitos decimais junto com o espaço em branco à esquerda e à direita, um sinal à esquerda, um separador decimal, um separador de grupo e um expoente.</span><span class="sxs-lookup"><span data-stu-id="29840-127">Strings that represent floating-point values are parsed using a combination of the [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) values; this composite style permits decimal digits along with leading and trailing white space, a leading sign, a decimal separator, a group separator, and an exponent.</span></span> <span data-ttu-id="29840-128">Chamando uma sobrecarga do método `Parse` ou `TryParse` que inclui um parâmetro do tipo [NumberStyles](xref:System.Globalization.NumberStyles) e definindo um ou mais sinalizadores [NumberStyles](xref:System.Globalization.NumberStyles), é possível controlar os elementos de estilo que podem estar presentes na cadeia de caracteres para que a operação de análise seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="29840-128">By calling an overload of the `Parse` or `TryParse` method that includes a parameter of type [NumberStyles](xref:System.Globalization.NumberStyles) and setting one or more [NumberStyles](xref:System.Globalization.NumberStyles) flags, you can control the style elements that can be present in the string for the parse operation to succeed.</span></span> 

<span data-ttu-id="29840-129">Por exemplo, uma cadeia de caracteres que contém um separador de grupo não pode ser convertida em um valor [Int32](xref:System.Int32) usando o método [Int32.Parse(String)](xref:System.Int32.Parse(System.String)).</span><span class="sxs-lookup"><span data-stu-id="29840-129">For example, a string that contains a group separator cannot be converted to an [Int32](xref:System.Int32) value by using the [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) method.</span></span> <span data-ttu-id="29840-130">No entanto, a conversão é bem-sucedida se você usar o sinalizador [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="29840-130">However, the conversion succeeds if you use the [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) flag, as the following example illustrates.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> <span data-ttu-id="29840-131">**Aviso**</span><span class="sxs-lookup"><span data-stu-id="29840-131">**Warning**</span></span>
>
> <span data-ttu-id="29840-132">A operação de análise sempre usa as convenções de formatação de uma determinada cultura.</span><span class="sxs-lookup"><span data-stu-id="29840-132">The parse operation always uses the formatting conventions of a particular culture.</span></span> <span data-ttu-id="29840-133">Se você não especificar uma cultura passando um objeto [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a cultura associada com o thread atual será usada.</span><span class="sxs-lookup"><span data-stu-id="29840-133">If you do not specify a culture by passing a [CultureInfo](xref:System.Globalization.CultureInfo) or [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object, the culture associated with the current thread is used.</span></span>
 
<span data-ttu-id="29840-134">A tabela a seguir lista os membros da enumeração [NumberStyles](xref:System.Globalization.NumberStyles) e descreve o efeito que eles têm sobre a operação de análise.</span><span class="sxs-lookup"><span data-stu-id="29840-134">The following table lists the members of the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration and describes the effect that they have on the parsing operation.</span></span>

<span data-ttu-id="29840-135">Valor NumberStyles</span><span class="sxs-lookup"><span data-stu-id="29840-135">NumberStyles value</span></span> | <span data-ttu-id="29840-136">Efeito sobre a cadeia de caracteres a ser analisada</span><span class="sxs-lookup"><span data-stu-id="29840-136">Effect on the string to be parsed</span></span>
------------------ | --------------------------------- 
[<span data-ttu-id="29840-137">NumberStyles.None</span><span class="sxs-lookup"><span data-stu-id="29840-137">NumberStyles.None</span></span>](xref:System.Globalization.NumberStyles.None) | <span data-ttu-id="29840-138">São permitidos apenas dígitos numéricos.</span><span class="sxs-lookup"><span data-stu-id="29840-138">Only numeric digits are permitted.</span></span>
[<span data-ttu-id="29840-139">NumberStyles.AllowDecimalPoint</span><span class="sxs-lookup"><span data-stu-id="29840-139">NumberStyles.AllowDecimalPoint</span></span>](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | <span data-ttu-id="29840-140">O separador decimal e dígitos fracionários são permitidos.</span><span class="sxs-lookup"><span data-stu-id="29840-140">The decimal separator and fractional digits are permitted.</span></span> <span data-ttu-id="29840-141">Para valores inteiros, apenas zero é permitido como um dígito fracionário.</span><span class="sxs-lookup"><span data-stu-id="29840-141">For integer values, only zero is permitted as a fractional digit.</span></span> <span data-ttu-id="29840-142">Os separadores decimais são determinados pela propriedade [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) ou [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator).</span><span class="sxs-lookup"><span data-stu-id="29840-142">Valid decimal separators are determined by the [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) or [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property.</span></span>
[<span data-ttu-id="29840-143">NumberStyles.AllowExponent</span><span class="sxs-lookup"><span data-stu-id="29840-143">NumberStyles.AllowExponent</span></span>](xref:System.Globalization.NumberStyles.AllowExponent) | <span data-ttu-id="29840-144">O caractere “e” ou “E” pode ser usado para indicar notação exponencial.</span><span class="sxs-lookup"><span data-stu-id="29840-144">The "e" or "E" character can be used to indicate exponential notation.</span></span>
[<span data-ttu-id="29840-145">NumberStyles.AllowLeadingWhite</span><span class="sxs-lookup"><span data-stu-id="29840-145">NumberStyles.AllowLeadingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | <span data-ttu-id="29840-146">É permitido um espaço em branco à esquerda.</span><span class="sxs-lookup"><span data-stu-id="29840-146">Leading white space is permitted.</span></span>
[<span data-ttu-id="29840-147">NumberStyles.AllowTrailingWhite</span><span class="sxs-lookup"><span data-stu-id="29840-147">NumberStyles.AllowTrailingWhite</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | <span data-ttu-id="29840-148">É permitido um espaço em branco à direita.</span><span class="sxs-lookup"><span data-stu-id="29840-148">Trailing white space is permitted.</span></span>
[<span data-ttu-id="29840-149">NumberStyles.AllowLeadingSign</span><span class="sxs-lookup"><span data-stu-id="29840-149">NumberStyles.AllowLeadingSign</span></span>](xref:System.Globalization.NumberStyles.AllowLeadingSign) | <span data-ttu-id="29840-150">Um sinal positivo ou negativo pode anteceder dígitos numéricos.</span><span class="sxs-lookup"><span data-stu-id="29840-150">A positive or negative sign can precede numeric digits.</span></span>
[<span data-ttu-id="29840-151">NumberStyles.AllowTrailingSign</span><span class="sxs-lookup"><span data-stu-id="29840-151">NumberStyles.AllowTrailingSign</span></span>](xref:System.Globalization.NumberStyles.AllowTrailingSign) | <span data-ttu-id="29840-152">Um sinal positivo ou negativo pode seguir dígitos numéricos.</span><span class="sxs-lookup"><span data-stu-id="29840-152">A positive or negative sign can follow numeric digits.</span></span>
[<span data-ttu-id="29840-153">NumberStyles.AllowParentheses</span><span class="sxs-lookup"><span data-stu-id="29840-153">NumberStyles.AllowParentheses</span></span>](xref:System.Globalization.NumberStyles.AllowParentheses) | <span data-ttu-id="29840-154">Parênteses podem ser usados para indicar valores negativos.</span><span class="sxs-lookup"><span data-stu-id="29840-154">Parentheses can be used to indicate negative values.</span></span>
[<span data-ttu-id="29840-155">NumberStyles.AllowThousands</span><span class="sxs-lookup"><span data-stu-id="29840-155">NumberStyles.AllowThousands</span></span>](xref:System.Globalization.NumberStyles.AllowThousands) | <span data-ttu-id="29840-156">É permitido um separador de grupo.</span><span class="sxs-lookup"><span data-stu-id="29840-156">The group separator is permitted.</span></span> <span data-ttu-id="29840-157">O caractere separador de grupo é determinado pela propriedade [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) ou [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator).</span><span class="sxs-lookup"><span data-stu-id="29840-157">The group separator character is determined by the [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) or [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property.</span></span>
[<span data-ttu-id="29840-158">NumberStyles.AllowCurrencySymbol</span><span class="sxs-lookup"><span data-stu-id="29840-158">NumberStyles.AllowCurrencySymbol</span></span>](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | <span data-ttu-id="29840-159">É permitido o símbolo de moeda.</span><span class="sxs-lookup"><span data-stu-id="29840-159">The currency symbol is permitted.</span></span> <span data-ttu-id="29840-160">O símbolo de moeda é definido pela propriedade [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol).</span><span class="sxs-lookup"><span data-stu-id="29840-160">The currency symbol is defined by the [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property.</span></span>
[<span data-ttu-id="29840-161">NumberStyles.AllowHexSpecifier</span><span class="sxs-lookup"><span data-stu-id="29840-161">NumberStyles.AllowHexSpecifier</span></span>](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | <span data-ttu-id="29840-162">A cadeia de caracteres a ser analisada é interpretada como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="29840-162">The string to be parsed is interpreted as a hexadecimal number.</span></span> <span data-ttu-id="29840-163">Pode incluir os dígitos decimais 0-9, A-F e a-f.</span><span class="sxs-lookup"><span data-stu-id="29840-163">It can include the hexadecimal digits 0-9, A-F, and a-f.</span></span> <span data-ttu-id="29840-164">Este sinalizador pode ser usado apenas para analisar valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="29840-164">This flag can be used only to parse integer values.</span></span>
 
<span data-ttu-id="29840-165">Além disso, a enumeração [NumberStyles](xref:System.Globalization.NumberStyles) oferece os seguintes estilos de composição, que incluem vários sinalizadores [NumberStyles](xref:System.Globalization.NumberStyles).</span><span class="sxs-lookup"><span data-stu-id="29840-165">In addition, the [NumberStyles](xref:System.Globalization.NumberStyles) enumeration provides the following composite styles, which include multiple [NumberStyles](xref:System.Globalization.NumberStyles) flags.</span></span> 

<span data-ttu-id="29840-166">Valor NumberStyles de composição</span><span class="sxs-lookup"><span data-stu-id="29840-166">Composite NumberStyles value</span></span> | <span data-ttu-id="29840-167">Inclui membros</span><span class="sxs-lookup"><span data-stu-id="29840-167">Includes members</span></span>
---------------------------- | ---------------- 
[<span data-ttu-id="29840-168">NumberStyles.Integer</span><span class="sxs-lookup"><span data-stu-id="29840-168">NumberStyles.Integer</span></span>](xref:System.Globalization.NumberStyles.Integer) | <span data-ttu-id="29840-169">Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) e [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign).</span><span class="sxs-lookup"><span data-stu-id="29840-169">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) styles.</span></span> <span data-ttu-id="29840-170">É o estilo padrão usado para analisar valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="29840-170">This is the default style used to parse integer values.</span></span>
[<span data-ttu-id="29840-171">NumberStyles.Number</span><span class="sxs-lookup"><span data-stu-id="29840-171">NumberStyles.Number</span></span>](xref:System.Globalization.NumberStyles.Number) | <span data-ttu-id="29840-172">Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) e [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands).</span><span class="sxs-lookup"><span data-stu-id="29840-172">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) styles.</span></span>
[<span data-ttu-id="29840-173">NumberStyles.Float</span><span class="sxs-lookup"><span data-stu-id="29840-173">NumberStyles.Float</span></span>](xref:System.Globalization.NumberStyles.Float) | <span data-ttu-id="29840-174">Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) e [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent).</span><span class="sxs-lookup"><span data-stu-id="29840-174">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint), and [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) styles.</span></span>
[<span data-ttu-id="29840-175">NumberStyles.Currency</span><span class="sxs-lookup"><span data-stu-id="29840-175">NumberStyles.Currency</span></span>](xref:System.Globalization.NumberStyles.Currency) | <span data-ttu-id="29840-176">Inclui todos os estilos, exceto [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) e [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="29840-176">Includes all styles except [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="29840-177">NumberStyles.Any</span><span class="sxs-lookup"><span data-stu-id="29840-177">NumberStyles.Any</span></span>](xref:System.Globalization.NumberStyles.Any) | <span data-ttu-id="29840-178">Inclui todos os estilos, exceto [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="29840-178">Includes all styles except [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span></span>
[<span data-ttu-id="29840-179">NumberStyles.HexNumber</span><span class="sxs-lookup"><span data-stu-id="29840-179">NumberStyles.HexNumber</span></span>](xref:System.Globalization.NumberStyles.HexNumber) | <span data-ttu-id="29840-180">Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) e [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).</span><span class="sxs-lookup"><span data-stu-id="29840-180">Includes the [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), and [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) styles.</span></span>
 
## <a name="parsing-and-unicode-digits"></a><span data-ttu-id="29840-181">Análise e dígitos Unicode</span><span class="sxs-lookup"><span data-stu-id="29840-181">Parsing and Unicode digits</span></span>

<span data-ttu-id="29840-182">O padrão Unicode define pontos de código para dígitos em diversos sistemas de escrita.</span><span class="sxs-lookup"><span data-stu-id="29840-182">The Unicode standard defines code points for digits in various writing systems.</span></span> <span data-ttu-id="29840-183">Por exemplo, os pontos de código de U+0030 a U+0039 representam os dígitos latinos básicos 0 a 9; os pontos de código de U+09E6 a U+09EF representam os dígitos bengali de 0 a 9; e os pontos de código de U+FF10 a U+FF19 representam os dígitos de largura inteira 0 a 9.</span><span class="sxs-lookup"><span data-stu-id="29840-183">For example, code points from U+0030 to U+0039 represent the basic Latin digits 0 through 9, code points from U+09E6 to U+09EF represent the Bangla digits 0 through 9, and code points from U+FF10 to U+FF19 represent the Fullwidth digits 0 through 9.</span></span> <span data-ttu-id="29840-184">No entanto, os únicos dígitos numéricos reconhecidos pelos métodos de análise são os dígitos latinos básicos 0-9 com os pontos de código de U+0030 a U+0039.</span><span class="sxs-lookup"><span data-stu-id="29840-184">However, the only numeric digits recognized by parsing methods are the basic Latin digits 0-9 with code points from U+0030 to U+0039.</span></span> <span data-ttu-id="29840-185">Se um método de análise numérica passa uma cadeia de caracteres que contém outros dígitos, o método lança uma [FormatException](xref:System.FormatException).</span><span class="sxs-lookup"><span data-stu-id="29840-185">If a numeric parsing method is passed a string that contains any other digits, the method throws a [FormatException](xref:System.FormatException).</span></span>

<span data-ttu-id="29840-186">O exemplo a seguir usa o método [Int32.Parse](xref:System.Int32.Parse(System.String)) para analisar cadeias de caracteres que consistem em dígitos em diferentes sistemas de escrita.</span><span class="sxs-lookup"><span data-stu-id="29840-186">The following example uses the [Int32.Parse](xref:System.Int32.Parse(System.String)) method to parse strings that consist of digits in different writing systems.</span></span> <span data-ttu-id="29840-187">Como mostra a saída do exemplo, a tentativa de analisar os dígitos latinos básicos é bem-sucedida, mas a tentativa de analisar os dígitos de largura inteira, indo-arábicos e bengali.</span><span class="sxs-lookup"><span data-stu-id="29840-187">As the output from the example shows, the attempt to parse the basic Latin digits succeeds, but the attempt to parse the Fullwidth, Arabic-Indic, and Bangla digits fails.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a><span data-ttu-id="29840-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29840-188">See also</span></span>

[<span data-ttu-id="29840-189">System.Globalization.NumberStyles</span><span class="sxs-lookup"><span data-stu-id="29840-189">System.Globalization.NumberStyles</span></span>](xref:System.Globalization.NumberStyles)

[<span data-ttu-id="29840-190">Analisando cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="29840-190">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="29840-191">Tipos de formatação no .NET</span><span class="sxs-lookup"><span data-stu-id="29840-191">Formatting types in .NET</span></span>](formatting-types.md)


