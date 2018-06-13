---
title: 'Como: permitir que os usuários a resolver horários ambíguos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083871dd97a36529351aacbdcd39980bdde74a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572821"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Como: permitir que os usuários a resolver horários ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

* Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

* Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

Este tópico mostra como permitir que o usuário resolva um horário ambíguo.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Permitir que o usuário resolva um horário ambíguo

1. Obtenha a entrada de data e hora do usuário.

2. Chamar o <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> método para determinar se o horário é ambíguo.

3. Se o tempo for ambíguo, chame o <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> método para recuperar uma matriz de <xref:System.TimeSpan> objetos. Cada elemento na matriz contém um deslocamento do UTC que pode ser mapeados para o horário ambíguo.

4. Permita que o usuário selecione o deslocamento desejado.

5. Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.

6. Chamar o `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> método para definir o UTC Data e hora do valor <xref:System.DateTime.Kind%2A> propriedade <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

O núcleo do exemplo de código usa uma matriz de <xref:System.TimeSpan> objetos para indicar possíveis deslocamentos do UTC do horário ambíguo. No entanto, esses deslocamentos provavelmente não serão significativos para o usuário. Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão. O código determina qual horário é padrão e qual é de verão comparando o deslocamento com o valor de <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriedade. Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.

Neste exemplo, todas as referências para o fuso horário local são feitas por meio de <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriedade; a hora local da zona nunca é atribuída a uma variável de objeto. Essa é uma prática recomendada, porque uma chamada para o <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> método invalida todos os objetos que o fuso horário local é atribuído a.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência a System.Core.dll seja adicionada ao projeto.

* Se o <xref:System> namespace importados com o `using` instrução (necessária em código c#).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[como: resolver horários ambíguos](../../../docs/standard/datetime/resolve-ambiguous-times.md)
