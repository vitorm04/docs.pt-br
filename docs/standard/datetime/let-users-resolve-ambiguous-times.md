---
title: 'Como: permitir que os usuários resolvam tempos ambíguos'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122273"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Como: permitir que os usuários resolvam tempos ambíguos

Um horário ambíguo é um horário que aponta para mais de um UTC (Tempo Universal Coordenado). Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Ao processar um horário ambíguo, você pode executar uma das seguintes ações:

- Se o horário ambíguo for um item de dados inserido pelo usuário, você pode deixar que o usuário resolva a ambiguidade.

- Faça uma suposição de como o tempo aponta para o UTC. Por exemplo, você pode supor que um horário ambíguo é sempre expresso no horário padrão do fuso horário.

Este tópico mostra como permitir que um usuário resolva um horário ambíguo.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Permitir que o usuário resolva um horário ambíguo

1. Obtenha a entrada de data e hora do usuário.

2. Chame o método <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> para determinar se o tempo é ambíguo.

3. Se o tempo for ambíguo, chame o método <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> para recuperar uma matriz de objetos <xref:System.TimeSpan>. Cada elemento na matriz contém um deslocamento UTC para o qual a hora ambígua pode ser mapeada.

4. Permita que o usuário selecione o deslocamento desejado.

5. Obtenha a data e hora de UTC subtraindo o deslocamento selecionado pelo usuário do horário local.

6. Chame o método `static` (`Shared` no Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> para definir a propriedade <xref:System.DateTime.Kind%2A> do valor de data e hora UTC como <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir solicita que o usuário insira uma data e hora e, se ela for ambígua, permite que o usuário selecione o horário UTC para o qual o horário ambíguo aponta.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

O núcleo do código de exemplo usa uma matriz de <xref:System.TimeSpan> objetos para indicar possíveis deslocamentos do tempo ambíguo do UTC. No entanto, esses deslocamentos provavelmente não serão significativos para o usuário. Para esclarecer o significado dos deslocamentos, o código também observa se um deslocamento representa o horário padrão do fuso horário local ou seu horário de verão. O código determina qual é a hora padrão e em qual horário é o horário de verão comparando o deslocamento com o valor da propriedade <xref:System.TimeZoneInfo.BaseUtcOffset%2A>. Essa propriedade indica a diferença entre o UTC e o horário padrão do fuso horário.

Neste exemplo, todas as referências ao fuso horário local são feitas por meio da propriedade <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; o fuso horário local nunca é atribuído a uma variável de objeto. Essa é uma prática recomendada porque uma chamada para o método <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalida todos os objetos aos quais o fuso horário local está atribuído.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que o namespace <xref:System> seja importado com a instrução `using` ( C# obrigatória no código).

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como resolver horários ambíguos](../../../docs/standard/datetime/resolve-ambiguous-times.md)
