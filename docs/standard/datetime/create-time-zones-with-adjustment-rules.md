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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80a5c04f7807638a4a8b114828083835f348ac08
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494129"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Como: criar fusos horários com regras de ajuste

As informações precisas de fuso horário que são exigidas por um aplicativo não podem estar presentes em um determinado sistema por diversos motivos:

* O fuso horário nunca foi definido no registro do sistema local.

* Dados sobre o fuso horário foi modificados ou removidos do registro.

* O fuso horário não tem informações precisas sobre ajustes de fuso horário para um determinado período de histórico.

Nesses casos, você pode chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método para definir o fuso horário exigido pelo seu aplicativo. Você pode usar as sobrecargas desse método para criar um fuso horário com ou sem regras de ajuste. Se o fuso horário der suporte ao horário de verão, você pode definir ajustes com a regras de ajuste fixa ou flutuante. (Para obter definições desses termos, consulte a seção "Terminologia de fuso horário" em [visão geral do fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Fusos horários personalizados criados ao chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são adicionados ao registro. Em vez disso, eles podem ser acessados apenas pela referência de objeto retornada pelo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> chamada de método.

Este tópico mostra como criar um fuso horário com regras de ajuste. Para criar um fuso horário que não dá suporte a regras de ajuste de horário de verão, consulte [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Para criar um fuso horário com regras de ajuste flutuantes

1. Para cada ajuste (isto é, para cada transição de e para o horário padrão de volta em um intervalo de tempo específico), faça o seguinte:

    1. Defina o tempo de transição inicial para o ajuste de fuso horário.

       Você deve chamar o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> método e passá-lo um <xref:System.DateTime> valor que define o tempo de transição, um valor inteiro que define o mês de transição, um valor inteiro que define a semana no qual ocorre a transição, e um <xref:System.DayOfWeek> valor que define o dia da semana no qual ocorre a transição. Esta chamada de método instancia um <xref:System.TimeZoneInfo.TransitionTime> objeto.

    2. Defina o tempo de transição final para o ajuste de fuso horário. Isso requer outra chamada para o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> método. Esta chamada de método cria uma instância de um segundo <xref:System.TimeZoneInfo.TransitionTime> objeto.

    3. Chame o <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> método e passá-lo eficaz datas de início e término do ajuste, um <xref:System.TimeSpan> objeto que define a quantidade de tempo na transição e os dois <xref:System.TimeZoneInfo.TransitionTime> objetos que definem quando as transições para e de verão hora de ocorrer. Esta chamada de método instancia um <xref:System.TimeZoneInfo.AdjustmentRule> objeto.

    4. Atribuir a <xref:System.TimeZoneInfo.AdjustmentRule> objeto em uma matriz de <xref:System.TimeZoneInfo.AdjustmentRule> objetos.

2. Defina nome de exibição do fuso horário. O nome de exibição segue um formato padrão no qual o deslocamento do fuso horário do tempo Universal Coordenado (UTC) é colocado entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais das cidades no fuso horário ou em um ou mais do cou ntries ou regiões no fuso horário.

3. Defina o nome do horário de padrão do fuso horário. Normalmente, essa cadeia de caracteres também é usada como identificador do fuso horário.

4. Defina o nome do horário de verão do fuso horário.

5. Se você quiser usar um identificador diferente do nome do padrão do fuso horário, defina o identificador de fuso horário.

6. Criar uma instância de um <xref:System.TimeSpan> objeto que define o deslocamento do fuso horário do UTC. Fusos horários com horários posteriores ao UTC têm um deslocamento positivo. Fusos horários com horários anteriores ao UTC têm um deslocamento negativo.

7. Chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> método para instanciar o novo fuso horário.

## <a name="example"></a>Exemplo

O exemplo a seguir define um fuso horário padrão Central para os Estados Unidos que inclui as regras de ajuste para uma variedade de intervalos de tempo de 1918 atual.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

O fuso horário criado neste exemplo tem várias regras de ajuste. É necessário ter cuidado para garantir que a efetivo datas de início e término de qualquer regra de ajuste não coincidem com as datas de outra regra de ajuste. Se houver uma sobreposição, um <xref:System.InvalidTimeZoneException> é gerada.

Para regras de ajuste flutuantes, o valor 5 é passado para o `week` parâmetro do <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> método para indicar que a transição ocorre na última semana de um mês específico.

Na criação da matriz de <xref:System.TimeZoneInfo.AdjustmentRule> objetos a serem usados no <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> chamada de método, o código pode inicializar a matriz para o tamanho exigido pelo número de ajustes a serem criados para o fuso horário. Em vez disso, este exemplo de código chama o <xref:System.Collections.Generic.List%601.Add%2A> método para adicionar cada regra de ajuste para um genérico <xref:System.Collections.Generic.List%601> coleção de <xref:System.TimeZoneInfo.AdjustmentRule> objetos. O código, em seguida, chama o <xref:System.Collections.Generic.List%601.CopyTo%2A> método para copiar os membros dessa coleção para a matriz.

O exemplo também usa o <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> método para definir os ajustes de data fixa. Isso é semelhante a chamar o <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> método, exceto que ela exige apenas a hora, mês e dia dos parâmetros de transição.

O exemplo pode ser testado usando um código como o seguinte:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll seja adicionada ao projeto.

* Se os seguintes namespaces sejam importados:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
* [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
* [Como criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
