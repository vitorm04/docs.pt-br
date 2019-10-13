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
ms.openlocfilehash: 22c2fd5fc5eaf7a5dc9b71a7335b0b844fa92b51
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291610"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="9fd01-102">Como serializar e desserializar JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="9fd01-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fd01-103">A documentação de serialização JSON está em construção.</span><span class="sxs-lookup"><span data-stu-id="9fd01-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="9fd01-104">Este artigo não abrange todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="9fd01-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="9fd01-105">Para obter mais informações, examine os [problemas de System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) no repositório dotnet/Corefx no GitHub, especialmente aqueles rotulados como [JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="9fd01-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="9fd01-106">Este artigo mostra como usar o namespace <xref:System.Text.Json> para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="9fd01-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="9fd01-107">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="9fd01-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="9fd01-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="9fd01-108">Namespaces</span></span>

<span data-ttu-id="9fd01-109">O namespace <xref:System.Text.Json> contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="9fd01-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="9fd01-110">O namespace <xref:System.Text.Json.Serialization> contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="9fd01-111">Portanto, os exemplos de código mostrados neste artigo exigem uma ou ambas as seguintes diretivas `using`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="9fd01-112">Atualmente, não há suporte para atributos do namespace <xref:System.Runtime.Serialization> no `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="9fd01-113">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="9fd01-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="9fd01-114">Para gravar JSON em uma cadeia de caracteres, chame o método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9fd01-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9fd01-115">O exemplo a seguir usa uma sobrecarga com um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="9fd01-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="9fd01-116">Você pode omitir o parâmetro de tipo genérico e usar a inferência de tipo genérico em vez disso:</span><span class="sxs-lookup"><span data-stu-id="9fd01-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="9fd01-117">Aqui está um tipo de exemplo a ser serializado, que contém coleções e classes aninhadas:</span><span class="sxs-lookup"><span data-stu-id="9fd01-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="9fd01-118">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="9fd01-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="9fd01-119">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="9fd01-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="9fd01-120">Sobrecargas de <xref:System.Text.Json.JsonSerializer.Serialize%2A> permitem que você Serialize para um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="9fd01-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="9fd01-121">As versões assíncronas das sobrecargas `Stream` estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9fd01-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="9fd01-122">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="9fd01-122">Serialize to UTF-8</span></span>

<span data-ttu-id="9fd01-123">Para serializar para UTF-8, chame o método <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9fd01-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="9fd01-124">Como alternativa, uma sobrecarga <xref:System.Text.Json.JsonSerializer.Serialize%2A> que usa um <xref:System.Text.Json.Utf8JsonWriter> está disponível.</span><span class="sxs-lookup"><span data-stu-id="9fd01-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="9fd01-125">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9fd01-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="9fd01-126">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="9fd01-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="9fd01-127">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="9fd01-127">Serialization behavior</span></span>

* <span data-ttu-id="9fd01-128">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="9fd01-129">Você pode [especificar propriedades a serem excluídas](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="9fd01-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="9fd01-130">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="9fd01-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="9fd01-131">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="9fd01-131">By default, JSON is minified.</span></span> <span data-ttu-id="9fd01-132">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="9fd01-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="9fd01-133">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="9fd01-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="9fd01-134">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="9fd01-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="9fd01-135">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="9fd01-136">Para obter mais informações, consulte o [problema em referências circulares](https://github.com/dotnet/corefx/issues/38579) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="9fd01-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="9fd01-137">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="9fd01-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="9fd01-138">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="9fd01-138">Supported types include:</span></span>

* <span data-ttu-id="9fd01-139">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="9fd01-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="9fd01-140">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9fd01-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="9fd01-141">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="9fd01-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="9fd01-142">`Dictionary<string,TValue>` em que `TValue` é `object`, `JsonElement` ou um POCO.</span><span class="sxs-lookup"><span data-stu-id="9fd01-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="9fd01-143">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="9fd01-143">Collections from the following namespaces.</span></span> <span data-ttu-id="9fd01-144">Para obter mais informações, consulte o [problema no suporte de coleção](https://github.com/dotnet/corefx/issues/36643) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="9fd01-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="9fd01-145">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="9fd01-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="9fd01-146">Para desserializar de uma cadeia de caracteres, chame o método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="9fd01-147">Para obter um exemplo, consulte a seção [serializar](#how-to-write-net-objects-to-json-serialize) .</span><span class="sxs-lookup"><span data-stu-id="9fd01-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="9fd01-148">O objeto JSON e .NET são os mesmos, mas a direção é invertida.</span><span class="sxs-lookup"><span data-stu-id="9fd01-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="9fd01-149">Sobrecargas de <xref:System.Text.Json.JsonSerializer.Deserialize*> permitem desserializar de um `Stream`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="9fd01-150">As versões assíncronas das sobrecargas `Stream` estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9fd01-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="9fd01-151">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="9fd01-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="9fd01-152">Para desserializar de UTF-8, chame uma sobrecarga <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="9fd01-153">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="9fd01-153">Deserialization behavior</span></span>

* <span data-ttu-id="9fd01-154">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="9fd01-155">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="9fd01-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="9fd01-156">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="9fd01-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="9fd01-157">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9fd01-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="9fd01-158">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="9fd01-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="9fd01-159">Para obter mais informações, consulte o [problema do GitHub no suporte a objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) e o [problema no suporte à propriedade somente leitura](https://github.com/dotnet/corefx/issues/38163) no repositório dotnet/corefx no github.</span><span class="sxs-lookup"><span data-stu-id="9fd01-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="9fd01-160">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="9fd01-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="9fd01-161">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="9fd01-161">Fields aren't supported.</span></span>
* <span data-ttu-id="9fd01-162">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="9fd01-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="9fd01-163">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas) , se necessário.</span><span class="sxs-lookup"><span data-stu-id="9fd01-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="9fd01-164">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="9fd01-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="9fd01-165">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="9fd01-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="9fd01-166">Para imprimir a saída JSON com muita impressão, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-167">Aqui está um tipo de exemplo a ser serializado e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-167">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="9fd01-168">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="9fd01-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="9fd01-169">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="9fd01-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="9fd01-170">Para permitir comentários no JSON, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> como `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="9fd01-171">E para permitir vírgulas à direita, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="9fd01-172">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

<span data-ttu-id="9fd01-173">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="9fd01-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="9fd01-174">Personalizar nomes JSON</span><span class="sxs-lookup"><span data-stu-id="9fd01-174">Customize JSON names</span></span>

<span data-ttu-id="9fd01-175">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="9fd01-176">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="9fd01-176">This section explains how to:</span></span>

* <span data-ttu-id="9fd01-177">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="9fd01-177">Customize individual property names</span></span>
* <span data-ttu-id="9fd01-178">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="9fd01-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="9fd01-179">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="9fd01-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="9fd01-180">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="9fd01-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="9fd01-181">Atualmente, não há suporte para converter automaticamente enums para o camel case.</span><span class="sxs-lookup"><span data-stu-id="9fd01-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="9fd01-182">Para obter mais informações, consulte o [problema em Enumeração camel case support](https://github.com/dotnet/corefx/issues/37725) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="9fd01-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="9fd01-183">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="9fd01-183">Customize individual property names</span></span>

<span data-ttu-id="9fd01-184">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9fd01-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="9fd01-185">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="9fd01-185">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="9fd01-186">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="9fd01-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="9fd01-187">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="9fd01-188">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="9fd01-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="9fd01-189">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="9fd01-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="9fd01-190">Para usar o camel case para todos os nomes de propriedade JSON, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-191">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-191">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="9fd01-192">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="9fd01-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="9fd01-193">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="9fd01-194">É substituído pelos atributos `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="9fd01-195">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="9fd01-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="9fd01-196">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe que derive de <xref:System.Text.Json.JsonNamingPolicy> e substitua o método <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="9fd01-197">Em seguida, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="9fd01-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-198">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-198">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="9fd01-199">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="9fd01-200">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="9fd01-201">É substituído pelos atributos `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="9fd01-202">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="9fd01-202">Camel case dictionary keys</span></span>

<span data-ttu-id="9fd01-203">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as chaves `string` poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="9fd01-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="9fd01-204">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-205">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="9fd01-206">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9fd01-206">Property</span></span> |<span data-ttu-id="9fd01-207">Valor</span><span class="sxs-lookup"><span data-stu-id="9fd01-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="9fd01-208">Date</span><span class="sxs-lookup"><span data-stu-id="9fd01-208">Date</span></span>    | <span data-ttu-id="9fd01-209">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="9fd01-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="9fd01-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="9fd01-210">TemperatureC</span></span>| <span data-ttu-id="9fd01-211">25</span><span class="sxs-lookup"><span data-stu-id="9fd01-211">25</span></span> |
| <span data-ttu-id="9fd01-212">Resumo</span><span class="sxs-lookup"><span data-stu-id="9fd01-212">Summary</span></span>| <span data-ttu-id="9fd01-213">Pontos</span><span class="sxs-lookup"><span data-stu-id="9fd01-213">Hot</span></span>|
| <span data-ttu-id="9fd01-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="9fd01-214">TemperatureRanges</span></span> | <span data-ttu-id="9fd01-215">Frio, 20</span><span class="sxs-lookup"><span data-stu-id="9fd01-215">Cold, 20</span></span><br><span data-ttu-id="9fd01-216">Quente, 40</span><span class="sxs-lookup"><span data-stu-id="9fd01-216">Hot, 40</span></span>|

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

<span data-ttu-id="9fd01-217">A política de nomenclatura do camel case se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="9fd01-218">Excluir propriedades</span><span class="sxs-lookup"><span data-stu-id="9fd01-218">Exclude properties</span></span>

<span data-ttu-id="9fd01-219">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="9fd01-220">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="9fd01-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="9fd01-221">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="9fd01-222">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="9fd01-222">Individual properties</span></span>
* <span data-ttu-id="9fd01-223">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="9fd01-223">All read-only properties</span></span>
* <span data-ttu-id="9fd01-224">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="9fd01-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="9fd01-225">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="9fd01-225">Exclude individual properties</span></span>

<span data-ttu-id="9fd01-226">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9fd01-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="9fd01-227">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-227">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="9fd01-228">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="9fd01-228">Exclude all read-only properties</span></span>

<span data-ttu-id="9fd01-229">Para excluir todas as propriedades somente leitura, defina o <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-230">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-230">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="9fd01-231">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-231">This option applies only to serialization.</span></span> <span data-ttu-id="9fd01-232">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9fd01-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="9fd01-233">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="9fd01-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="9fd01-234">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="9fd01-234">Exclude all null value properties</span></span>

<span data-ttu-id="9fd01-235">Para excluir todas as propriedades de valor nulo, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9fd01-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="9fd01-236">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="9fd01-237">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9fd01-237">Property</span></span> |<span data-ttu-id="9fd01-238">Valor</span><span class="sxs-lookup"><span data-stu-id="9fd01-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="9fd01-239">Date</span><span class="sxs-lookup"><span data-stu-id="9fd01-239">Date</span></span>    | <span data-ttu-id="9fd01-240">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="9fd01-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="9fd01-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="9fd01-241">TemperatureC</span></span>| <span data-ttu-id="9fd01-242">25</span><span class="sxs-lookup"><span data-stu-id="9fd01-242">25</span></span> |
| <span data-ttu-id="9fd01-243">Resumo</span><span class="sxs-lookup"><span data-stu-id="9fd01-243">Summary</span></span>| <span data-ttu-id="9fd01-244">nulo</span><span class="sxs-lookup"><span data-stu-id="9fd01-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="9fd01-245">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="9fd01-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="9fd01-246">Durante a desserialização, os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="9fd01-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="9fd01-247">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="9fd01-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="9fd01-248">Para obter mais informações, consulte o [problema em tipos de valores não anuláveis](https://github.com/dotnet/corefx/issues/40922) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="9fd01-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="9fd01-249">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="9fd01-249">Case-insensitive property matching</span></span>

<span data-ttu-id="9fd01-250">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="9fd01-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="9fd01-251">Para alterar esse comportamento, defina o <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="9fd01-252">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="9fd01-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="9fd01-253">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="9fd01-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="9fd01-254">Incluir propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="9fd01-254">Include properties of derived classes</span></span>

<span data-ttu-id="9fd01-255">Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado.</span><span class="sxs-lookup"><span data-stu-id="9fd01-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="9fd01-256">Por exemplo, suponha que você tenha uma classe `WeatherForecast` e uma classe derivada `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="9fd01-257">E suponha que o tipo passado para, ou inferido por, o método `Serialize` em tempo de compilação seja `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="9fd01-258">Nesse cenário, a propriedade `WindSpeed` não é serializada mesmo que o objeto `weatherForecast` seja, na verdade, um objeto `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="9fd01-259">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="9fd01-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="9fd01-260">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="9fd01-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="9fd01-261">Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="9fd01-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="9fd01-262">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="9fd01-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="9fd01-263">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="9fd01-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="9fd01-264">No cenário de exemplo anterior, ambas as abordagens fazem com que a propriedade `WindSpeed` seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="9fd01-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="9fd01-265">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="9fd01-265">Handle overflow JSON</span></span>

<span data-ttu-id="9fd01-266">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="9fd01-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="9fd01-267">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9fd01-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="9fd01-268">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9fd01-268">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="9fd01-269">Se você desserializar o JSON mostrado no tipo mostrado, as propriedades `DatesAvailable` e `SummaryWords` terão em qualquer lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="9fd01-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="9fd01-270">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="9fd01-271">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares chave-valor da propriedade `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="9fd01-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="9fd01-272">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9fd01-272">Property</span></span> |<span data-ttu-id="9fd01-273">Valor</span><span class="sxs-lookup"><span data-stu-id="9fd01-273">Value</span></span>  |<span data-ttu-id="9fd01-274">Observações</span><span class="sxs-lookup"><span data-stu-id="9fd01-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="9fd01-275">Date</span><span class="sxs-lookup"><span data-stu-id="9fd01-275">Date</span></span>    | <span data-ttu-id="9fd01-276">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="9fd01-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="9fd01-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="9fd01-277">TemperatureC</span></span>| <span data-ttu-id="9fd01-278">0</span><span class="sxs-lookup"><span data-stu-id="9fd01-278">0</span></span> | <span data-ttu-id="9fd01-279">Incompatibilidade de maiúsculas e minúsculas (`temperatureC` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="9fd01-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="9fd01-280">Resumo</span><span class="sxs-lookup"><span data-stu-id="9fd01-280">Summary</span></span> | <span data-ttu-id="9fd01-281">Pontos</span><span class="sxs-lookup"><span data-stu-id="9fd01-281">Hot</span></span> ||
| <span data-ttu-id="9fd01-282">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="9fd01-282">ExtensionData</span></span> | <span data-ttu-id="9fd01-283">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="9fd01-283">temperatureC: 25</span></span> |<span data-ttu-id="9fd01-284">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="9fd01-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="9fd01-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="9fd01-285">DatesAvailable:</span></span><br>  <span data-ttu-id="9fd01-286">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="9fd01-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="9fd01-287">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="9fd01-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="9fd01-288">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="9fd01-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="9fd01-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="9fd01-289">SummaryWords:</span></span><br><span data-ttu-id="9fd01-290">Legais</span><span class="sxs-lookup"><span data-stu-id="9fd01-290">Cool</span></span><br><span data-ttu-id="9fd01-291">Vento</span><span class="sxs-lookup"><span data-stu-id="9fd01-291">Windy</span></span><br><span data-ttu-id="9fd01-292">Humid</span><span class="sxs-lookup"><span data-stu-id="9fd01-292">Humid</span></span> |<span data-ttu-id="9fd01-293">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="9fd01-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="9fd01-294">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="9fd01-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="9fd01-295">Observe que o nome da propriedade `ExtensionData` não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="9fd01-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="9fd01-296">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="9fd01-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="9fd01-297">Usar o Utf8JsonWriter diretamente</span><span class="sxs-lookup"><span data-stu-id="9fd01-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="9fd01-298">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonWriter> diretamente.</span><span class="sxs-lookup"><span data-stu-id="9fd01-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="9fd01-299">Usar o Utf8JsonReader diretamente</span><span class="sxs-lookup"><span data-stu-id="9fd01-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="9fd01-300">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonReader> diretamente.</span><span class="sxs-lookup"><span data-stu-id="9fd01-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="9fd01-301">O código pressupõe que a variável `jsonUtf8` é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9fd01-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

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

## <a name="additional-resources"></a><span data-ttu-id="9fd01-302">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="9fd01-302">Additional resources</span></span>

* [<span data-ttu-id="9fd01-303">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="9fd01-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9fd01-304">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="9fd01-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="9fd01-305">Suporte a DateTime e DateTimeOffset em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="9fd01-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
