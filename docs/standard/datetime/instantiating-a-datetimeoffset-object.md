---
title: Criando uma instância de um objeto DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8f4254da256bf2814f66aa62d43204fb302701
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494051"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Criando uma instância de um objeto DateTimeOffset

O <xref:System.DateTimeOffset> estrutura oferece várias maneiras de criar um novo <xref:System.DateTimeOffset> valores. Muitas delas correspondem diretamente aos métodos disponíveis para instanciar novos <xref:System.DateTime> valores, com aprimoramentos que permitem que você especifique o valor de data e hora de deslocamento do tempo Universal Coordenado (UTC). Em particular, você pode instanciar um <xref:System.DateTimeOffset> valor das seguintes maneiras:

* Usando uma data e hora literal.

* Chamando um <xref:System.DateTimeOffset> construtor.

* Convertendo implicitamente um valor para <xref:System.DateTimeOffset> valor.

* Analisando a representação de cadeia de caracteres de data e hora.

Este tópico fornece mais detalhes e exemplos de código que ilustram esses métodos de instanciar <xref:System.DateTimeOffset> valores.

## <a name="date-and-time-literals"></a>Literais de data e hora

Para linguagens que dão suporte a ele, uma das maneiras mais comuns para instanciar um <xref:System.DateTime> valor é fornecer a data e hora como um valor literal embutido em código. Por exemplo, o código de Visual Basic a seguir cria um <xref:System.DateTime> objeto cujo valor é 1 de janeiro de 2008, às 10H00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> valores também podem ser inicializados usando literais de data e hora ao usar linguagens que dão suporte a <xref:System.DateTime> literais. Por exemplo, o código de Visual Basic a seguir cria um <xref:System.DateTimeOffset> objeto.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Como mostra a saída do console, o <xref:System.DateTimeOffset> valor criado dessa maneira é atribuído o deslocamento do fuso horário local. Isso significa que um <xref:System.DateTimeOffset> valor atribuído usando um caractere literal não identifica um único ponto de tempo se o código é executado em computadores diferentes.

## <a name="datetimeoffset-constructors"></a>Construtores DateTimeOffset

O <xref:System.DateTimeOffset> tipo define seis construtores. Quatro deles correspondem diretamente aos <xref:System.DateTime> construtores, com um parâmetro adicional do tipo <xref:System.TimeSpan> que define a data e tempo de deslocamento do UTC. Eles permitem que você defina um <xref:System.DateTimeOffset> valor com base no valor da sua data individual e componentes de tempo. Por exemplo, o código a seguir usa esses quatro construtores para instanciar <xref:System.DateTimeOffset> objetos com valores idênticos de 7/1/2008 12:05, + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Observe que, quando o valor da <xref:System.DateTimeOffset> objeto instanciado usando um <xref:System.Globalization.PersianCalendar> objeto como um dos argumentos para o construtor é exibido no console, ele é expresso como uma data no calendário gregoriano em vez do calendário persa. Para exibir uma data usando o calendário persa, consulte o exemplo a <xref:System.Globalization.PersianCalendar> tópico.

Os outros dois construtores criam um <xref:System.DateTimeOffset> do objeto de um <xref:System.DateTime> valor. O primeiro desses tem um único parâmetro, o <xref:System.DateTime> valor a ser convertido para um <xref:System.DateTimeOffset> valor. O deslocamento do resultante <xref:System.DateTimeOffset> depende do valor de <xref:System.DateTime.Kind%2A> propriedade de um único parâmetro do construtor. Se o valor for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o deslocamento é definido igual ao <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Caso contrário, o deslocamento será definido como igual ao fuso horário local. O exemplo a seguir ilustra o uso desse construtor para instanciar <xref:System.DateTimeOffset> objetos que representam o UTC e o fuso horário local:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Chamar a sobrecarga da <xref:System.DateTimeOffset> construtor que tem uma única <xref:System.DateTime> parâmetro é equivalente a executar uma conversão implícita de um <xref:System.DateTime> de valor para um <xref:System.DateTimeOffset> valor.

O segundo construtor que cria um <xref:System.DateTimeOffset> do objeto de um <xref:System.DateTime> valor tem dois parâmetros: o <xref:System.DateTime> valor a ser convertido e um <xref:System.TimeSpan> que representa a data e hora do valor de deslocamento do UTC. Esse valor de deslocamento deverá corresponder para o <xref:System.DateTime.Kind%2A> propriedade do primeiro parâmetro do construtor ou um <xref:System.ArgumentException> é gerada. Se o <xref:System.DateTime.Kind%2A> é de propriedade do primeiro parâmetro <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o valor do segundo parâmetro deve ser <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Se o <xref:System.DateTime.Kind%2A> é de propriedade do primeiro parâmetro <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, o valor do segundo parâmetro deve ser o deslocamento de fuso horário do sistema local. Se o <xref:System.DateTime.Kind%2A> é de propriedade do primeiro parâmetro <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, o deslocamento pode ser qualquer valor válido. O código a seguir ilustra chamadas para esse construtor para converter <xref:System.DateTime> para <xref:System.DateTimeOffset> valores.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Conversão implícita de tipo

O <xref:System.DateTimeOffset> tipo dá suporte a uma conversão implícita de tipos: de um <xref:System.DateTime> valor para um <xref:System.DateTimeOffset> valor. (Uma conversão implícita de tipo é uma conversão de um tipo para outro que não requer uma conversão explícita (em C#) ou conversão (no Visual Basic) e não perde informações). Isso torna o código, como o seguinte, possível.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

O deslocamento do resultante <xref:System.DateTimeOffset> depende do valor de <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> valor da propriedade. Se o valor for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o deslocamento é definido igual ao <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Se o valor for <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ou <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, o deslocamento é definido igual do fuso horário local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Ao analisar a representação de cadeia de caracteres de data e hora

O <xref:System.DateTimeOffset> tipo dá suporte a quatro métodos que permitem que você converta a representação de cadeia de caracteres de uma data e hora em um <xref:System.DateTimeOffset> valor:

* <xref:System.DateTimeOffset.Parse%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um <xref:System.DateTimeOffset> de valor e gera uma exceção se a conversão falhar.

* <xref:System.DateTimeOffset.TryParse%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um <xref:System.DateTimeOffset> valor e retorna `false` se a conversão falhar.

* <xref:System.DateTimeOffset.ParseExact%2A>, que tenta converter a representação de cadeia de caracteres de data e hora em um formato especificado em um <xref:System.DateTimeOffset> valor. Na ocorrência de erros, o método lança uma exceção.

* <xref:System.DateTimeOffset.TryParseExact%2A>, que tenta converter a representação de cadeia de caracteres de data e hora em um formato especificado em um <xref:System.DateTimeOffset> valor. O método retornará `false` se a conversão falhar.

O exemplo a seguir ilustra chamadas para cada um desses métodos de conversão de cadeia de caracteres de quatro para instanciar um <xref:System.DateTimeOffset> valor.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
