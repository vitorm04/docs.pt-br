---
title: Como serializar e desserializar JSON usando C# -.net
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3d3dc0011562e25854938aff857f2832a5978b49
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283329"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>Como serializar e desserializar JSON no .NET

Este artigo mostra como usar o namespace <xref:System.Text.Json> para serializar e desserializar de e para o JavaScript Object Notation (JSON).

As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).

A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> a `true` como "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana). Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.

## <a name="namespaces"></a>Namespaces

O namespace <xref:System.Text.Json> contém todos os pontos de entrada e os tipos principais. O namespace <xref:System.Text.Json.Serialization> contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização. Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atualmente, não há suporte para atributos do namespace <xref:System.Runtime.Serialization> no `System.Text.Json`.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Como gravar objetos .NET em JSON (Serialize)

Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

O exemplo a seguir cria JSON como uma cadeia de caracteres:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

O exemplo a seguir usa código síncrono para criar um arquivo JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

O exemplo a seguir usa código assíncrono para criar um arquivo JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado. Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Exemplo de serialização

Aqui está uma classe de exemplo que contém coleções e uma classe aninhada:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir. A saída JSON é reduzidos por padrão: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a>Serializar para UTF-8

Para serializar para UTF-8, chame o método <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

Uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que usa uma <xref:System.Text.Json.Utf8JsonWriter> também está disponível.

A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres. A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).

## <a name="serialization-behavior"></a>Comportamento de serialização

* Por padrão, todas as propriedades públicas são serializadas. Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).
* O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Por padrão, o JSON é reduzidos. Você pode [muito imprimir o JSON](#serialize-to-formatted-json).
* Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET. Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).
* Referências circulares são detectadas e exceções geradas. Para obter mais informações, consulte [emitir 38579 em referências circulares](https://github.com/dotnet/corefx/issues/38579) no repositório dotnet/Corefx no github.
* No momento, os campos são excluídos.

Os tipos com suporte incluem:

* Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.
* [Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.
* Matrizes unidimensionais e denteadas (`ArrayName[][]`).
* `Dictionary<string,TValue>` em que `TValue` é `object`, `JsonElement`ou um POCO.
* Coleções dos namespaces a seguir. Para obter mais informações, consulte o [problema no suporte de coleção](https://github.com/dotnet/corefx/issues/36643) no repositório dotnet/Corefx no github.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Como ler JSON em objetos .NET (desserializar)

Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da classe `WeatherForecast` mostrada anteriormente para o [exemplo de serialização](#serialization-example):

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Para desserializar de um arquivo usando código assíncrono, chame o método <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Desserializar de UTF-8

Para desserializar do UTF-8, chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> que usa uma `Utf8JsonReader` ou uma `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir. Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Comportamento de desserialização

* Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas. Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).
* Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.
* Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.
* A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte. Para obter mais informações, consulte o [problema do GitHub 38569 no suporte a objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) e o [problema 38163 em suporte à propriedade somente leitura](https://github.com/dotnet/corefx/issues/38163) no repositório dotnet/corefx no github.
* Por padrão, há suporte para enums como números. Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).
* Não há suporte para campos.
* Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw. Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).
* A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.

Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.

## <a name="serialize-to-formatted-json"></a>Serializar para JSON formatado

Para imprimir a saída JSON, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>Personalizar nomes e valores JSON

Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas. Os valores de enumeração são representados como números. Esta seção explica como:

* [Personalizar nomes de propriedade individuais](#customize-individual-property-names)
* [Converter todos os nomes de propriedade em camel case](#use-camel-case-for-all-json-property-names)
* [Implementar uma política de nomenclatura de propriedade personalizada](#use-a-custom-json-property-naming-policy)
* [Converter chaves de dicionário em camel case](#camel-case-dictionary-keys)
* [Converter enums em cadeias de caracteres e camel case](#enums-as-strings) 

Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Personalizar nomes de propriedade individuais

Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Veja um exemplo de tipo para serializar e o JSON resultante:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

O nome da propriedade definido por este atributo:

* Aplica-se em ambas as direções, para serialização e desserialização.
* Tem precedência sobre as políticas de nomenclatura de propriedade.

### <a name="use-camel-case-for-all-json-property-names"></a>Usar o camel case para todos os nomes de propriedade JSON

Para usar o camel case para todos os nomes de propriedade JSON, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Aqui está uma classe de exemplo para serializar e a saída JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

A política de nomenclatura de Propriedade do camel case:

* Aplica-se à serialização e desserialização.
* É substituído por `[JsonPropertyName]` atributos. É por isso que o nome da propriedade JSON `Wind` no exemplo não é o camel case.

### <a name="use-a-custom-json-property-naming-policy"></a>Usar uma política de nomenclatura de propriedade JSON personalizada

Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o método <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Em seguida, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como uma instância da sua classe de política de nomenclatura:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Aqui está uma classe de exemplo para serializar e a saída JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

A política de nomenclatura de propriedade JSON:

* Aplica-se à serialização e desserialização.
* É substituído por `[JsonPropertyName]` atributos. É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.

### <a name="camel-case-dictionary-keys"></a>Chaves de dicionário do camel case

Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as chaves de `string` poderão ser convertidas em camel case. Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

A serialização de um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria na saída JSON, como no exemplo a seguir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização. Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo se você especificar `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy`.

### <a name="enums-as-strings"></a>Enumerações como cadeias de caracteres

Por padrão, as enumerações são serializadas como números. Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Se o resumo for `Hot`, por padrão, o JSON serializado terá o valor numérico 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

O JSON resultante é semelhante ao exemplo a seguir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Excluir propriedades da serialização

Por padrão, todas as propriedades públicas são serializadas. Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções. Esta seção explica como excluir:

* [Propriedades individuais](#exclude-individual-properties)
* [Todas as propriedades somente leitura](#exclude-all-read-only-properties)
* [Todas as propriedades de valor nulo](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Excluir propriedades individuais

Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Aqui está um tipo de exemplo para serializar e a saída JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Excluir todas as propriedades somente leitura

Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público. Para excluir todas as propriedades somente leitura, defina o <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Aqui está um tipo de exemplo para serializar e a saída JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Essa opção se aplica somente à serialização. Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.

### <a name="exclude-all-null-value-properties"></a>Excluir todas as propriedades de valor nulo

Para excluir todas as propriedades de valor nulo, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como `true`, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Aqui está um objeto de exemplo para serializar e a saída JSON:

|Propriedade |Valor  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureCelsius| 25 |
| Resumo| nulo|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

Essa configuração se aplica à serialização e desserialização. Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Personalizar codificação de caracteres

Por padrão, o serializador escapa todos os caracteres não ASCII.  Ou seja, ele os substitui por `\uxxxx` em que `xxxx` é o código Unicode do caractere.  Por exemplo, se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializar conjuntos de caracteres de idioma

Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique [intervalo (s) Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Este código não sai de escape de caracteres cirílico ou grego. Se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Serializar caracteres específicos

Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape. O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Aqui está um exemplo de JSON produzido pelo código anterior:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializar todos os caracteres

Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Em comparação com o codificador padrão, o codificador de `UnsafeRelaxedJsonEscaping` é mais permissivo de permitir que os caracteres passem sem escape:
>
> * Ele não sai de caracteres sensíveis a HTML, como `<`, `>`, `&`e `'`.
> * Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.
>
> Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8. Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8`. Nunca permita que a saída de `UnsafeRelaxedJsonEscaping` bruta seja emitida em uma página HTML ou em um elemento `<script>`.

## <a name="serialize-properties-of-derived-classes"></a>Serializar Propriedades de classes derivadas

Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado. Por exemplo, suponha que você tenha uma classe `WeatherForecast` e uma classe derivada `WeatherForecastWithWind`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

E suponha que o argumento de tipo do método de `Serialize` em tempo de compilação seja `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Nesse cenário, a propriedade `WindSpeed` não é serializada, mesmo que o objeto `weatherForecast` seja, na verdade, um objeto `WeatherForecastWithWind`. Somente as propriedades da classe base são serializadas:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.

Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:

* Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Declare o objeto a ser serializado como `object`.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

No cenário de exemplo anterior, ambas as abordagens fazem com que a propriedade `WindSpeed` seja incluída na saída JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Para obter informações sobre desserialização polimórfica, consulte [dar suporte à desserialização polimórfica](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Permitir comentários e vírgulas à direita

Por padrão, comentários e vírgulas à direita não são permitidos em JSON. Para permitir comentários no JSON, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> como `JsonCommentHandling.Skip`.
E para permitir vírgulas à direita, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> como `true`. O exemplo a seguir mostra como permitir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Aqui está um exemplo de JSON com comentários e uma vírgula à direita:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Correspondência de propriedade que não diferencia maiúsculas de minúsculas

Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino. Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Aqui está um exemplo de JSON com nomes de Propriedade do camel case. Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Processar JSON de estouro

Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino. Por exemplo, suponha que o tipo de destino seja o seguinte:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

E o JSON a ser desserializado é o seguinte:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

Se você desserializar o JSON mostrado no tipo mostrado, as propriedades `DatesAvailable` e `SummaryWords` ficarão em qualquer lugar e serão perdidas. Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares chave-valor da propriedade `ExtensionData`:

|Propriedade |Valor  |Observações  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureCelsius| 0 | Incompatibilidade de maiúsculas e minúsculas (`temperatureCelsius` no JSON), portanto, a propriedade não está definida. |
| Resumo | Pontos ||
| ExtensionData | temperatureCelsius: 25 |Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|
| |SummaryWords:<br>Legais<br>Vento<br>Humid |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|

Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

Observe que o nome da propriedade `ExtensionData` não aparece no JSON. Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.

## <a name="ignore-null-when-deserializing"></a>Ignorar nulo ao desserializar

Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL. Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.

Por exemplo, suponha que o código a seguir represente o objeto de destino:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

E suponha que o JSON a seguir seja desserializado:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Após a desserialização, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é nula.

Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Com essa opção, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é o valor padrão "sem Resumo" após a desserialização.

Os valores nulos no JSON serão ignorados somente se forem válidos. Valores nulos para tipos de valores não anuláveis causam exceções. Para obter mais informações, consulte [emitir 40922 em tipos de valores não anuláveis](https://github.com/dotnet/corefx/issues/40922) no repositório dotnet/Corefx no github.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter e JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`. O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados. O método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> usa `Utf8JsonReader` nos bastidores.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET, como `String`, `Int32`e `DateTime`. O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados. O método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> usa `Utf8JsonWriter` nos bastidores.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento (DOM) somente leitura usando `Utf8JsonReader`. O DOM fornece acesso aleatório aos dados em uma carga JSON. Os elementos JSON que compõem a carga podem ser acessados por meio do tipo de <xref:System.Text.Json.JsonElement>. O tipo de `JsonElement` fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .NET comuns. `JsonDocument` expõe uma propriedade <xref:System.Text.Json.JsonDocument.RootElement>.

As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Usar o JsonDocument para acessar dados

O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.JsonDocument> para acesso aleatório a dados em uma cadeia de caracteres JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

O código anterior:

* Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString`.
* Calcula uma classificação média para objetos em uma matriz de `Students` que têm uma propriedade `Grade`. 
* Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.
* Conta os alunos incrementando uma `count` variável com cada iteração. Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, conforme mostrado no exemplo a seguir:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Veja um exemplo do JSON que esse código processa:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Usar JsonDocument para gravar JSON

O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

O código anterior:

* Lê um arquivo JSON, carrega os dados em um `JsonDocument`e grava JSON formatado (bem impresso) em um arquivo.
* Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.
* Quando terminar, o chamará <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> no gravador. Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado. 

Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

O resultado é a seguinte saída JSON bem impressa:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Usar Utf8JsonWriter

O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonWriter>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Usar Utf8JsonReader

O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonReader>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

O código anterior pressupõe que a variável `jsonUtf8` é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrar dados usando Utf8JsonReader

O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

O código anterior:

* Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8. Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>`, usando o seguinte código:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.
* Conta objetos e `name` valores de propriedade que terminam com "University".

Aqui está um exemplo de JSON que o código anterior pode ler. A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Recursos adicionais

* [Visão geral de System. Text. JSON](system-text-json-overview.md)
* [Referência da API System. Text. JSON](xref:System.Text.Json)
* [Gravar conversores personalizados para System. Text. JSON](system-text-json-converters-how-to.md)
* [Suporte a DateTime e DateTimeOffset em System. Text. JSON](../datetime/system-text-json-support.md)
* [Problemas do GitHub no repositório dotnet/corefx rotulados como JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
