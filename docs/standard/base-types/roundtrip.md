---
title: Como aplicar uma viagem de ida e volta a valores de data e hora
description: Como aplicar uma viagem de ida e volta a valores de data e hora
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 15690f18-1bb9-4bb8-bc11-0b737e2f0859
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 79c4da0cc6b4436fcbd5b345e23b387f2ad933d1
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-round-trip-date-and-time-values"></a>Como aplicar uma viagem de ida e volta a valores de data e hora

Em muitos aplicativos, um valor de data e hora destina-se a identificar sem ambiguidade um único ponto no tempo. Este tópico mostra como salvar e restaurar um valor [DateTime](xref:System.DateTime) e um valor [DateTimeOffset](xref:System.DateTimeOffset) para que o valor restaurado identifique o mesmo horário que o valor salvo.

## <a name="to-round-trip-a-datetime-value"></a>Para fazer uma viagem de ida e volta de um valor DateTime

1. Converta o valor [DateTime](xref:System.DateTime) para a representação de cadeia de caracteres chamando o método [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) com o especificador de formato “o”.

2. Salve a representação de cadeia de caracteres do valor [DateTime](xref:System.DateTime) em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.

3. Recupere a cadeia de caracteres que representa o valor [DateTime](xref:System.DateTime).

4. Chame o método [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) e passe [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) como o valor do parâmetro *DateTimeStyles*.

O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor [DateTime](xref:System.DateTime).

```csharp
const string fileName = @".\DateFile.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTime dateToSave = DateTime.SpecifyKind(new DateTime(2008, 6, 12, 18, 45, 15), 
                                           DateTimeKind.Local);
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} ({1}) to {2}.", 
                  dateToSave.ToString(), 
                  dateToSave.Kind.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTime restoredDate;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), 
                                              fileName, 
                                              restoredDate.Kind.ToString());
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
//    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
//    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

```vb
Const fileName As String = ".\DateFile.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As Date = DateTime.SpecifyKind(#06/12/2008 6:45:15 PM#, _
                                              DateTimeKind.Local)
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} ({1}) to {2}.", dateToSave.ToString(), _
                  dateToSave.Kind.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDate As Date

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDate = DateTime.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), _
                  fileName, restoredDAte.Kind.ToString())
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
'    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
'    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

Ao fazer a viagem de ida e volta de um valor [DateTime](xref:System.DateTime), essa técnica consegue preservar o horário para todos os horários locais e universais. Por exemplo, se um valor [DateTime](xref:System.DateTime) local for salvo em um sistema nos EUA, o fuso horário padrão do Pacífico será restaurado em um sistema no fuso horário padrão da região central dos EUA; a data e hora restauradas estarão duas horas à frente da hora original, o que reflete a diferença de hora entre os dois fusos horários. No entanto, essa técnica não é necessariamente exata para horários não especificados. Todos os valores [DateTime](xref:System.DateTime) cuja propriedade [Kind](xref:System.DateTime.Kind) é [Unspecified](xref:System.DateTimeKind.Unspecified) são tratados como se fossem horários locais. Se não for o caso, o [DateTime](xref:System.DateTime) não conseguirá identificar o momento correto. A solução alternativa para essa limitação é acoplar rigorosamente um valor de data e hora com seu fuso horário para salvar e restaurar a operação.

## <a name="to-round-trip-a-datetimeoffset-value"></a>Para fazer uma viagem de ida e volta de um valor DateTimeOffset

Converta o valor [DateTimeOffset](xref:System.DateTimeOffset) para a representação de cadeia de caracteres chamando o método [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) com o especificador de formato “o”.

2. Salve a representação de cadeia de caracteres do valor [DateTimeOffset](xref:System.DateTimeOffset) em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.

3. Recupere a cadeia de caracteres que representa o valor [DateTimeOffset](xref:System.DateTimeOffset).

4. Chame o método [DateTimeOffset.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTimeOffset.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) e passe [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) como o valor do parâmetro *styles*.

O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
const string fileName = @".\DateOff.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTimeOffset dateToSave = new DateTimeOffset(2008, 6, 12, 18, 45, 15, 
                                               new TimeSpan(7, 0, 0));
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTimeOffset restoredDateOff;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDateOff = DateTimeOffset.Parse(dateString, null, 
                                       DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), 
                  fileName);
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
//    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
//    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

```vb
Const fileName As String = ".\DateOff.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As New DateTimeOffset(2008, 6, 12, 18, 45, 15, _
                                     New TimeSpan(7, 0, 0))
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDateOff As DateTimeOffset

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDateOff = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), fileName)
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
'    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
'    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

Essa técnica sempre identifica sem ambiguidade um valor [DateTimeOffset](xref:System.DateTimeOffset) como um único momento. Em seguida, o valor pode ser convertido para UTC (Tempo Universal Coordenado) chamando o método [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) ou pode ser convertido para o horário em um fuso horário específico chamando o método [DateTimeOffset.ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) ou [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo). A principal limitação dessa técnica é que a aritmética de data e hora, quando executada em um valor [DateTimeOffset](xref:System.DateTimeOffset) que representa o horário em determinado fuso horário, talvez não produza resultados precisos para esse fuso horário. Isso ocorre porque, quando um valor [DateTimeOffset](xref:System.DateTimeOffset) é instanciado, é dissociado do seu fuso horário. Portanto, as regras de ajuste do fuso horário não podem mais ser aplicadas quando você executa cálculos de data e hora. É possível solucionar esse problema definindo um tipo personalizado que inclui um valor de data e hora e o respectivo fuso horário.

## <a name="see-also"></a>Consulte também

[Executando operações de formatação](performing-formatting-operations.md)

[Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md)


