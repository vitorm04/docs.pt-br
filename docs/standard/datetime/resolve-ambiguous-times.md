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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106778"
---
# <a name="how-to-resolve-ambiguous-times"></a>Como: resolver horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

- Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

- Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

Este tópico mostra como resolver um tempo ambíguo supondo que ele representa o horário padrão do fuso horário.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Para apontar um horário ambíguo para o horário padrão de um fuso horário

1. Chame o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o tempo é ambíguo.

2. Se o tempo for ambíguo, subtraia a hora <xref:System.TimeSpan> do objeto retornado pela propriedade do <xref:System.TimeZoneInfo.BaseUtcOffset%2A> fuso horário.

3. Chame o `static` método`Shared` (no Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A> ) para <xref:System.DateTime.Kind%2A> definir a propriedade de valor de data e hora UTC <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>como.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra como converter um horário ambíguo em UTC supondo que ele representa o horário padrão do fuso horário local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o <xref:System.DateTime> valor passado para ele é ambíguo. Se o valor for ambíguo, o método retornará um <xref:System.DateTime> valor que representa a hora UTC correspondente. O método manipula essa conversão subtraindo o valor da <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Propriedade do fuso horário local da hora local.

Normalmente, uma hora ambígua é tratada chamando o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> objetos que contêm os deslocamentos de UTC possíveis. No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário. A <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade retorna o deslocamento entre o UTC e o horário padrão de um fuso horário.

Neste exemplo, todas as referências ao fuso horário local são feitas por meio da <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Propriedade; o fuso horário local nunca é atribuído a uma variável de objeto. Essa é uma prática recomendada porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos aos quais o fuso horário local está atribuído.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que o <xref:System> namespace seja importado `using` com a instrução ( C# obrigatória no código).

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como: Permitir que os usuários resolvam tempos ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
