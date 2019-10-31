---
title: 'Como: criar fusos horários com regras de ajuste'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: 4ef3d93746c5688dc15fc7e45d9be054dcfba4c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132546"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Como: criar fusos horários com regras de ajuste

As informações precisas de fuso horário exigidas por um aplicativo podem não estar presentes em um sistema específico por vários motivos:

- O fuso horário nunca foi definido no registro do sistema local.

- Os dados sobre o fuso horário foram modificados ou removidos do registro.

- O fuso horário não tem informações precisas sobre os ajustes de fuso horário de um período histórico específico.

Nesses casos, você pode chamar o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> para definir o fuso horário exigido pelo seu aplicativo. Você pode usar as sobrecargas desse método para criar um fuso horário com ou sem regras de ajuste. Se o fuso horário der suporte ao horário de verão, você poderá definir ajustes com regras de ajuste fixos ou flutuantes. (Para obter as definições desses termos, consulte a seção "terminologia de fuso horário" em [visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Os fusos horários personalizados criados chamando o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> não são adicionados ao registro. Em vez disso, eles podem ser acessados somente por meio da referência de objeto retornada pela chamada do método <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.

Este tópico mostra como criar um fuso horário com regras de ajuste. Para criar um fuso horário que não ofereça suporte às regras de ajuste de horário de verão, consulte [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Para criar um fuso horário com regras de ajuste flutuantes

1. Para cada ajuste (ou seja, para cada transição de distância de e para o horário padrão em um intervalo de tempo específico), faça o seguinte:

    1. Defina o tempo de transição inicial para o ajuste de fuso horário.

       Você deve chamar o método <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> e passá-lo um valor <xref:System.DateTime> que define a hora da transição, um valor inteiro que define o mês da transição, um valor inteiro que define a semana em que a transição ocorre e um valor <xref:System.DayOfWeek> que define o dia da semana em que ocorre a transição. Essa chamada de método instancia um objeto <xref:System.TimeZoneInfo.TransitionTime>.

    2. Defina o tempo de transição final para o ajuste de fuso horário. Isso requer outra chamada para o método <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>. Essa chamada de método instancia um segundo objeto <xref:System.TimeZoneInfo.TransitionTime>.

    3. Chame o método <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> e passe-o para as datas de início e término efetivas do ajuste, um objeto <xref:System.TimeSpan> que define a quantidade de tempo na transição e os dois objetos <xref:System.TimeZoneInfo.TransitionTime> que definem quando ocorre a transição de e para o horário de verão. Essa chamada de método instancia um objeto <xref:System.TimeZoneInfo.AdjustmentRule>.

    4. Atribua o objeto <xref:System.TimeZoneInfo.AdjustmentRule> a uma matriz de objetos <xref:System.TimeZoneInfo.AdjustmentRule>.

2. Defina o nome de exibição do fuso horário. O nome de exibição segue um formato bastante padrão no qual o deslocamento do fuso horário do UTC (tempo Universal Coordenado) é incluído entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais cidades no fuso horário ou um ou mais dos cou ntries ou regiões no fuso horário.

3. Defina o nome do horário padrão do fuso horário. Normalmente, essa cadeia de caracteres também é usada como o identificador do fuso horário.

4. Defina o nome do horário de Verão do fuso horário.

5. Se você quiser usar um identificador diferente do nome padrão do fuso horário, defina o identificador de fuso horário.

6. Crie uma instância de um objeto <xref:System.TimeSpan> que define o deslocamento do fuso horário do UTC. Fusos horários com horas posteriores a UTC têm um deslocamento positivo. Fusos horários com horários que são anteriores ao UTC têm um deslocamento negativo.

7. Chame o método <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> para instanciar o novo fuso horário.

## <a name="example"></a>Exemplo

O exemplo a seguir define um fuso horário padrão central para o Estados Unidos que inclui regras de ajuste para uma variedade de intervalos de tempo de 1918 para o presente.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

O fuso horário criado neste exemplo tem várias regras de ajuste. Deve-se ter cuidado para garantir que as datas de início e término efetivas de qualquer regra de ajuste não se sobreponham às datas de outra regra de ajuste. Se houver uma sobreposição, uma <xref:System.InvalidTimeZoneException> será lançada.

Para regras de ajuste flutuantes, o valor 5 é passado para o parâmetro `week` do método <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> para indicar que a transição ocorre na última semana de um mês específico.

Ao criar a matriz de objetos <xref:System.TimeZoneInfo.AdjustmentRule> para usar na chamada do método <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>, o código pode inicializar a matriz para o tamanho exigido pelo número de ajustes a serem criados para o fuso horário. Em vez disso, este exemplo de código chama o método <xref:System.Collections.Generic.List%601.Add%2A> para adicionar cada regra de ajuste a uma coleção genérica <xref:System.Collections.Generic.List%601> de objetos <xref:System.TimeZoneInfo.AdjustmentRule>. Em seguida, o código chama o método <xref:System.Collections.Generic.List%601.CopyTo%2A> para copiar os membros dessa coleção para a matriz.

O exemplo também usa o método <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> para definir ajustes de data fixas. Isso é semelhante à chamada do método <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, exceto pelo fato de que ele requer apenas a hora, o mês e o dia dos parâmetros de transição.

O exemplo pode ser testado usando um código como o seguinte:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que os seguintes namespaces sejam importados:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
