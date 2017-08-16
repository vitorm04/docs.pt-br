---
title: "Como resolver horários ambíguos"
description: "Como resolver horários ambíguos"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f4ab3b4bf3487e70be7e885e9b8a2281927eb30e
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-resolve-ambiguous-times"></a>Como resolver horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

* Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

* Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

Este artigo mostra como resolver um horário ambíguo supondo que ele representa o horário padrão do fuso horário.

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Para apontar um horário ambíguo para o horário padrão de um fuso horário

1. Chame o método [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) para determinar se o horário é ambíguo.

2. Se o horário for ambíguo, subtraia o horário do objeto [TimeSpan](xref:System.TimeSpan) retornado pela propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) do fuso horário.

3. Chame `static` (`Shared` no Visual Basic) o método [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) para definir a propriedade [Kind](xref:System.DateTime.Kind) do valor de data e hora do UTC como [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como converter um [DateTime](xref:System.DateTime) ambíguo em UTC supondo que representa o horário padrão do fuso horário local. 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o valor [DateTime](xref:System.DateTime) passado para ele é ambíguo. Se o valor for ambíguo, o método retorna um valor [DateTime](xref:System.DateTime) que representa o horário UTC correspondente. O método trata essa conversão subtraindo do horário local o valor da propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) do fuso horário local. 

Normalmente, um horário ambíguo é tratado chamando o método [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) para recuperar uma matriz de objetos [TimeSpan](xref:System.TimeSpan) que contêm os possíveis deslocamentos de UTC do horário ambíguo. No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário. A propriedade [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) retorna a diferença entre o UTC e o horário padrão de um fuso horário.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Como permitir que os usuários resolvam horários ambíguos](let-users-resolve-ambiguous-times.md)


