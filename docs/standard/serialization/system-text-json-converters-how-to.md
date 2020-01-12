---
title: Como escrever conversores personalizados para serialização JSON-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 8a2af76ca64359c12fafce6678def14d11d9f029
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904561"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>Como escrever conversores personalizados para serialização JSON (Marshalling) no .NET

Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no namespace <xref:System.Text.Json>. Para obter uma introdução ao `System.Text.Json`, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).

Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON. O namespace `System.Text.Json` tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivos JavaScript. Você pode escrever conversores personalizados:

* Para substituir o comportamento padrão de um conversor interno. Por exemplo, talvez você queira `DateTime` valores a serem representados pelo formato mm/dd/aaaa em vez do formato ISO 8601-1:2019 padrão.
* Para dar suporte a um tipo de valor personalizado. Por exemplo, um struct `PhoneNumber`.

Você também pode escrever conversores personalizados para personalizar ou estender `System.Text.Json` com funcionalidade não incluída na versão atual. Os cenários a seguir serão abordados posteriormente neste artigo:

* [Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).
* [Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).
* [Suporte à desserialização polimórfico](#support-polymorphic-deserialization).

## <a name="custom-converter-patterns"></a>Padrões de conversor personalizado

Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica. O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos. O padrão básico é para tipos genéricos não genéricos e fechados.  Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

O padrão básico cria uma classe que pode manipular um tipo. O padrão de fábrica cria uma classe que determina no tempo de execução qual tipo específico é necessário e cria dinamicamente o conversor apropriado.

## <a name="sample-basic-converter"></a>Conversor básico de exemplo

O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente. O conversor usa o formato mm/dd/aaaa para propriedades de `DateTimeOffset`.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Conversor de padrão de fábrica de exemplo

O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`. O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto. O método `CanConvert` retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um tipo `Enum`. O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue`. 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.

## <a name="steps-to-follow-the-basic-pattern"></a>Etapas para seguir o padrão básico

As etapas a seguir explicam como criar um conversor seguindo o padrão básico:

* Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.
* Substitua o método `Read` para desserializar o JSON de entrada e convertê-lo no tipo `T`. Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.
* Substitua o método `Write` para serializar o objeto de entrada do tipo `T`. Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.
* Substitua o método `CanConvert` somente se necessário. A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T`. Portanto, os conversores que dão suporte apenas ao tipo `T` não precisam substituir esse método. Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.

Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.

## <a name="steps-to-follow-the-factory-pattern"></a>Etapas para seguir o padrão de fábrica

As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:

* Crie uma classe derivada de <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Substitua o método `CanConvert` para retornar true quando o tipo a ser convertido for aquele que o conversor possa manipular. Por exemplo, se o conversor for para `List<T>` ele pode manipular apenas `List<int>`, `List<string>`e `List<DateTime>`. 
* Substitua o método `CreateConverter` para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.
* Crie a classe de conversor que o método de `CreateConverter` instancia. 

O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos. Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano. O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.

O tipo de `Enum` é semelhante a um tipo genérico aberto: um conversor para `Enum` tem que criar um conversor para um `Enum` específico (`WeekdaysEnum`, por exemplo) nos bastidores. 

## <a name="error-handling"></a>Manipulação de erros

Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem. Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro. Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred")`, a exceção ainda fornecerá o caminho na propriedade <xref:System.Text.Json.JsonException.Path>.

## <a name="register-a-custom-converter"></a>Registrar um conversor personalizado

*Registre* um conversor personalizado para fazer com que os métodos `Serialize` e `Deserialize` o usem. Escolha uma das seguintes abordagens:

* Adicione uma instância da classe converter à coleção de <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.
* Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.

## <a name="registration-sample---converters-collection"></a>Amostra de registro – coleção de conversores 

Veja um exemplo que torna o <xref:System.ComponentModel.DateTimeOffsetConverter> o padrão para propriedades do tipo <xref:System.DateTimeOffset>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

Suponha que você Serialize uma instância do seguinte tipo:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

O código a seguir usa a mesma abordagem para desserializar usando o conversor de `DateTimeOffset` personalizado:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Exemplo de registro-[Jsonconverter] em uma propriedade

O código a seguir seleciona um conversor personalizado para a propriedade `Date`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

O código para serializar `WeatherForecastWithConverterAttribute` não requer o uso de `JsonSerializeOptions.Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

O código para desserializar também não requer o uso de `Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Exemplo de registro-[Jsonconverter] em um tipo

Aqui está o código que cria um struct e aplica o atributo `[JsonConverter]` a ele:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

Este é o conversor personalizado para o struct anterior:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

O atributo `[JsonConvert]` na struct registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`. O conversor é usado automaticamente na propriedade `TemperatureCelsius` do seguinte tipo ao serializar ou desserializar:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Precedência de registro do conversor

Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:

* `[JsonConverter]` aplicado a uma propriedade.
* Um conversor adicionado à coleção de `Converters`.
* `[JsonConverter]` aplicado a um tipo de valor personalizado ou POCO.

Se vários conversores personalizados para um tipo forem registrados na coleção de `Converters`, o primeiro conversor que retorna true para `CanConvert` será usado.

Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.

## <a name="converter-samples-for-common-scenarios"></a>Exemplos de conversor para cenários comuns

As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.

* [Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties)
* [Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key)
* [Suporte à desserialização polimórfico](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a>Desserializar tipos inferidos para propriedades de objeto

Ao desserializar para uma propriedade do tipo `object`, um objeto `JsonElement` é criado. O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar. Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é um `Boolean`e, se um elemento tiver "01/01/2019", o desserializador não inferirá que se trata de um `DateTime`.

A inferência de tipos pode ser imprecisa. Se o desserializador analisar um número JSON que não tenha um ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger`. A análise de um número que tenha um ponto decimal como um `double` poderá perder a precisão se o número tiver sido originalmente serializado como um `decimal`.

Para cenários que exigem inferência de tipos, o código a seguir mostra um conversor personalizado para propriedades de `object`. O código converte:

* `true` e `false` para `Boolean`
* Números sem um decimal para `long`
* Números com um decimal para `double`
* Datas para `DateTime`
* Cadeias de caracteres para `string`
* Tudo o mais a ser `JsonElement`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

O código a seguir registra o conversor:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

Aqui está um tipo de exemplo com propriedades de `object`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Sem o conversor personalizado, a desserialização coloca uma `JsonElement` em cada propriedade.

A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam a desserialização para `object` Propriedades.

### <a name="support-dictionary-with-non-string-key"></a>Dicionário de suporte com chave não cadeia de caracteres

O suporte interno para coleções de dicionários é para `Dictionary<string, TValue>`. Ou seja, a chave deve ser uma cadeia de caracteres. Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.

O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

O código a seguir registra o conversor:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

O conversor pode serializar e desserializar a propriedade `TemperatureRanges` da seguinte classe que usa os seguintes `Enum`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

A saída JSON da serialização é semelhante ao exemplo a seguir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.

### <a name="support-polymorphic-deserialization"></a>Suporte à desserialização polimórfico

Os recursos internos fornecem um intervalo limitado de [serialização polimórfico](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mas não há suporte para desserialização. A desserialização requer um conversor personalizado.

Suponha, por exemplo, que você tenha uma classe base abstrata `Person`, com `Employee` e `Customer` classes derivadas. A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` e `Employee` objetos no JSON são corretamente desserializados em tempo de execução. Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON. Os tipos de pistas disponíveis variam de acordo com cada cenário. Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade. A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.

O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas. O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica. O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

O código a seguir registra o conversor:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a>Outras amostras de conversor personalizadas

O artigo [migrar do Newtonsoft. JSON para System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md) contém exemplos adicionais de conversores personalizados.

A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no código-fonte `System.Text.Json.Serialization` inclui outras amostras de conversores personalizados, como:

* [Conversor de Int32 que converte NULL para 0 em desserializar](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Conversor de Int32 que permite valores de cadeia de caracteres e de número na desserialização](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Conversor de enumeração](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [List\<T > converter que aceita dados externos](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Conversor Long [] que funciona com uma lista de números delimitada por vírgulas](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs) 

Se você precisar criar um conversor que modifique o comportamento de um conversor interno existente, poderá obter [o código-fonte do conversor existente](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) para servir como ponto de partida para personalização.

## <a name="additional-resources"></a>Recursos adicionais

* [Código-fonte para conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [Suporte a DateTime e DateTimeOffset em System. Text. JSON](../datetime/system-text-json-support.md)
* [Visão geral de System. Text. JSON](system-text-json-overview.md)
* [Como usar System. Text. JSON](system-text-json-how-to.md)
* [Como migrar do Newtonsoft. JSON](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Referência da API System. Text. JSON](xref:System.Text.Json)
* [Referência da API System. Text. JSON. Serialization](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
