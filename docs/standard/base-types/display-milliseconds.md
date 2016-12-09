---
title: Como exibir milissegundos em valores de data e hora
description: Como exibir milissegundos em valores de data e hora
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 78599e33-1c3f-4335-b320-751e35906338
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 9bcec8a610ed0fd47d168e23fb1454067e2d3fac

---

# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Como exibir milissegundos em valores de data e hora

Os métodos padrão de formatação de data e hora, como [DateTime.ToString()](xref:System.DateTime.ToString), incluem as horas, minutos e segundos de um valor temporal, mas excluem seu componente de milissegundos. Este tópico mostra como incluir um componente de milissegundos de uma data e hora em cadeias de caracteres de data e hora formatadas.

## <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Para exibir o componente de milissegundos de um valor DateTime

1. Se você estiver trabalhando com a representação de cadeia de caracteres de uma data, converta-a para um valor [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) usando o método estático [DateTime.Parse(String)](xref:System.DateTime.Parse(System.String)) ou [DateTimeOffset.Parse(String)](xref:System.DateTimeOffset.Parse(System.String)).

2. Para extrair a representação de cadeia de caracteres do componente de milissegundos de um valor de data e hora, chame o método [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String)) do valor de data e hora e passe o padrão de formato personalizado `fff` ou `FFF`, sozinho ou com outros especificadores de formato personalizado como o parâmetro de formato.

## <a name="example"></a>Exemplo

O exemplo exibe o componente de milissegundos de um valor de [DateTime](xref:System.DateTime) e [DateTimeOffset](xref:System.DateTimeOffset) para console, sozinho e incluído em uma cadeia de caracteres de data e hora mais longa. 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class MillisecondDisplay
{
   public static void Main()
   {
      string dateString = "7/16/2008 8:32:45.126 AM";

      try
      {
         DateTime dateValue = DateTime.Parse(dateString);
         DateTimeOffset dateOffsetValue = DateTimeOffset.Parse(dateString);

         // Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", 
                           dateValue.ToString("fff"));
         Console.WriteLine("Millisecond component only: {0}", 
                           dateOffsetValue.ToString("fff"));

         // Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));

         // Append millisecond pattern to current culture's full date time pattern
         string fullPattern = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern;
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff");

         // Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", 
                           dateValue.ToString(fullPattern));
         Console.WriteLine("Modified full date time pattern: {0}",
                           dateOffsetValue.ToString(fullPattern));
      }
      catch (FormatException)
      {
         Console.WriteLine("Unable to convert {0} to a date.", dateString);
      }
   }
}
// The example displays the following output if the current culture is en-US:
//    Millisecond component only: 126
//    Millisecond component only: 126
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

```vb
Imports System.Globalization
Imports System.Text.REgularExpressions

Module MillisecondDisplay
   Public Sub Main()

      Dim dateString As String = "7/16/2008 8:32:45.126 AM"

      Try
         Dim dateValue As Date = Date.Parse(dateString)
         Dim dateOffsetValue As DateTimeOffset = DateTimeOffset.Parse(dateString)

         ' Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", _
                           dateValue.ToString("fff"))
         Console.WriteLine("Millisecond component only: {0}", _
                           dateOffsetValue.ToString("fff"))

         ' Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))

         ' Append millisecond pattern to current culture's full date time pattern
         Dim fullPattern As String = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff")

         ' Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateValue.ToString(fullPattern))                        
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateOffsetValue.ToString(fullPattern))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)      
      End Try
   End Sub
End Module
' The example displays the following output if the current culture is en-US:
'    Millisecond component only: 126
'    Millisecond component only: 126
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

O padrão de formato `fff` inclui os zeros à direita no valor de milissegundos. O padrão de formato `FFF` os suprime. A diferença é ilustrada no exemplo a seguir.

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine(dateValue.ToString("fff"));    
Console.WriteLine(dateValue.ToString("FFF"));
// The example displays the following output to the console:
//    180
//    18 
```

```vb
Dim dateValue As New Date(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLIne(dateValue.ToString("fff"))    
Console.WriteLine(dateValue.ToString("FFF"))
' The example displays the following output to the console:
'    180
'    18
```

Um problema ao definir um especificador de formato personalizado completo que inclui o componente de milissegundos de uma data e hora é que ele define um formato embutido em código que pode não corresponder à organização de elementos de hora na cultura atual do aplicativo. Uma alternativa melhor é recuperar um dos padrões de exibição de data e hora definidos pelo objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) da cultura atual e modificá-lo para incluir milissegundos. O exemplo também ilustra esta abordagem. Ele recupera o padrão de data e hora completo da cultura atual da propriedade [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) e insere o padrão personalizado `.ffff` após seu padrão de segundos. Observe que o exemplo usa uma expressão regular para executar esta operação em uma única chamada de método.

Você também pode usar um especificador de formato personalizado para exibir uma parte fracionária dos segundos que não sejam milissegundos. Por exemplo, o especificador de formato personalizado `f` ou `F` exibe décimos de segundo, o especificador de formato personalizado `ff` ou `FF` exibe centésimos de segundo e o especificador de formato personalizado `ffff` ou `FFFF` exibe décimos de milésimos de segundo. Partes fracionárias de um milissegundo são truncadas em vez de arredondadas na cadeia de caracteres retornada. Esses especificadores de formato são usados no exemplo a seguir.

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"));
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"));      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"));
// The example displays the following output to the console:
//    45.1 seconds
//    45.18 seconds
//    45.1800 seconds
```

```vb
Dim dateValue As New DateTime(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"))
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"))      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"))
' The example displays the following output to the console:
'    45.1 seconds
'    45.18 seconds
'    45.1800 seconds
```

> [!NOTE]
> É possível exibir unidades fracionárias muito pequenas de um segundo, como dez milésimos de segundo ou centésimos de milésimos de segundo. No entanto, esses valores podem não ser significativos. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.

## <a name="see-also"></a>Consulte também

[System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)

[Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md)




<!--HONumber=Dec16_HO1-->


