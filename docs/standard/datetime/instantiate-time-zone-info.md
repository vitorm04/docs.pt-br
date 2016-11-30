---
title: "Como criar uma instância de um objeto TimeZoneInfo"
description: "Como criar uma instância de um objeto TimeZoneInfo"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 1c619cf6bd150e009367b43d1d83fa1713ec2690

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Como criar uma instância de um objeto TimeZoneInfo

A maneira mais comum para criar uma instância de um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) é recuperar informações sobre ele do sistema operacional. Este tópico aborda como criar uma instância de um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) do sistema local.

## <a name="to-instantiate-a-timezoneinfo-object"></a>Para criar uma instância de um objeto TimeZoneInfo

1. Declare um objeto [TimeZoneInfo](xref:System.TimeZoneInfo).

2. Chame o método `static` (`Shared` no Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)).

3. Solucione eventuais exceções geradas pelo método.

## <a name="example"></a>Exemplo

O código a seguir recupera um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário padrão do Leste dos EUA e exibe a hora oficial do Leste dos EUA que corresponde à hora local.

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

O único parâmetro do método [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) é o identificador do fuso horário que você deseja recuperar, que corresponde à propriedade [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) do objeto. O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário. Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo. Na maioria dos casos, seu valor corresponde à propriedade [StandardName](xref:System.TimeZoneInfo.StandardName) do objeto [TimeZoneInfo](xref:System.TimeZoneInfo), que é usada para fornecer o nome da hora padrão do fuso horário. No entanto, há exceções. A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores dos fusos horários presentes nele. Para obter uma ilustração, veja [Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md). O tópico [Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md) também contém uma lista de identificadores de fuso horário selecionados.

Se o fuso horário for encontrado, o método retornará seu objeto [TimeZoneInfo](xref:System.TimeZoneInfo). Se o fuso horário for encontrado mas seus dados estiverem corrompidos ou incompletos, o método gerará uma [InvalidTimeZoneException](xref:System.InvalidTimeZoneException). 

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md)


<!--HONumber=Nov16_HO5-->


