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
# <a name="how-to-serialize-json-in-net"></a><span data-ttu-id="ec2c9-102">Como serializar JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="ec2c9-102">How to serialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec2c9-103">A documentação de serialização JSON está em construção.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="ec2c9-104">Este artigo não abrange todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="ec2c9-105">Para obter mais informações, examine os [problemas de System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) no repositório dotnet/Corefx no GitHub, especialmente aqueles rotulados como [JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="ec2c9-106">Este artigo mostra como usar o <xref:System.Text.Json> namespace para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ec2c9-107">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="ec2c9-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="ec2c9-108">Namespaces</span></span>

<span data-ttu-id="ec2c9-109">O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="ec2c9-110">O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="ec2c9-111">Portanto, os exemplos de código mostrados neste artigo exigem uma ou ambas as `using` seguintes diretivas:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-111">Therefore the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="ec2c9-112">Atualmente, não <xref:System.Runtime.Serialization> há suporte para atributos do `System.Text.Json`namespace no.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="ec2c9-113">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="ec2c9-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="ec2c9-114">Para gravar JSON em uma cadeia de caracteres, chame [JsonSerializer. Serialize](xref:System.Text.Json.JsonSerializer.Serialize*), usando um parâmetro de tipo genérico ou inferência de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-114">To write JSON to a string, call [JsonSerializer.Serialize](xref:System.Text.Json.JsonSerializer.Serialize*), using a generic type parameter or generic type inference:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="ec2c9-115">Aqui está um tipo de exemplo a ser serializado, que contém coleções e classes aninhadas:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-115">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="ec2c9-116">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-116">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="ec2c9-117">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="ec2c9-117">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="ec2c9-118">Sobrecargas de <xref:System.Text.Json.JsonSerializer.Serialize%2A> permitem que você Serialize para <xref:System.IO.Stream>um.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-118">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ec2c9-119">As versões assíncronas das `Stream` sobrecargas estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-119">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="ec2c9-120">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="ec2c9-120">Serialize to UTF-8</span></span>

<span data-ttu-id="ec2c9-121">Chame [JsonSerializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*):</span><span class="sxs-lookup"><span data-stu-id="ec2c9-121">Call [JsonSerializer.SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*):</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="ec2c9-122">Como alternativa, uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> está disponível.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-122">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="ec2c9-123">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-123">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="ec2c9-124">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-124">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="default-serialization-behavior"></a><span data-ttu-id="ec2c9-125">Comportamento de serialização padrão</span><span class="sxs-lookup"><span data-stu-id="ec2c9-125">Default serialization behavior</span></span>

* <span data-ttu-id="ec2c9-126">Todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-126">All public properties are serialized.</span></span> <span data-ttu-id="ec2c9-127">Você pode [especificar propriedades a serem excluídas](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-127">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="ec2c9-128">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-128">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes  non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ec2c9-129">JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-129">JSON is minified.</span></span> <span data-ttu-id="ec2c9-130">Opcionalmente, você pode [imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-130">You can optionally [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ec2c9-131">A capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-131">Casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ec2c9-132">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-132">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="ec2c9-133">[Referências circulares](https://github.com/dotnet/corefx/issues/38579) são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-133">[Circular references](https://github.com/dotnet/corefx/issues/38579) are detected and exceptions thrown.</span></span>
* <span data-ttu-id="ec2c9-134">Os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-134">Fields are excluded.</span></span>

<span data-ttu-id="ec2c9-135">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-135">Supported types include:</span></span>

* <span data-ttu-id="ec2c9-136">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-136">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and boolean.</span></span>
* <span data-ttu-id="ec2c9-137">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-137">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="ec2c9-138">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-138">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="ec2c9-139">`Dictionary<string,TValue>`onde `TValue` é `object` ,`JsonElement`, ou um poco.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-139">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="ec2c9-140">[Tipos de coleção](https://github.com/dotnet/corefx/issues/36643) dos seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-140">[Collection types](https://github.com/dotnet/corefx/issues/36643) from the following namespaces:</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="ec2c9-141">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="ec2c9-141">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="ec2c9-142">Para desserializar de uma cadeia de caracteres, chame [JsonSerializer. desserializar](xref:System.Text.Json.JsonSerializer.Deserialize*):</span><span class="sxs-lookup"><span data-stu-id="ec2c9-142">To deserialize from a string, call [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*):</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="ec2c9-143">Para obter um exemplo, consulte a seção [serializar](#how-to-write-net-objects-to-json-serialize) .</span><span class="sxs-lookup"><span data-stu-id="ec2c9-143">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="ec2c9-144">O objeto JSON e .NET são os mesmos, mas a direção é invertida.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-144">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="ec2c9-145">Sobrecargas de <xref:System.Text.Json.JsonSerializer.Deserialize*> permitem desserializar de um `Stream`.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-145">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="ec2c9-146">As versões assíncronas das `Stream` sobrecargas estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-146">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="ec2c9-147">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="ec2c9-147">Deserialize from UTF-8</span></span>

<span data-ttu-id="ec2c9-148">Chame uma sobrecarga [JsonSerializer. desserializate](xref:System.Text.Json.JsonSerializer.Deserialize*) que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>`:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-148">Call a [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*) overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`:</span></span>

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

## <a name="default-deserialization-behavior"></a><span data-ttu-id="ec2c9-149">Comportamento de desserialização padrão</span><span class="sxs-lookup"><span data-stu-id="ec2c9-149">Default deserialization behavior</span></span>

* <span data-ttu-id="ec2c9-150">A correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-150">Property name matching is case-sensitive.</span></span> <span data-ttu-id="ec2c9-151">Opcionalmente, você pode especificar [a diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-151">You can optionally specify [case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="ec2c9-152">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-152">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ec2c9-153">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-153">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="ec2c9-154">A desserialização para [objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) ou [Propriedades somente leitura](https://github.com/dotnet/corefx/issues/38163) não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-154">Deserialization to [immutable objects](https://github.com/dotnet/corefx/issues/38569) or [read-only properties](https://github.com/dotnet/corefx/issues/38163) isn't supported.</span></span>
* <span data-ttu-id="ec2c9-155">Enums têm suporte como números.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-155">Enums are supported as numbers.</span></span>
* <span data-ttu-id="ec2c9-156">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-156">Fields aren't supported.</span></span>
* <span data-ttu-id="ec2c9-157">Comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-157">Comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ec2c9-158">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-158">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="ec2c9-159">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-159">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="ec2c9-160">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="ec2c9-160">Serialize to formatted JSON</span></span>

<span data-ttu-id="ec2c9-161">Defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> como true:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-161">Set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-162">Aqui está um tipo de exemplo a ser serializado e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-162">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="ec2c9-163">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="ec2c9-163">Allow comments and trailing commas</span></span>

<span data-ttu-id="ec2c9-164">Defina <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> como `JsonCommentHandling.Skip`e defina<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas> como true:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-164">Set <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> to `JsonCommentHandling.Skip`, and set <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="ec2c9-165">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-165">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="ec2c9-166">Personalizar nomes JSON</span><span class="sxs-lookup"><span data-stu-id="ec2c9-166">Customize JSON names</span></span>

<span data-ttu-id="ec2c9-167">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-167">This section explains how to:</span></span>

* <span data-ttu-id="ec2c9-168">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-168">Customize individual property names</span></span>
* <span data-ttu-id="ec2c9-169">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="ec2c9-169">Convert all property names to camel case</span></span>
* <span data-ttu-id="ec2c9-170">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="ec2c9-170">Implement a custom property naming policy</span></span>
* <span data-ttu-id="ec2c9-171">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="ec2c9-171">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="ec2c9-172">Não há suporte para converter automaticamente [enums para o camel case](https://github.com/dotnet/corefx/issues/37725).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-172">There's no support for automatically [converting enums to camel case](https://github.com/dotnet/corefx/issues/37725).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="ec2c9-173">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-173">Customize individual property names</span></span>

<span data-ttu-id="ec2c9-174">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ec2c9-174">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="ec2c9-175">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-175">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="ec2c9-176">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-176">The property name set by this attribute:</span></span>

* <span data-ttu-id="ec2c9-177">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-177">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="ec2c9-178">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-178">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="ec2c9-179">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="ec2c9-179">Use camel case for all JSON property names</span></span>

<span data-ttu-id="ec2c9-180">Defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> como `JsonNamingPolicy.CamelCase`:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-180">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-181">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-181">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="ec2c9-182">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-182">The camel case property naming policy:</span></span>

* <span data-ttu-id="ec2c9-183">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-183">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ec2c9-184">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-184">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="ec2c9-185">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="ec2c9-185">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="ec2c9-186">Derivar <xref:System.Text.Json.JsonNamingPolicy> de e <xref:System.Text.Json.JsonNamingPolicy.ConvertName*>substituir:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-186">Derive from <xref:System.Text.Json.JsonNamingPolicy> and override <xref:System.Text.Json.JsonNamingPolicy.ConvertName*>:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="ec2c9-187">Defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-187">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-188">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-188">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="ec2c9-189">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-189">The JSON property naming policy:</span></span>

* <span data-ttu-id="ec2c9-190">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ec2c9-191">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-191">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="ec2c9-192">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="ec2c9-192">Camel case dictionary keys</span></span>

<span data-ttu-id="ec2c9-193">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,Tvalue>`, as `string` chaves poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-193">If a property of an object to be serialized is of type `Dictionary<string,Tvalue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="ec2c9-194">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-194">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-195">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-195">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="ec2c9-196">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ec2c9-196">Property</span></span> |<span data-ttu-id="ec2c9-197">Valor</span><span class="sxs-lookup"><span data-stu-id="ec2c9-197">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="ec2c9-198">Date</span><span class="sxs-lookup"><span data-stu-id="ec2c9-198">Date</span></span>    | <span data-ttu-id="ec2c9-199">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="ec2c9-199">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="ec2c9-200">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ec2c9-200">TemperatureC</span></span>| <span data-ttu-id="ec2c9-201">25</span><span class="sxs-lookup"><span data-stu-id="ec2c9-201">25</span></span> |
| <span data-ttu-id="ec2c9-202">Resumo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-202">Summary</span></span>| <span data-ttu-id="ec2c9-203">Pontos</span><span class="sxs-lookup"><span data-stu-id="ec2c9-203">Hot</span></span>|
| <span data-ttu-id="ec2c9-204">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="ec2c9-204">TemperatureRanges</span></span> | <span data-ttu-id="ec2c9-205">Frio, 20</span><span class="sxs-lookup"><span data-stu-id="ec2c9-205">Cold, 20</span></span><br><span data-ttu-id="ec2c9-206">Quente, 40</span><span class="sxs-lookup"><span data-stu-id="ec2c9-206">Hot, 40</span></span>|

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

<span data-ttu-id="ec2c9-207">A política de nomenclatura do camel case se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-207">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="ec2c9-208">Excluir propriedades</span><span class="sxs-lookup"><span data-stu-id="ec2c9-208">Exclude properties</span></span>

<span data-ttu-id="ec2c9-209">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-209">This section explains how to exclude:</span></span>

* <span data-ttu-id="ec2c9-210">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-210">Individual properties</span></span>
* <span data-ttu-id="ec2c9-211">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="ec2c9-211">All read-only properties</span></span>
* <span data-ttu-id="ec2c9-212">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-212">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="ec2c9-213">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-213">Exclude individual properties</span></span>

<span data-ttu-id="ec2c9-214">Use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ec2c9-214">Use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="ec2c9-215">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-215">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="ec2c9-216">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="ec2c9-216">Exclude all read-only properties</span></span>

<span data-ttu-id="ec2c9-217">Defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> como true:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-217">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-218">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-218">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="ec2c9-219">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-219">This option applies only to serialization.</span></span> <span data-ttu-id="ec2c9-220">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-220">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="ec2c9-221">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-221">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="ec2c9-222">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-222">Exclude all null value properties</span></span>

<span data-ttu-id="ec2c9-223">Defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como true:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-223">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ec2c9-224">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-224">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="ec2c9-225">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ec2c9-225">Property</span></span> |<span data-ttu-id="ec2c9-226">Valor</span><span class="sxs-lookup"><span data-stu-id="ec2c9-226">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="ec2c9-227">Date</span><span class="sxs-lookup"><span data-stu-id="ec2c9-227">Date</span></span>    | <span data-ttu-id="ec2c9-228">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="ec2c9-228">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="ec2c9-229">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ec2c9-229">TemperatureC</span></span>| <span data-ttu-id="ec2c9-230">25</span><span class="sxs-lookup"><span data-stu-id="ec2c9-230">25</span></span> |
| <span data-ttu-id="ec2c9-231">Resumo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-231">Summary</span></span>| <span data-ttu-id="ec2c9-232">nulo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-232">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="ec2c9-233">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-233">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="ec2c9-234">Durante a desserialização, os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-234">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="ec2c9-235">[Valores nulos para tipos de valores não anuláveis causam exceções](https://github.com/dotnet/corefx/issues/40922).</span><span class="sxs-lookup"><span data-stu-id="ec2c9-235">[Null values for non-nullable value types cause exceptions](https://github.com/dotnet/corefx/issues/40922).</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="ec2c9-236">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="ec2c9-236">Case-insensitive property matching</span></span>

<span data-ttu-id="ec2c9-237">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-237">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="ec2c9-238">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> como true:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-238">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="ec2c9-239">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-239">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="ec2c9-240">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-240">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="ec2c9-241">Incluir propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="ec2c9-241">Include properties of derived classes</span></span>

<span data-ttu-id="ec2c9-242">Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-242">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="ec2c9-243">Por exemplo, suponha que você tenha `WeatherForecast` uma classe e uma classe `WeatherForecastWithWind`derivada:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-243">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="ec2c9-244">E suponha que o tipo passado para, ou inferido por, `Serialize` o método em tempo de `WeatherForecast`compilação seja:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-244">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="ec2c9-245">Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que o `weatherForecast` objeto seja, `WeatherForecastWithWind` na verdade, um objeto.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-245">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="ec2c9-246">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-246">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="ec2c9-247">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-247">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="ec2c9-248">Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-248">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="ec2c9-249">Chame uma sobrecarga de `Serialize` que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-249">Call an overload of `Serialize` that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="ec2c9-250">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-250">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="ec2c9-251">No cenário de exemplo anterior, ambas as abordagens fazem `WindSpeed` com que a propriedade seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-251">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="ec2c9-252">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="ec2c9-252">Handle overflow JSON</span></span>

<span data-ttu-id="ec2c9-253">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-253">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="ec2c9-254">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-254">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="ec2c9-255">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-255">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="ec2c9-256">Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-256">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="ec2c9-257">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-257">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="ec2c9-258">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave- `ExtensionData` valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-258">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="ec2c9-259">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ec2c9-259">Property</span></span> |<span data-ttu-id="ec2c9-260">Valor</span><span class="sxs-lookup"><span data-stu-id="ec2c9-260">Value</span></span>  |<span data-ttu-id="ec2c9-261">Observações</span><span class="sxs-lookup"><span data-stu-id="ec2c9-261">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="ec2c9-262">Date</span><span class="sxs-lookup"><span data-stu-id="ec2c9-262">Date</span></span>    | <span data-ttu-id="ec2c9-263">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="ec2c9-263">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="ec2c9-264">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ec2c9-264">TemperatureC</span></span>| <span data-ttu-id="ec2c9-265">0</span><span class="sxs-lookup"><span data-stu-id="ec2c9-265">0</span></span> | <span data-ttu-id="ec2c9-266">Incompatibilidade de maiúsculas`temperatureC` e minúsculas (no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-266">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="ec2c9-267">Resumo</span><span class="sxs-lookup"><span data-stu-id="ec2c9-267">Summary</span></span> | <span data-ttu-id="ec2c9-268">Pontos</span><span class="sxs-lookup"><span data-stu-id="ec2c9-268">Hot</span></span> ||
| <span data-ttu-id="ec2c9-269">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="ec2c9-269">ExtensionData</span></span> | <span data-ttu-id="ec2c9-270">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="ec2c9-270">temperatureC: 25</span></span> |<span data-ttu-id="ec2c9-271">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-271">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="ec2c9-272">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-272">DatesAvailable:</span></span><br>  <span data-ttu-id="ec2c9-273">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="ec2c9-273">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="ec2c9-274">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="ec2c9-274">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="ec2c9-275">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-275">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="ec2c9-276">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-276">SummaryWords:</span></span><br><span data-ttu-id="ec2c9-277">Legais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-277">Cool</span></span><br><span data-ttu-id="ec2c9-278">Vento</span><span class="sxs-lookup"><span data-stu-id="ec2c9-278">Windy</span></span><br><span data-ttu-id="ec2c9-279">Humid</span><span class="sxs-lookup"><span data-stu-id="ec2c9-279">Humid</span></span> |<span data-ttu-id="ec2c9-280">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-280">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="ec2c9-281">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="ec2c9-281">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="ec2c9-282">Observe que o `ExtensionData` nome da propriedade não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-282">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="ec2c9-283">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-283">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="ec2c9-284">Usar o Utf8JsonWriter diretamente</span><span class="sxs-lookup"><span data-stu-id="ec2c9-284">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="ec2c9-285">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-285">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="ec2c9-286">Usar o Utf8JsonReader diretamente</span><span class="sxs-lookup"><span data-stu-id="ec2c9-286">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="ec2c9-287">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-287">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="ec2c9-288">O código pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ec2c9-288">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="ec2c9-289">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ec2c9-289">Additional resources</span></span>

* [<span data-ttu-id="ec2c9-290">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="ec2c9-290">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ec2c9-291">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="ec2c9-291">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="ec2c9-292">Suporte a DateTime e DateTimeOffset em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="ec2c9-292">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
