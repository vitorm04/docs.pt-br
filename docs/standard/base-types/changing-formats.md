---
title: "Exemplo de expressão regular: alterando formatos de data"
description: "Exemplo de expressão regular alterando formatos de data"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3e196697-981c-4c1d-93dd-c3b236ef36dd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f801e8761ad2dfe80915cc4425c359cfae99949e
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expression-example-changing-date-formats"></a>Exemplo de expressão regular: alterando formatos de data

O seguinte exemplo de código usa o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) para substituir datas que têm o formato *mm/dd/aa* por datas que têm o formato *dd-mm-aa*.

## <a name="example"></a>Exemplo

```csharp
static string MDYToDMY(string input) 
{
   try {
      return Regex.Replace(input, 
            "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
            "${day}-${month}-${year}", RegexOptions.None,
            TimeSpan.FromMilliseconds(150));
   }         
   catch (RegexMatchTimeoutException) {
      return input;
   }
}
```

```vb
Function MDYToDMY(input As String) As String
   Try
      Return Regex.Replace(input, _
             "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
             "${day}-${month}-${year}", RegexOptions.None,
             TimeSpan.FromMilliseconds(150))
    Catch e As RegexMatchTimeoutException
       Return input
    End Try         
End Function
```

O código a seguir mostra como o método `MDYToDMY` pode ser chamado em um aplicativo. 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string dateString = DateTime.Today.ToString("d", 
                                        DateTimeFormatInfo.InvariantInfo);
      string resultString = MDYToDMY(dateString);
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString);
   }

   static string MDYToDMY(string input) 
   {
      try {
         return Regex.Replace(input, 
               "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
               "${day}-${month}-${year}", RegexOptions.None,
               TimeSpan.FromMilliseconds(150));
      }         
      catch (RegexMatchTimeoutException) {
         return input;
      }
   }

}
// The example displays the following output to the console if run on 8/21/2007:
//      Converted 08/21/2007 to 21-08-2007.
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module DateFormatReplacement
   Public Sub Main()
      Dim dateString As String = Date.Today.ToString("d", _
                                           DateTimeFormatInfo.InvariantInfo)
      Dim resultString As String = MDYToDMY(dateString)
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString)
   End Sub

    Function MDYToDMY(input As String) As String
       Try
          Return Regex.Replace(input, _
                 "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
                 "${day}-${month}-${year}", RegexOptions.None,
                 TimeSpan.FromMilliseconds(150))
        Catch e As RegexMatchTimeoutException
           Return input
        End Try         
    End Function
End Module
' The example displays the following output to the console if run on 8/21/2007:
'      Converted 08/21/2007 to 21-08-2007.
```

## <a name="comments"></a>Comentários

O padrão da expressão regular `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começar a correspondência em um limite de palavra.
`(?<month>\d{1,2})` | Corresponder a um ou dois dígitos decimais. Este é o grupo capturado do `month`.
`/` | Corresponde à barra.
`(?<day>\d{1,2})` | Corresponder a um ou dois dígitos decimais. Este é o grupo capturado do `day`.
`/` | Corresponde à barra.
`(?<year>\d{2,4})` | Corresponder de dois a quatro dígitos decimais. Este é o grupo capturado do `year`.
`\b` | Termina a correspondência em um limite de palavra.
 
O padrão `${day}-${month}-${year}` define a cadeia de caracteres de substituição conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`$(day)` | Adicionar a cadeia de caracteres capturada pelo grupo de captura `day`.
`-` | Adicionar um hífen.
`$(month)` | Adicionar a cadeia de caracteres capturada pelo grupo de captura `month`.
`-` | Adicionar um hífen.
`$(year)` | Adicionar a cadeia de caracteres capturada pelo grupo de captura `year`.
 
## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)

[Exemplos de expressões regulares](regex-examples.md)

