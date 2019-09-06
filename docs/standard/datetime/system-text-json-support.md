---
title: Suporte a DateTime e DateTimeOffset em System.Text.Json
description: Uma visão geral de como os tipos DateTime e DateTimeOffset têm suporte na biblioteca System. Text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 5bff01b10b2bdea4fdcfee86e348c47f44d50103
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374471"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Suporte a DateTime e DateTimeOffset em System.Text.Json

A biblioteca System. Text. JSON analisa e grava <xref:System.DateTime> e <xref:System.DateTimeOffset> valores de acordo com o perfil estendido ISO 8601:-2019.
Os [conversores](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) fornecem suporte personalizado para serialização e desserialização <xref:System.Text.Json.JsonSerializer>com o.

## <a name="support-for-the-iso-8601-12019-format"></a>Suporte para o formato ISO 8601-1:2019

Os <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonReader> <xref:System.DateTime> <xref:System.DateTimeOffset> tipos, ,<xref:System.Text.Json.Utf8JsonWriter>e analisam e gravam e representam representações de texto de acordo com o perfil estendido do formato ISO 8601-1:2019; por exemplo, 2019-07-26T16 <xref:System.Text.Json.JsonElement> : 59:57-05:00.

<xref:System.DateTime>e <xref:System.DateTimeOffset> os dados podem ser serializados com <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

Eles também podem ser desserializados com <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

Com opções padrão, as <xref:System.DateTime> representações de entrada e <xref:System.DateTimeOffset> de texto devem estar em conformidade com o perfil ISO 8601-1:2019 estendido.
A tentativa de desserializar representações que não estão em conformidade com o perfil fará <xref:System.Text.Json.JsonSerializer> com que o <xref:System.Text.Json.JsonException>gere um:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

O <xref:System.Text.Json.JsonDocument> fornece acesso estruturado ao conteúdo de uma carga JSON, incluindo <xref:System.DateTime> e <xref:System.DateTimeOffset> representações. O exemplo a seguir mostra como, quando é dada uma coleção de temperaturas, a temperatura média nas segundas-feiras pode ser calculada:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

A tentativa de calcular a temperatura média devido a uma carga com representações <xref:System.DateTime> sem conformidade causará <xref:System.Text.Json.JsonDocument> a geração de <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

As gravações <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> e osdadosdenívelinferior:<xref:System.DateTimeOffset>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> análises e<xref:System.DateTimeOffset> dados:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

A tentativa de ler formatos sem conformidade com <xref:System.Text.Json.Utf8JsonReader> o fará com que ele gere um: <xref:System.FormatException>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a>Suporte personalizado para <xref:System.DateTime> e <xref:System.DateTimeOffset> em<xref:System.Text.Json.JsonSerializer>

Se você quiser que o serializador execute a análise ou a formatação personalizada, poderá implementar [conversores personalizados](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).
Veja aqui alguns exemplos:

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Usando `DateTime(Offset).Parse` o e o`DateTime(Offset).ToString`

Se você não puder determinar os formatos de suas <xref:System.DateTime> representações de entrada ou <xref:System.DateTimeOffset> de texto, poderá usar `DateTime(Offset).Parse` o método em sua lógica de leitura do conversor. Isso permite que você use o. O amplo suporte da net para análise de <xref:System.DateTime> vários <xref:System.DateTimeOffset> formatos de texto e, incluindo cadeias de caracteres não ISO 8601 e formatos ISO 8601 que não estão em conformidade com o perfil ISO 8601-1:2019 estendido. Essa abordagem é significativamente menos eficaz do que usar a implementação nativa do serializador.

Para serialização, você pode usar o `DateTime(Offset).ToString` método em sua lógica de gravação do conversor. Isso permite que você escreva <xref:System.DateTime> e <xref:System.DateTimeOffset> valores usando qualquer um dos [formatos de data e hora padrão](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)e os [formatos de data e hora personalizados](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
Isso também é significativamente menos eficaz do que usar a implementação nativa do serializador.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Ao implementar <xref:System.Text.Json.Serialization.JsonConverter%601>, e `T` é <xref:System.DateTime>, o `typeToConvert` parâmetro sempre `typeof(DateTime)`será.
O parâmetro é útil para lidar com casos polimórficos e ao usar genéricos para obter `typeof(T)` uma maneira de desempenho.

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Usando <xref:System.Buffers.Text.Utf8Parser> o e o<xref:System.Buffers.Text.Utf8Formatter>

Você pode usar os métodos de análise e formatação baseados em UTF-8 rápidos na lógica do conversor se suas <xref:System.DateTime> representações de entrada ou <xref:System.DateTimeOffset> de texto estiverem em conformidade com uma das [cadeias de caracteres de formato de data e hora padrão](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" ou "G", ou se você quiser Escreva de acordo com um desses formatos. Isso é muito mais rápido do `DateTime(Offset).Parse` que `DateTime(Offset).ToString`usar o e o.

Este exemplo mostra um conversor personalizado que serializa e <xref:System.DateTime> desserializa valores de acordo com [o formato padrão "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> O formato padrão "R" terá sempre 29 caracteres.

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Usando `DateTime(Offset).Parse` como um fallback para a análise nativa do serializador

Se, em geral, você <xref:System.DateTime> esperar <xref:System.DateTimeOffset> que sua entrada ou seus dados estejam de acordo com o perfil ISO 8601-1:2019 estendido, poderá usar a lógica de análise nativa do serializador. Você também pode implementar um mecanismo de fallback apenas no caso.
Este exemplo mostra que, após a falha de análise <xref:System.DateTime> de uma representação <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>de texto usando, o conversor analisa os dados com <xref:System.DateTime.Parse(System.String)>êxito usando.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>O perfil ISO 8601-1:2019 estendido em System. Text. JSON

### <a name="date-and-time-components"></a>Componentes de data e hora

O perfil ISO 8601-1:2019 estendido implementado <xref:System.Text.Json> em define os seguintes componentes para representações de data e hora. Esses componentes são usados para definir vários níveis de granularidade com suporte durante a análise e a <xref:System.DateTime> formatação <xref:System.DateTimeOffset> e as representações.

| Componente       | Formatar                      | Descrição                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| Month           | "MM"                        | 01-12                                                                           |
| Day             | "dd"                        | 01-28, 01-29, 01-30, 01-31 com base no mês/ano                                  |
| Hora            | "HH"                        | 00-23                                                                           |
| Minuto          | "mm"                        | 00-59                                                                           |
| Segundo          | "ss"                        | 00-59                                                                           |
| Segunda fração | "FFFFFFF"                   | Mínimo de um dígito, no máximo 16 dígitos                                      |
| Diferença de tempo     | "K"                         | "Z" ou "(' + '/'-') HH ': ' mm '                                                |
| Hora parcial    | "HH": "mm": "SS [FFFFFFF]"     | Tempo sem informações de deslocamento UTC                                             |
| Data completa       | "yyyy'-'MM'-'dd"            | Data do calendário                                                                   |
| Tempo total       | "Time'K parcial"           | UTC do dia ou hora local do dia com o deslocamento de tempo entre a hora local e o UTC |
| Data e hora       | "Hora completa ' ' T' ' ' | Data do calendário e hora do dia, por exemplo, 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Suporte para análise

Os seguintes níveis de granularidade são definidos para análise:

1. ' Data completa '
    1. "yyyy'-'MM'-'dd"

2. "Data completa ' T' ' ' hora ' ': ' ' minuto '"
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm"

3. "A data completa ' T' ' ' t ' ' hora parcial '"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

4. "" Data completa "' T' ' hora ' ': ' ' minuto ' ' deslocamento de tempo '"
    1. "yyyy'-'MM'-'dd'T'HH':'mmZ"
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm (' + '/'-') HH ': ' mm '

5. ' Data e hora '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ '
    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"
    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '
    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '

Se houver frações decimais para segundos, deve haver pelo menos um dígito; `2019-07-26T00:00:00.` não é permitido.
Embora sejam permitidos até 16 dígitos fracionários, somente os primeiros sete são analisados. Qualquer coisa além disso é considerada um zero.
Por exemplo, `2019-07-26T00:00:00.1234567890` será analisado como se `2019-07-26T00:00:00.1234567`fosse.
Isso é para se manter compatível com <xref:System.DateTime> a implementação, que está limitada a essa resolução.

Não há suporte para segundos bissextos.

### <a name="support-for-formatting"></a>Suporte para formatação

Os seguintes níveis de granularidade são definidos para formatação:

1. "A data completa ' T' ' ' t ' ' hora parcial '"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        Usado para formatar um <xref:System.DateTime> sem segundos fracionários e sem informações de deslocamento.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

        Usado para formatar um <xref:System.DateTime> com segundos fracionários, mas sem informações de deslocamento.

2. ' Data e hora '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ '

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> sem segundos fracionários, mas com um deslocamento UTC.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> com segundos fracionários e com um deslocamento UTC.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> sem segundos fracionários, mas com um deslocamento local.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> com segundos fracionários e com um deslocamento local.
