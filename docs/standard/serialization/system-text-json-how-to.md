---
title: Como serializar JSON-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5c499e7a0abcbf141b6fc68f6eb9ec8983c0a7cf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054352"
---
# <a name="how-to-serialize-json-in-net"></a>Como serializar JSON no .NET

> [!IMPORTANT]
> A documentação de serialização JSON está em construção. Este artigo não abrange todos os cenários. Para obter mais informações, examine os [problemas de System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) no repositório dotnet/Corefx no GitHub, especialmente aqueles rotulados como [JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

Este artigo mostra como usar o <xref:System.Text.Json> namespace para serializar e desserializar de e para o JavaScript Object Notation (JSON). As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).

## <a name="namespaces"></a>Namespaces

O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais. O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização. Portanto, os exemplos de código mostrados neste artigo exigem uma ou ambas as `using` seguintes diretivas:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atualmente, não <xref:System.Runtime.Serialization> há suporte para atributos do `System.Text.Json`namespace no.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Como gravar objetos .NET em JSON (Serialize)

Para gravar JSON em uma cadeia de caracteres, chame [JsonSerializer. Serialize](xref:System.Text.Json.JsonSerializer.Serialize*), usando um parâmetro de tipo genérico ou inferência de tipo genérico:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

Aqui está um tipo de exemplo a ser serializado, que contém coleções e classes aninhadas:

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

A saída JSON é reduzidos por padrão: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

Sobrecargas de <xref:System.Text.Json.JsonSerializer.Serialize%2A> permitem que você Serialize para <xref:System.IO.Stream>um. As versões assíncronas das `Stream` sobrecargas estão disponíveis.

### <a name="serialize-to-utf-8"></a>Serializar para UTF-8

Chame [JsonSerializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*):

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Como alternativa, uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> está disponível.

A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres. A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).

## <a name="default-serialization-behavior"></a>Comportamento de serialização padrão

* Todas as propriedades públicas são serializadas. Você pode [especificar propriedades a serem excluídas](#exclude-properties).
* O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON](https://tools.ietf.org/html/rfc8259#section-7).
* JSON é reduzidos. Opcionalmente, você pode [imprimir o JSON](#serialize-to-formatted-json).
* A capitalização de nomes JSON corresponde aos nomes .NET. Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names).
* [Referências circulares](https://github.com/dotnet/corefx/issues/38579) são detectadas e exceções geradas.
* Os campos são excluídos.

Os tipos com suporte incluem:

* Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.
* [Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.
* Matrizes unidimensionais e denteadas (`ArrayName[][]`).
* `Dictionary<string,TValue>`onde `TValue` é `object` ,`JsonElement`, ou um poco.
* [Tipos de coleção](https://github.com/dotnet/corefx/issues/36643) dos seguintes namespaces:
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Como ler JSON em objetos .NET (desserializar)

Para desserializar de uma cadeia de caracteres, chame [JsonSerializer. desserializar](xref:System.Text.Json.JsonSerializer.Deserialize*):

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Para obter um exemplo, consulte a seção [serializar](#how-to-write-net-objects-to-json-serialize) . O objeto JSON e .NET são os mesmos, mas a direção é invertida.

Sobrecargas de <xref:System.Text.Json.JsonSerializer.Deserialize*> permitem desserializar de um `Stream`.  As versões assíncronas das `Stream` sobrecargas estão disponíveis.

### <a name="deserialize-from-utf-8"></a>Desserializar de UTF-8

Chame uma sobrecarga [JsonSerializer. desserializate](xref:System.Text.Json.JsonSerializer.Deserialize*) que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>`:

```csharp
byte[] utf8Json = ... ;

var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json = ... ;

var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="default-deserialization-behavior"></a>Comportamento de desserialização padrão

* A correspondência de nome de propriedade diferencia maiúsculas de minúsculas. Opcionalmente, você pode especificar [a diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).
* Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.
* Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.
* A desserialização para [objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) ou [Propriedades somente leitura](https://github.com/dotnet/corefx/issues/38163) não tem suporte.
* Enums têm suporte como números.
* Não há suporte para campos.
* Comentários ou vírgulas à direita nas exceções do JSON throw. Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).
* A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.

## <a name="serialize-to-formatted-json"></a>Serializar para JSON formatado

Defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> como true:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está um tipo de exemplo a ser serializado e a saída JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a>Permitir comentários e vírgulas à direita

Defina <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> como `JsonCommentHandling.Skip`e defina<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas> como true:

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Aqui está um exemplo de JSON com comentários e uma vírgula à direita:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a>Personalizar nomes JSON

Esta seção explica como:

* Personalizar nomes de propriedade individuais
* Converter todos os nomes de propriedade em camel case
* Implementar uma política de nomenclatura de propriedade personalizada
* Converter chaves de dicionário em camel case

Não há suporte para converter automaticamente [enums para o camel case](https://github.com/dotnet/corefx/issues/37725).

### <a name="customize-individual-property-names"></a>Personalizar nomes de propriedade individuais

Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Veja um exemplo de tipo para serializar e o JSON resultante:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

O nome da propriedade definido por este atributo:

* Aplica-se em ambas as direções, para serialização e desserialização.
* Tem precedência sobre as políticas de nomenclatura de propriedade.

### <a name="use-camel-case-for-all-json-property-names"></a>Usar o camel case para todos os nomes de propriedade JSON

Defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> como `JsonNamingPolicy.CamelCase`:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está uma classe de exemplo para serializar e a saída JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

A política de nomenclatura de Propriedade do camel case:

* Aplica-se à serialização e desserialização.
* É substituído por `[JsonPropertyName]` atributos.

### <a name="use-a-custom-json-property-naming-policy"></a>Usar uma política de nomenclatura de propriedade JSON personalizada

Derivar <xref:System.Text.Json.JsonNamingPolicy> de e <xref:System.Text.Json.JsonNamingPolicy.ConvertName*>substituir:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> como uma instância da sua classe de política de nomenclatura:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está uma classe de exemplo para serializar e a saída JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

A política de nomenclatura de propriedade JSON:

* Aplica-se à serialização e desserialização.
* É substituído por `[JsonPropertyName]` atributos.

### <a name="camel-case-dictionary-keys"></a>Chaves de dicionário do camel case

Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,Tvalue>`, as `string` chaves poderão ser convertidas em camel case. Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está um objeto de exemplo para serializar e a saída JSON:

|Propriedade |Valor  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| Resumo| Pontos|
| TemperatureRanges | Frio, 20<br>Quente, 40|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

A política de nomenclatura do camel case se aplica somente à serialização.

## <a name="exclude-properties"></a>Excluir propriedades

Esta seção explica como excluir:

* Propriedades individuais
* Todas as propriedades somente leitura
* Todas as propriedades de valor nulo 

### <a name="exclude-individual-properties"></a>Excluir propriedades individuais

Use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Aqui está um tipo de exemplo para serializar e a saída JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a>Excluir todas as propriedades somente leitura

Defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> como true:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está um tipo de exemplo para serializar e a saída JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

Essa opção se aplica somente à serialização. Durante a desserialização, as propriedades somente leitura são ignoradas por padrão. Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.

### <a name="exclude-all-null-value-properties"></a>Excluir todas as propriedades de valor nulo

Defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como true:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aqui está um objeto de exemplo para serializar e a saída JSON:

|Propriedade |Valor  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| Resumo| nulo|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Essa configuração se aplica à serialização e desserialização. Durante a desserialização, os valores nulos no JSON serão ignorados somente se forem válidos. [Valores nulos para tipos de valores não anuláveis causam exceções](https://github.com/dotnet/corefx/issues/40922).

## <a name="case-insensitive-property-matching"></a>Correspondência de propriedade que não diferencia maiúsculas de minúsculas

Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino. Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> como true:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Aqui está um exemplo de JSON com nomes de Propriedade do camel case. Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="include-properties-of-derived-classes"></a>Incluir propriedades de classes derivadas

Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado. Por exemplo, suponha que você tenha `WeatherForecast` uma classe e uma classe `WeatherForecastWithWind`derivada:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

E suponha que o tipo passado para, ou inferido por, `Serialize` o método em tempo de `WeatherForecast`compilação seja:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que o `weatherForecast` objeto seja, `WeatherForecastWithWind` na verdade, um objeto. Somente as propriedades da classe base são serializadas:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.

Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:

* Chame uma sobrecarga de `Serialize` que permite especificar o tipo em tempo de execução:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Declare o objeto a ser serializado como `object`.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

No cenário de exemplo anterior, ambas as abordagens fazem `WindSpeed` com que a propriedade seja incluída na saída JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a>Processar JSON de estouro

Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino. Por exemplo, suponha que o tipo de destino seja o seguinte:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

E o JSON a ser desserializado é o seguinte:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas. Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave- `ExtensionData` valor da propriedade:

|Propriedade |Valor  |Observações  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureC| 0 | Incompatibilidade de maiúsculas`temperatureC` e minúsculas (no JSON), portanto, a propriedade não está definida. |
| Resumo | Pontos ||
| ExtensionData | temperatureC: 25 |Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|
| |SummaryWords:<br>Legais<br>Vento<br>Humid |A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.|

Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

## <a name="use-utf8jsonwriter-directly"></a>Usar o Utf8JsonWriter diretamente

O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe diretamente.

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader-directly"></a>Usar o Utf8JsonReader diretamente

O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe diretamente. O código pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.

```csharp
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, isFinalBlock: true, state: default);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

## <a name="additional-resources"></a>Recursos adicionais

* [Visão geral de System. Text. JSON](system-text-json-overview.md)
* [Referência da API System. Text. JSON](xref:System.Text.Json)
* [Suporte a DateTime e DateTimeOffset em System. Text. JSON](../datetime/system-text-json-support.md)
