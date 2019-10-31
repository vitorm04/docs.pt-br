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
ms.openlocfilehash: 1b1178623258393eab28a7087eb04c47b55a9176
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122319"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Criando uma instância de um objeto DateTimeOffset

A estrutura de <xref:System.DateTimeOffset> oferece várias maneiras de criar novos valores de <xref:System.DateTimeOffset>. Muitos deles correspondem diretamente aos métodos disponíveis para instanciar novos valores de <xref:System.DateTime>, com aprimoramentos que permitem que você especifique o deslocamento do valor de data e hora do UTC (tempo Universal Coordenado). Em particular, você pode criar uma instância de um valor de <xref:System.DateTimeOffset> das seguintes maneiras:

- Usando um literal de data e hora.

- Chamando um construtor de <xref:System.DateTimeOffset>.

- Convertendo implicitamente um valor para <xref:System.DateTimeOffset> valor.

- Analisando a representação de cadeia de caracteres de data e hora.

Este tópico fornece mais detalhes e exemplos de código que ilustram esses métodos de instanciação de novos valores de <xref:System.DateTimeOffset>.

## <a name="date-and-time-literals"></a>Literais de data e hora

Para idiomas que dão suporte a ele, uma das maneiras mais comuns de instanciar um valor de <xref:System.DateTime> é fornecer a data e a hora como um valor literal embutido em código. Por exemplo, o código de Visual Basic a seguir cria um objeto <xref:System.DateTime> cujo valor é 1 de janeiro de 2008, às 10:00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> valores também podem ser inicializados usando literais de data e hora ao usar linguagens que dão suporte a literais de <xref:System.DateTime>. Por exemplo, o código de Visual Basic a seguir cria um objeto <xref:System.DateTimeOffset>.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

À medida que a saída do console mostra, o valor <xref:System.DateTimeOffset> criado dessa forma é atribuído ao deslocamento do fuso horário local. Isso significa que um valor <xref:System.DateTimeOffset> atribuído usando um literal de caractere não identificará um único ponto de tempo se o código for executado em computadores diferentes.

## <a name="datetimeoffset-constructors"></a>Construtores de DateTimeOffset

O tipo de <xref:System.DateTimeOffset> define seis construtores. Quatro delas correspondem diretamente a construtores de <xref:System.DateTime>, com um parâmetro adicional do tipo <xref:System.TimeSpan> que define o deslocamento de data e hora do UTC. Eles permitem que você defina um valor <xref:System.DateTimeOffset> com base no valor de seus componentes individuais de data e hora. Por exemplo, o código a seguir usa esses quatro construtores para instanciar <xref:System.DateTimeOffset> objetos com valores idênticos de 7/1/2008 12:05 AM + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Observe que, quando o valor do objeto <xref:System.DateTimeOffset> instanciado usando um objeto <xref:System.Globalization.PersianCalendar> como um dos argumentos para seu construtor é exibido para o console, ele é expresso como uma data no gregoriano em vez do calendário persa. Para produzir uma data usando o calendário persa, consulte o exemplo no tópico <xref:System.Globalization.PersianCalendar>.

Os outros dois construtores criam um objeto <xref:System.DateTimeOffset> de um valor <xref:System.DateTime>. O primeiro deles tem um único parâmetro, o valor <xref:System.DateTime> a ser convertido em um valor <xref:System.DateTimeOffset>. O deslocamento do valor <xref:System.DateTimeOffset> resultante depende da propriedade <xref:System.DateTime.Kind%2A> do parâmetro único do construtor. Se seu valor for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o deslocamento será definido igual a <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Caso contrário, o deslocamento será definido como igual ao fuso horário local. O exemplo a seguir ilustra o uso desse construtor para instanciar <xref:System.DateTimeOffset> objetos que representam UTC e o fuso horário local:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Chamar a sobrecarga do construtor de <xref:System.DateTimeOffset> que tem um único parâmetro <xref:System.DateTime> é equivalente a executar uma conversão implícita de um valor <xref:System.DateTime> para um valor de <xref:System.DateTimeOffset>.

O segundo construtor que cria um objeto de <xref:System.DateTimeOffset> de um valor de <xref:System.DateTime> tem dois parâmetros: o valor de <xref:System.DateTime> a ser convertido e um valor de <xref:System.TimeSpan> que representa o deslocamento de data e hora do UTC. Esse valor de deslocamento deve corresponder à propriedade <xref:System.DateTime.Kind%2A> do primeiro parâmetro do construtor ou um <xref:System.ArgumentException> é gerado. Se a propriedade <xref:System.DateTime.Kind%2A> do primeiro parâmetro for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o valor do segundo parâmetro deverá ser <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Se a propriedade <xref:System.DateTime.Kind%2A> do primeiro parâmetro for <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, o valor do segundo parâmetro deverá ser o deslocamento do fuso horário do sistema local. Se a propriedade <xref:System.DateTime.Kind%2A> do primeiro parâmetro for <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, o deslocamento poderá ser qualquer valor válido. O código a seguir ilustra as chamadas para esse construtor para converter <xref:System.DateTime> em valores <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Conversão de tipo implícita

O tipo de <xref:System.DateTimeOffset> dá suporte a uma conversão de tipo implícito: de um valor de <xref:System.DateTime> para um valor de <xref:System.DateTimeOffset>. (Uma conversão implícita de tipo é uma conversão de um tipo para outro que não requer uma conversão explícita (em C#) ou conversão (no Visual Basic) e não perde informações). Isso torna o código, como o seguinte, possível.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

O deslocamento do valor <xref:System.DateTimeOffset> resultante depende do valor da propriedade <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>. Se seu valor for <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, o deslocamento será definido igual a <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Se seu valor for <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ou <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, o deslocamento será definido igual ao do fuso horário local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analisando a representação da cadeia de caracteres de uma data e hora

O tipo de <xref:System.DateTimeOffset> dá suporte a quatro métodos que permitem converter a representação de cadeia de caracteres de uma data e hora em um valor de <xref:System.DateTimeOffset>:

- <xref:System.DateTimeOffset.Parse%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um valor de <xref:System.DateTimeOffset> e gera uma exceção se a conversão falhar.

- <xref:System.DateTimeOffset.TryParse%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um valor de <xref:System.DateTimeOffset> e retorna `false` se a conversão falhar.

- <xref:System.DateTimeOffset.ParseExact%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um formato especificado para um valor de <xref:System.DateTimeOffset>. Na ocorrência de erros, o método lança uma exceção.

- <xref:System.DateTimeOffset.TryParseExact%2A>, que tenta converter a representação de cadeia de caracteres de uma data e hora em um formato especificado para um valor de <xref:System.DateTimeOffset>. O método retornará `false` se a conversão falhar.

O exemplo a seguir ilustra as chamadas para cada um desses quatro métodos de conversão de cadeia de caracteres para criar uma instância de um valor <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
