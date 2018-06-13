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
ms.openlocfilehash: a92081a164d15e5150c582b37c6c688cd15e619e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571193"
---
# <a name="how-to-resolve-ambiguous-times"></a>Como: resolver horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

* Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

* Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

Este tópico mostra como resolver um horário ambíguo, supondo que ele representa a hora de padrão do fuso horário.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Para apontar um horário ambíguo para o horário padrão de um fuso horário

1. Chamar o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o horário é ambíguo.

2. Se o tempo for ambíguo, subtraia o horário do <xref:System.TimeSpan> objeto retornado pelo fuso horário <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade.

3. Chamar o `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> método para definir o UTC Data e hora do valor <xref:System.DateTime.Kind%2A> propriedade <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra como converter um horário ambíguo UTC, supondo que ele representa a hora de padrão do fuso horário local.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

O exemplo consiste em um método chamado `ResolveAmbiguousTime` que determina se o <xref:System.DateTime> valor passado a ele é ambíguo. Se o valor for ambíguo, o método retorna um <xref:System.DateTime> valor que representa a hora UTC correspondente. O método trata essa conversão subtraindo o valor do fuso horário local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade do horário local.

Normalmente, um tempo ambíguo é tratado chamando o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> deslocamentos de objetos que contêm o UTC horário ambíguo possíveis. No entanto, esse exemplo faz a suposição arbitrária de que um horário ambíguo deve sempre apontar para o horário padrão do fuso horário. O <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade retorna a diferença entre o UTC e a hora padrão de uma zona de tempo.

Neste exemplo, todas as referências para o fuso horário local são feitas por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade; a hora local da zona nunca é atribuída a uma variável de objeto. Essa é uma prática recomendada, porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos que o fuso horário local é atribuído a.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência a System.Core.dll seja adicionada ao projeto.

* Se o <xref:System> namespace importados com o `using` instrução (necessária em código c#).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[como: permitir que os usuários a resolver horários ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
