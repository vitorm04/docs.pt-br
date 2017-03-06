---
title: "Convertendo horários entre fusos horários"
description: "Convertendo horários entre fusos horários"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: c2baa48c3b79dfbc5d39652cc57fe015a2313d6e

---

# <a name="converting-times-between-time-zones"></a>Convertendo horários entre fusos horários

Está se tornando cada vez mais importante para qualquer aplicativo que trabalha com datas e horas lidar com diferenças entre fusos horários. Os aplicativos não podem mais presumir que todos os horários podem ser expressos na hora local, que é a hora disponível na estrutura [System.DateTime](xref:System.DateTime). Por exemplo, uma página da Web que exibe a hora atual no leste dos Estados Unidos não terá credibilidade para um cliente no leste da Ásia. Este tópico explica como converter horas de um fuso horário para outro, bem como converter valores de [System.DateTimeOffset](xref:System.DateTimeOffset) que têm percepção limitada de fuso horário.

## <a name="converting-to-coordinated-universal-time"></a>Convertendo para o Tempo Universal Coordenado

O UTC (Tempo Universal Coordenado) é um padrão de tempo atômico de alta precisão. Os fusos horários do mundo são expressos como deslocamentos positivos ou negativos com relação ao UTC. Sendo assim, o UTC fornece uma espécie de hora livre de fuso horário ou com fuso horário neutro. O uso da hora em UTC é recomendado quando a portabilidade da data e hora entre computadores é importante. Converter fusos horários individuais em UTC facilita comparações de hora.

> [!NOTE]
> Você também pode serializar uma estrutura [DateTimeOffset](xref:System.DateTimeOffset) para representar sem ambiguidade um único ponto no tempo. Uma vez que objetos [DateTimeOffset](xref:System.DateTimeOffset) armazenam um valor de data e hora com seu deslocamento com relação ao UTC, eles sempre representam um ponto específico no tempo em relação ao UTC.

A maneira mais fácil para converter uma hora para UTC é chamar o método `static` (`Shared` no Visual Basic) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx). 

> [!IMPORTANT]
> O método `TimeZoneInfo.ConvertTimeToUtc(DateTime)` não está disponível no .NET Core. 

A conversão exata executada pelo método depende do valor da propriedade [Kind](xref:System.DateTime.Kind) do parâmetro `DateTime`, conforme é mostrado na tabela a seguir.

Propriedade [DateTime.Kind](xref:System.DateTimeKind) | Conversão
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | Converte a hora local para UTC.
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | Presume que o parâmetro `DateTime` é a hora local e converte a hora local para UTC.
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | Retorna o parâmetro `DateTime` inalterado.

O código a seguir converte a hora local atual para UTC e exibe o resultado no console.

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
>O método [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) não produz necessariamente resultados idênticos aos dos métodos [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) e [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime). Se o fuso horário local do sistema host incluir várias regras de ajuste, [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) aplica a regra apropriada a uma data e hora determinada. Os outros dois métodos sempre aplicam a regra de ajuste mais recente.

Se o valor de data e hora não representar a hora local ou o UTC, o método [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) provavelmente retornará um resultado com erro. No entanto, você pode usar o método [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) para converter a data e hora de um fuso horário especificado. Para obter detalhes sobre como recuperar um objeto TimeZoneInfo que representa o fuso horário de destino, consulte [Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md). O código a seguir usa o método [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) para converter a Zona de Tempo Oriental para UTC.

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

Observe que esse método lança um [ArgumentException](xref:System.ArgumentException) se a propriedade [Kind](xref:System.DateTimeKind) do objeto [DateTime](xref:System.DateTime) e o fuso horário forem incompatíveis. Uma incompatibilidade ocorre se a propriedade Kind for é [DateTimeKind.Local](xref:System.DateTimeKind.Local), mas o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) não representar o fuso horário local ou se a propriedade Kind for [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) mas o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) não for igual a [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

Todos esses métodos usam valores de [DateTime](xref:System.DateTime) como parâmetros e retornam um valor de [DateTime](xref:System.DateTime). Para valores de [DateTimeOffset](xref:System.DateTimeOffset), a estrutura [DateTimeOffset](xref:System.DateTimeOffset) tem um método de instância [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) que converte a data e hora da instância atual para UTC. O exemplo a seguir chama o método [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) para converter uma hora local e várias outras horas para UTC (Tempo Universal Coordenado).

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a>Convertendo UTC em um fuso horário designado

Para converter UTC em hora local, consulte a seção [Convertendo UTC em hora local](#converting-utc-to-local-time) a seguir. 

Para converter de UTC para a hora correspondente a qualquer fuso horário que você designar, chame o método [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx). 

> [!IMPORTANT]
> Atualmente, o método “TimeZoneInfo.ConvertTimeFromUtc” não está disponível no .NET Core. 

O método utiliza dois parâmetros:

* O UTC a ser convertido. Ele deve ser um valor [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) está definida como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified). 

* O fuso horário no qual o UTC deve ser convertido. 

O código a seguir converte o UTC para o Horário Padrão Central.

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a>Convertendo UTC em hora local

Para converter UTC para a hora local, chame o método [DateTime.ToLocalTime](xref:System.DateTime) do objeto [DateTime](xref:System.DateTime) cuja hora você deseja converter. O comportamento exato do método depende do valor da propriedade [Kind](xref:System.DateTime.Kind) do objeto, conforme mostrado na tabela a seguir.

Propriedade [DateTime.Kind](xref:System.DateTimeKind) | Conversão
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | Retorna o valor [DateTime](xref:System.DateTime) inalterado.
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | Pressupõe que o valor [DateTime](xref:System.DateTime) está no UTC e o converte do UTC para a hora local.
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | Converte o valor [DateTime](xref:System.DateTime) para a hora local.

## <a name="converting-between-any-two-time-zones"></a>Convertendo entre dois fusos horários

Você pode converter entre quaisquer dois fusos horários usando o método estático [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)). Os parâmetros desse método são o valor de [DateTime](xref:System.DateTime) a ser convertido, um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário do valor de data e hora e um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa o fuso horário no qual o valor de data e hora deverá ser convertido.

O método requer que a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora a ser convertido e o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) ou o identificador de fuso horário que representa seu fuso horário, sejam correspondentes. Caso contrário, uma [ArgumentException](xref:System.ArgumentException) será gerada. Por exemplo, se a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora for [DateTimeKind.Local](xref:System.DateTimeKind.Local), uma exceção será lançada se o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) passado como um parâmetro para o método não for igual a [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local). Também é gerada uma exceção se o identificador passado como parâmetro para o método não for igual a [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id).

O exemplo a seguir usa o método [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) para converter da Hora Oficial do Havaí para a hora local.

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a>Convertendo valores de DateTimeOffset

Valores de data e hora representados por objetos [System.DateTimeOffset](xref:System.DateTimeOffset) não são totalmente cientes do fuso horário porque o objeto é desassociado de seu fuso horário no momento em que é instanciado. No entanto, em muitos casos o aplicativo precisa apenas converter uma data e hora com base em dois deslocamentos diferentes do UTC, em vez da hora em fusos horários específicos. Para realizar essa conversão, você pode chamar o método [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) da instância atual. O parâmetro único do método é [TimeSpan](xref:System.TimeSpan), que representa o deslocamento do novo valor de data e hora que o método deve retornar.  

Por exemplo, se a data e hora da solicitação de um usuário de uma página da Web for conhecida e for serializada como uma cadeia de caracteres no formato MM/dd/aaaa hh:mm:ss zzzz, o seguinte método `ReturnTimeOnServer` converte esse valor de data e hora para a data e hora no servidor Web.

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

Se a cadeia de caracteres "9/1/2007 5:32:07 -05:00" for passada ao método, representando a data e hora em um fuso horário cinco horas anteriores ao UTC, ele retornará 9/1/2007 3:32:07 AM -07:00 para um servidor localizado nos EUA. Fuso horário padrão do Pacífico.

A classe [TimeZoneInfo](xref:System.TimeZoneInfo) também inclui um método [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) com sobrecarga que realiza conversões de fuso horário com valores de [System.DateTimeOffset](xref:System.DateTimeOffset). Os parâmetros do método são um valor de [System.DateTimeOffset](xref:System.DateTimeOffset) e uma referência ao fuso horário no qual a hora será convertida. A chamada de método retorna um valor [System.DateTimeOffset](xref:System.DateTimeOffset). Por exemplo, o método `ReturnTimeOnServer` no exemplo anterior poderia ser reescrito da seguinte maneira para chamar o método [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)).

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a>Consulte também

[TimeZoneInfo](xref:System.TimeZoneInfo)

[Datas, horas e fusos horários](index.md)

[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md)





<!--HONumber=Nov16_HO3-->


