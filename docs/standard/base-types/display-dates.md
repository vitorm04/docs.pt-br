---
title: "Como exibir datas em calendários não gregorianos"
description: "Como exibir datas em calendários não gregorianos"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 93f06e1d-544b-4ccc-a0b2-95cd674852cb
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 85c9d450be48c553ea3a1f1a0f16c298941fa325

---

# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Como exibir datas em calendários não gregorianos

Os tipos [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) usam o calendário gregoriano como seu calendário padrão. Isso significa que chamar o método `ToString` de um valor de data e hora exibe a representação de cadeia de caracteres da data e hora no calendário gregoriano, mesmo que a data e hora tenha sido criada usando outro calendário. Isso é ilustrado no exemplo a seguir, que usa duas maneiras diferentes para criar um valor de data e hora com o calendário persa, mas ainda exibe esses valores de data e hora no calendário gregoriano quando chama o método [ToString](xref:System.DateTime.ToString). Este exemplo reflete duas técnicas comumente usadas, mas incorretas, para exibir a data em um calendário específico.

```csharp
PersianCalendar persianCal = new PersianCalendar();

DateTime persianDate = persianCal.ToDateTime(1387, 3, 18, 12, 0, 0, 0);
Console.WriteLine(persianDate.ToString());

persianDate = new DateTime(1387, 3, 18, persianCal);
Console.WriteLine(persianDate.ToString());
// The example displays the following output to the console:
//       6/7/2008 12:00:00 PM
//       6/7/2008 12:00:00 AM
```

```vb
Dim persianCal As New PersianCalendar()

Dim persianDate As Date = persianCal.ToDateTime(1387, 3, 18, _
                                                12, 0, 0, 0)
Console.WriteLine(persianDate.ToString())

persianDate = New DateTime(1387, 3, 18, persianCal)
Console.WriteLine(persianDate.ToString())
' The example displays the following output to the console:
'       6/7/2008 12:00:00 PM
'       6/7/2008 12:00:00 AM
```

Duas técnicas diferentes podem ser usadas para exibir a data em um calendário específico. A primeira requer que o calendário seja o calendário padrão de uma determinada cultura. O segundo pode ser usado com qualquer calendário.

## <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Para exibir a data do calendário padrão de uma cultura

1. Crie uma instância de um objeto de calendário derivado da classe [Calendar](xref:System.Globalization.Calendar) que representa o calendário a ser usado.

2. Crie uma instância de um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa a cultura cuja formatação será usada para exibir a data.

3. Chame o método [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) para determinar se o objeto de calendário é um membro da matriz retornada pela propriedade [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars). Isso indica que o calendário pode servir como calendário padrão para o objeto [CultureInfo](xref:System.Globalization.CultureInfo). Se ele não for membro da matriz, siga as instruções na seção "Para exibir a data em qualquer calendário".

4. Atribua o objeto de calendário à propriedade [Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) retornado pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).

  > [!NOTE]
  > A classe [CultureInfo](xref:System.Globalization.CultureInfo) também tem uma propriedade [Calendar](xref:System.Globalization.CultureInfo.Calendar). No entanto, ela é somente leitura e constante; não é alterada para refletir o novo calendário padrão atribuído à propriedade [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar).
  
5. Chame o método [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) ou [DateTime.ToString(String,IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) e passe-o para o objeto [CultureInfo](xref:System.Globalization.CultureInfo) cujo calendário padrão foi modificado na etapa anterior.

## <a name="to-display-the-date-in-any-calendar"></a>Para exibir a data em qualquer calendário

1. Crie uma instância de um objeto de calendário derivado da classe [Calendar](xref:System.Globalization.Calendar) que representa o calendário a ser usado.

2. Determine quais elementos de data e hora devem aparecer na representação de cadeia de caracteres do valor de data e hora.

3. Para cada elemento de data e hora que você deseja exibir, chame o método `Get…` do objeto do calendário. Os métodos a seguir estão disponíveis:

    * [GetYear](xref:System.Globalization.Calendar.GetYear(System.DateTime)), para exibir o ano no calendário apropriado.
    
    * [GetMonth](xref:System.Globalization.Calendar.GetMonth(System.DateTime)), para exibir o mês no calendário apropriado. 
    
    * [GetDayOfMonth](xref:System.Globalization.Calendar.GetDayOfMonth(System.DateTime)), para exibir o número do dia do mês no calendário apropriado.
    
    * [GetHour](xref:System.Globalization.Calendar.GetHour(System.DateTime)), para exibir a hora do dia no calendário apropriado.
    
    * [GetMinute](xref:System.Globalization.Calendar.GetMinute(System.DateTime)), para exibir os minutos da hora no calendário apropriado.
    
    * [GetSecond](xref:System.Globalization.Calendar.GetSecond(System.DateTime)), para exibir os segundos do minuto no calendário apropriado. 
    
    * [GetMilliseconds](xref:System.Globalization.Calendar.GetMilliseconds(System.DateTime)), para exibir os milissegundos do segundo no calendário apropriado.
    
## <a name="example"></a>Exemplo
    
O exemplo exibe uma data usando dois calendários diferentes. Ele exibe a data após definir o calendário islâmico como calendário padrão para a cultura ar-JO e exibe a data usando o calendário persa, que não tem suporte como calendário opcional pela cultura fa-IR.

```csharp
using System;
using System.Globalization;

public class CalendarDates
{
   public static void Main()
   {
      HijriCalendar hijriCal = new HijriCalendar();
      CalendarUtility hijriUtil = new CalendarUtility(hijriCal);
      DateTime dateValue1 = new DateTime(1429, 6, 29, hijriCal);
      DateTimeOffset dateValue2 = new DateTimeOffset(dateValue1, 
                                  TimeZoneInfo.Local.GetUtcOffset(dateValue1));
      CultureInfo jc = CultureInfo.CreateSpecificCulture("ar-JO");

      // Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", 
                        dateValue1.ToString("d"));
      // Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", 
                        dateValue1.ToString("d", jc));
      // Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:");
      // Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc));
      // Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc));

      Console.WriteLine();

      PersianCalendar persianCal = new PersianCalendar();
      CalendarUtility persianUtil = new CalendarUtility(persianCal);
      CultureInfo ic = CultureInfo.CreateSpecificCulture("fa-IR");

      // Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}",       
                        dateValue1.ToString("d", ic));
      // Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic));
      // Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic));
   }
}

public class CalendarUtility
{
   private Calendar thisCalendar;
   private CultureInfo targetCulture;

   public CalendarUtility(Calendar cal)
   {
      this.thisCalendar = cal;
   }

   private bool CalendarExists(CultureInfo culture)
   {
      this.targetCulture = culture;
      return Array.Exists(this.targetCulture.OptionalCalendars, 
                          this.HasSameName);
   }

   private bool HasSameName(Calendar cal)
   {
      if (cal.ToString() == thisCalendar.ToString())
         return true;
      else
         return false;
   }

   public string DisplayDate(DateTime dateToDisplay, CultureInfo culture)
   {
      DateTimeOffset displayOffsetDate = dateToDisplay;
      return DisplayDate(displayOffsetDate, culture);
   }

   public string DisplayDate(DateTimeOffset dateToDisplay, 
                             CultureInfo culture)
   {
      string specifier = "yyyy/MM/dd";

      if (this.CalendarExists(culture))
      {
         Console.WriteLine("Displaying date in supported {0} calendar...", 
                           this.thisCalendar.GetType().Name);
         culture.DateTimeFormat.Calendar = this.thisCalendar;
         return dateToDisplay.ToString(specifier, culture);
      }
      else
      {
         Console.WriteLine("Displaying date in unsupported {0} calendar...", 
                           thisCalendar.GetType().Name);

         string separator = targetCulture.DateTimeFormat.DateSeparator;

         return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") +
                separator +
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") + 
                separator +
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00"); 
      }
   } 
}
// The example displays the following output to the console:
//       Using the system default culture: 7/3/2008
//       Using the ar-JO culture's original default calendar: 03/07/2008
//       Using the ar-JO culture with Hijri as the default calendar:
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       
//       Using the ir-FA culture's default calendar: 7/3/2008
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
```

```vb
Imports System.Globalization

Public Class CalendarDates
   Public Shared Sub Main()
      Dim hijriCal As New HijriCalendar()
      Dim hijriUtil As New CalendarUtility(hijriCal)
      Dim dateValue1 As Date = New Date(1429, 6, 29, hijriCal)
      Dim dateValue2 As DateTimeOffset = New DateTimeOffset(dateValue1, _
                                         TimeZoneInfo.Local.GetUtcOffset(dateValue1))
      Dim jc As CultureInfo = CultureInfo.CreateSpecificCulture("ar-JO")

      ' Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", _
                        dateValue1.ToString("d"))
      ' Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", _
                        dateValue1.ToString("d", jc))
      ' Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:")
      ' Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc))
      ' Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc))

      Console.WriteLine()

      Dim persianCal As New PersianCalendar()
      Dim persianUtil As New CalendarUtility(persianCal)
      Dim ic As CultureInfo = CultureInfo.CreateSpecificCulture("fa-IR")

      ' Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}", _      
                        dateValue1.ToString("d", ic))
      ' Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic))
      ' Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic))
   End Sub
End Class

Public Class CalendarUtility
   Private thisCalendar As Calendar
   Private targetCulture As CultureInfo

   Public Sub New(cal As Calendar)
      Me.thisCalendar = cal
   End Sub

   Private Function CalendarExists(culture As CultureInfo) As Boolean
      Me.targetCulture = culture
      Return Array.Exists(Me.targetCulture.OptionalCalendars, _
                          AddressOf Me.HasSameName)
   End Function 

   Private Function HasSameName(cal As Calendar) As Boolean
      If cal.ToString() = thisCalendar.ToString() Then
         Return True
      Else
         Return False
      End If
   End Function

   Public Function DisplayDate(dateToDisplay As Date, _
                               culture As CultureInfo) As String
      Dim displayOffsetDate As DateTimeOffset = dateToDisplay
      Return DisplayDate(displayOffsetDate, culture)
   End Function

   Public Function DisplayDate(dateToDisplay As DateTimeOffset, _
                               culture As CultureInfo) As String
      Dim specifier As String = "yyyy/MM/dd"

      If Me.CalendarExists(culture) Then
         Console.WriteLine("Displaying date in supported {0} calendar...", _
                           thisCalendar.GetType().Name)
         culture.DateTimeFormat.Calendar = Me.thisCalendar
         Return dateToDisplay.ToString(specifier, culture)
      Else
         Console.WriteLine("Displaying date in unsupported {0} calendar...", _
                           thisCalendar.GetType().Name)

         Dim separator As String = targetCulture.DateTimeFormat.DateSeparator

         Return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") & separator & _
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") & separator & _
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00") 
      End If             
   End Function
End Class
' The example displays the following output to the console:
'       Using the system default culture: 7/3/2008
'       Using the ar-JO culture's original default calendar: 03/07/2008
'       Using the ar-JO culture with Hijri as the default calendar:
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       
'       Using the ir-FA culture's default calendar: 7/3/2008
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
```

Cada objeto [CultureInfo](xref:System.Globalization.CultureInfo) pode dar suporte a um ou mais calendários, que são indicados pela propriedade [OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars). Um deles é designado como o calendário padrão da cultura e é retornado pela propriedade somente leitura [CultureInfo.Calendar](xref:System.Globalization.CultureInfo.Calendar). Outro dos calendários opcionais pode ser designado como padrão atribuindo um objeto [Calendar](xref:System.Globalization.Calendar) que representa o calendário à propriedade [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) retornada pela propriedade [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). No entanto, alguns calendários, como o calendário persa representado pela classe [PersianCalendar](xref:System.Globalization.PersianCalendar), não servem como calendários opcionais para nenhuma cultura.   

O exemplo define uma classe de utilitário de calendário reutilizável, `CalendarUtility`, para manipular muitos dos detalhes de gerar a representação de cadeia de caracteres de uma data usando um calendário específico. A classe `CalendarUtility` tem os seguintes membros: 

* Um construtor parametrizado cujo único parâmetro é um objeto [Calendar](xref:System.Globalization.Calendar) em que uma data deve ser representada. Ele é atribuído a um campo particular da classe.

* `CalendarExists`, um método particular que retorna um valor booliano que indica se o calendário representado pelo `CalendarUtility` objeto tem suporte do objeto [CultureInfo](xref:System.Globalization.CultureInfo) passado para o método como um parâmetro. O método encapsula uma chamada para o método [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})), a que ele passa a matriz [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars).

* `HasSameName`, um método particular atribuído ao delegado [Predicate&lt;T&gt;](xref:System.Predicate%601) que é passado como parâmetro para o método [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})). Cada membro da matriz é passado ao método até que o método retorne `true`. O método determina se o nome de um calendário opcional é o mesmo que o calendário representado pelo objeto `CalendarUtility`.

* `DisplayDate`, um método público sobrecarregado a que são passados dois parâmetros: um valor de [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) para expressar no calendário representado pelo objeto `CalendarUtility`; e a cultura cujas regras de formatação devem ser usadas. Seu comportamento ao retornar a representação de cadeia de caracteres de uma data depende de o calendário de destino ter suporte da cultura cujas regras de formatação devem ser usadas.

Independentemente do calendário usado para criar um valor [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) neste exemplo, o valor normalmente é expresso como uma data no calendário gregoriano. Isso ocorre porque os tipos [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) não preservam nenhuma informação de calendário. Internamente, eles são representados como o número de marcadores decorridos desde a meia-noite de 1º de janeiro de 0001. A interpretação desse número depende do calendário. Na maioria das culturas, o calendário padrão é o calendário gregoriano. 

## <a name="see-also"></a>Consulte também

[Executando operações de formatação](performing-formatting-operations.md)



<!--HONumber=Dec16_HO1-->


