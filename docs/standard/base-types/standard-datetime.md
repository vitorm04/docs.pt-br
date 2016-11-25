---
title: "Cadeias de caracteres de formato de data e hora padrão"
description: "Cadeias de caracteres de formato de data e hora padrão"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: be239871-10cc-4949-b548-200bb260630a
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 56da9671a0849b0f0a94d8881cdc28e70bcf8549

---

# <a name="standard-date-and-time-format-strings"></a>Cadeias de caracteres de formato de data e hora padrão

Uma cadeia de caracteres de formato de data e hora padrão usa um especificador de formato único para definir a representação do texto de um valor de data e hora. Qualquer cadeia de caracteres de formato de data e hora que contém mais de um caractere, incluindo espaço em branco, é interpretada como uma cadeia de caracteres de formato de data e hora personalizado. Para obter mais informações, consulte [Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md). Uma cadeia de caracteres de formato padrão ou personalizado pode ser usada de duas maneiras:

* Para definir a cadeia de caracteres que resulta de uma operação de formatação.

* Para definir a representação de texto de um valor de data e hora que possa ser convertido em valor de [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) por uma operação de análise.

Cadeias de caracteres de formato de data e hora padrão podem ser usadas com valores [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset). 

A tabela a seguir descreve os especificadores de formato de data e hora padrão. Salvo indicação em contrário, um determinado especificador de formato de data e hora padrão produz uma representação de cadeia de caracteres idêntica independente de ela ser usada com um valor [DateTime](xref:System.DateTime) ou um valor [DateTimeOffset](xref:System.DateTimeOffset). Consulte a seção [Observações](#notes) para obter informações adicionais sobre como usar as cadeias de caracteres de formato de data e hora padrão.

Especificador de formato | Descrição | Exemplos
---------------- | ----------- | --------
"d" | Padrão de data abreviada. | `2009-06-15T13:45:30 -> 6/15/2009 (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)`; `2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)`
"D" | Padrão de data completa. | `2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)`; `2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)`; `2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)`
"f" | Padrão de data/hora completa (hora abreviada). | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)`
"F" | Padrão de data/hora completa (hora completa). | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)`
"g" | Padrão geral de data/hora (hora abreviada). | `2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)`
"G" | Padrão geral de data/hora (hora completa). | `2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)`
"M", "m' | Padrão de mês/dia. | `2009-06-15T13:45:30 -> June 15 (en-US)`; `2009-06-15T13:45:30 -> 15. juni (da-DK)`; `2009-06-15T13:45:30 -> 15 Juni (id-ID)`
"O", "o" | Padrão de data/hora de ida e volta. | Valores [DateTime](xref:System.DateTime): `2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00`; `2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z`; `2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000`. Valores [DateTimeOffset](xref:System.DateTimeOffset): `2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00`
"R", "r" | Padrão RFC1123. | `2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT`
"s" | Padrão de data/hora classificável. | `2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30`; `2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30`
"t" | Padrão de hora abreviada. | `2009-06-15T13:45:30 -> 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45 م (ar-EG)` 
"T" | Padrão de hora completa. | `2009-06-15T13:45:30 -> 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45:30 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)`
"u" | Padrão classificável universal de data/hora. | Com um valor [DateTime](xref:System.DateTime): `2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z`. Com um valor [DateTimeOffset](xref:System.DateTimeOffset): `2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z`
"U" | Padrão universal de data/hora completa. | `2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)`
"Y", "y" | Padrão ano mês. | `2009-06-15T13:45:30 -> June, 2009 (en-US)`; `2009-06-15T13:45:30 -> juni 2009 (da-DK)`; `2009-06-15T13:45:30 -> Juni 2009 (id-ID)`
Qualquer outro caractere único | Especificador desconhecido. | Gera um tempo de execução [FormatException](xref:System.FormatException).

## <a name="how-standard-format-strings-work"></a>Como funcionam as cadeias de caracteres de formato padrão

Em uma operação de formatação, uma cadeia de formato padrão é simplesmente um alias para uma cadeia de caracteres de formato personalizado. A vantagem de usar um alias para se referir a uma cadeia de caracteres de formato personalizado é que, embora o alias permaneça invariável, a cadeia de caracteres de formato personalizado em si pode variar. Isso é importante porque as representações de cadeia de caracteres de valores de data e hora normalmente variam de acordo com a cultura. Por exemplo, a cadeia de caracteres de formato padrão "d" indica que um valor de data e hora deve ser exibido usando um formato de data abreviada. Para a cultura invariável, esse padrão é "MM/dd/aaaa". Para a cultura fr-FR, ele é " dd/MM/aaaa ". Para a cultura ja-JP, ele é " aaaa/MM/dd ".

Se uma cadeia de caracteres de formato padrão em uma operação de formatação aponta para uma cadeia de caracteres de formato personalizado de uma cultura, seu aplicativo pode definir a cultura específica cujas cadeias de caracteres de formato personalizado são usadas de uma dessas maneiras:

* Você pode usar a cultura padrão (ou atual). O exemplo a seguir exibe uma data usando o formato de data abreviada da cultura atual. Nesse caso, a cultura atual é en-US. 

  ```csharp
  // Display using current (en-us) culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  Console.WriteLine(thisDate.ToString("d"));           // Displays 3/15/2008
  ```

  ```vb
  ' Display using current (en-us) culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Console.WriteLine(thisDate.ToString("d"))     ' Displays 3/15/2008
  ```
  
* Você pode passar um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa a cultura cuja formatação deve ser usada para um método que possua um parâmetro [IFormatProvider](xref:System.IFormatProvider). O exemplo a seguir exibe uma data usando o formato de data abreviada da cultura pt-BR.
  
  ```csharp
  // Display using pt-BR culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  CultureInfo culture = new CultureInfo("pt-BR");      
  Console.WriteLine(thisDate.ToString("d", culture));  // Displays 15/3/2008
  ```

  ```vb
  ' Display using pt-BR culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Dim culture As New CultureInfo("pt-BR")      
  Console.WriteLine(thisDate.ToString("d", culture))   ' Displays 15/3/2008
  ```
  
* Você pode passar um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que fornece informações de formatação para um método que tem um parâmetro [IFormatProvider](xref:System.IFormatProvider). O exemplo a seguir exibe uma data usando o formato de data abreviada de um objeto DateTimeFormatInfo para a cultura hr-HR.  

  ```csharp
  // Display using date format information from hr-HR culture
  DateTime thisDate = new DateTime(2008, 3, 15);
  DateTimeFormatInfo fmt = (new CultureInfo("hr-HR")).DateTimeFormat;
  Console.WriteLine(thisDate.ToString("d", fmt));      // Displays 15.3.2008
  ```

  ```vb
  ' Display using date format information from hr-HR culture
  Dim thisDate As Date = #03/15/2008#
  Dim fmt As DateTimeFormatInfo = (New CultureInfo("hr-HR")).DateTimeFormat
  Console.WriteLine(thisDate.ToString("d", fmt))   ' Displays 15.3.2008
  ```
  
Em alguns casos, a cadeia de caracteres de formato padrão funciona como uma abreviação conveniente de uma cadeia de caracteres de formato personalizado maior que é invariável. Quatro cadeias de caracteres de formato padrão se enquadram nesta categoria: "O" (ou "o"), "R" (ou "r"), "s" e "u". Estas cadeias de caracteres correspondem às cadeias de caracteres de formato personalizado definidas pela cultura invariável. Elas produzem representações de cadeias de caracteres de valores de data e hora que são feitos para ser idênticos entre culturas. A tabela a seguir fornece informações sobre essas quatro cadeias de caracteres de formato de data e hora padrão.

Cadeias de caracteres de formato padrão | Definidas pela propriedade DateTimeFormatInfo.InvariantInfo | Cadeia de caracteres de formato personalizado
---------------------- | ---------------------------------------------------- | --------------------
"O" ou "o" | Nenhum | yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz
"R" ou "r" | [RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
"s" | [SortableDateTime](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) | yyyy'-'MM'-'dd'T'HH':'mm':'ss
"u" | [UniversalSortableDateTime](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) | yyyy'-'MM'-'dd HH':'mm':'ss'Z'

As seções a seguir descrevem os especificadores de formato padrão para valores [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset).

## <a name="the-short-date-d-format-specifier"></a>Especificador de formato de data abreviada ("d")

O especificador de formato padrão "d" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) de uma cultura específica. Por exemplo, a cadeia de caracteres de formato personalizado retornada pela propriedade [ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) da cultura invariável é "MM/dd/aaaa ". 

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que controlam a formatação da cadeia de caracteres retornada.
O exemplo a seguir utiliza o especificador de formato "d" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008,4, 10);
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-NZ")));
// Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("de-DE")));
// Displays 10.04.2008 
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-NZ")))
' Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("de-DE")))
' Displays 10.04.2008 
```

## <a name="the-long-date-d-format-specifier"></a>Especificador de formato de data completa ("D")

O especificador de formato padrão "D" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) atual. Por exemplo, a cadeia de caracteres de formato personalizado para a cultura invariável é "dddd, dd MMMM aaaa".

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade | Descrição
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | Define o formato geral da cadeia de caracteres de resultado.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Define os nomes de dias localizados que podem aparecer na cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.

O exemplo a seguir utiliza o especificador de formato "D" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10);
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("pt-BR")));
// Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays jueves, 10 de abril de 2008
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("pt-BR")))
' Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays jueves, 10 de abril de 2008
```

## <a name="the-full-date-short-time-f-format-specifier"></a>Especificador de formato de data completa e hora abreviada ("f")

O especificador de formato padrão "f" representa uma combinação dos padrões de data completa ("D") e hora abreviada ("t"), separados por um espaço.

A cadeia de caracteres do resultado é afetada pelas informações de formatação de um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) específico. A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado, retornado pelas propriedades [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) e [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de algumas culturas, pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | Define o formato do componente de data da cadeia de caracteres de resultado.
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Define o formato do componente de hora da cadeia de caracteres de resultado.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Define os nomes de dias localizados que podem aparecer na cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "f" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30 
```

## <a name="the-full-date-long-time-f-format-specifier"></a>Especificador de formato de data completa e hora completa (“F”)

O especificador de formato padrão "F" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) atual. Por exemplo, a cadeia de caracteres de formato personalizado para a cultura invariável é "dddd, dd MMMM aaaa HH:mm:ss".

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado que é retornado pela propriedade [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) de algumas culturas pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | Define o formato geral da cadeia de caracteres de resultado.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Define os nomes de dias localizados que podem aparecer na cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "F" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30:00 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30:00 
```

## <a name="the-general-date-short-time-g-format-specifier"></a>Especificador de formato de data geral e hora abreviada (“g”)

O especificador de formato padrão "g" representa uma combinação dos padrões de data abreviada ("d") e hora abreviada ("t"), separados por um espaço.

A cadeia de caracteres do resultado é afetada pelas informações de formatação de um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) específico. A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado, que é retornado pelas propriedades [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) e [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de algumas culturas, pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | Define o formato do componente de data da cadeia de caracteres de resultado.
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Define o formato do componente de hora da cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "g" para exibir um valor de data e hora. 

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("g", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("fr-BE")));
// Displays 10/04/2008 6:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("g", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("fr-BE")))
' Displays 10/04/2008 6:30  
```

## <a name="the-general-date-long-time-g-format-specifier"></a>Especificador de formato de data geral e hora completa (“G”)

O especificador de formato padrão "G" representa uma combinação dos padrões de data abreviada ("d") e hora completa ("T"), separados por um espaço.

A cadeia de caracteres do resultado é afetada pelas informações de formatação de um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) específico. A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado, que é retornado pelas propriedades [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) e [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) de algumas culturas, pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | Define o formato do componente de data da cadeia de caracteres de resultado.
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | Define o formato do componente de hora da cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "G" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("G", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("nl-BE")));
// Displays 10/04/2008 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("G", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("nl-BE")))
' Displays 10/04/2008 6:30:00                       
```

## <a name="the-month-m-m-format-specifier"></a>Especificador de formato de mês ("M", "m")

O especificador de formato padrão "M" ou "m" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) atual. Por exemplo, a cadeia de caracteres de formato personalizado para o cultura invariável é "MMMM dd".

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade | Descrição
-------- | -----------
[MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) | Define o formato geral da cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.

O exemplo a seguir utiliza o especificador de formato "m" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays April 10                        
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("ms-MY")));
// Displays 10 April  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays April 10                        
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("ms-MY")))
' Displays 10 April
```

## <a name="the-round-trip-o-o-format-specifier"></a>Especificador de formato de ida e volta ("O", "o")

O especificador de formato padrão "O" ou "o" representa uma cadeia de caracteres de data e hora personalizada usando um padrão que preserva as informações de fuso horário e emite uma cadeia de caracteres de resultado compilada com ISO 8601. Para valores [DateTime](xref:System.DateTime), este especificador de formato foi projetado para manter valores de data e hora junto à propriedade [DateTime.Kind](xref:System.DateTime.Kind) no texto. A cadeia de caracteres formatada pode ser analisada novamente usando o método [DateTime.Parse(String,IFormatProvider,DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) ou [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) se o parâmetro de estilos é definido como [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind). 

O especificador de formato padrão "O" ou "o" corresponde à cadeia de caracteres de formato personalizado "aaaa'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" para valores DateTime e à cadeia de caracteres de formato personalizado "aaaa'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" para valores [DateTimeOffset](xref:System.DateTimeOffset). Nesta cadeia de caracteres, os pares de aspas simples que delimitam caracteres individuais, como hifens, dois-pontos e a letra "T", indicam que o caractere individual é literal e não pode ser alterado. As aspas simples em si não aparecem na cadeia de caracteres de saída. 

O especificador de formato padrão "O" ou "o" (e a cadeia de caracteres de formato personalizado "aaaa'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK") aproveita as três maneiras do ISO 8601 representar as informações de fuso horário para preservar a propriedade [Kind](xref:System.DateTime.Kind) dos valores [DateTime](xref:System.DateTime): 

* O componente de fuso horário dos valores de data e hora [DateTimeKind.Local](xref:System.DateTimeKind.Local) é um deslocamento em relação ao UTC (por exemplo, +01:00, -07:00). Todos os valores DateTimeOffset também estão representados nesse formato. 

* O componente de fuso horário dos valores de data e hora [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) usa "Z" (que significa deslocamento zero) para representar o UTC. 

* Os valores de data e hora [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) não têm informações de fuso horário. 

Como o especificador de formato padrão O" ou "o" está de acordo com um padrão internacional, a operação de formatação ou análise que usa o especificador sempre usa a cultura invariável e o calendário gregoriano. 

As cadeias de caracteres passadas para os métodos `Parse`, `TryParse`, `ParseExact` e `TryParseExact` de [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) podem ser analisadas usando o especificador de formato "O" ou "o", caso estejam em um desses formatos. No caso de objetos [DateTime](xref:System.DateTime), a sobrecarga de análise chamada também deve incluir um parâmetro de estilos com um valor de [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind). Se chamar um método de análise com a cadeia de caracteres de formato personalizado correspondente ao especificador de formato "O" ou "o", você não terá os mesmos resultados de "O" ou "o". Isso porque os métodos de análise que usam uma cadeia de caracteres de formato personalizado não podem analisar a representação da cadeia de caracteres de valores de data e hora que não tenham um componente de fuso horário ou usem "Z" para indicar o UTC. 

O exemplo a seguir usa o especificador de formato "o" para exibir uma série de valores [DateTime](xref:System.DateTime) e um valor [DateTimeOffset](xref:System.DateTimeOffset) em um sistema no Fuso horário do Pacífico. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
       DateTime dat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                   DateTimeKind.Unspecified);
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind); 

       DateTime uDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Utc);
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind);

       DateTime lDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Local);
       Console.WriteLine("{0} ({1}) --> {0:O}\n", lDat, lDat.Kind);

       DateTimeOffset dto = new DateTimeOffset(lDat);
       Console.WriteLine("{0} --> {0:O}", dto);
   }
}
// The example displays the following output:
//    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
//    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
//    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
//    
//    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

```vb
Module Example
   Public Sub Main()
       Dim dat As New Date(2009, 6, 15, 13, 45, 30, 
                           DateTimeKind.Unspecified)
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind) 

       Dim uDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Utc)
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind)

       Dim lDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Local)
       Console.WriteLine("{0} ({1}) --> {0:O}", lDat, lDat.Kind)
       Console.WriteLine()

       Dim dto As New DateTimeOffset(lDat)
       Console.WriteLine("{0} --> {0:O}", dto)
   End Sub
End Module
' The example displays the following output:
'    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
'    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
'    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
'    
'    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

O exemplo a seguir usa o especificador do formato “o” para criar uma cadeia de caracteres formatada e, em seguida, restaurar o valor de data e hora original ao chamar um método `Parse` de data e hora.

```csharp
// Round-trip DateTime values.
DateTime originalDate, newDate;
string dateString;
// Round-trip a local time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 10, 6, 30, 0), DateTimeKind.Local);
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip a UTC time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 12, 9, 30, 0), DateTimeKind.Utc);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip time in an unspecified time zone.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 13, 12, 30, 0), DateTimeKind.Unspecified);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);

// Round-trip a DateTimeOffset value.
DateTimeOffset originalDTO = new DateTimeOffset(2008, 4, 12, 9, 30, 0, new TimeSpan(-8, 0, 0));
dateString = originalDTO.ToString("o");
DateTimeOffset newDTO = DateTimeOffset.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO);
// The example displays the following output:
//    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
//    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
//    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
//    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

```vb
' Round-trip DateTime values.
Dim originalDate, newDate As Date
Dim dateString As String
' Round-trip a local time.
originalDate = Date.SpecifyKind(#4/10/2008 6:30AM#, DateTimeKind.Local)
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip a UTC time.
originalDate = Date.SpecifyKind(#4/12/2008 9:30AM#, DateTimeKind.Utc)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip time in an unspecified time zone.
originalDate = Date.SpecifyKind(#4/13/2008 12:30PM#, DateTimeKind.Unspecified)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)

' Round-trip a DateTimeOffset value.
Dim originalDTO As New DateTimeOffset(#4/12/2008 9:30AM#, New TimeSpan(-8, 0, 0))
dateString = originalDTO.ToString("o")
Dim newDTO As DateTimeOffset = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO)
' The example displays the following output:
'    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
'    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
'    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
'    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

## <a name="the-rfc1123-r-r-format-specifier"></a>Especificador de formato RFC1123 ("R", "r")

O especificador de formato padrão "R" ou "r" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern). O padrão reflete um padrão definido e a propriedade é somente leitura. Portanto, ele é sempre o mesmo, independentemente da cultura usada ou do provedor de formato fornecido. A cadeia de caracteres de formato personalizado é "ddd, dd MMM aaaa HH':'mm':'ss 'GMT' ". Quando esse especificador de formato padrão é usado, a operação de formatação ou análise sempre usa a cultura invariável.

A cadeia de caracteres de resultado é afetada pelas seguintes propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) retornado pela propriedade [DateTimeFormatInfo.InvariantInfo](xref:System.Globalization.DateTimeFormatInfo.InvariantInfo) que representa a cultura invariável.

Propriedade | Descrição
-------- | -----------
[RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | Define o formato da cadeia de caracteres de resultado.
[AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) | Define os nomes de dias abreviados que podem aparecer na cadeia de caracteres de resultado.
[AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) | Define os nomes dos meses abreviados que podem aparecer na cadeia de caracteres de resultado.

Embora o padrão RFC 1123 expresse a hora no formato UTC (Hora Universal Coordenada), a operação de formatação não altera o valor do objeto [DateTime](xref:System.DateTime) que está sendo formatado. Assim, você deve converter o valor de [DateTime](xref:System.DateTime) em UTC ao chamar o método [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) antes de executar a operação de formatação. Por outro lado, os valores [DateTimeOffset](xref:System.DateTimeOffset) realizam essa conversão automaticamente; não há necessidade de chamar o método [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) antes da operação de formatação. 

O exemplo a seguir usa o especificador de formato "r" para exibir um [DateTime](xref:System.DateTime) e um valor [DateTimeOffset](xref:System.DateTimeOffset) em um sistema no Fuso horário do Pacífico.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
DateTimeOffset dateOffset = new DateTimeOffset(date1, 
                            TimeZoneInfo.Local.GetUtcOffset(date1));
Console.WriteLine(date1.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Dim dateOffset As New DateTimeOffset(date1, TimeZoneInfo.Local.GetUtcOFfset(date1))
Console.WriteLine(date1.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT
```

## <a name="the-sortable-s-format-specifier"></a>Especificador de formato classificável ("s")

O especificador de formato padrão "s" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.SortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern). O padrão reflete um padrão definido (ISO 8601) e a propriedade é somente leitura. Portanto, ele é sempre o mesmo, independentemente da cultura usada ou do provedor de formato fornecido. A cadeia de caracteres de formato personalizado é "aaaa'-'MM'-'dd'T'HH':'mm':'ss".

A finalidade do especificador de formato "s" é produzir cadeias de caracteres de resultado que classificam consistentemente em ordem crescente ou decrescente com base nos valores de data e hora. Como resultado, embora o especificador de formato padrão "s" represente um valor de data e hora em um formato consistente, a operação de formatação não modifica o valor do objeto de data e hora que está sendo formatado para refletir sua propriedade [DateTime.Kind](xref:System.DateTime.Kind) ou seu valor [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset). Por exemplo, as cadeias de caracteres de resultado produzidas pela formatação de valores de data e hora 2014-11-15T18:32:17+00:00 e 2014-11-15T18:32:17+08:00 são idênticas. 

Quando esse especificador de formato padrão é usado, a operação de formatação ou análise sempre usa a cultura invariável. 

O exemplo a seguir usa o especificador de formato "s" para exibir um [DateTime](xref:System.DateTime) e um valor [DateTimeOffset](xref:System.DateTimeOffset) em um sistema no Fuso horário do Pacífico.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("s"));
// Displays 2008-04-10T06:30:00
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("s"))
' Displays 2008-04-10T06:30:00 
```

## <a name="the-short-time-t-format-specifier"></a>Especificador de formato de hora abreviada ("t")

O especificador de formato padrão "t" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) atual. Por exemplo, a cadeia de caracteres de formato personalizado para a cultura invariável é "HH:mm".

A cadeia de caracteres do resultado é afetada pelas informações de formatação de um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) específico. A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado que é retornado pela propriedade [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de algumas culturas pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Define o formato do componente de hora da cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "t" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30
```

## <a name="the-long-time-t-format-specifier"></a>Especificador de formato de hora completa ("T")

O especificador de formato padrão "T" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) de uma cultura específica. Por exemplo, a cadeia de caracteres de formato personalizado para a cultura invariável é "HH:mm:ss".

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado que é retornado pela propriedade [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) de algumas culturas pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | Define o formato do componente de hora da cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

O exemplo a seguir utiliza o especificador de formato "T" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30:00 
```

## <a name="the-universal-sortable-u-format-specifier"></a>Especificador de formato classificável universal ("u")

O especificador de formato padrão "u" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.UniversalSortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern). O padrão reflete um padrão definido e a propriedade é somente leitura. Portanto, ele é sempre o mesmo, independentemente da cultura usada ou do provedor de formato fornecido. A cadeia de caracteres de formato personalizado é "aaaa'-'MM'-'dd HH':'mm':'ss'Z'". Quando esse especificador de formato padrão é usado, a operação de formatação ou análise sempre usa a cultura invariável. 

Embora a cadeia de caracteres de resultado deva expressar a hora no formato UTC, nenhuma conversão do valor de [DateTime](xref:System.DateTime) original é executada durante a operação de formatação. Assim, você deve converter o valor de [DateTime](xref:System.DateTime) em UTC ao chamar o método [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) antes de formatá-lo. Por outro lado, os valores [DateTimeOffset](xref:System.DateTimeOffset) realizam essa conversão automaticamente; não há necessidade de chamar o método [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) antes da operação de formatação.   

O exemplo a seguir utiliza o especificador de formato "u" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToUniversalTime().ToString("u"));
// Displays 2008-04-10 13:30:00Z
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToUniversalTime.ToString("u"))
' Displays 2008-04-10 13:30:00Z                       
```

## <a name="the-universal-full-u-format-specifier"></a>Especificador de formato completo universal ("U")

O especificador de formato padrão "U" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) de uma cultura específica. O padrão é o mesmo que o padrão "F". Entretanto, o valor de [DateTime](xref:System.DateTime) é automaticamente convertido em UTC antes de ser formatado.

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que podem controlar a formatação da cadeia de caracteres retornada. O especificador de formato personalizado que é retornado pela propriedade [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) de algumas culturas pode não fazer uso de todas as propriedades.

Propriedade | Descrição
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | Define o formato geral da cadeia de caracteres de resultado.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Define os nomes de dias localizados que podem aparecer na cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Define a cadeia de caracteres que indica as horas da meia-noite até antes do meio-dia em um relógio de 12 horas.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Define a cadeia de caracteres que indica as horas do meio-dia até antes da meia-noite em um relógio de 12 horas.

Não há suporte para o especificador de formato "U" no tipo [DateTimeOffset](xref:System.DateTimeOffset) e ele gera um [FormatException](xref:System.FormatException) se é usado para formatar um valor [DateTimeOffset](xref:System.DateTimeOffset).

O exemplo a seguir utiliza o especificador de formato "U" para exibir um valor de data e hora.

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("sv-FI")));
// Displays den 10 april 2008 13:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("sv-FI")))
' Displays den 10 april 2008 13:30:00                       
```

## <a name="the-year-month-y-y-format-specifier"></a>Especificador de formato de ano mês ("Y", "y")

O especificador de formato padrão “Y” ou "y" representa uma cadeia de caracteres de formato de data e hora personalizado que é definida pela propriedade [DateTimeFormatInfo.YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) de uma cultura específica. Por exemplo, a cadeia de caracteres de formato personalizado para o cultura invariável é "aaaa MMMM".

A tabela a seguir lista as propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade | Descrição
-------- | -----------
[YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) | Define o formato geral da cadeia de caracteres de resultado.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Define os nomes dos meses localizados que podem aparecer na cadeia de caracteres de resultado.

O exemplo a seguir utiliza o especificador de formato "y" para exibir um valor de data e hora.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("Y", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays April, 2008                       
Console.WriteLine(date1.ToString("y", 
                  CultureInfo.CreateSpecificCulture("af-ZA")));
// Displays April 2008 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("Y", CultureInfo.CreateSpecificCulture("en-US")))
' Displays April, 2008                       
Console.WriteLine(date1.ToString("y", CultureInfo.CreateSpecificCulture("af-ZA")))
' Displays April 2008
```                       

## <a name="notes"></a>Anotações

### <a name="datetimeformatinfo-properties"></a>Propriedades DateTimeFormatInfo

A formatação é influenciada pelas propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual, que é fornecido implicitamente pela cultura de thread atual ou explicitamente pelo parâmetro [IFormatProvider](xref:System.IFormatProvider) do método que invoca a formatação. Para o parâmetro [IFormatProvider](xref:System.IFormatProvider), seu aplicativo deve especificar um objeto [CultureInfo](xref:System.Globalization.CultureInfo), que representa uma cultura ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), que representa as convenções de formatação de data e hora de uma determinada cultura. Muitos dos especificadores de formato padrão de data e hora são aliases para padrões de formatação definidos pelas propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual. Seu aplicativo pode alterar o resultado produzido por alguns especificadores de formato padrão de data e hora alterando os padrões de formatação de data e hora correspondentes da propriedade [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) correlata.

## <a name="see-also"></a>Consulte também

[Formatando tipos](formatting-types.md)

[Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md)




<!--HONumber=Nov16_HO3-->


