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
ms.openlocfilehash: 8198359e2c54c4ed098703fbcc070f7469b3362a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344649"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Suporte a DateTime e DateTimeOffset em System.Text.Json

A biblioteca System. Text. JSON analisa e grava <xref:System.DateTime> e <xref:System.DateTimeOffset> valores de acordo com o perfil estendido ISO 8601:-2019.
Os [conversores](xref:System.Text.Json.Serialization.JsonConverter%601) fornecem suporte personalizado para serialização e desserialização com <xref:System.Text.Json.JsonSerializer>.
O suporte personalizado também pode ser implementado ao usar <xref:System.Text.Json.Utf8JsonReader> e <xref:System.Text.Json.Utf8JsonWriter>.

## <a name="support-for-the-iso-8601-12019-format"></a>Suporte para o formato ISO 8601-1:2019

Os tipos <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>e <xref:System.Text.Json.JsonElement> analisam e gravam <xref:System.DateTime> e <xref:System.DateTimeOffset> representações de texto de acordo com o perfil estendido do formato ISO 8601-1:2019; por exemplo, 2019-07-26T16:59:57-05:00.

os dados de <xref:System.DateTime> e <xref:System.DateTimeOffset> podem ser serializados com <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Eles também podem ser desserializados com <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Com as opções padrão, os <xref:System.DateTime> de entrada e as representações de texto de <xref:System.DateTimeOffset> devem estar em conformidade com o perfil ISO 8601-1:2019 estendido.
A tentativa de desserializar representações que não estão em conformidade com o perfil fará com que <xref:System.Text.Json.JsonSerializer> gere um <xref:System.Text.Json.JsonException>:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

O <xref:System.Text.Json.JsonDocument> fornece acesso estruturado ao conteúdo de uma carga JSON, incluindo <xref:System.DateTime> e <xref:System.DateTimeOffset> representações. O exemplo a seguir mostra como, quando é dada uma coleção de temperaturas, a temperatura média nas segundas-feiras pode ser calculada:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

A tentativa de calcular a temperatura média devido a uma carga com representações <xref:System.DateTime> não compatíveis causará <xref:System.Text.Json.JsonDocument> lançar uma <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

O nível inferior <xref:System.Text.Json.Utf8JsonWriter> grava <xref:System.DateTime> e dados de <xref:System.DateTimeOffset>:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> analisa <xref:System.DateTime> e dados de <xref:System.DateTimeOffset>:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

A tentativa de ler formatos sem conformidade com <xref:System.Text.Json.Utf8JsonReader> fará com que ele gere uma <xref:System.FormatException>:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Suporte personalizado para <xref:System.DateTime> e <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Ao usar <xref:System.Text.Json.JsonSerializer>

Se você quiser que o serializador execute a análise ou a formatação personalizada, poderá implementar [conversores personalizados](xref:System.Text.Json.Serialization.JsonConverter%601).
Veja aqui alguns exemplos:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Usando `DateTime(Offset).Parse` e `DateTime(Offset).ToString`

Se você não puder determinar os formatos de sua entrada <xref:System.DateTime> ou de <xref:System.DateTimeOffset> representações de texto, poderá usar o método `DateTime(Offset).Parse` em sua lógica de leitura do conversor. Isso permite que você use o. Amplo suporte da rede para análise de vários formatos de texto <xref:System.DateTime> e <xref:System.DateTimeOffset>, incluindo cadeias de caracteres não ISO 8601 e formatos ISO 8601 que não estão em conformidade com o perfil ISO 8601-1:2019 estendido. Essa abordagem é significativamente menos eficaz do que usar a implementação nativa do serializador.

Para serialização, você pode usar o método `DateTime(Offset).ToString` em sua lógica de gravação do conversor. Isso permite que você escreva <xref:System.DateTime> e <xref:System.DateTimeOffset> valores usando qualquer um dos [formatos de data e hora padrão](../base-types/standard-date-and-time-format-strings.md)e os [formatos de data e hora personalizados](../base-types/custom-date-and-time-format-strings.md).
Isso também é significativamente menos eficaz do que usar a implementação nativa do serializador.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Ao implementar <xref:System.Text.Json.Serialization.JsonConverter%601>e `T` é <xref:System.DateTime>, o parâmetro `typeToConvert` sempre será `typeof(DateTime)`.
O parâmetro é útil para lidar com casos polimórficos e ao usar genéricos para obter `typeof(T)` de uma maneira de desempenho.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Usando <xref:System.Buffers.Text.Utf8Parser> e <xref:System.Buffers.Text.Utf8Formatter>

Você pode usar os métodos de análise e formatação baseados em UTF-8 rápidos na lógica do conversor se suas <xref:System.DateTime> de entrada ou representações de texto de <xref:System.DateTimeOffset> são compatíveis com uma das [cadeias de caracteres de formato de data e hora padrão](../base-types/standard-date-and-time-format-strings.md)"R", "l", "O" ou "G", ou você deseja gravar de acordo com um desses formatos. Isso é muito mais rápido do que usar `DateTime(Offset).Parse` e `DateTime(Offset).ToString`.

Este exemplo mostra um conversor personalizado que serializa e desserializa <xref:System.DateTime> valores de acordo com [o formato padrão "R"](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> O formato padrão "R" terá sempre 29 caracteres.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Usando `DateTime(Offset).Parse` como um fallback para a análise nativa do serializador

Se você costuma esperar que sua entrada <xref:System.DateTime> ou <xref:System.DateTimeOffset> dados para estar em conformidade com o perfil ISO 8601-1:2019 estendido, você pode usar a lógica de análise nativa do serializador. Você também pode implementar um mecanismo de fallback apenas no caso.
Este exemplo mostra que, após a falha de análise de uma representação de texto <xref:System.DateTime> usando <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, o conversor analisa os dados com êxito usando <xref:System.DateTime.Parse(System.String)>.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Ao gravar com <xref:System.Text.Json.Utf8JsonWriter>

Se você quiser gravar uma representação de texto <xref:System.DateTime> ou <xref:System.DateTimeOffset> personalizada com <xref:System.Text.Json.Utf8JsonWriter>, poderá Formatar sua representação personalizada para uma <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`ou <xref:System.Text.Json.JsonEncodedText>, em seguida, passá-la para o método <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> ou <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> correspondente.

O exemplo a seguir mostra como um formato de <xref:System.DateTime> personalizado pode ser criado com <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>e, em seguida, escrito com o método <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Ao ler com <xref:System.Text.Json.Utf8JsonReader>

Se você quiser ler uma representação de texto <xref:System.DateTime> ou de <xref:System.DateTimeOffset> personalizada com <xref:System.Text.Json.Utf8JsonReader>, poderá obter o valor do token JSON atual como um <xref:System.String> usando <xref:System.Text.Json.Utf8JsonReader.GetString>e, em seguida, analisar o valor usando a lógica personalizada.

O exemplo a seguir mostra como uma representação de texto de <xref:System.DateTimeOffset> personalizada pode ser recuperada usando <xref:System.Text.Json.Utf8JsonReader.GetString>e, em seguida, analisada usando <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>O perfil ISO 8601-1:2019 estendido em System. Text. JSON

### <a name="date-and-time-components"></a>Componentes de data e hora

O perfil ISO 8601-1:2019 estendido implementado no <xref:System.Text.Json> define os seguintes componentes para representações de data e hora. Esses componentes são usados para definir vários níveis de granularidade com suporte ao analisar e formatar <xref:System.DateTime> e <xref:System.DateTimeOffset> representações.

| Componente       | Formato                      | Descrição                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Ano            | "yyyy"                      | 0001-9999                                                                       |
| Mês           | "MM"                        | 01-12                                                                           |
| Dia             | "dd"                        | 01-28, 01-29, 01-30, 01-31 com base no mês/ano                                  |
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
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
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
Por exemplo, `2019-07-26T00:00:00.1234567890` será analisado como se fosse `2019-07-26T00:00:00.1234567`.
Isso é para se manter compatível com a implementação de <xref:System.DateTime>, que é limitada a essa resolução.

Não há suporte para segundos bissextos.

### <a name="support-for-formatting"></a>Suporte para formatação

Os seguintes níveis de granularidade são definidos para formatação:

1. "A data completa ' T' ' ' t ' ' hora parcial '"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([o especificador de formato classificável ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Usado para formatar um <xref:System.DateTime> sem segundos fracionários e sem informações de deslocamento.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF

        Usado para formatar um <xref:System.DateTime> com segundos fracionários, mas sem informações de deslocamento.

2. ' Data e hora '
    1. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ssZ '

        Usado para formatar um <xref:System.DateTime> sem segundos fracionários, mas com um deslocamento UTC.

    2. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFFZ"

        Usado para formatar um <xref:System.DateTime> com segundos fracionários e com um deslocamento UTC.

    3. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' SS (' + '/'-') HH ': ' mm '

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> sem segundos fracionários, mas com um deslocamento local.

    4. "yyyy'-'MM'-'dd'T'HH ': ' mm ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '

        Usado para formatar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> com segundos fracionários e com um deslocamento local.

Se houver, um máximo de sete dígitos fracionários será gravado. Isso se alinha com a implementação de <xref:System.DateTime>, que é limitada a essa resolução.
