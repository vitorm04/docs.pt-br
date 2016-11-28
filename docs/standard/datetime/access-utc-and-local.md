---
title: "Como acessar os objetos de fuso horário UTC e Local predefinidos"
description: "Como acessar os objetos de fuso horário predefinidos UTC e Local"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: ab419cf365b61399ea41e99c15e276584ad0db31

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Como acessar os objetos de fuso horário UTC e Local predefinidos

A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) fornece duas propriedades, `Utc` e `Local`, que fornecem seu acesso de código para objetos de fuso horário predefinidos. Este tópico discute como acessar os objetos `TimeZoneInfo` retornados por essas propriedades.

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Para acessar o objeto TimeZoneInfo de UTC (Tempo Universal Coordenado)

1. Use a propriedade **static** (**Shared** no Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) para acessar o Tempo Universal Coordenado.

2. Em vez de atribuir o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) retornado pela propriedade a uma variável de objeto, continue a acessar o Tempo Universal Coordenado por meio da propriedade [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc).


## <a name="to-access-the-local-time-zone"></a>Para acessar o fuso horário local

1. Use a propriedade **static** (**Shared** no Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) para acessar o fuso horário do sistema local.

2. Em vez de atribuir o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) retornado pela propriedade a uma variável de objeto, continue a acessar o fuso horário local por meio da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).

## <a name="example"></a>Exemplo

O código a seguir usa as propriedades [TimeZoneInfo](xref:System.TimeZoneInfo.Local) e [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) para converter um horário do fuso horário Padrão do Leste do Canadá e EUA, bem como para exibir o nome do fuso horário no console.

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

Você deve sempre acessar o fuso horário local por meio da propriedade [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) em vez de atribuir o fuso horário local a uma variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo). Da mesma forma, você deve sempre acessar o Tempo Universal Coordenado por meio da propriedade [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) em vez de atribuir o fuso horário UTC a uma variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo). Isso impede que a variável de objeto [TimeZoneInfo](xref:System.TimeZoneInfo) seja invalidada por um método externo.


## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md)



<!--HONumber=Nov16_HO4-->


