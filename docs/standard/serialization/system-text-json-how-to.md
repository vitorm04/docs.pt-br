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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740439"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="cdef6-102">Como serializar e desserializar JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="cdef6-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cdef6-103">A documentação de serialização JSON está em construção.</span><span class="sxs-lookup"><span data-stu-id="cdef6-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="cdef6-104">Este artigo não abrange todos os cenários.</span><span class="sxs-lookup"><span data-stu-id="cdef6-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="cdef6-105">Para obter mais informações, examine os [problemas de System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) no repositório dotnet/Corefx no GitHub, especialmente aqueles rotulados como [JSON-funcionalidade-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="cdef6-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="cdef6-106">Este artigo mostra como usar o namespace <xref:System.Text.Json> para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="cdef6-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="cdef6-107">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="cdef6-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="cdef6-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="cdef6-108">Namespaces</span></span>

<span data-ttu-id="cdef6-109">O namespace <xref:System.Text.Json> contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="cdef6-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="cdef6-110">O namespace <xref:System.Text.Json.Serialization> contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="cdef6-111">Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="cdef6-111">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="cdef6-112">Atualmente, não há suporte para atributos do namespace <xref:System.Runtime.Serialization> no `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="cdef6-113">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="cdef6-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="cdef6-114">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-114">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cdef6-115">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="cdef6-115">The following example creates JSON as a string:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="cdef6-116">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-116">The following example uses synchronous code to create a JSON file:</span></span>

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

<span data-ttu-id="cdef6-117">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-117">The following example uses asynchronous code to create a JSON file:</span></span>

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

<span data-ttu-id="cdef6-118">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="cdef6-118">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="cdef6-119">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="cdef6-119">An overload of `Serialize()` takes a generic type parameter:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a><span data-ttu-id="cdef6-120">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="cdef6-120">Serialization example</span></span>

<span data-ttu-id="cdef6-121">Aqui está um tipo de exemplo que contém coleções e classes aninhadas:</span><span class="sxs-lookup"><span data-stu-id="cdef6-121">Here's an example type that contains collections and nested classes:</span></span>

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

<span data-ttu-id="cdef6-122">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cdef6-122">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="cdef6-123">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="cdef6-123">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="cdef6-124">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="cdef6-124">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="cdef6-125">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="cdef6-125">Serialize to UTF-8</span></span>

<span data-ttu-id="cdef6-126">Para serializar para UTF-8, chame o método <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-126">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="cdef6-127">Uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que usa uma <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="cdef6-127">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="cdef6-128">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cdef6-128">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="cdef6-129">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="cdef6-129">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="cdef6-130">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="cdef6-130">Serialization behavior</span></span>

* <span data-ttu-id="cdef6-131">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-131">By default, all public properties are serialized.</span></span> <span data-ttu-id="cdef6-132">Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="cdef6-132">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="cdef6-133">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="cdef6-133">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="cdef6-134">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-134">By default, JSON is minified.</span></span> <span data-ttu-id="cdef6-135">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="cdef6-135">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="cdef6-136">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="cdef6-136">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="cdef6-137">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="cdef6-137">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="cdef6-138">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-138">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="cdef6-139">Para obter mais informações, consulte o [problema em referências circulares](https://github.com/dotnet/corefx/issues/38579) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="cdef6-139">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="cdef6-140">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="cdef6-141">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="cdef6-141">Supported types include:</span></span>

* <span data-ttu-id="cdef6-142">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="cdef6-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="cdef6-143">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cdef6-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="cdef6-144">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="cdef6-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="cdef6-145">`Dictionary<string,TValue>` em que `TValue` é `object`, `JsonElement`ou um POCO.</span><span class="sxs-lookup"><span data-stu-id="cdef6-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="cdef6-146">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="cdef6-146">Collections from the following namespaces.</span></span> <span data-ttu-id="cdef6-147">Para obter mais informações, consulte o [problema no suporte de coleção](https://github.com/dotnet/corefx/issues/36643) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="cdef6-147">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="cdef6-148">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="cdef6-149">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="cdef6-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="cdef6-150">Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cdef6-151">O exemplo a seguir lê JSON de uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="cdef6-151">The following example reads JSON from a string:</span></span>

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="cdef6-152">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="cdef6-153">Para desserializar de um arquivo usando código assíncrono, chame o método <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

<span data-ttu-id="cdef6-154">Para obter um exemplo de tipo e JSON correspondente, consulte a seção [exemplo de serialização](#serialization-example) .</span><span class="sxs-lookup"><span data-stu-id="cdef6-154">For an example type and corresponding JSON, see the [Serialization example](#serialization-example) section.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="cdef6-155">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="cdef6-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="cdef6-156">Para desserializar do UTF-8, chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> que usa uma `Utf8JsonReader` ou uma `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="cdef6-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="cdef6-157">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="cdef6-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="cdef6-158">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="cdef6-158">Deserialization behavior</span></span>

* <span data-ttu-id="cdef6-159">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="cdef6-160">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="cdef6-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="cdef6-161">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="cdef6-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="cdef6-162">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cdef6-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="cdef6-163">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="cdef6-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="cdef6-164">Para obter mais informações, consulte o [problema do GitHub no suporte a objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) e o [problema no suporte à propriedade somente leitura](https://github.com/dotnet/corefx/issues/38163) no repositório dotnet/corefx no github.</span><span class="sxs-lookup"><span data-stu-id="cdef6-164">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="cdef6-165">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="cdef6-165">By default, enums are supported as numbers.</span></span> <span data-ttu-id="cdef6-166">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="cdef6-166">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="cdef6-167">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-167">Fields aren't supported.</span></span>
* <span data-ttu-id="cdef6-168">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="cdef6-168">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="cdef6-169">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="cdef6-169">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="cdef6-170">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="cdef6-170">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="cdef6-171">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-171">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="cdef6-172">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="cdef6-172">Serialize to formatted JSON</span></span>

<span data-ttu-id="cdef6-173">Para imprimir a saída JSON, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-173">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-174">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="cdef6-174">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

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

## <a name="customize-json-names-and-values"></a><span data-ttu-id="cdef6-175">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-175">Customize JSON names and values</span></span>

<span data-ttu-id="cdef6-176">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-176">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="cdef6-177">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="cdef6-177">Enum values are represented as numbers.</span></span> <span data-ttu-id="cdef6-178">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="cdef6-178">This section explains how to:</span></span>

* <span data-ttu-id="cdef6-179">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="cdef6-179">Customize individual property names</span></span>
* <span data-ttu-id="cdef6-180">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="cdef6-180">Convert all property names to camel case</span></span>
* <span data-ttu-id="cdef6-181">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="cdef6-181">Implement a custom property naming policy</span></span>
* <span data-ttu-id="cdef6-182">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="cdef6-182">Convert dictionary keys to camel case</span></span>
* <span data-ttu-id="cdef6-183">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="cdef6-183">Convert enums to strings and camel case</span></span> 

<span data-ttu-id="cdef6-184">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="cdef6-184">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="cdef6-185">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="cdef6-185">Customize individual property names</span></span>

<span data-ttu-id="cdef6-186">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="cdef6-186">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="cdef6-187">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="cdef6-187">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="cdef6-188">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="cdef6-188">The property name set by this attribute:</span></span>

* <span data-ttu-id="cdef6-189">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-189">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="cdef6-190">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cdef6-190">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="cdef6-191">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-191">Use camel case for all JSON property names</span></span>

<span data-ttu-id="cdef6-192">Para usar o camel case para todos os nomes de propriedade JSON, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-192">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-193">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-193">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="cdef6-194">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="cdef6-194">The camel case property naming policy:</span></span>

* <span data-ttu-id="cdef6-195">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-195">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="cdef6-196">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-196">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="cdef6-197">É por isso que o nome da propriedade JSON `Wind` no exemplo não é o camel case.</span><span class="sxs-lookup"><span data-stu-id="cdef6-197">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="cdef6-198">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="cdef6-198">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="cdef6-199">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o método <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-199">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="cdef6-200">Em seguida, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="cdef6-200">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-201">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-201">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="cdef6-202">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-202">The JSON property naming policy:</span></span>

* <span data-ttu-id="cdef6-203">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-203">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="cdef6-204">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-204">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="cdef6-205">É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="cdef6-205">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="cdef6-206">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="cdef6-206">Camel case dictionary keys</span></span>

<span data-ttu-id="cdef6-207">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as chaves de `string` poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="cdef6-207">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="cdef6-208">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-208">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-209">A serialização de um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria na saída JSON, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-209">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="cdef6-210">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-210">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="cdef6-211">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo se você especificar `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-211">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="cdef6-212">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="cdef6-212">Enums as strings</span></span>

<span data-ttu-id="cdef6-213">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="cdef6-213">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="cdef6-214">Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-214">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="cdef6-215">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="cdef6-215">For example, suppose you need to serialize the following class that has an enum:</span></span>

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

<span data-ttu-id="cdef6-216">Se o resumo for `Hot`, por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="cdef6-216">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

<span data-ttu-id="cdef6-217">O código de exemplo a seguir serializa os nomes de enumeração e os converte em camel case:</span><span class="sxs-lookup"><span data-stu-id="cdef6-217">The following sample code serializes the enum names instead, and converts them to camel case:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

<span data-ttu-id="cdef6-218">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-218">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="cdef6-219">O suporte a enums como cadeias de caracteres se aplica à desserialização também, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-219">The support for enums as strings applies to deserialization also, as shown in the following example:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="cdef6-220">Excluir propriedades da serialização</span><span class="sxs-lookup"><span data-stu-id="cdef6-220">Exclude properties from serialization</span></span>

<span data-ttu-id="cdef6-221">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-221">By default, all public properties are serialized.</span></span> <span data-ttu-id="cdef6-222">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="cdef6-222">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="cdef6-223">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-223">This section explains how to exclude:</span></span>

* <span data-ttu-id="cdef6-224">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="cdef6-224">Individual properties</span></span>
* <span data-ttu-id="cdef6-225">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="cdef6-225">All read-only properties</span></span>
* <span data-ttu-id="cdef6-226">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="cdef6-226">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="cdef6-227">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="cdef6-227">Exclude individual properties</span></span>

<span data-ttu-id="cdef6-228">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="cdef6-228">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="cdef6-229">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-229">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="cdef6-230">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="cdef6-230">Exclude all read-only properties</span></span>

<span data-ttu-id="cdef6-231">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="cdef6-231">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="cdef6-232">Para excluir todas as propriedades somente leitura, defina o <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-232">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-233">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-233">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="cdef6-234">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-234">This option applies only to serialization.</span></span> <span data-ttu-id="cdef6-235">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="cdef6-235">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="cdef6-236">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="cdef6-236">Exclude all null value properties</span></span>

<span data-ttu-id="cdef6-237">Para excluir todas as propriedades de valor nulo, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-237">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-238">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-238">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="cdef6-239">propriedade</span><span class="sxs-lookup"><span data-stu-id="cdef6-239">Property</span></span> |<span data-ttu-id="cdef6-240">Valor</span><span class="sxs-lookup"><span data-stu-id="cdef6-240">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="cdef6-241">Date</span><span class="sxs-lookup"><span data-stu-id="cdef6-241">Date</span></span>    | <span data-ttu-id="cdef6-242">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="cdef6-242">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="cdef6-243">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="cdef6-243">TemperatureC</span></span>| <span data-ttu-id="cdef6-244">25</span><span class="sxs-lookup"><span data-stu-id="cdef6-244">25</span></span> |
| <span data-ttu-id="cdef6-245">Resumo</span><span class="sxs-lookup"><span data-stu-id="cdef6-245">Summary</span></span>| <span data-ttu-id="cdef6-246">nulo</span><span class="sxs-lookup"><span data-stu-id="cdef6-246">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="cdef6-247">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-247">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="cdef6-248">Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="cdef6-248">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="cdef6-249">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="cdef6-249">Customize character encoding</span></span>

<span data-ttu-id="cdef6-250">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="cdef6-250">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="cdef6-251">Ou seja, ele os substitui por `\uxxxx` em que `xxxxx` é o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="cdef6-251">That is, it replaces them with `\uxxxx` where `xxxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="cdef6-252">Por exemplo, se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="cdef6-252">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="cdef6-253">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="cdef6-253">Serialize language character sets</span></span>

<span data-ttu-id="cdef6-254">Para serializar os conjuntos de caracteres de um ou mais idiomas, especifique [intervalo (s) Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-254">To serialize the character set(s) of one or more languages, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-255">Esse código serializa os caracteres cirílico e grego.</span><span class="sxs-lookup"><span data-stu-id="cdef6-255">This code serializes Cyrillic and Greek characters.</span></span> <span data-ttu-id="cdef6-256">Os caracteres cirílicos são mostrados no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-256">Cyrillic characters are shown in the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

<span data-ttu-id="cdef6-257">Para especificar todos os idiomas, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-257">To specify all languages, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="cdef6-258">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="cdef6-258">Serialize specific characters</span></span>

<span data-ttu-id="cdef6-259">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="cdef6-259">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="cdef6-260">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="cdef6-260">The following example serializes only the first two characters of жарко:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cdef6-261">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="cdef6-261">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="cdef6-262">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="cdef6-262">Serialize all characters</span></span>

<span data-ttu-id="cdef6-263">Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-263">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> <span data-ttu-id="cdef6-264">Ao contrário do codificador padrão, o codificador de `UnsafeRelaxedJsonEscaping`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-264">Unlike the default encoder, the `UnsafeRelaxedJsonEscaping` encoder:</span></span>
>
> * <span data-ttu-id="cdef6-265">Não sai de caracteres sensíveis a HTML, como `<`, `>`, `&`e `'`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-265">Doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="cdef6-266">O não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que desconcordem com o conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="cdef6-266">Doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
> * <span data-ttu-id="cdef6-267">É mais permissivo do que o codificador padrão no qual os caracteres têm permissão para passar sem escape.</span><span class="sxs-lookup"><span data-stu-id="cdef6-267">Is more permissive than the default encoder on which characters are allowed to pass through unescaped.</span></span>
>
> <span data-ttu-id="cdef6-268">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cdef6-268">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="cdef6-269">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-269">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="cdef6-270">Nunca permita que a saída de `UnsafeRelaxedJsonEscaping` bruta seja emitida em uma página HTML ou em um elemento `<script>`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-270">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="cdef6-271">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="cdef6-271">Serialize properties of derived classes</span></span>

<span data-ttu-id="cdef6-272">Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado.</span><span class="sxs-lookup"><span data-stu-id="cdef6-272">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="cdef6-273">Por exemplo, suponha que você tenha uma classe `WeatherForecast` e uma classe derivada `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="cdef6-274">E suponha que o argumento de tipo do método de `Serialize` em tempo de compilação seja `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="cdef6-275">Nesse cenário, a propriedade `WindSpeed` não é serializada, mesmo que o objeto `weatherForecast` seja, na verdade, um objeto `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="cdef6-276">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="cdef6-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="cdef6-277">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="cdef6-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="cdef6-278">Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="cdef6-278">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="cdef6-279">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="cdef6-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="cdef6-280">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-280">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="cdef6-281">No cenário de exemplo anterior, ambas as abordagens fazem com que a propriedade `WindSpeed` seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="cdef6-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="cdef6-282">Para obter informações sobre desserialização polimórfica, consulte [dar suporte à desserialização polimórfica](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="cdef6-282">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="cdef6-283">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="cdef6-283">Allow comments and trailing commas</span></span>

<span data-ttu-id="cdef6-284">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="cdef6-284">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="cdef6-285">Para permitir comentários no JSON, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> como `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-285">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="cdef6-286">E para permitir vírgulas à direita, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-286">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="cdef6-287">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-287">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="cdef6-288">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="cdef6-288">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="cdef6-289">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="cdef6-289">Case-insensitive property matching</span></span>

<span data-ttu-id="cdef6-290">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="cdef6-290">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="cdef6-291">Para alterar esse comportamento, defina o <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-291">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="cdef6-292">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="cdef6-292">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="cdef6-293">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="cdef6-293">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="handle-overflow-json"></a><span data-ttu-id="cdef6-294">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="cdef6-294">Handle overflow JSON</span></span>

<span data-ttu-id="cdef6-295">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="cdef6-295">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="cdef6-296">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cdef6-296">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="cdef6-297">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cdef6-297">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="cdef6-298">Se você desserializar o JSON mostrado no tipo mostrado, as propriedades `DatesAvailable` e `SummaryWords` ficarão em qualquer lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="cdef6-298">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="cdef6-299">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-299">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="cdef6-300">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares chave-valor da propriedade `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="cdef6-300">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="cdef6-301">propriedade</span><span class="sxs-lookup"><span data-stu-id="cdef6-301">Property</span></span> |<span data-ttu-id="cdef6-302">Valor</span><span class="sxs-lookup"><span data-stu-id="cdef6-302">Value</span></span>  |<span data-ttu-id="cdef6-303">Anotações</span><span class="sxs-lookup"><span data-stu-id="cdef6-303">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="cdef6-304">Date</span><span class="sxs-lookup"><span data-stu-id="cdef6-304">Date</span></span>    | <span data-ttu-id="cdef6-305">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="cdef6-305">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="cdef6-306">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="cdef6-306">TemperatureC</span></span>| <span data-ttu-id="cdef6-307">0</span><span class="sxs-lookup"><span data-stu-id="cdef6-307">0</span></span> | <span data-ttu-id="cdef6-308">Incompatibilidade de maiúsculas e minúsculas (`temperatureC` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="cdef6-308">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="cdef6-309">Resumo</span><span class="sxs-lookup"><span data-stu-id="cdef6-309">Summary</span></span> | <span data-ttu-id="cdef6-310">Pontos</span><span class="sxs-lookup"><span data-stu-id="cdef6-310">Hot</span></span> ||
| <span data-ttu-id="cdef6-311">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="cdef6-311">ExtensionData</span></span> | <span data-ttu-id="cdef6-312">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="cdef6-312">temperatureC: 25</span></span> |<span data-ttu-id="cdef6-313">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="cdef6-313">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="cdef6-314">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="cdef6-314">DatesAvailable:</span></span><br>  <span data-ttu-id="cdef6-315">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="cdef6-315">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="cdef6-316">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="cdef6-316">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="cdef6-317">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="cdef6-317">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="cdef6-318">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="cdef6-318">SummaryWords:</span></span><br><span data-ttu-id="cdef6-319">Legais</span><span class="sxs-lookup"><span data-stu-id="cdef6-319">Cool</span></span><br><span data-ttu-id="cdef6-320">Vento</span><span class="sxs-lookup"><span data-stu-id="cdef6-320">Windy</span></span><br><span data-ttu-id="cdef6-321">Humid</span><span class="sxs-lookup"><span data-stu-id="cdef6-321">Humid</span></span> |<span data-ttu-id="cdef6-322">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="cdef6-322">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="cdef6-323">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="cdef6-323">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="cdef6-324">Observe que o nome da propriedade `ExtensionData` não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="cdef6-324">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="cdef6-325">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="cdef6-325">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="cdef6-326">Ignorar nulo ao desserializar</span><span class="sxs-lookup"><span data-stu-id="cdef6-326">Ignore null when deserializing</span></span>

<span data-ttu-id="cdef6-327">Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL.</span><span class="sxs-lookup"><span data-stu-id="cdef6-327">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="cdef6-328">Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.</span><span class="sxs-lookup"><span data-stu-id="cdef6-328">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="cdef6-329">Por exemplo, suponha que o código a seguir represente o objeto de destino:</span><span class="sxs-lookup"><span data-stu-id="cdef6-329">For example, suppose the following code represents your target object:</span></span>

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="cdef6-330">E suponha que o JSON a seguir seja desserializado:</span><span class="sxs-lookup"><span data-stu-id="cdef6-330">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

<span data-ttu-id="cdef6-331">Após a desserialização, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é nula.</span><span class="sxs-lookup"><span data-stu-id="cdef6-331">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="cdef6-332">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cdef6-332">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

<span data-ttu-id="cdef6-333">Com essa opção, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é o valor padrão "sem Resumo" após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="cdef6-333">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="cdef6-334">Os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="cdef6-334">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="cdef6-335">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="cdef6-335">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="cdef6-336">Para obter mais informações, consulte o [problema em tipos de valores não anuláveis](https://github.com/dotnet/corefx/issues/40922) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="cdef6-336">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="cdef6-337">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="cdef6-337">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="cdef6-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="cdef6-339">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="cdef6-339">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="cdef6-340">O método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="cdef6-340">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="cdef6-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET, como `String`, `Int32`e `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="cdef6-342">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="cdef6-342">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="cdef6-343">O método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="cdef6-343">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="cdef6-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento (DOM) somente leitura usando `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="cdef6-345">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="cdef6-345">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="cdef6-346">Os elementos JSON que compõem a carga podem ser acessados por meio do tipo de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-346">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="cdef6-347">O `JsonElement` fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="cdef6-347">The `JsonElement` provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="cdef6-348">`JsonDocument` expõe uma propriedade <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="cdef6-348">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="cdef6-349">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="cdef6-349">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="cdef6-350">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="cdef6-350">Use JsonDocument for access to data</span></span>

<span data-ttu-id="cdef6-351">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.JsonDocument> para acesso aleatório aos dados:</span><span class="sxs-lookup"><span data-stu-id="cdef6-351">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data:</span></span>

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

<span data-ttu-id="cdef6-352">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="cdef6-352">The preceding code:</span></span>

* <span data-ttu-id="cdef6-353">Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-353">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="cdef6-354">Calcula uma classificação média para objetos em uma matriz de `Students` que têm uma propriedade `Grade`.</span><span class="sxs-lookup"><span data-stu-id="cdef6-354">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="cdef6-355">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="cdef6-355">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="cdef6-356">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="cdef6-356">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="cdef6-357">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-357">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span></span>

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

<span data-ttu-id="cdef6-358">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="cdef6-358">Here's an example of the JSON that this code processes:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="cdef6-359">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-359">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="cdef6-360">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-360">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

<span data-ttu-id="cdef6-361">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="cdef6-361">The preceding code:</span></span>

* <span data-ttu-id="cdef6-362">Lê um arquivo JSON, carrega os dados em um `JsonDocument`e grava JSON formatado (bem impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cdef6-362">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="cdef6-363">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="cdef6-363">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="cdef6-364">Quando terminar, o chamará <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> no gravador.</span><span class="sxs-lookup"><span data-stu-id="cdef6-364">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="cdef6-365">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="cdef6-365">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="cdef6-366">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="cdef6-366">Here's an example of JSON input to be processed by the example code:</span></span>

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

<span data-ttu-id="cdef6-367">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="cdef6-367">The result is the following pretty-printed JSON output:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="cdef6-368">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="cdef6-368">Use Utf8JsonWriter</span></span>

<span data-ttu-id="cdef6-369">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-369">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

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

## <a name="use-utf8jsonreader"></a><span data-ttu-id="cdef6-370">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="cdef6-370">Use Utf8JsonReader</span></span>

<span data-ttu-id="cdef6-371">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="cdef6-371">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

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

<span data-ttu-id="cdef6-372">O código anterior pressupõe que a variável `jsonUtf8` é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cdef6-372">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="cdef6-373">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="cdef6-373">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="cdef6-374">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="cdef6-374">The following example shows how to read a file synchronously and search for a value:</span></span>

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

<span data-ttu-id="cdef6-375">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="cdef6-375">The preceding code:</span></span>

* <span data-ttu-id="cdef6-376">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cdef6-376">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="cdef6-377">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="cdef6-377">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="cdef6-378">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cdef6-378">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="cdef6-379">Conta objetos e `name` valores de propriedade que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="cdef6-379">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="cdef6-380">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="cdef6-380">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="cdef6-381">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="cdef6-381">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a><span data-ttu-id="cdef6-382">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="cdef6-382">Additional resources</span></span>

* [<span data-ttu-id="cdef6-383">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-383">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="cdef6-384">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-384">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="cdef6-385">Gravar conversores personalizados para System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-385">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="cdef6-386">Suporte a DateTime e DateTimeOffset em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="cdef6-386">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
