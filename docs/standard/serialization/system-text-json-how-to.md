---
title: Como serializar e desserializar JSON usando C# -.net
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8025f84f2425f5b91e08b28ddb24d105d8c4d1a3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159579"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="aaa7c-102">Como serializar e desserializar (empacotar e desempacotar) JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="aaa7c-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="aaa7c-103">Este artigo mostra como usar o namespace <xref:System.Text.Json> para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="aaa7c-104">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="aaa7c-105">A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> a `true` como "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="aaa7c-106">Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="aaa7c-107">Namespaces</span><span class="sxs-lookup"><span data-stu-id="aaa7c-107">Namespaces</span></span>

<span data-ttu-id="aaa7c-108">O namespace <xref:System.Text.Json> contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="aaa7c-109">O namespace <xref:System.Text.Json.Serialization> contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="aaa7c-110">Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="aaa7c-111">Atualmente, não há suporte para atributos do namespace <xref:System.Runtime.Serialization> no `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="aaa7c-112">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="aaa7c-113">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="aaa7c-114">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-115">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-116">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-117">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="aaa7c-118">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="aaa7c-119">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="aaa7c-119">Serialization example</span></span>

<span data-ttu-id="aaa7c-120">Aqui está uma classe de exemplo que contém coleções e uma classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="aaa7c-121">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="aaa7c-122">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-122">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="aaa7c-123">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="aaa7c-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="aaa7c-124">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="aaa7c-124">Serialize to UTF-8</span></span>

<span data-ttu-id="aaa7c-125">Para serializar para UTF-8, chame o método <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-126">Uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que usa uma <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="aaa7c-127">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="aaa7c-128">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="aaa7c-129">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="aaa7c-129">Serialization behavior</span></span>

* <span data-ttu-id="aaa7c-130">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="aaa7c-131">Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="aaa7c-132">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="aaa7c-133">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-133">By default, JSON is minified.</span></span> <span data-ttu-id="aaa7c-134">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="aaa7c-135">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="aaa7c-136">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="aaa7c-137">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-137">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="aaa7c-138">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-138">Currently, fields are excluded.</span></span>

<span data-ttu-id="aaa7c-139">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-139">Supported types include:</span></span>

* <span data-ttu-id="aaa7c-140">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-140">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="aaa7c-141">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-141">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="aaa7c-142">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-142">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="aaa7c-143">`Dictionary<string,TValue>` em que `TValue` é `object`, `JsonElement`ou um POCO.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-143">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="aaa7c-144">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-144">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="aaa7c-145">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-145">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="aaa7c-146">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-146">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="aaa7c-147">Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-147">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="aaa7c-148">O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da classe `WeatherForecast` mostrada anteriormente para o [exemplo de serialização](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="aaa7c-148">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-149">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-149">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-150">Para desserializar de um arquivo usando código assíncrono, chame o método <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-150">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="aaa7c-151">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="aaa7c-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="aaa7c-152">Para desserializar do UTF-8, chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> que usa uma `Utf8JsonReader` ou uma `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="aaa7c-153">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-153">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="aaa7c-154">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="aaa7c-154">Deserialization behavior</span></span>

* <span data-ttu-id="aaa7c-155">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-155">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="aaa7c-156">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-156">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="aaa7c-157">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-157">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="aaa7c-158">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-158">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="aaa7c-159">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-159">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="aaa7c-160">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-160">By default, enums are supported as numbers.</span></span> <span data-ttu-id="aaa7c-161">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-161">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="aaa7c-162">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-162">Fields aren't supported.</span></span>
* <span data-ttu-id="aaa7c-163">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-163">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="aaa7c-164">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-164">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="aaa7c-165">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-165">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="aaa7c-166">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-166">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="aaa7c-167">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="aaa7c-167">Serialize to formatted JSON</span></span>

<span data-ttu-id="aaa7c-168">Para imprimir a saída JSON, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-168">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="aaa7c-169">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-169">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="aaa7c-170">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="aaa7c-170">Customize JSON names and values</span></span>

<span data-ttu-id="aaa7c-171">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-171">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="aaa7c-172">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-172">Enum values are represented as numbers.</span></span> <span data-ttu-id="aaa7c-173">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-173">This section explains how to:</span></span>

* [<span data-ttu-id="aaa7c-174">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="aaa7c-174">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="aaa7c-175">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="aaa7c-175">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="aaa7c-176">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="aaa7c-176">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="aaa7c-177">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="aaa7c-177">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="aaa7c-178">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="aaa7c-178">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="aaa7c-179">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-179">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="aaa7c-180">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="aaa7c-180">Customize individual property names</span></span>

<span data-ttu-id="aaa7c-181">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="aaa7c-181">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="aaa7c-182">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-182">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="aaa7c-183">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-183">The property name set by this attribute:</span></span>

* <span data-ttu-id="aaa7c-184">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-184">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="aaa7c-185">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-185">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="aaa7c-186">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="aaa7c-186">Use camel case for all JSON property names</span></span>

<span data-ttu-id="aaa7c-187">Para usar o camel case para todos os nomes de propriedade JSON, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-187">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="aaa7c-188">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-188">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="aaa7c-189">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-189">The camel case property naming policy:</span></span>

* <span data-ttu-id="aaa7c-190">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="aaa7c-191">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-191">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="aaa7c-192">É por isso que o nome da propriedade JSON `Wind` no exemplo não é o camel case.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-192">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="aaa7c-193">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="aaa7c-193">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="aaa7c-194">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o método <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-194">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="aaa7c-195">Em seguida, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-195">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-196">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-196">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="aaa7c-197">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-197">The JSON property naming policy:</span></span>

* <span data-ttu-id="aaa7c-198">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-198">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="aaa7c-199">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-199">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="aaa7c-200">É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-200">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="aaa7c-201">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="aaa7c-201">Camel case dictionary keys</span></span>

<span data-ttu-id="aaa7c-202">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as chaves de `string` poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-202">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="aaa7c-203">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-203">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-204">A serialização de um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria na saída JSON, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-204">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="aaa7c-205">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-205">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="aaa7c-206">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo se você especificar `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-206">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="aaa7c-207">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="aaa7c-207">Enums as strings</span></span>

<span data-ttu-id="aaa7c-208">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-208">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="aaa7c-209">Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-209">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="aaa7c-210">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-210">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="aaa7c-211">Se o resumo for `Hot`, por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-211">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="aaa7c-212">O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-212">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-213">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-213">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="aaa7c-214">Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-214">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="aaa7c-215">Excluir propriedades da serialização</span><span class="sxs-lookup"><span data-stu-id="aaa7c-215">Exclude properties from serialization</span></span>

<span data-ttu-id="aaa7c-216">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-216">By default, all public properties are serialized.</span></span> <span data-ttu-id="aaa7c-217">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-217">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="aaa7c-218">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-218">This section explains how to exclude:</span></span>

* [<span data-ttu-id="aaa7c-219">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="aaa7c-219">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="aaa7c-220">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="aaa7c-220">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="aaa7c-221">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="aaa7c-221">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="aaa7c-222">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="aaa7c-222">Exclude individual properties</span></span>

<span data-ttu-id="aaa7c-223">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="aaa7c-223">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="aaa7c-224">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-224">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="aaa7c-225">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="aaa7c-225">Exclude all read-only properties</span></span>

<span data-ttu-id="aaa7c-226">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-226">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="aaa7c-227">Para excluir todas as propriedades somente leitura, defina o <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-227">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-228">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="aaa7c-229">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-229">This option applies only to serialization.</span></span> <span data-ttu-id="aaa7c-230">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-230">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="aaa7c-231">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="aaa7c-231">Exclude all null value properties</span></span>

<span data-ttu-id="aaa7c-232">Para excluir todas as propriedades de valor nulo, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-232">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-233">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-233">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="aaa7c-234">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aaa7c-234">Property</span></span> |<span data-ttu-id="aaa7c-235">Valor</span><span class="sxs-lookup"><span data-stu-id="aaa7c-235">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="aaa7c-236">Data</span><span class="sxs-lookup"><span data-stu-id="aaa7c-236">Date</span></span>    | <span data-ttu-id="aaa7c-237">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="aaa7c-237">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="aaa7c-238">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="aaa7c-238">TemperatureCelsius</span></span>| <span data-ttu-id="aaa7c-239">25</span><span class="sxs-lookup"><span data-stu-id="aaa7c-239">25</span></span> |
| <span data-ttu-id="aaa7c-240">Resumo</span><span class="sxs-lookup"><span data-stu-id="aaa7c-240">Summary</span></span>| <span data-ttu-id="aaa7c-241">nulo</span><span class="sxs-lookup"><span data-stu-id="aaa7c-241">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="aaa7c-242">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-242">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="aaa7c-243">Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-243">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="aaa7c-244">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="aaa7c-244">Customize character encoding</span></span>

<span data-ttu-id="aaa7c-245">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-245">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="aaa7c-246">Ou seja, ele os substitui por `\uxxxx` em que `xxxx` é o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-246">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="aaa7c-247">Por exemplo, se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-247">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="aaa7c-248">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="aaa7c-248">Serialize language character sets</span></span>

<span data-ttu-id="aaa7c-249">Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique [intervalo (s) Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-249">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="aaa7c-250">Este código não sai de escape de caracteres cirílico ou grego.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-250">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="aaa7c-251">Se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-251">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="aaa7c-252">Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-252">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="aaa7c-253">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="aaa7c-253">Serialize specific characters</span></span>

<span data-ttu-id="aaa7c-254">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-254">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="aaa7c-255">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-255">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="aaa7c-256">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-256">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="aaa7c-257">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="aaa7c-257">Serialize all characters</span></span>

<span data-ttu-id="aaa7c-258">Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-258">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="aaa7c-259">Em comparação com o codificador padrão, o codificador de `UnsafeRelaxedJsonEscaping` é mais permissivo de permitir que os caracteres passem sem escape:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-259">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="aaa7c-260">Ele não sai de caracteres sensíveis a HTML, como `<`, `>`, `&`e `'`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-260">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="aaa7c-261">Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-261">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="aaa7c-262">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-262">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="aaa7c-263">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-263">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="aaa7c-264">Nunca permita que a saída de `UnsafeRelaxedJsonEscaping` bruta seja emitida em uma página HTML ou em um elemento `<script>`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-264">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="aaa7c-265">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="aaa7c-265">Serialize properties of derived classes</span></span>

<span data-ttu-id="aaa7c-266">Não há suporte para a serialização de uma hierarquia de tipo polimórfico.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-266">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="aaa7c-267">Por exemplo, se uma propriedade for definida como uma interface ou uma classe abstrata, somente as propriedades definidas na interface ou na classe abstrata serão serializadas, mesmo que o tipo de tempo de execução tenha propriedades adicionais.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-267">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="aaa7c-268">As exceções a esse comportamento são explicadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-268">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="aaa7c-269">Por exemplo, suponha que você tenha uma classe `WeatherForecast` e uma classe derivada `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-269">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="aaa7c-270">E suponha que o argumento de tipo do método de `Serialize` em tempo de compilação seja `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-270">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="aaa7c-271">Nesse cenário, a propriedade `WindSpeed` não é serializada, mesmo que o objeto `weatherForecast` seja, na verdade, um objeto `WeatherForecastDerived`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-271">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="aaa7c-272">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-272">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="aaa7c-273">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-273">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="aaa7c-274">Para serializar as propriedades do tipo derivado no exemplo anterior, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-274">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="aaa7c-275">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-275">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="aaa7c-276">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-276">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="aaa7c-277">No cenário de exemplo anterior, ambas as abordagens fazem com que a propriedade `WindSpeed` seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-277">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="aaa7c-278">Essas abordagens fornecem serialização polimórfica somente para o objeto raiz a ser serializado, não para propriedades desse objeto raiz.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-278">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="aaa7c-279">Você pode obter a serialização polimórfica para objetos de nível inferior se defini-los como tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-279">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="aaa7c-280">Por exemplo, suponha que sua classe `WeatherForecast` tenha uma propriedade chamada `PreviousForecast` que possa ser definida como tipo `WeatherForecast` ou `object`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-280">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="aaa7c-281">Se a propriedade `PreviousForecast` contiver uma instância de `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-281">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="aaa7c-282">A saída JSON da serialização `WeatherForecastWithPrevious` **não inclui** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-282">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="aaa7c-283">A saída JSON da serialização `WeatherForecastWithPreviousAsObject` **inclui** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-283">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="aaa7c-284">Para serializar `WeatherForecastWithPreviousAsObject`, não é necessário chamar `Serialize<object>` ou `GetType` porque o objeto raiz não é aquele que pode ser de um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-284">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="aaa7c-285">O exemplo de código a seguir não chama `Serialize<object>` ou `GetType`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-285">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="aaa7c-286">O código anterior serializa corretamente `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-286">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="aaa7c-287">A mesma abordagem de definir propriedades como `object` funciona com interfaces.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-287">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="aaa7c-288">Suponha que você tenha a seguinte interface e implementação e queira serializar uma classe com propriedades que contêm instâncias de implementação:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-288">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="aaa7c-289">Quando você serializa uma instância do `Forecasts`, somente `Tuesday` mostra a propriedade `WindSpeed`, porque `Tuesday` é definido como `object`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-289">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="aaa7c-290">O exemplo a seguir mostra o JSON que resulta do código anterior:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-290">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="aaa7c-291">Para obter mais informações sobre **serialização**polimórfica e informações sobre **desserialização**, consulte [como migrar de Newtonsoft. JSON para System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="aaa7c-291">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="aaa7c-292">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="aaa7c-292">Allow comments and trailing commas</span></span>

<span data-ttu-id="aaa7c-293">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-293">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="aaa7c-294">Para permitir comentários no JSON, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> como `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-294">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="aaa7c-295">E para permitir vírgulas à direita, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-295">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="aaa7c-296">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-296">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-297">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-297">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="aaa7c-298">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="aaa7c-298">Case-insensitive property matching</span></span>

<span data-ttu-id="aaa7c-299">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-299">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="aaa7c-300">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-300">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-301">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-301">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="aaa7c-302">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-302">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="aaa7c-303">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="aaa7c-303">Handle overflow JSON</span></span>

<span data-ttu-id="aaa7c-304">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-304">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="aaa7c-305">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-305">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="aaa7c-306">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-306">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="aaa7c-307">Se você desserializar o JSON mostrado no tipo mostrado, as propriedades `DatesAvailable` e `SummaryWords` ficarão em qualquer lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-307">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="aaa7c-308">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-308">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="aaa7c-309">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares chave-valor da propriedade `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-309">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="aaa7c-310">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aaa7c-310">Property</span></span> |<span data-ttu-id="aaa7c-311">Valor</span><span class="sxs-lookup"><span data-stu-id="aaa7c-311">Value</span></span>  |<span data-ttu-id="aaa7c-312">Observações</span><span class="sxs-lookup"><span data-stu-id="aaa7c-312">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="aaa7c-313">Data</span><span class="sxs-lookup"><span data-stu-id="aaa7c-313">Date</span></span>    | <span data-ttu-id="aaa7c-314">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="aaa7c-314">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="aaa7c-315">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="aaa7c-315">TemperatureCelsius</span></span>| <span data-ttu-id="aaa7c-316">0</span><span class="sxs-lookup"><span data-stu-id="aaa7c-316">0</span></span> | <span data-ttu-id="aaa7c-317">Incompatibilidade de maiúsculas e minúsculas (`temperatureCelsius` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-317">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="aaa7c-318">Resumo</span><span class="sxs-lookup"><span data-stu-id="aaa7c-318">Summary</span></span> | <span data-ttu-id="aaa7c-319">Dinâmica</span><span class="sxs-lookup"><span data-stu-id="aaa7c-319">Hot</span></span> ||
| <span data-ttu-id="aaa7c-320">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="aaa7c-320">ExtensionData</span></span> | <span data-ttu-id="aaa7c-321">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="aaa7c-321">temperatureCelsius: 25</span></span> |<span data-ttu-id="aaa7c-322">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-322">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="aaa7c-323">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-323">DatesAvailable:</span></span><br>  <span data-ttu-id="aaa7c-324">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="aaa7c-324">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="aaa7c-325">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="aaa7c-325">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="aaa7c-326">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-326">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="aaa7c-327">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-327">SummaryWords:</span></span><br><span data-ttu-id="aaa7c-328">Estática</span><span class="sxs-lookup"><span data-stu-id="aaa7c-328">Cool</span></span><br><span data-ttu-id="aaa7c-329">Vento</span><span class="sxs-lookup"><span data-stu-id="aaa7c-329">Windy</span></span><br><span data-ttu-id="aaa7c-330">Humid</span><span class="sxs-lookup"><span data-stu-id="aaa7c-330">Humid</span></span> |<span data-ttu-id="aaa7c-331">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-331">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="aaa7c-332">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-332">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="aaa7c-333">Observe que o nome da propriedade `ExtensionData` não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-333">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="aaa7c-334">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-334">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="aaa7c-335">Ignorar nulo ao desserializar</span><span class="sxs-lookup"><span data-stu-id="aaa7c-335">Ignore null when deserializing</span></span>

<span data-ttu-id="aaa7c-336">Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-336">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="aaa7c-337">Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-337">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="aaa7c-338">Por exemplo, suponha que o código a seguir represente o objeto de destino:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-338">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="aaa7c-339">E suponha que o JSON a seguir seja desserializado:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-339">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="aaa7c-340">Após a desserialização, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é nula.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-340">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="aaa7c-341">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-341">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-342">Com essa opção, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é o valor padrão "sem Resumo" após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-342">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="aaa7c-343">Os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-343">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="aaa7c-344">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-344">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="aaa7c-345">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="aaa7c-345">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="aaa7c-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, de baixa alocação e somente de encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>` ou `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="aaa7c-347">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-347">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="aaa7c-348">O método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-348">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="aaa7c-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET, como `String`, `Int32`e `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="aaa7c-350">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-350">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="aaa7c-351">O método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-351">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="aaa7c-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento (DOM) somente leitura usando `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="aaa7c-353">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-353">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="aaa7c-354">Os elementos JSON que compõem a carga podem ser acessados por meio do tipo de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-354">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="aaa7c-355">O tipo de `JsonElement` fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-355">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="aaa7c-356">`JsonDocument` expõe uma propriedade <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-356">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="aaa7c-357">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-357">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="aaa7c-358">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="aaa7c-358">Use JsonDocument for access to data</span></span>

<span data-ttu-id="aaa7c-359">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.JsonDocument> para acesso aleatório a dados em uma cadeia de caracteres JSON:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-359">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="aaa7c-360">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-360">The preceding code:</span></span>

* <span data-ttu-id="aaa7c-361">Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-361">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="aaa7c-362">Calcula uma classificação média para objetos em uma matriz de `Students` que têm uma propriedade `Grade`.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-362">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="aaa7c-363">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-363">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="aaa7c-364">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-364">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="aaa7c-365">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-365">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="aaa7c-366">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-366">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="aaa7c-367">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="aaa7c-367">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="aaa7c-368">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-368">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="aaa7c-369">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-369">The preceding code:</span></span>

* <span data-ttu-id="aaa7c-370">Lê um arquivo JSON, carrega os dados em um `JsonDocument`e grava JSON formatado (bem impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-370">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="aaa7c-371">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-371">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="aaa7c-372">Quando terminar, o chamará <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> no gravador.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-372">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="aaa7c-373">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-373">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="aaa7c-374">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-374">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="aaa7c-375">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-375">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="aaa7c-376">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="aaa7c-376">Use Utf8JsonWriter</span></span>

<span data-ttu-id="aaa7c-377">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-377">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="aaa7c-378">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="aaa7c-378">Use Utf8JsonReader</span></span>

<span data-ttu-id="aaa7c-379">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="aaa7c-380">O código anterior pressupõe que a variável `jsonUtf8` é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-380">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="aaa7c-381">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="aaa7c-381">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="aaa7c-382">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-382">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="aaa7c-383">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-383">The preceding code:</span></span>

* <span data-ttu-id="aaa7c-384">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-384">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="aaa7c-385">Conta objetos e valores de propriedade "Name" que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="aaa7c-385">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="aaa7c-386">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-386">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="aaa7c-387">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="aaa7c-387">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="aaa7c-388">Se o arquivo contiver uma marca de ordem de byte (BOM) UTF-8, remova-a antes de passar os bytes para a `Utf8JsonReader`, já que o leitor espera texto.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-388">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="aaa7c-389">Caso contrário, a BOM será considerada JSON inválido e o leitor lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-389">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="aaa7c-390">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="aaa7c-390">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="aaa7c-391">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="aaa7c-391">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="aaa7c-392">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="aaa7c-392">Additional resources</span></span>

* <span data-ttu-id="aaa7c-393">[Visão geral de System.Text.Json](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-393">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="aaa7c-394">Como escrever conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="aaa7c-394">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="aaa7c-395">[Como migrar do Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-395">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="aaa7c-396">[Suporte a DateTime e DateTimeOffset no System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-396">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="aaa7c-397">[referência de API de System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="aaa7c-397">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
