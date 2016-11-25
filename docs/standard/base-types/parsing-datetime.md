---
title: Analisando cadeias de caracteres de data e hora no .NET
description: Analisando cadeias de caracteres de data e hora no .NET
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8b0c5a64db50163d196017ebb410e454eb5a6af9

---

# <a name="parsing-date-and-time-strings-in-net"></a>Analisando cadeias de caracteres de data e hora no .NET

Os métodos de análise convertem a representação em cadeia de caracteres de data e hora em um objeto [DateTime](xref:System.DateTime) equivalente. Os métodos [Parse](xref:System.DateTime.Parse(System.String)) e [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) convertem qualquer uma das várias representações comuns de data e hora. Os métodos [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) e [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) convertem uma representação em cadeia de caracteres que cumpra o padrão especificado por uma cadeia de caracteres de formato de data e hora. (Consulte os tópicos sobre [cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) e [cadeias de caracteres de formato de data e hora personalizadas](custom-datetime.md).) 

A análise é influenciada pelas propriedades de um provedor de formato que fornece informações como as cadeias de caracteres usadas para separadores de data e hora, além dos nomes dos meses, dias e eras. O provedor de formato é o objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual, que é fornecido implicitamente pela cultura de thread atual ou explicitamente pelo parâmetro [IFormatProvider](xref:System.IFormatProvider) de um método de análise. Para o parâmetro [IFormatProvider](xref:System.IFormatProvider), especifique um objeto [CultureInfo](xref:System.Globalization.CultureInfo), que representa uma cultura ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). 

A representação de cadeia de caracteres de uma data a ser analisada deve incluir o mês e, pelo menos, um dia ou ano. A representação de cadeia de caracteres de um horário deve incluir a hora e, pelo menos, os minutos ou o designador AM/PM. No entanto, análise fornece valores padrão para componentes omitidos, se possível. O padrão de data ausente é a data atual; o padrão de ano ausente é o ano atual; o padrão de dia do mês ausente é o primeiro dia do mês; o padrão de horário ausente é meia-noite. 

Se a representação de cadeia de caracteres especifica somente um horário, a análise retorna um objeto [DateTime](xref:System.DateTime) com as propriedades [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month) e [Day](xref:System.DateTime.Day) definidas para os valores correspondentes da propriedade [Today](xref:System.DateTime.Today). No entanto, se a constante [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) estiver especificada no método de análise, as propriedades resultantes de ano, mês e dia serão definidas com o valor 1.

Além de um componente de data e hora, a representação de cadeia de caracteres de data e hora pode incluir um deslocamento que indique a diferença de tempo em relação ao UTC (Tempo Universal Coordenado). Por exemplo, a cadeia de caracteres “2/14/2007 5:32:00 -7:00” define um horário sete horas antes do UTC. Se um deslocamento for omitido da representação de cadeia de caracteres de horário, a análise retorna um objeto [DateTime](xref:System.DateTime) com a propriedade [Kind](xref:System.DateTime.Kind) definida como [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified). Se um deslocamento for especificado, a análise retorna um objeto [DateTime](xref:System.DateTime) com a propriedade [Kind](xref:System.DateTime.Kind) definida como [Local](xref:System.DateTimeKind.Local) e seu valor ajustado de acordo com o fuso horário local do seu computador. É possível modificar esse comportamento usando uma constante [DateTimeStyles](xref:System.Globalization.DateTimeStyles) com o método de análise.

O provedor de formato também é usado para interpretar uma data numérica ambígua. Por exemplo, não está claro quais componentes da data representada pela cadeia de caracteres “02/03/04” são o mês, o dia e o ano. Nesse caso, os componentes são interpretados de acordo com a ordem dos formatos de data semelhantes no provedor de formato. 

## <a name="parse"></a>Parse

O exemplo de código a seguir ilustra o uso do método `Parse` para converter uma cadeia de caracteres em um `DateTime`. Este exemplo usa a cultura associada com o thread atual para realizar a análise. Se o [CultureInfo](xref:System.Globalization.CultureInfo) associado com a cultura atual não conseguir analisar a cadeia de caracteres de entrada, será lançada uma [FormatException](xref:System.FormatException).

```csharp
string MyString = "Jan 1, 2009";
DateTime MyDateTime = DateTime.Parse(MyString);
Console.WriteLine(MyDateTime);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```

```vb
Dim MyString As String = "Jan 1, 2009"
Dim MyDateTime As DateTime = DateTime.Parse(MyString)
Console.WriteLine(MyDateTime)
' Displays the following output on a system whose culture is en-US:
'       1/1/2009 12:00:00 AM
```

Também é possível especificar um `CultureInfo` definido como uma das culturas definidas por tal objeto ou especificar um dos objetos [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) padrão retornados pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). O exemplo de código a seguir usa um provedor de formato para analisar uma cadeia de caracteres em alemão em um `DateTime`. Um `CultureInfo` que representa a cultura de-DE é definido e passado com a cadeia de caracteres sendo analisada para assegurar uma análise bem-sucedida dessa cadeia de caracteres específica. Isso impede qualquer configuração que está no `CurrentCulture` do `CurrentThread`.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output:
//       6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

No entanto, apesar de ser possível usar sobrecargas do método [Parse](xref:System.DateTime.Parse(System.String)) para especificar os provedores de formato personalizado, o método não dá suporte ao uso de provedores de formato não padrão. Para analisar data e hora expressadas em um formato não padrão, use o método [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)).

O exemplo de código a seguir usa a enumeração [DateTimeStyles](xref:System.Globalization.DateTimeStyles) para especificar que as informações atuais de data e hora não devem ser adicionadas ao `DateTime` para campos que a cadeia de caracteres não define.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo, 
                                           DateTimeStyles.NoCurrentDateDefault);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output if the current culture is en-US:
//      6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

## <a name="parseexact"></a>ParseExact

O método [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) converte uma cadeia de caracteres que cumpre um padrão de cadeia de caracteres especificado para um objeto `DateTime`. Quando uma cadeia de caracteres que não é da forma especificada é passada para esse método, é lançada uma [FormatException](xref:System.FormatException). Você pode especificar um dos especificadores de formato de data e hora padrão ou uma combinação limitada dos especificadores de formato de data e hora personalizados. Usando os especificadores de formato personalizados, é possível construir uma cadeia de caracteres de reconhecimento personalizada. Para ver uma explicação dos especificadores, consulte os tópicos [cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) e [cadeias de caracteres de formato de data e hora personalizadas](custom-datetime.md). 

Cada sobrecarga do método [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) também tem um parâmetro [IFormatProvider](xref:System.IFormatProvider) que normalmente oferece informações específicas da cultura sobre a formatação da cadeia de caracteres. Normalmente, esse objeto [IFormatProvider](xref:System.IFormatProvider) é um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa uma cultura padrão ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que é retornado pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). Entretanto, ao contrário das outras funções de análise de data e hora, esse método também dá suporte a um [IFormatProvider](xref:System.IFormatProvider) que define um formato de data e hora não padrão. 

No exemplo de código a seguir, o método `ParseExact` recebe um objeto de cadeia de caracteres para analisar, seguido por um especificador de formato, seguido por um objeto `CultureInfo`. Esse método `ParseExact` só consegue analisar cadeias de caracteres que exibem o padrão de data por extenso na cultura en-US.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("en-US");
      string[] MyString = {" Friday, April 10, 2009", "Friday, April 10, 2009"};
      foreach (string dateString in MyString)
      {
         try {
            DateTime MyDateTime = DateTime.ParseExact(dateString, "D", MyCultureInfo);
            Console.WriteLine(MyDateTime);
         }
         catch (FormatException) {
            Console.WriteLine("Unable to parse '{0}'", dateString);
         }
      }
   }
}
// The example displays the following output:
//       Unable to parse ' Friday, April 10, 2009'
//       4/10/2009 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("en-US")
      Dim MyString() As String = {" Friday, April 10, 2009", "Friday, April 10, 2009"}
      For Each dateString As String In MyString
         Try
            Dim MyDateTime As DateTime = DateTime.ParseExact(dateString, "D", _
                                                             MyCultureInfo)
            Console.WriteLine(MyDateTime)
         Catch e As FormatException
            Console.WriteLine("Unable to parse '{0}'", dateString)
         End Try
      Next
   End Sub
End Module
' The example displays the following output:
'       Unable to parse ' Friday, April 10, 2009'
'       4/10/2009 12:00:00 AM
```

## <a name="see-also"></a>Consulte também

[Analisando cadeias de caracteres no .NET](parsing-strings.md)

[Tipos de formatação no .NET](formatting-types.md)

[Conversão de tipo no .NET](type-conversion.md)




<!--HONumber=Nov16_HO3-->


