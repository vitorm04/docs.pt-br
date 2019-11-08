---
title: Como escrever conversores personalizados para serialização JSON-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741888"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>Como escrever conversores personalizados para serialização JSON no .NET

Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no namespace <xref:System.Text.Json>. Para obter uma introdução ao `System.Text.Json`, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).

Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON. O namespace `System.Text.Json` tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivos JavaScript. Você pode escrever conversores personalizados:

* Para substituir o comportamento padrão de um conversor interno. Por exemplo, talvez você queira `DateTime` valores a serem representados pelo formato mm/dd/aaaa em vez do formato ISO 8601-1:2019 padrão.
* Para dar suporte a um tipo de valor personalizado. Por exemplo, um struct `PhoneNumber`.

Você também pode escrever conversores personalizados para estender `System.Text.Json` com funcionalidade não incluída na versão atual. Os cenários a seguir serão abordados posteriormente neste artigo:

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

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a>Conversor de padrão de fábrica de exemplo

O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`. O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto. O método `CanConvert` retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um tipo `Enum`. O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue`. 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.

## <a name="steps-to-follow-the-basic-pattern"></a>Etapas para seguir o padrão básico

As etapas a seguir explicam como criar um conversor seguindo o padrão básico:

* Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.
* Substitua o método `Read` para desserializar o JSON de entrada e convertê-lo no tipo `T`. Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.
* Substitua o método `Write` para serializar o objeto de entrada do tipo `T`. Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.
* Substitua o método `CanConvert` somente se necessário. A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T`. Portanto, os conversores que dão suporte apenas ao tipo `T` não precisam substituir esse método. Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.

Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.

## <a name="steps-to-follow-the-factory-pattern"></a>Etapas para seguir o padrão de fábrica

As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:

* Crie uma classe que deriva de <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Substitua o método `CanConvert` para retornar true quando o tipo a ser convertido for aquele que o conversor possa manipular. Por exemplo, se o conversor for para `List<T>` ele pode manipular apenas `List<int>`, `List<string>`e `List<DateTime>`. 
* Substitua o método `CreateConverter` para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.
* Crie a classe de conversor que o método de `CreateConverter` instancia. 

O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos. Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano. O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.

O tipo de `Enum` é semelhante a um tipo genérico aberto: um conversor para `Enum` tem que criar um conversor para um `Enum` específico (`WeekdaysEnum`, por exemplo) nos bastidores. 

## <a name="error-handling"></a>Tratamento de erros

Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem. Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro. Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred)`, a exceção ainda fornecerá o caminho na propriedade <xref:System.Text.Json.JsonException.Path>.

## <a name="register-a-custom-converter"></a>Registrar um conversor personalizado

*Registre* um conversor personalizado para fazer com que os métodos `Serialize` e `Deserialize` o usem. Escolha uma das seguintes abordagens:

* Adicione uma instância da classe converter à coleção de <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.
* Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.

## <a name="registration-sample---converters-collection"></a>Amostra de registro – coleção de conversores 

Veja um exemplo que torna o `ExampleDateTimeOffsetConverter` o padrão para propriedades do tipo `DateTimeOffset`:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

Suponha que você Serialize o seguinte tipo:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

O código a seguir usa a mesma abordagem para desserializar usando o conversor de `DateTimeOffset` personalizado:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a>Exemplo de registro-[Jsonconverter] em uma propriedade

O código a seguir seleciona um conversor personalizado para a propriedade `Date`:

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

O código para serializar e desserializar `WeatherForecastWithConverter` não requer o uso de `JsonSerializeOptions.Converters`:

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a>Exemplo de registro-[Jsonconverter] em um tipo

Aqui está o código que cria um struct e aplica o atributo `[JsonConverter]` a ele:

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

Este é o conversor personalizado para o struct anterior:

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

O atributo `[JsonConvert]` na struct registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`. O conversor é usado automaticamente na propriedade `TemperatureC` do seguinte tipo ao serializar ou desserializar:

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a>Precedência de registro do conversor

Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:

* `[JsonConverter]` aplicado a uma propriedade.
* Um conversor adicionado à coleção de `Converters`.
* `[JsonConverter]` aplicado a um tipo de valor personalizado ou POCO.

Se vários conversores personalizados para um tipo forem registrados na coleção de `Converters`, o primeiro conversor que retorna true para `CanConvert` será usado.

Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.

## <a name="converter-samples-for-common-scenarios"></a>Exemplos de conversor para cenários comuns

As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.

### <a name="deserialize-inferred-types-to-object-properties"></a>Desserializar tipos inferidos para propriedades de objeto

Ao desserializar para uma propriedade do tipo `Object`, um objeto `JsonElement` é criado. O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar. Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é um `Boolean`e, se um elemento tiver "01/01/2019", o desserializador não inferirá que se trata de um `DateTime`.

A inferência de tipos pode ser imprecisa. Se o desserializador analisar um número JSON que não tenha um ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger`. A análise de um número que tenha um ponto decimal como um `double` poderá perder a precisão se o número tiver sido originalmente serializado como um `decimal`.

Para cenários que exigem inferência de tipos, o código a seguir mostra um conversor personalizado para propriedades de `Object`. O código converte:

* `true` e `false` para `Boolean`
* Números para `long` ou `double`
* Datas para `DateTime`
* Cadeias de caracteres para `string`
* Tudo o mais a ser `JsonElement`

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

O código a seguir registra o conversor:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

Aqui está um tipo de exemplo com uma propriedade de objeto:

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

Sem o conversor personalizado, a desserialização coloca uma `JsonElement` em cada propriedade.

A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam a desserialização nas propriedades do objeto.

### <a name="support-dictionary-with-non-string-key"></a>Dicionário de suporte com chave não cadeia de caracteres

O suporte interno para coleções de dicionários é para `Dictionary<string, TValue>`. Ou seja, a chave deve ser uma cadeia de caracteres. Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.

O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`:

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

O código a seguir registra o conversor:

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

O conversor pode serializar e desserializar a propriedade `TemperatureRanges` da seguinte classe que usa os seguintes `Enum`:

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

A saída JSON da serialização é semelhante ao exemplo a seguir:

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.

### <a name="support-polymorphic-deserialization"></a>Suporte à desserialização polimórfico

A [serialização polimórfica](system-text-json-how-to.md#serialize-properties-of-derived-classes) não requer um conversor personalizado, mas a desserialização requer um conversor personalizado.

Suponha, por exemplo, que você tenha uma classe base abstrata `Person`, com `Employee` e `Customer` classes derivadas. A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` e `Employee` objetos no JSON são corretamente desserializados em tempo de execução. Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON. Os tipos de pistas disponíveis variam de acordo com cada cenário. Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade. A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.

O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas. O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica. O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

O código a seguir registra o conversor:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

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

A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no código-fonte `System.Text.Json.Serialization` inclui outras amostras de conversores personalizados, como:

* `Int32` o conversor que converte NULL em 0 em desserializar
* `Int32` conversor que permite valores de cadeia de caracteres e de número na desserialização
* conversor de `Enum`
* `List<T>` o conversor que aceita dados externos
* `Long[]` conversor que funciona com uma lista de números delimitada por vírgulas 

## <a name="additional-resources"></a>Recursos adicionais

* [Visão geral de System. Text. JSON](system-text-json-overview.md)
* [Referência da API System. Text. JSON](xref:System.Text.Json)
* [Como usar System. Text. JSON](system-text-json-how-to.md)
* [Código-fonte para conversores internos](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* Problemas do GitHub relacionados a conversores personalizados para `System.Text.Json`
  * [36639 apresentando conversores personalizados](https://github.com/dotnet/corefx/issues/36639)
  * [38713 sobre desserialização para objeto](https://github.com/dotnet/corefx/issues/38713)
  * [40120 sobre dicionários de chave não cadeia de caracteres](https://github.com/dotnet/corefx/issues/40120)
  * [37787 sobre desserialização polimórfica](https://github.com/dotnet/corefx/issues/37787)
