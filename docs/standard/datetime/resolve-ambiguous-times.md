---
title: 'Como: resolver horários ambíguos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122243"
---
# <a name="how-to-resolve-ambiguous-times"></a>Como: resolver horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

- Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

- Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

Este tópico mostra como resolver um tempo ambíguo supondo que ele representa o horário padrão do fuso horário.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Para apontar um horário ambíguo para o horário padrão de um fuso horário

1. Chame o método <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> para determinar se o tempo é ambíguo.

2. Se o tempo for ambíguo, subtraia a hora do objeto <xref:System.TimeSpan> retornado pela propriedade <xref:System.TimeZoneInfo.BaseUtcOffset%2A> do fuso horário.

3. Chame o método `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> para definir a propriedade <xref:System.DateTime.Kind%2A> do valor de data e hora UTC como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra como converter um horário ambíguo em UTC supondo que ele representa o horário padrão do fuso horário local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o valor de <xref:System.DateTime> passado para ele é ambíguo. Se o valor for ambíguo, o método retornará um valor <xref:System.DateTime> que representa a hora UTC correspondente. O método manipula essa conversão subtraindo o valor da propriedade <xref:System.TimeZoneInfo.BaseUtcOffset%2A> do fuso horário local da hora local.

Normalmente, uma hora ambígua é tratada chamando o método <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> para recuperar uma matriz de objetos <xref:System.TimeSpan> que contêm os deslocamentos de UTC possíveis. No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário. A propriedade <xref:System.TimeZoneInfo.BaseUtcOffset%2A> retorna o deslocamento entre o UTC e o horário padrão de um fuso horário.

Neste exemplo, todas as referências ao fuso horário local são feitas por meio da propriedade <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; o fuso horário local nunca é atribuído a uma variável de objeto. Essa é uma prática recomendada porque uma chamada para o método <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalida todos os objetos aos quais o fuso horário local está atribuído.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que o namespace <xref:System> seja importado com a instrução `using` ( C# obrigatória no código).

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como permitir que os usuários resolvam horários ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
