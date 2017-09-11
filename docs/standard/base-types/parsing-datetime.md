---
title: Analisando cadeias de caracteres de data e hora no .NET
description: Analisando cadeias de caracteres de data e hora no .NET
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f0131baa0874880b6697458426da5ae9ce1705b7
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-date-and-time-strings-in-net"></a><span data-ttu-id="c01fa-104">Analisando cadeias de caracteres de data e hora no .NET</span><span class="sxs-lookup"><span data-stu-id="c01fa-104">Parsing date and time strings in .NET</span></span>

<span data-ttu-id="c01fa-105">Os métodos de análise convertem a representação em cadeia de caracteres de data e hora em um objeto [DateTime](xref:System.DateTime) equivalente.</span><span class="sxs-lookup"><span data-stu-id="c01fa-105">Parsing methods convert the string representation of a date and time to an equivalent [DateTime](xref:System.DateTime) object.</span></span> <span data-ttu-id="c01fa-106">Os métodos [Parse](xref:System.DateTime.Parse(System.String)) e [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) convertem qualquer uma das várias representações comuns de data e hora.</span><span class="sxs-lookup"><span data-stu-id="c01fa-106">The [Parse](xref:System.DateTime.Parse(System.String)) and [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) methods convert any of several common representations of a date and time.</span></span> <span data-ttu-id="c01fa-107">Os métodos [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) e [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) convertem uma representação em cadeia de caracteres que cumpra o padrão especificado por uma cadeia de caracteres de formato de data e hora.</span><span class="sxs-lookup"><span data-stu-id="c01fa-107">The [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) and [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) methods convert a string representation that conforms to the pattern specified by a date and time format string.</span></span> <span data-ttu-id="c01fa-108">(Consulte os tópicos sobre [cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) e [cadeias de caracteres de formato de data e hora personalizadas](custom-datetime.md).)</span><span class="sxs-lookup"><span data-stu-id="c01fa-108">(See the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).)</span></span> 

<span data-ttu-id="c01fa-109">A análise é influenciada pelas propriedades de um provedor de formato que fornece informações como as cadeias de caracteres usadas para separadores de data e hora, além dos nomes dos meses, dias e eras.</span><span class="sxs-lookup"><span data-stu-id="c01fa-109">Parsing is influenced by the properties of a format provider that supplies information such as the strings used for date and time separators, and the names of months, days, and eras.</span></span> <span data-ttu-id="c01fa-110">O provedor de formato é o objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) atual, que é fornecido implicitamente pela cultura de thread atual ou explicitamente pelo parâmetro [IFormatProvider](xref:System.IFormatProvider) de um método de análise.</span><span class="sxs-lookup"><span data-stu-id="c01fa-110">The format provider is the current [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object, which is provided implicitly by the current thread culture or explicitly by the [IFormatProvider](xref:System.IFormatProvider) parameter of a parsing method.</span></span> <span data-ttu-id="c01fa-111">Para o parâmetro [IFormatProvider](xref:System.IFormatProvider), especifique um objeto [CultureInfo](xref:System.Globalization.CultureInfo), que representa uma cultura ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo).</span><span class="sxs-lookup"><span data-stu-id="c01fa-111">For the [IFormatProvider](xref:System.IFormatProvider) parameter, specify a [CultureInfo](xref:System.Globalization.CultureInfo) object, which represents a culture, or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> 

<span data-ttu-id="c01fa-112">A representação de cadeia de caracteres de uma data a ser analisada deve incluir o mês e, pelo menos, um dia ou ano.</span><span class="sxs-lookup"><span data-stu-id="c01fa-112">The string representation of a date to be parsed must include the month and at least a day or year.</span></span> <span data-ttu-id="c01fa-113">A representação de cadeia de caracteres de um horário deve incluir a hora e, pelo menos, os minutos ou o designador AM/PM.</span><span class="sxs-lookup"><span data-stu-id="c01fa-113">The string representation of a time must include the hour and at least minutes or the AM/PM designator.</span></span> <span data-ttu-id="c01fa-114">No entanto, análise fornece valores padrão para componentes omitidos, se possível.</span><span class="sxs-lookup"><span data-stu-id="c01fa-114">However, parsing supplies default values for omitted components if possible.</span></span> <span data-ttu-id="c01fa-115">O padrão de data ausente é a data atual; o padrão de ano ausente é o ano atual; o padrão de dia do mês ausente é o primeiro dia do mês; o padrão de horário ausente é meia-noite.</span><span class="sxs-lookup"><span data-stu-id="c01fa-115">A missing date defaults to the current date, a missing year defaults to the current year, a missing day of the month defaults to the first day of the month, and a missing time defaults to midnight.</span></span> 

<span data-ttu-id="c01fa-116">Se a representação de cadeia de caracteres especifica somente um horário, a análise retorna um objeto [DateTime](xref:System.DateTime) com as propriedades [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month) e [Day](xref:System.DateTime.Day) definidas para os valores correspondentes da propriedade [Today](xref:System.DateTime.Today).</span><span class="sxs-lookup"><span data-stu-id="c01fa-116">If the string representation specifies only a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Year](xref:System.DateTime.Year), [Month](xref:System.DateTime.Month), and [Day](xref:System.DateTime.Day) properties set to the corresponding values of the [Today](xref:System.DateTime.Today) property.</span></span> <span data-ttu-id="c01fa-117">No entanto, se a constante [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) estiver especificada no método de análise, as propriedades resultantes de ano, mês e dia serão definidas com o valor 1.</span><span class="sxs-lookup"><span data-stu-id="c01fa-117">However, if the [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) constant is specified in the parsing method, the resulting year, month, and day properties are set to the value 1.</span></span>

<span data-ttu-id="c01fa-118">Além de um componente de data e hora, a representação de cadeia de caracteres de data e hora pode incluir um deslocamento que indique a diferença de tempo em relação ao UTC (Tempo Universal Coordenado).</span><span class="sxs-lookup"><span data-stu-id="c01fa-118">In addition to a date and a time component, the string representation of a date and time can include an offset that indicates how much the time differs from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="c01fa-119">Por exemplo, a cadeia de caracteres “2/14/2007 5:32:00 -7:00” define um horário sete horas antes do UTC.</span><span class="sxs-lookup"><span data-stu-id="c01fa-119">For example, the string "2/14/2007 5:32:00 -7:00" defines a time that is seven hours earlier than UTC.</span></span> <span data-ttu-id="c01fa-120">Se um deslocamento for omitido da representação de cadeia de caracteres de horário, a análise retorna um objeto [DateTime](xref:System.DateTime) com a propriedade [Kind](xref:System.DateTime.Kind) definida como [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span><span class="sxs-lookup"><span data-stu-id="c01fa-120">If an offset is omitted from the string representation of a time, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> <span data-ttu-id="c01fa-121">Se um deslocamento for especificado, a análise retorna um objeto [DateTime](xref:System.DateTime) com a propriedade [Kind](xref:System.DateTime.Kind) definida como [Local](xref:System.DateTimeKind.Local) e seu valor ajustado de acordo com o fuso horário local do seu computador.</span><span class="sxs-lookup"><span data-stu-id="c01fa-121">If an offset is specified, parsing returns a [DateTime](xref:System.DateTime) object with its [Kind](xref:System.DateTime.Kind) property set to [Local](xref:System.DateTimeKind.Local) and its value adjusted to the local time zone of your machine.</span></span> <span data-ttu-id="c01fa-122">É possível modificar esse comportamento usando uma constante [DateTimeStyles](xref:System.Globalization.DateTimeStyles) com o método de análise.</span><span class="sxs-lookup"><span data-stu-id="c01fa-122">You can modify this behavior by using a [DateTimeStyles](xref:System.Globalization.DateTimeStyles) constant with the parsing method.</span></span>

<span data-ttu-id="c01fa-123">O provedor de formato também é usado para interpretar uma data numérica ambígua.</span><span class="sxs-lookup"><span data-stu-id="c01fa-123">The format provider is also used to interpret an ambiguous numeric date.</span></span> <span data-ttu-id="c01fa-124">Por exemplo, não está claro quais componentes da data representada pela cadeia de caracteres “02/03/04” são o mês, o dia e o ano.</span><span class="sxs-lookup"><span data-stu-id="c01fa-124">For example, it is not clear which components of the date represented by the string "02/03/04" are the month, day, and year.</span></span> <span data-ttu-id="c01fa-125">Nesse caso, os componentes são interpretados de acordo com a ordem dos formatos de data semelhantes no provedor de formato.</span><span class="sxs-lookup"><span data-stu-id="c01fa-125">In this case, the components are interpreted according to the order of similar date formats in the format provider.</span></span> 

## <a name="parse"></a><span data-ttu-id="c01fa-126">Parse</span><span class="sxs-lookup"><span data-stu-id="c01fa-126">Parse</span></span>

<span data-ttu-id="c01fa-127">O exemplo de código a seguir ilustra o uso do método `Parse` para converter uma cadeia de caracteres em um `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c01fa-127">The following code example illustrates the use of the `Parse` method to convert a string into a `DateTime`.</span></span> <span data-ttu-id="c01fa-128">Este exemplo usa a cultura associada com o thread atual para realizar a análise.</span><span class="sxs-lookup"><span data-stu-id="c01fa-128">This example uses the culture associated with the current thread to perform the parse.</span></span> <span data-ttu-id="c01fa-129">Se o [CultureInfo](xref:System.Globalization.CultureInfo) associado com a cultura atual não conseguir analisar a cadeia de caracteres de entrada, será lançada uma [FormatException](xref:System.FormatException).</span><span class="sxs-lookup"><span data-stu-id="c01fa-129">If the [CultureInfo](xref:System.Globalization.CultureInfo) associated with the current culture cannot parse the input string, a [FormatException](xref:System.FormatException) is thrown.</span></span>

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

<span data-ttu-id="c01fa-130">Também é possível especificar um `CultureInfo` definido como uma das culturas definidas por tal objeto ou especificar um dos objetos [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) padrão retornados pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).</span><span class="sxs-lookup"><span data-stu-id="c01fa-130">You can also specify a `CultureInfo` set to one of the cultures defined by that object, or you can specify one of the standard [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="c01fa-131">O exemplo de código a seguir usa um provedor de formato para analisar uma cadeia de caracteres em alemão em um `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c01fa-131">The following code example uses a format provider to parse a German string into a `DateTime`.</span></span> <span data-ttu-id="c01fa-132">Um `CultureInfo` que representa a cultura de-DE é definido e passado com a cadeia de caracteres sendo analisada para assegurar uma análise bem-sucedida dessa cadeia de caracteres específica.</span><span class="sxs-lookup"><span data-stu-id="c01fa-132">A `CultureInfo` representing the de-DE culture is defined and passed with the string being parsed to ensure successful parsing of this particular string.</span></span> <span data-ttu-id="c01fa-133">Isso impede qualquer configuração que está no `CurrentCulture` do `CurrentThread`.</span><span class="sxs-lookup"><span data-stu-id="c01fa-133">This precludes whatever setting is in the `CurrentCulture` of the `CurrentThread`.</span></span>

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

<span data-ttu-id="c01fa-134">No entanto, apesar de ser possível usar sobrecargas do método [Parse](xref:System.DateTime.Parse(System.String)) para especificar os provedores de formato personalizado, o método não dá suporte ao uso de provedores de formato não padrão.</span><span class="sxs-lookup"><span data-stu-id="c01fa-134">However, although you can use overloads of the [Parse](xref:System.DateTime.Parse(System.String)) method to specify custom format providers, the method does not support the use of non-standard format providers.</span></span> <span data-ttu-id="c01fa-135">Para analisar data e hora expressadas em um formato não padrão, use o método [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)).</span><span class="sxs-lookup"><span data-stu-id="c01fa-135">To parse a date and time expressed in a non-standard format, use the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method instead.</span></span>

<span data-ttu-id="c01fa-136">O exemplo de código a seguir usa a enumeração [DateTimeStyles](xref:System.Globalization.DateTimeStyles) para especificar que as informações atuais de data e hora não devem ser adicionadas ao `DateTime` para campos que a cadeia de caracteres não define.</span><span class="sxs-lookup"><span data-stu-id="c01fa-136">The following code example uses the [DateTimeStyles](xref:System.Globalization.DateTimeStyles) enumeration to specify that the current date and time information should not be added to the `DateTime` for fields that the string does not define.</span></span>

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

## <a name="parseexact"></a><span data-ttu-id="c01fa-137">ParseExact</span><span class="sxs-lookup"><span data-stu-id="c01fa-137">ParseExact</span></span>

<span data-ttu-id="c01fa-138">O método [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) converte uma cadeia de caracteres que cumpre um padrão de cadeia de caracteres especificado para um objeto `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c01fa-138">The [DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method converts a string that conforms to a specified string pattern to a `DateTime` object.</span></span> <span data-ttu-id="c01fa-139">Quando uma cadeia de caracteres que não é da forma especificada é passada para esse método, é lançada uma [FormatException](xref:System.FormatException).</span><span class="sxs-lookup"><span data-stu-id="c01fa-139">When a string that is not of the form specified is passed to this method, a [FormatException](xref:System.FormatException) is thrown.</span></span> <span data-ttu-id="c01fa-140">Você pode especificar um dos especificadores de formato de data e hora padrão ou uma combinação limitada dos especificadores de formato de data e hora personalizados.</span><span class="sxs-lookup"><span data-stu-id="c01fa-140">You can specify one of the standard date and time format specifiers or a limited combination of the custom date and time format specifiers.</span></span> <span data-ttu-id="c01fa-141">Usando os especificadores de formato personalizados, é possível construir uma cadeia de caracteres de reconhecimento personalizada.</span><span class="sxs-lookup"><span data-stu-id="c01fa-141">Using the custom format specifiers, it is possible for you to construct a custom recognition string.</span></span> <span data-ttu-id="c01fa-142">Para ver uma explicação dos especificadores, consulte os tópicos [cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) e [cadeias de caracteres de formato de data e hora personalizadas](custom-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="c01fa-142">For an explanation of the specifiers, see the topics on [standard date and time format strings](standard-datetime.md) and [custom date and time format strings](custom-datetime.md).</span></span> 

<span data-ttu-id="c01fa-143">Cada sobrecarga do método [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) também tem um parâmetro [IFormatProvider](xref:System.IFormatProvider) que normalmente oferece informações específicas da cultura sobre a formatação da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c01fa-143">Each overload of the [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) method also has an [IFormatProvider](xref:System.IFormatProvider) parameter that typically provides culture-specific information about the formatting of the string.</span></span> <span data-ttu-id="c01fa-144">Normalmente, esse objeto [IFormatProvider](xref:System.IFormatProvider) é um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa uma cultura padrão ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que é retornado pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).</span><span class="sxs-lookup"><span data-stu-id="c01fa-144">Typically, this [IFormatProvider](xref:System.IFormatProvider) object is a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents a standard culture or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that is returned by the [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) property.</span></span> <span data-ttu-id="c01fa-145">Entretanto, ao contrário das outras funções de análise de data e hora, esse método também dá suporte a um [IFormatProvider](xref:System.IFormatProvider) que define um formato de data e hora não padrão.</span><span class="sxs-lookup"><span data-stu-id="c01fa-145">However, unlike the other date and time parsing functions, this method also supports an [IFormatProvider](xref:System.IFormatProvider) that defines a non-standard date and time format.</span></span> 

<span data-ttu-id="c01fa-146">No exemplo de código a seguir, o método `ParseExact` recebe um objeto de cadeia de caracteres para analisar, seguido por um especificador de formato, seguido por um objeto `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="c01fa-146">In the following code example, the `ParseExact` method is passed a string object to parse, followed by a format specifier, followed by a `CultureInfo` object.</span></span> <span data-ttu-id="c01fa-147">Esse método `ParseExact` só consegue analisar cadeias de caracteres que exibem o padrão de data por extenso na cultura en-US.</span><span class="sxs-lookup"><span data-stu-id="c01fa-147">This `ParseExact` method can only parse strings that exhibit the long date pattern in the en-US culture.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c01fa-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c01fa-148">See Also</span></span>

[<span data-ttu-id="c01fa-149">Analisando cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="c01fa-149">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="c01fa-150">Tipos de formatação no .NET</span><span class="sxs-lookup"><span data-stu-id="c01fa-150">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="c01fa-151">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="c01fa-151">Type conversion in .NET</span></span>](type-conversion.md)


