---
title: Como serializar e desserializar JSON usando C#-.NET
description: Saiba como usar o System.Text.Json namespace para serializar e desserializar do JSON no .net. Inclui o código de exemplo.
ms.date: 11/05/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c1358b2b63a92cb50b853043adbfaae23ccd897
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329866"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Como serializar e desserializar (empacotar e desempacotar) JSON no .NET

Este artigo mostra como usar o <xref:System.Text.Json?displayProperty=fullName> namespace para serializar e desserializar de JavaScript Object Notation (JSON). Se você estiver portando um código existente do `Newtonsoft.Json` , consulte [como migrar `System.Text.Json` para o ](system-text-json-migrate-from-newtonsoft-how-to.md).

As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).

A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana). Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.

Os exemplos de código referem-se à seguinte classe e variantes dela:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Namespaces

O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais. O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização. Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization>Não há suporte para atributos do namespace no `System.Text.Json` .

## <a name="how-to-write-net-objects-to-json-serialize"></a>Como gravar objetos .NET em JSON (Serialize)

Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método.

O exemplo a seguir cria JSON como uma cadeia de caracteres:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

O exemplo a seguir usa código síncrono para criar um arquivo JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

O exemplo a seguir usa código assíncrono para criar um arquivo JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado. Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Exemplo de serialização

Aqui está uma classe de exemplo que contém propriedades de tipo de coleção e um tipo definido pelo usuário:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> "POCO" significa [objeto CLR antigo](https://en.wikipedia.org/wiki/Plain_old_CLR_object). Um POCO é um tipo .NET que não depende de nenhum tipo específico de estrutura, por exemplo, por meio de herança ou atributos.

A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir. A saída JSON é reduzidos por padrão:

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

O exemplo a seguir mostra o mesmo JSON, mas formatado (ou seja, muito impresso com espaço em branco e recuo):

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

Para serializar para UTF-8, chame o <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> método:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

Uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> também está disponível.

A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres. A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).

## <a name="serialization-behavior"></a>Comportamento de serialização
::: zone pivot="dotnet-5-0"

* Por padrão, todas as propriedades públicas são serializadas. Você pode [especificar propriedades a serem ignoradas](#ignore-properties).
* O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Por padrão, o JSON é reduzidos. Você pode [muito imprimir o JSON](#serialize-to-formatted-json).
* Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET. Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).
* Por padrão, referências circulares são detectadas e exceções geradas. Você pode [preservar referências e manipular referências circulares](#preserve-references-and-handle-circular-references).
* Por padrão, os [campos](../../csharp/programming-guide/classes-and-structs/fields.md) são ignorados. Você pode [incluir campos](#include-fields).

Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes. Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Por padrão, todas as propriedades públicas são serializadas. Você pode [especificar propriedades a serem ignoradas](#ignore-properties).
* O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Por padrão, o JSON é reduzidos. Você pode [muito imprimir o JSON](#serialize-to-formatted-json).
* Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET. Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).
* Referências circulares são detectadas e exceções geradas.
* Os [campos](../../csharp/programming-guide/classes-and-structs/fields.md) são ignorados.
::: zone-end

Os tipos com suporte incluem:
::: zone pivot="dotnet-5-0"

* Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.
* [Pocos (objetos CLR antigos)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)definidos pelo usuário.
* Matrizes unidimensionais e denteadas ( `T[][]` ).
* Coleções e dicionários dos namespaces a seguir.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.
* [Pocos (objetos CLR antigos)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)definidos pelo usuário.
* Matrizes unidimensionais e denteadas ( `ArrayName[][]` ).
* `Dictionary<string,TValue>` onde `TValue` é `object` , `JsonElement` , ou um poco.
* Coleções dos namespaces a seguir.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Como ler JSON em objetos .NET (desserializar)

Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método.

O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da `WeatherForecastWithPOCOs` classe mostrada anteriormente para o [exemplo de serialização](#serialization-example):

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Para desserializar de um arquivo usando código assíncrono, chame o <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> método:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Desserializar de UTF-8

Para desserializar do UTF-8, chame uma <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> sobrecarga que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>` , conforme mostrado nos exemplos a seguir. Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Comportamento de desserialização

Os seguintes comportamentos se aplicam ao desserializar JSON:

::: zone pivot="dotnet-5-0"

* Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas. Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).
* Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.
* Os construtores não públicos são ignorados pelo serializador.
* Há suporte para desserialização para objetos imutáveis ou propriedades somente leitura. Consulte [tipos e registros imutáveis](#immutable-types-and-records).
* Por padrão, há suporte para enums como números. Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).
* Por padrão, os campos são ignorados. Você pode [incluir campos](#include-fields).
* Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw. Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).
* A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.

Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes. Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas. Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching). ASP.NET Core aplicativos [especificam a diferenciação de maiúsculas e minúsculas por padrão](#web-defaults-for-jsonserializeroptions).
* Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.
* Um construtor sem parâmetros, que pode ser público, interno ou privado, é usado para desserialização.
* A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.
* Por padrão, há suporte para enums como números. Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).
* Não há suporte para campos.
* Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw. Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).
* A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.

Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes. Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).
::: zone-end

Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.

## <a name="serialize-to-formatted-json"></a>Serializar para JSON formatado

Para imprimir a saída JSON com muita impressão, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a>Incluir campos

::: zone pivot="dotnet-5-0"
Use a <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> configuração global ou o atributo [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) para incluir campos ao serializar ou desserializar, conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

Para ignorar campos somente leitura, use a <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> configuração global.
::: zone-end

::: zone pivot="dotnet-core-3-1"
Não há suporte para campos no System.Text.Json no .NET Core 3,1. [Conversores personalizados](system-text-json-converters-how-to.md) podem fornecer essa funcionalidade.
::: zone-end

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

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

Para usar o camel case para todos os nomes de propriedade JSON, defina como <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Aqui está uma classe de exemplo para serializar e a saída JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* É substituído por `[JsonPropertyName]` atributos. É por isso que o nome da propriedade JSON `Wind` no exemplo não é camel case.

### <a name="use-a-custom-json-property-naming-policy"></a>Usar uma política de nomenclatura de propriedade JSON personalizada

Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> método, conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

Em seguida, defina a <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriedade como uma instância da sua classe de política de nomenclatura:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Aqui está uma classe de exemplo para serializar e a saída JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>` , as `string` chaves poderão ser convertidas em camel case. Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Serializar um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria em uma saída JSON como o exemplo a seguir:

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

A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização. Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo que você especifique `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy` .

### <a name="enums-as-strings"></a>Enumerações como cadeias de caracteres

Por padrão, as enumerações são serializadas como números. Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .

Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Se o resumo for `Hot` , por padrão, o JSON serializado terá o valor numérico 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

O JSON resultante é semelhante ao exemplo a seguir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a>Ignorar Propriedades

Por padrão, todas as propriedades públicas são serializadas. Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções. Esta seção explica como ignorar:

::: zone pivot="dotnet-5-0"

* [Propriedades individuais](#ignore-individual-properties)
* [Todas as propriedades somente leitura](#ignore-all-read-only-properties)
* [Todas as propriedades de valor nulo](#ignore-all-null-value-properties)
* [Todas as propriedades de valor padrão](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Propriedades individuais](#ignore-individual-properties)
* [Todas as propriedades somente leitura](#ignore-all-read-only-properties)
* [Todas as propriedades de valor nulo](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a>Ignorar propriedades individuais

Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Aqui está um tipo de exemplo para serializar e a saída JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
Você pode especificar a exclusão condicional definindo a propriedade do atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` . A <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enumeração fornece as seguintes opções:

* `Always` -A propriedade é sempre ignorada. Se não `Condition` for especificado, essa opção será assumida.
* `Never` -A propriedade é sempre serializada e desserializada, independentemente das `DefaultIgnoreCondition` `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` configurações globais, e.
* `WhenWritingDefault` -A propriedade será ignorada na serialização se for um tipo de referência `null` ou um tipo de valor `default` .
* `WhenWritingNull` -A propriedade será ignorada na serialização se for um tipo de referência `null` .

O exemplo a seguir ilustra o uso da Propriedade do atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a>Ignorar todas as propriedades somente leitura

Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público. Para ignorar todas as propriedades somente leitura ao serializar, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true` , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Aqui está um tipo de exemplo para serializar e a saída JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Essa opção se aplica somente à serialização. Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.

::: zone pivot="dotnet-5-0"
Essa opção se aplica somente a propriedades. Para ignorar campos somente leitura ao [serializar campos](#include-fields), use a <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> configuração global.
::: zone-end

### <a name="ignore-all-null-value-properties"></a>Ignorar todas as propriedades de valor nulo

::: zone pivot="dotnet-5-0"
Para ignorar todas as propriedades de valor nulo, defina a <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> propriedade como <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
Para ignorar todas as propriedades de valor nulo ao serializar, defina a <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> propriedade como `true` , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Aqui está um objeto de exemplo para serializar e a saída JSON:

|Propriedade |Valor  |
|---------|---------|
| Data    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureCelsius| 25 |
| Resumo| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a>Ignorar todas as propriedades de valor padrão

::: zone pivot="dotnet-5-0"
Para evitar a serialização de valores padrão em Propriedades de tipo de valor, defina a <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> propriedade como <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

A `WhenWritingDefault` configuração também impede a serialização de propriedades de tipo de referência de valor nulo.

::: zone pivot="dotnet-core-3-1"
Não há uma maneira interna de impedir a serialização de propriedades com padrões de tipo de valor no System.Text.Json .NET Core 3,1.
::: zone-end

## <a name="customize-character-encoding"></a>Personalizar codificação de caracteres

Por padrão, o serializador escapa todos os caracteres não ASCII.  Ou seja, ele substitui por `\uxxxx` onde `xxxx` está o código Unicode do caractere.  Por exemplo, se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializar conjuntos de caracteres de idioma

Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique os [intervalos Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância do <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Este código não sai de escape de caracteres cirílico ou grego. Se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

### <a name="serialize-specific-characters"></a>Serializar caracteres específicos

Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape. O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Aqui está um exemplo de JSON produzido pelo código anterior:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializar todos os caracteres

Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , conforme mostrado no exemplo a seguir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Em comparação com o codificador padrão, o `UnsafeRelaxedJsonEscaping` codificador é mais permissivo de permitir que os caracteres passem sem escape:
>
> * Ele não sai de caracteres sensíveis a HTML, como `<` ,, `>` `&` e `'` .
> * Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.
>
> Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8. Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8` . Nunca permita que a `UnsafeRelaxedJsonEscaping` saída bruta seja emitida em uma página HTML ou em um `<script>` elemento.

## <a name="serialize-properties-of-derived-classes"></a>Serializar Propriedades de classes derivadas

Não há suporte para a serialização de uma hierarquia de tipo polimórfico. Por exemplo, se uma propriedade for definida como uma interface ou uma classe abstrata, somente as propriedades definidas na interface ou na classe abstrata serão serializadas, mesmo que o tipo de tempo de execução tenha propriedades adicionais. As exceções a esse comportamento são explicadas nesta seção.

Por exemplo, suponha que você tenha uma `WeatherForecast` classe e uma classe derivada `WeatherForecastDerived` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

E suponha que o argumento de tipo do `Serialize` método em tempo de compilação seja `WeatherForecast` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que o `weatherForecast` objeto seja, na verdade, um `WeatherForecastDerived` objeto. Somente as propriedades da classe base são serializadas:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.

Para serializar as propriedades do tipo derivado no exemplo anterior, use uma das seguintes abordagens:

* Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Declare o objeto a ser serializado como `object` .

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

No cenário de exemplo anterior, ambas as abordagens fazem com que a `WindSpeed` propriedade seja incluída na saída JSON:

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> Essas abordagens fornecem serialização polimórfica somente para o objeto raiz a ser serializado, não para propriedades desse objeto raiz.

Você pode obter a serialização polimórfica para objetos de nível inferior se defini-los como tipo `object` . Por exemplo, suponha que sua `WeatherForecast` classe tenha uma propriedade chamada `PreviousForecast` que possa ser definida como tipo `WeatherForecast` ou `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Se a `PreviousForecast` Propriedade contiver uma instância de `WeatherForecastDerived` :

* A saída JSON da serialização `WeatherForecastWithPrevious` **não inclui** `WindSpeed` .
* A saída JSON da serialização `WeatherForecastWithPreviousAsObject` **inclui** `WindSpeed` .

Para serializar `WeatherForecastWithPreviousAsObject` , não é necessário chamar `Serialize<object>` ou `GetType` porque o objeto raiz não é aquele que pode ser de um tipo derivado. O exemplo de código a seguir não chama `Serialize<object>` ou `GetType` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

O código anterior serializa corretamente `WeatherForecastWithPreviousAsObject` :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

A mesma abordagem de definir propriedades como `object` funciona com interfaces. Suponha que você tenha a seguinte interface e implementação e queira serializar uma classe com propriedades que contêm instâncias de implementação:

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

Quando você serializa uma instância do `Forecasts` , `Tuesday` o mostra apenas a `WindSpeed` propriedade, porque `Tuesday` é definido como `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

O exemplo a seguir mostra o JSON que resulta do código anterior:

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

Para obter mais informações sobre a **serialização** polimórfica e informações sobre a **desserialização** , consulte [como migrar do Newtonsoft.Json para System.Text.Json o](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Permitir comentários e vírgulas à direita

Por padrão, comentários e vírgulas à direita não são permitidos em JSON. Para permitir comentários no JSON, defina a <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> propriedade como `JsonCommentHandling.Skip` .
E para permitir vírgulas à direita, defina a <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> propriedade como `true` . O exemplo a seguir mostra como permitir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Aqui está um exemplo de JSON com comentários e uma vírgula à direita:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Correspondência de propriedade que não diferencia maiúsculas de minúsculas

Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino. Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Aqui está um exemplo de JSON com nomes de Propriedade do camel case. Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Processar JSON de estouro

Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino. Por exemplo, suponha que o tipo de destino seja o seguinte:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

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

Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas. Para capturar dados adicionais, como essas propriedades, aplique o atributo [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave-valor da `ExtensionData` Propriedade:

|Propriedade |Valor  |Observações  |
|---------|---------|---------|
| Data    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureCelsius| 0 | Incompatibilidade de maiúsculas e minúsculas ( `temperatureCelsius` no JSON), portanto, a propriedade não está definida. |
| Resumo | Frequente ||
| ExtensionData | temperatureCelsius: 25 |Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|
| |SummaryWords:<br>Esporádico<br>Vento<br>Humid |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|

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

Observe que o `ExtensionData` nome da propriedade não aparece no JSON. Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.

## <a name="preserve-references-and-handle-circular-references"></a>Preservar referências e manipular referências circulares

::: zone pivot="dotnet-5-0"

Para preservar referências e manipular referências circulares, defina <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> como <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> . Essa configuração causa o seguinte comportamento:

* Em serializar:

  Ao escrever tipos complexos, o serializador também grava Propriedades de metadados ( `$id` , `$values` e `$ref` ).

* Ao desserializar:

  Os metadados são esperados (embora não obrigatórios) e o desserializador tenta compreendê-lo.

O código a seguir ilustra o uso da `Preserve` configuração.

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

Esse recurso não pode ser usado para preservar tipos de valor ou tipos imutáveis. Na desserialização, a instância de um tipo imutável é criada depois que a carga inteira é lida. Portanto, seria impossível desserializar a mesma instância se uma referência a ela aparecer dentro da carga JSON.

Para tipos de valor, tipos imutáveis e matrizes, nenhum metadado de referência é serializado. Na desserialização, uma exceção será lançada se `$ref` ou `$id` for encontrada. No entanto, os tipos de valor ignoram `$id` (e, `$values` no caso de coleções) para possibilitar a desserialização de cargas que foram serializadas usando Newtonsoft.Json .  Newtonsoft.Json Serializa metadados para esses tipos.

Para determinar se os objetos são iguais, System.Text.Json usa <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , que usa igualdade de referência ( <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> ) em vez de igualdade de valor ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> ao comparar duas instâncias de objeto.

Para obter mais informações sobre como as referências são serializadas e desserializadas, consulte <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .

A <xref:System.Text.Json.Serialization.ReferenceResolver> classe define o comportamento de preservar referências na serialização e desserialização. Crie uma classe derivada para especificar o comportamento personalizado. Para obter um exemplo, consulte [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json no .NET Core 3,1 dá suporte apenas a serialização por valor e gera uma exceção para referências circulares.
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a>Permitir ou gravar números entre aspas

::: zone pivot="dotnet-5-0"

Alguns serializadores codificam números como cadeias de caracteres JSON (entre aspas). Por exemplo: `{"DegreesCelsius":"23"}` em vez de `{"DegreesCelsius":23}` . Para serializar números entre aspas ou aceitar números entre aspas em todo o grafo de objeto de entrada, defina <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

Quando você usa System.Text.Json indiretamente por meio de ASP.NET Core, são permitidos números entre aspas ao desserializar porque ASP.NET Core especifica [opções padrão da Web](xref:System.Text.Json.JsonSerializerDefaults.Web).

Para permitir ou gravar números entre aspas para propriedades, campos ou tipos específicos, use o atributo [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) .
::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json no .NET Core 3,1 não dá suporte à serialização ou desserialização de números entre aspas. Para obter mais informações, consulte [permitir ou gravar números entre aspas](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).
::: zone-end

## <a name="immutable-types-and-records"></a>Tipos e registros imutáveis

::: zone pivot="dotnet-5-0"
System.Text.Json pode usar um construtor com parâmetros, o que torna possível desserializar uma classe ou estrutura imutável. Para uma classe, se o único Construtor for um parametrizado, esse construtor será usado. Para uma struct ou uma classe com vários construtores, especifique o que deve ser usado aplicando o atributo [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) . Quando o atributo não é usado, um construtor público sem parâmetros é sempre usado, se estiver presente. O atributo só pode ser usado com construtores públicos. O exemplo a seguir usa o `[JsonConstructor]` atributo:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

Também há suporte para registros no C# 9, conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

Para tipos que são imutáveis porque todos os seus setters de propriedade são não públicos, consulte a seção a seguir sobre [acessadores de propriedade não pública](#non-public-property-accessors).
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` e o suporte a registros do C# 9 não está disponível no .NET Core 3,1.
::: zone-end

## <a name="non-public-property-accessors"></a>Acessadores de propriedade não pública

::: zone pivot="dotnet-5-0"
Para habilitar o uso de um acessador de propriedade não público, use o atributo [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) , conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Não há suporte para acessadores de propriedade não pública no .NET Core 3,1. Para obter mais informações, consulte [o Newtonsoft.Json artigo migrar de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).
::: zone-end

## <a name="copy-jsonserializeroptions"></a>Copiar JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Há um [Construtor JsonSerializerOptions] (xref: System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) que permite criar uma nova instância com as mesmas opções de uma instância existente, conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Um `JsonSerializerOptions` Construtor que usa uma instância existente não está disponível no .NET Core 3,1.
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>Padrões da Web para JsonSerializerOptions

::: zone pivot="dotnet-5-0"
Aqui estão as opções que têm padrões diferentes para aplicativos Web:

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

Há um [Construtor JsonSerializerOptions] (xref: System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = NET-5,0&preserve-View = true) que permite criar uma nova instância com as opções padrão que ASP.NET Core usa para aplicativos Web, conforme mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Aqui estão as opções que têm padrões diferentes para aplicativos Web:

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

Um `JsonSerializerOptions` Construtor que especifica um conjunto de padrões não está disponível no .NET Core 3,1.
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>Métodos de extensão HttpClient e HttpContent

::: zone pivot="dotnet-5-0"

A serialização e a desserialização de cargas JSON da rede são operações comuns. Os métodos de extensão em [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) e [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) permitem que você execute essas operações em uma única linha de código. Esses métodos de extensão usam [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).

O exemplo a seguir ilustra o uso de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> e <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

Também há métodos de extensão para System.Text.Json em [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).
::: zone-end

::: zone pivot="dotnet-core-3-1"
Métodos de extensão em `HttpClient` e `HttpContent` não estão disponíveis no System.Text.Json no .NET Core 3,1.
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter e JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, de baixa alocação e somente de encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>` ou `ReadOnlySequence<byte>` . O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados. O <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método usa `Utf8JsonReader` nos bastidores.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET como `String` , `Int32` e `DateTime` . O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados. O <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método usa `Utf8JsonWriter` nos bastidores.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento somente leitura (DOM) usando o `Utf8JsonReader` . O DOM fornece acesso aleatório aos dados em uma carga JSON. Os elementos JSON que compõem a carga podem ser acessados por meio do <xref:System.Text.Json.JsonElement> tipo. O `JsonElement` tipo fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .net comuns. `JsonDocument` expõe uma <xref:System.Text.Json.JsonDocument.RootElement> propriedade.

As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Usar o JsonDocument para acessar dados

O exemplo a seguir mostra como usar a <xref:System.Text.Json.JsonDocument> classe para acesso aleatório a dados em uma cadeia de caracteres JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

O código anterior:

* Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString` .
* Calcula uma classificação média para objetos em uma `Students` matriz que tem uma `Grade` propriedade.
* Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.
* Conta os alunos incrementando uma `count` variável com cada iteração. Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , conforme mostrado no exemplo a seguir:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Veja um exemplo do JSON que esse código processa:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Usar JsonDocument para gravar JSON

O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

O código anterior:

* Lê um arquivo JSON, carrega os dados em um `JsonDocument` e grava JSON formatado (bem-impresso) em um arquivo.
* Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.
* Quando terminar, chama <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> o gravador. Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.

Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

O resultado é a seguinte saída JSON bem impressa:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Usar Utf8JsonWriter

O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Usar Utf8JsonReader

O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

O código anterior pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrar dados usando Utf8JsonReader

O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

O código anterior:

* Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.
* Conta objetos e valores de propriedade "Name" que terminam com "University".
* Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8. Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>` , usando o seguinte código:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Se o arquivo contiver uma marca de ordem de byte (BOM) UTF-8, remova-a antes de passar os bytes para o `Utf8JsonReader` , uma vez que o leitor espera o texto. Caso contrário, a BOM será considerada JSON inválido e o leitor lançará uma exceção.

Aqui está um exemplo de JSON que o código anterior pode ler. A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Ler de um fluxo usando Utf8JsonReader

Ao ler um arquivo grande (um gigabyte ou mais, por exemplo), talvez você queira evitar ter que carregar todo o arquivo na memória de uma só vez. Para esse cenário, você pode usar um <xref:System.IO.FileStream> .

Ao usar o `Utf8JsonReader` para ler de um fluxo, as seguintes regras se aplicam:

* O buffer que contém a carga JSON parcial deve ser pelo menos tão grande quanto o maior token JSON dentro dele, de modo que o leitor possa progredir em encaminhar.
* O buffer deve ser pelo menos tão grande quanto a maior sequência de espaços em branco dentro do JSON.
* O leitor não mantém o controle dos dados lidos até que ele leia completamente o próximo <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> na carga JSON. Assim, quando houver bytes restantes no buffer, você precisa passá-los para o leitor novamente. Você pode usar <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> para determinar quantos bytes serão deixados.

O código a seguir ilustra como ler de um fluxo. O exemplo mostra um <xref:System.IO.MemoryStream> . O código semelhante funcionará com um <xref:System.IO.FileStream> , exceto quando o `FileStream` contiver uma bom UTF-8 no início. Nesse caso, você precisa remover esses três bytes do buffer antes de passar os bytes restantes para o `Utf8JsonReader` . Caso contrário, o leitor lançaria uma exceção, uma vez que a BOM não é considerada uma parte válida do JSON.

O código de exemplo começa com um buffer de 4 KB e dobra o tamanho do buffer sempre que ele descobre que o tamanho não é grande o suficiente para se ajustar a um token JSON completo, que é necessário para que o leitor faça o progresso no conteúdo JSON. O exemplo de JSON fornecido no trecho de código dispara um aumento de tamanho de buffer somente se você definir um tamanho de buffer inicial muito pequeno, por exemplo, 10 bytes. Se você definir o tamanho do buffer inicial como 10, as `Console.WriteLine` instruções ilustrarão a causa e o efeito do tamanho do buffer aumentará. No tamanho do buffer inicial de 4 KB, o JSON de exemplo inteiro é mostrado por cada um `Console.WriteLine` , e o tamanho do buffer nunca precisa ser aumentado.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

O exemplo anterior não define nenhum limite quanto ao tamanho do buffer pode crescer. Se o tamanho do token for muito grande, o código poderá falhar com uma <xref:System.OutOfMemoryException> exceção. Isso pode acontecer se o JSON contiver um token com cerca de 1 GB ou mais de tamanho, porque dobrar o tamanho de 1 GB resulta em um tamanho muito grande para caber em um `int32` buffer.

## <a name="additional-resources"></a>Recursos adicionais

* [System.Text.Json sobre](system-text-json-overview.md)
* [Como gravar conversores personalizados](system-text-json-converters-how-to.md)
* [Como migrar do Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Suporte a DateTime e DateTimeOffset em System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json Referência de API](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
