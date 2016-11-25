---
title: "Analisando cadeias de caracteres numéricas no .NET"
description: "Analisando cadeias de caracteres numéricas no .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 209d24d32eb3b235ff2fde2ef11ffd0ee4e930cf

---

# <a name="parsing-numeric-strings-in-net"></a>Analisando cadeias de caracteres numéricas no .NET

Todos os tipos numéricos têm dois métodos de análise estáticos, `Parse` e `TryParse`, que podem ser usados para converter a representação de cadeia de caracteres de um número em um tipo numérico. Esses métodos permitem analisar cadeias de caracteres que foram produzidas usando as cadeias de caracteres de formato documentadas em [Cadeias de caracteres de formato numérico padrão](standard-numeric.md) e [Cadeias de caracteres de formato numérico personalizadas](custom-numeric.md). Por padrão, os métodos `Parse` e `TryParse` conseguem converter cadeias de caracteres que contêm dígitos decimais integrais somente em valores inteiros. Podem converter cadeias de caracteres que contêm dígitos decimais integrais e dígitos fracionários, separadores de grupo e um separador decimal em valores de ponto flutuante. O método `Parse` lança uma exceção se a operação falhar, enquanto o método `TryParse` retorna `false`.

## <a name="parsing-and-format-providers"></a>Provedores de análise e formato

Normalmente, as representações de cadeia de caracteres de valores numéricos diferem por cultura. Elementos de separadores de cadeias de caracteres numéricas, como símbolos de moeda, separadores de grupo (ou milhares) e separadores decimais, variam por cultura. Os métodos de análise usam, implícita ou explicitamente, um provedor de formato que reconhece essas variações específicas da cultura. Se nenhum provedor de formato for especificado em uma chamada para o método `Parse` ou `TryParse`, será usado o provedor de formato associado com a cultura do thread atual (o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) retornado pela propriedade [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo)). 

Um provedor de formato é representado por uma implementação [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo). Essa interface tem um único membro, o método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)), cujo único parâmetro é um objeto [Type](xref:System.Type) que representa o tipo a ser formatado. Esse método retorna um objeto que fornece informações de formatação. O .NET dá suporte às duas implementações [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) a seguir para analisar cadeias de caracteres numéricas:

* Um objeto [CultureInfo](xref:System.Globalization.CultureInfo) cujo método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que fornece informações de formatação específicas da cultura.

* Um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) cujo método [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retorna ele próprio.

O exemplo a seguir tenta converter cada cadeia de caracteres em uma matriz para um valor [Double](xref:System.Double). Em primeiro lugar, tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura do inglês (Estados Unidos). Se essa operação lançar uma [FormatException](xref:System.FormatException), tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura francês (França).

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

## <a name="parsing-and-numberstyles-values"></a>Análise e valores NumberStyles

Os elementos de estilo (como espaço em branco, separadores de grupo e separador decimal) que a operação de análise pode manipular são definidos por um valor de enumeração [NumberStyles](xref:System.Globalization.NumberStyles). Por padrão, as cadeias de caracteres que representam valores inteiros são analisadas usando o valor [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer), que permite apenas dígitos numéricos, espaço em branco à esquerda e à direita e um sinal à esquerda. Cadeias de caracteres que representam valores de ponto flutuante são analisadas usando uma combinação dos valores [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) e [AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands); esse estilo de composição permite dígitos decimais junto com o espaço em branco à esquerda e à direita, um sinal à esquerda, um separador decimal, um separador de grupo e um expoente. Chamando uma sobrecarga do método `Parse` ou `TryParse` que inclui um parâmetro do tipo [NumberStyles](xref:System.Globalization.NumberStyles) e definindo um ou mais sinalizadores [NumberStyles](xref:System.Globalization.NumberStyles), é possível controlar os elementos de estilo que podem estar presentes na cadeia de caracteres para que a operação de análise seja bem-sucedida. 

Por exemplo, uma cadeia de caracteres que contém um separador de grupo não pode ser convertida em um valor [Int32](xref:System.Int32) usando o método [Int32.Parse(String)](xref:System.Int32.Parse(System.String)). No entanto, a conversão é bem-sucedida se você usar o sinalizador [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands), como mostra o exemplo a seguir.

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

> **Aviso**
>
> A operação de análise sempre usa as convenções de formatação de uma determinada cultura. Se você não especificar uma cultura passando um objeto [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a cultura associada com o thread atual será usada.
 
A tabela a seguir lista os membros da enumeração [NumberStyles](xref:System.Globalization.NumberStyles) e descreve o efeito que eles têm sobre a operação de análise.

Valor NumberStyles | Efeito sobre a cadeia de caracteres a ser analisada
------------------ | --------------------------------- 
[NumberStyles.None](xref:System.Globalization.NumberStyles.None) | São permitidos apenas dígitos numéricos.
[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | O separador decimal e dígitos fracionários são permitidos. Para valores inteiros, apenas zero é permitido como um dígito fracionário. Os separadores decimais são determinados pela propriedade [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) ou [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator).
[NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) | O caractere “e” ou “E” pode ser usado para indicar notação exponencial.
[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | É permitido um espaço em branco à esquerda.
[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | É permitido um espaço em branco à direita.
[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) | Um sinal positivo ou negativo pode anteceder dígitos numéricos.
[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign) | Um sinal positivo ou negativo pode seguir dígitos numéricos.
[NumberStyles.AllowParentheses](xref:System.Globalization.NumberStyles.AllowParentheses) | Parênteses podem ser usados para indicar valores negativos.
[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) | É permitido um separador de grupo. O caractere separador de grupo é determinado pela propriedade [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) ou [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator).
[NumberStyles.AllowCurrencySymbol](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | É permitido o símbolo de moeda. O símbolo de moeda é definido pela propriedade [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol).
[NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | A cadeia de caracteres a ser analisada é interpretada como um número hexadecimal. Pode incluir os dígitos decimais 0-9, A-F e a-f. Este sinalizador pode ser usado apenas para analisar valores inteiros.
 
Além disso, a enumeração [NumberStyles](xref:System.Globalization.NumberStyles) oferece os seguintes estilos de composição, que incluem vários sinalizadores [NumberStyles](xref:System.Globalization.NumberStyles). 

Valor NumberStyles de composição | Inclui membros
---------------------------- | ---------------- 
[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) | Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) e [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign). É o estilo padrão usado para analisar valores inteiros.
[NumberStyles.Number](xref:System.Globalization.NumberStyles.Number) | Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) e [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands).
[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) | Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) e [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent).
[NumberStyles.Currency](xref:System.Globalization.NumberStyles.Currency) | Inclui todos os estilos, exceto [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) e [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
[NumberStyles.Any](xref:System.Globalization.NumberStyles.Any) | Inclui todos os estilos, exceto [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
[NumberStyles.HexNumber](xref:System.Globalization.NumberStyles.HexNumber) | Inclui os estilos [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) e [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
 
## <a name="parsing-and-unicode-digits"></a>Análise e dígitos Unicode

O padrão Unicode define pontos de código para dígitos em diversos sistemas de escrita. Por exemplo, os pontos de código de U+0030 a U+0039 representam os dígitos latinos básicos 0 a 9; os pontos de código de U+09E6 a U+09EF representam os dígitos bengali de 0 a 9; e os pontos de código de U+FF10 a U+FF19 representam os dígitos de largura inteira 0 a 9. No entanto, os únicos dígitos numéricos reconhecidos pelos métodos de análise são os dígitos latinos básicos 0-9 com os pontos de código de U+0030 a U+0039. Se um método de análise numérica passa uma cadeia de caracteres que contém outros dígitos, o método lança uma [FormatException](xref:System.FormatException).

O exemplo a seguir usa o método [Int32.Parse](xref:System.Int32.Parse(System.String)) para analisar cadeias de caracteres que consistem em dígitos em diferentes sistemas de escrita. Como mostra a saída do exemplo, a tentativa de analisar os dígitos latinos básicos é bem-sucedida, mas a tentativa de analisar os dígitos de largura inteira, indo-arábicos e bengali.

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

## <a name="see-also"></a>Consulte também

[System.Globalization.NumberStyles](xref:System.Globalization.NumberStyles)

[Analisando cadeias de caracteres no .NET](parsing-strings.md)

[Tipos de formatação no .NET](formatting-types.md)




<!--HONumber=Nov16_HO3-->


