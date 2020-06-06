---
title: Como serializar e desserializar JSON usando C#-.NET
description: Este artigo mostra como usar o System.Text.Json namespace para serializar e desserializar do JSON no .net. Ele inclui o código de exemplo.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 7ad2721f12c5d14b61b35ecf7696ff0d6a6f27da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289506"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="44308-104">Como serializar e desserializar (empacotar e desempacotar) JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="44308-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="44308-105">Este artigo mostra como usar o <xref:System.Text.Json> namespace para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="44308-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="44308-106">Se você estiver portando um código existente do `Newtonsoft.Json` , consulte [como migrar `System.Text.Json` para o ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="44308-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="44308-107">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="44308-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="44308-108">A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana).</span><span class="sxs-lookup"><span data-stu-id="44308-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="44308-109">Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="44308-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="44308-110">Os exemplos de código referem-se à seguinte classe e variantes dela:</span><span class="sxs-lookup"><span data-stu-id="44308-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="44308-111">Namespaces</span><span class="sxs-lookup"><span data-stu-id="44308-111">Namespaces</span></span>

<span data-ttu-id="44308-112">O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="44308-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="44308-113">O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="44308-114">Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="44308-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="44308-115"><xref:System.Runtime.Serialization>Atualmente, não há suporte para atributos do namespace no `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="44308-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="44308-116">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="44308-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="44308-117">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="44308-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="44308-118">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="44308-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-119">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-120">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-121">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="44308-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="44308-122">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="44308-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="44308-123">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="44308-123">Serialization example</span></span>

<span data-ttu-id="44308-124">Aqui está uma classe de exemplo que contém coleções e uma classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="44308-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="44308-125">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="44308-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="44308-126">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="44308-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="44308-127">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="44308-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="44308-128">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="44308-128">Serialize to UTF-8</span></span>

<span data-ttu-id="44308-129">Para serializar para UTF-8, chame o <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> método:</span><span class="sxs-lookup"><span data-stu-id="44308-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-130">Uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="44308-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="44308-131">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="44308-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="44308-132">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="44308-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="44308-133">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="44308-133">Serialization behavior</span></span>

* <span data-ttu-id="44308-134">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="44308-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="44308-135">Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="44308-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="44308-136">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="44308-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="44308-137">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="44308-137">By default, JSON is minified.</span></span> <span data-ttu-id="44308-138">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="44308-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="44308-139">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="44308-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="44308-140">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="44308-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="44308-141">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="44308-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="44308-142">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="44308-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="44308-143">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="44308-143">Supported types include:</span></span>

* <span data-ttu-id="44308-144">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="44308-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="44308-145">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="44308-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="44308-146">Matrizes unidimensionais e denteadas ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="44308-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="44308-147">`Dictionary<string,TValue>`onde `TValue` é `object` , `JsonElement` , ou um poco.</span><span class="sxs-lookup"><span data-stu-id="44308-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="44308-148">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="44308-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="44308-149">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="44308-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="44308-150">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="44308-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="44308-151">Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="44308-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="44308-152">O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da `WeatherForecast` classe mostrada anteriormente para o [exemplo de serialização](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="44308-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-153">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-154">Para desserializar de um arquivo usando código assíncrono, chame o <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> método:</span><span class="sxs-lookup"><span data-stu-id="44308-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="44308-155">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="44308-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="44308-156">Para desserializar do UTF-8, chame uma <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> sobrecarga que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>` , conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="44308-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="44308-157">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="44308-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="44308-158">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="44308-158">Deserialization behavior</span></span>

* <span data-ttu-id="44308-159">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="44308-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="44308-160">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="44308-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="44308-161">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="44308-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="44308-162">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="44308-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="44308-163">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="44308-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="44308-164">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="44308-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="44308-165">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="44308-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="44308-166">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="44308-166">Fields aren't supported.</span></span>
* <span data-ttu-id="44308-167">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="44308-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="44308-168">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="44308-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="44308-169">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="44308-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="44308-170">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="44308-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="44308-171">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="44308-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="44308-172">Para imprimir a saída JSON com muita impressão, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` :</span><span class="sxs-lookup"><span data-stu-id="44308-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="44308-173">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="44308-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="44308-174">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="44308-174">Customize JSON names and values</span></span>

<span data-ttu-id="44308-175">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="44308-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="44308-176">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="44308-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="44308-177">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="44308-177">This section explains how to:</span></span>

* [<span data-ttu-id="44308-178">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="44308-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="44308-179">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="44308-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="44308-180">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="44308-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="44308-181">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="44308-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="44308-182">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="44308-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="44308-183">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="44308-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="44308-184">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="44308-184">Customize individual property names</span></span>

<span data-ttu-id="44308-185">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="44308-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="44308-186">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="44308-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="44308-187">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="44308-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="44308-188">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="44308-189">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="44308-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="44308-190">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="44308-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="44308-191">Para usar o camel case para todos os nomes de propriedade JSON, defina como <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="44308-192">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="44308-193">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="44308-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="44308-194">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="44308-195">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="44308-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="44308-196">É por isso que o nome da propriedade JSON `Wind` no exemplo não é camel case.</span><span class="sxs-lookup"><span data-stu-id="44308-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="44308-197">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="44308-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="44308-198">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> método, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="44308-199">Em seguida, defina a <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriedade como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="44308-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-200">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="44308-201">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="44308-202">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="44308-203">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="44308-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="44308-204">É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="44308-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="44308-205">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="44308-205">Camel case dictionary keys</span></span>

<span data-ttu-id="44308-206">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>` , as `string` chaves poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="44308-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="44308-207">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-208">Serializar um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria em uma saída JSON como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="44308-209">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="44308-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="44308-210">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo que você especifique `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="44308-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="44308-211">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="44308-211">Enums as strings</span></span>

<span data-ttu-id="44308-212">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="44308-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="44308-213">Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="44308-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="44308-214">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="44308-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="44308-215">Se o resumo for `Hot` , por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="44308-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="44308-216">O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:</span><span class="sxs-lookup"><span data-stu-id="44308-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-217">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="44308-218">Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="44308-219">Excluir propriedades da serialização</span><span class="sxs-lookup"><span data-stu-id="44308-219">Exclude properties from serialization</span></span>

<span data-ttu-id="44308-220">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="44308-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="44308-221">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="44308-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="44308-222">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="44308-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="44308-223">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="44308-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="44308-224">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="44308-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="44308-225">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="44308-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="44308-226">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="44308-226">Exclude individual properties</span></span>

<span data-ttu-id="44308-227">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="44308-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="44308-228">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="44308-229">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="44308-229">Exclude all read-only properties</span></span>

<span data-ttu-id="44308-230">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="44308-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="44308-231">Para excluir todas as propriedades somente leitura, defina como <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-232">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="44308-233">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="44308-233">This option applies only to serialization.</span></span> <span data-ttu-id="44308-234">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="44308-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="44308-235">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="44308-235">Exclude all null value properties</span></span>

<span data-ttu-id="44308-236">Para excluir todas as propriedades de valor nulo, defina a <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> propriedade como `true` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-237">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="44308-238">Propriedade</span><span class="sxs-lookup"><span data-stu-id="44308-238">Property</span></span> |<span data-ttu-id="44308-239">Valor</span><span class="sxs-lookup"><span data-stu-id="44308-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="44308-240">Data</span><span class="sxs-lookup"><span data-stu-id="44308-240">Date</span></span>    | <span data-ttu-id="44308-241">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="44308-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="44308-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="44308-242">TemperatureCelsius</span></span>| <span data-ttu-id="44308-243">25</span><span class="sxs-lookup"><span data-stu-id="44308-243">25</span></span> |
| <span data-ttu-id="44308-244">Resumo</span><span class="sxs-lookup"><span data-stu-id="44308-244">Summary</span></span>| <span data-ttu-id="44308-245">nulo</span><span class="sxs-lookup"><span data-stu-id="44308-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="44308-246">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="44308-247">Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="44308-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="44308-248">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="44308-248">Customize character encoding</span></span>

<span data-ttu-id="44308-249">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="44308-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="44308-250">Ou seja, ele substitui por `\uxxxx` onde `xxxx` está o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="44308-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="44308-251">Por exemplo, se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="44308-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="44308-252">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="44308-252">Serialize language character sets</span></span>

<span data-ttu-id="44308-253">Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique os [intervalos Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância do <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="44308-254">Este código não sai de escape de caracteres cirílico ou grego.</span><span class="sxs-lookup"><span data-stu-id="44308-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="44308-255">Se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="44308-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="44308-256">Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="44308-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="44308-257">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="44308-257">Serialize specific characters</span></span>

<span data-ttu-id="44308-258">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="44308-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="44308-259">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="44308-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="44308-260">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="44308-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="44308-261">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="44308-261">Serialize all characters</span></span>

<span data-ttu-id="44308-262">Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="44308-263">Em comparação com o codificador padrão, o `UnsafeRelaxedJsonEscaping` codificador é mais permissivo de permitir que os caracteres passem sem escape:</span><span class="sxs-lookup"><span data-stu-id="44308-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="44308-264">Ele não sai de caracteres sensíveis a HTML, como `<` ,, `>` `&` e `'` .</span><span class="sxs-lookup"><span data-stu-id="44308-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="44308-265">Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="44308-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="44308-266">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44308-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="44308-267">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="44308-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="44308-268">Nunca permita que a `UnsafeRelaxedJsonEscaping` saída bruta seja emitida em uma página HTML ou em um `<script>` elemento.</span><span class="sxs-lookup"><span data-stu-id="44308-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="44308-269">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="44308-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="44308-270">Não há suporte para a serialização de uma hierarquia de tipo polimórfico.</span><span class="sxs-lookup"><span data-stu-id="44308-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="44308-271">Por exemplo, se uma propriedade for definida como uma interface ou uma classe abstrata, somente as propriedades definidas na interface ou na classe abstrata serão serializadas, mesmo que o tipo de tempo de execução tenha propriedades adicionais.</span><span class="sxs-lookup"><span data-stu-id="44308-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="44308-272">As exceções a esse comportamento são explicadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="44308-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="44308-273">Por exemplo, suponha que você tenha uma `WeatherForecast` classe e uma classe derivada `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="44308-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="44308-274">E suponha que o argumento de tipo do `Serialize` método em tempo de compilação seja `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="44308-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="44308-275">Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que o `weatherForecast` objeto seja, na verdade, um `WeatherForecastDerived` objeto.</span><span class="sxs-lookup"><span data-stu-id="44308-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="44308-276">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="44308-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="44308-277">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="44308-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="44308-278">Para serializar as propriedades do tipo derivado no exemplo anterior, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="44308-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="44308-279">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="44308-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="44308-280">Declare o objeto a ser serializado como `object` .</span><span class="sxs-lookup"><span data-stu-id="44308-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="44308-281">No cenário de exemplo anterior, ambas as abordagens fazem com que a `WindSpeed` propriedade seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="44308-282">Essas abordagens fornecem serialização polimórfica somente para o objeto raiz a ser serializado, não para propriedades desse objeto raiz.</span><span class="sxs-lookup"><span data-stu-id="44308-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="44308-283">Você pode obter a serialização polimórfica para objetos de nível inferior se defini-los como tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="44308-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="44308-284">Por exemplo, suponha que sua `WeatherForecast` classe tenha uma propriedade chamada `PreviousForecast` que possa ser definida como tipo `WeatherForecast` ou `object` :</span><span class="sxs-lookup"><span data-stu-id="44308-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="44308-285">Se a `PreviousForecast` Propriedade contiver uma instância de `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="44308-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="44308-286">A saída JSON da serialização `WeatherForecastWithPrevious` **não inclui** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="44308-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="44308-287">A saída JSON da serialização `WeatherForecastWithPreviousAsObject` **inclui** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="44308-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="44308-288">Para serializar `WeatherForecastWithPreviousAsObject` , não é necessário chamar `Serialize<object>` ou `GetType` porque o objeto raiz não é aquele que pode ser de um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="44308-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="44308-289">O exemplo de código a seguir não chama `Serialize<object>` ou `GetType` :</span><span class="sxs-lookup"><span data-stu-id="44308-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="44308-290">O código anterior serializa corretamente `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="44308-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="44308-291">A mesma abordagem de definir propriedades como `object` funciona com interfaces.</span><span class="sxs-lookup"><span data-stu-id="44308-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="44308-292">Suponha que você tenha a seguinte interface e implementação e queira serializar uma classe com propriedades que contêm instâncias de implementação:</span><span class="sxs-lookup"><span data-stu-id="44308-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="44308-293">Quando você serializa uma instância do `Forecasts` , `Tuesday` o mostra apenas a `WindSpeed` propriedade, porque `Tuesday` é definido como `object` :</span><span class="sxs-lookup"><span data-stu-id="44308-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="44308-294">O exemplo a seguir mostra o JSON que resulta do código anterior:</span><span class="sxs-lookup"><span data-stu-id="44308-294">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="44308-295">Para obter mais informações sobre a **serialização**polimórfica e informações sobre a **desserialização**, consulte [como migrar do Newtonsoft.Json para System.Text.Json o ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="44308-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="44308-296">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="44308-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="44308-297">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="44308-298">Para permitir comentários no JSON, defina a <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> propriedade como `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="44308-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="44308-299">E para permitir vírgulas à direita, defina a <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="44308-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="44308-300">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="44308-300">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-301">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="44308-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="44308-302">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="44308-302">Case-insensitive property matching</span></span>

<span data-ttu-id="44308-303">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="44308-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="44308-304">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true` :</span><span class="sxs-lookup"><span data-stu-id="44308-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-305">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="44308-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="44308-306">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="44308-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="44308-307">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="44308-307">Handle overflow JSON</span></span>

<span data-ttu-id="44308-308">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="44308-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="44308-309">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="44308-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="44308-310">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="44308-310">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="44308-311">Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="44308-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="44308-312">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="44308-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="44308-313">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave-valor da `ExtensionData` Propriedade:</span><span class="sxs-lookup"><span data-stu-id="44308-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="44308-314">Propriedade</span><span class="sxs-lookup"><span data-stu-id="44308-314">Property</span></span> |<span data-ttu-id="44308-315">Valor</span><span class="sxs-lookup"><span data-stu-id="44308-315">Value</span></span>  |<span data-ttu-id="44308-316">Observações</span><span class="sxs-lookup"><span data-stu-id="44308-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="44308-317">Data</span><span class="sxs-lookup"><span data-stu-id="44308-317">Date</span></span>    | <span data-ttu-id="44308-318">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="44308-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="44308-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="44308-319">TemperatureCelsius</span></span>| <span data-ttu-id="44308-320">0</span><span class="sxs-lookup"><span data-stu-id="44308-320">0</span></span> | <span data-ttu-id="44308-321">Incompatibilidade de maiúsculas e minúsculas ( `temperatureCelsius` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="44308-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="44308-322">Resumo</span><span class="sxs-lookup"><span data-stu-id="44308-322">Summary</span></span> | <span data-ttu-id="44308-323">Dinâmica</span><span class="sxs-lookup"><span data-stu-id="44308-323">Hot</span></span> ||
| <span data-ttu-id="44308-324">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="44308-324">ExtensionData</span></span> | <span data-ttu-id="44308-325">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="44308-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="44308-326">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="44308-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="44308-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="44308-327">DatesAvailable:</span></span><br>  <span data-ttu-id="44308-328">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="44308-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="44308-329">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="44308-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="44308-330">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="44308-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="44308-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="44308-331">SummaryWords:</span></span><br><span data-ttu-id="44308-332">Estática</span><span class="sxs-lookup"><span data-stu-id="44308-332">Cool</span></span><br><span data-ttu-id="44308-333">Vento</span><span class="sxs-lookup"><span data-stu-id="44308-333">Windy</span></span><br><span data-ttu-id="44308-334">Humid</span><span class="sxs-lookup"><span data-stu-id="44308-334">Humid</span></span> |<span data-ttu-id="44308-335">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="44308-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="44308-336">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="44308-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="44308-337">Observe que o `ExtensionData` nome da propriedade não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="44308-338">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="44308-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="44308-339">Ignorar nulo ao desserializar</span><span class="sxs-lookup"><span data-stu-id="44308-339">Ignore null when deserializing</span></span>

<span data-ttu-id="44308-340">Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL.</span><span class="sxs-lookup"><span data-stu-id="44308-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="44308-341">Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.</span><span class="sxs-lookup"><span data-stu-id="44308-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="44308-342">Por exemplo, suponha que o código a seguir represente o objeto de destino:</span><span class="sxs-lookup"><span data-stu-id="44308-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="44308-343">E suponha que o JSON a seguir seja desserializado:</span><span class="sxs-lookup"><span data-stu-id="44308-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="44308-344">Após a desserialização, a `Summary` Propriedade do `WeatherForecastWithDefault` objeto é nula.</span><span class="sxs-lookup"><span data-stu-id="44308-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="44308-345">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-346">Com essa opção, a `Summary` Propriedade do `WeatherForecastWithDefault` objeto é o valor padrão "sem Resumo" após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="44308-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="44308-347">Os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="44308-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="44308-348">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="44308-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="44308-349">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="44308-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="44308-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>é um leitor de alto desempenho, de baixa alocação e somente de encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>` ou `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="44308-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="44308-351">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="44308-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="44308-352">O <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="44308-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="44308-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET como `String` , `Int32` e `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="44308-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="44308-354">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="44308-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="44308-355">O <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="44308-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="44308-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>fornece a capacidade de criar um Modelo de Objeto do Documento somente leitura (DOM) usando o `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="44308-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="44308-357">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="44308-358">Os elementos JSON que compõem a carga podem ser acessados por meio do <xref:System.Text.Json.JsonElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="44308-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="44308-359">O `JsonElement` tipo fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .net comuns.</span><span class="sxs-lookup"><span data-stu-id="44308-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="44308-360">`JsonDocument`expõe uma <xref:System.Text.Json.JsonDocument.RootElement> propriedade.</span><span class="sxs-lookup"><span data-stu-id="44308-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="44308-361">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="44308-362">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="44308-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="44308-363">O exemplo a seguir mostra como usar a <xref:System.Text.Json.JsonDocument> classe para acesso aleatório a dados em uma cadeia de caracteres JSON:</span><span class="sxs-lookup"><span data-stu-id="44308-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="44308-364">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="44308-364">The preceding code:</span></span>

* <span data-ttu-id="44308-365">Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="44308-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="44308-366">Calcula uma classificação média para objetos em uma `Students` matriz que tem uma `Grade` propriedade.</span><span class="sxs-lookup"><span data-stu-id="44308-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="44308-367">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="44308-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="44308-368">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="44308-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="44308-369">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="44308-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="44308-370">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="44308-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="44308-371">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="44308-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="44308-372">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="44308-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="44308-373">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="44308-373">The preceding code:</span></span>

* <span data-ttu-id="44308-374">Lê um arquivo JSON, carrega os dados em um `JsonDocument` e grava JSON formatado (bem-impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="44308-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="44308-375">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="44308-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="44308-376">Quando terminar, chama <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> o gravador.</span><span class="sxs-lookup"><span data-stu-id="44308-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="44308-377">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="44308-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="44308-378">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="44308-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="44308-379">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="44308-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="44308-380">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="44308-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="44308-381">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe:</span><span class="sxs-lookup"><span data-stu-id="44308-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="44308-382">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="44308-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="44308-383">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe:</span><span class="sxs-lookup"><span data-stu-id="44308-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="44308-384">O código anterior pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44308-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="44308-385">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="44308-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="44308-386">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="44308-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="44308-387">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="44308-387">The preceding code:</span></span>

* <span data-ttu-id="44308-388">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="44308-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="44308-389">Conta objetos e valores de propriedade "Name" que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="44308-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="44308-390">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44308-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="44308-391">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>` , usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="44308-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="44308-392">Se o arquivo contiver uma marca de ordem de byte (BOM) UTF-8, remova-a antes de passar os bytes para o `Utf8JsonReader` , uma vez que o leitor espera o texto.</span><span class="sxs-lookup"><span data-stu-id="44308-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="44308-393">Caso contrário, a BOM será considerada JSON inválido e o leitor lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="44308-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="44308-394">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="44308-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="44308-395">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="44308-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="44308-396">Ler de um fluxo usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="44308-396">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="44308-397">Ao ler um arquivo grande (um gigabyte ou mais, por exemplo), talvez você queira evitar ter que carregar todo o arquivo na memória de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="44308-397">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="44308-398">Para esse cenário, você pode usar um <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="44308-398">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="44308-399">Ao usar o `Utf8JsonReader` para ler de um fluxo, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="44308-399">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="44308-400">O buffer que contém a carga JSON parcial deve ser pelo menos tão grande quanto o maior token JSON dentro dele, de modo que o leitor possa progredir em encaminhar.</span><span class="sxs-lookup"><span data-stu-id="44308-400">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="44308-401">O buffer deve ser pelo menos tão grande quanto a maior sequência de espaços em branco dentro do JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-401">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="44308-402">O leitor não mantém o controle dos dados lidos até que ele leia completamente o próximo <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> na carga JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-402">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="44308-403">Assim, quando houver bytes restantes no buffer, você precisa passá-los para o leitor novamente.</span><span class="sxs-lookup"><span data-stu-id="44308-403">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="44308-404">Você pode usar <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> para determinar quantos bytes serão deixados.</span><span class="sxs-lookup"><span data-stu-id="44308-404">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="44308-405">O código a seguir ilustra como ler de um fluxo.</span><span class="sxs-lookup"><span data-stu-id="44308-405">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="44308-406">O exemplo mostra um <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="44308-406">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="44308-407">O código semelhante funcionará com um <xref:System.IO.FileStream> , exceto quando o `FileStream` contiver uma bom UTF-8 no início.</span><span class="sxs-lookup"><span data-stu-id="44308-407">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="44308-408">Nesse caso, você precisa remover esses três bytes do buffer antes de passar os bytes restantes para o `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="44308-408">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="44308-409">Caso contrário, o leitor lançaria uma exceção, uma vez que a BOM não é considerada uma parte válida do JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-409">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="44308-410">O código de exemplo começa com um buffer de 4 KB e dobra o tamanho do buffer sempre que ele descobre que o tamanho não é grande o suficiente para se ajustar a um token JSON completo, que é necessário para que o leitor faça o progresso no conteúdo JSON.</span><span class="sxs-lookup"><span data-stu-id="44308-410">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="44308-411">O exemplo de JSON fornecido no trecho de código dispara um aumento de tamanho de buffer somente se você definir um tamanho de buffer inicial muito pequeno, por exemplo, 10 bytes.</span><span class="sxs-lookup"><span data-stu-id="44308-411">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="44308-412">Se você definir o tamanho do buffer inicial como 10, as `Console.WriteLine` instruções ilustrarão a causa e o efeito do tamanho do buffer aumentará.</span><span class="sxs-lookup"><span data-stu-id="44308-412">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="44308-413">No tamanho do buffer inicial de 4 KB, o JSON de exemplo inteiro é mostrado por cada um `Console.WriteLine` , e o tamanho do buffer nunca precisa ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="44308-413">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="44308-414">O exemplo anterior não define nenhum limite quanto ao tamanho do buffer pode crescer.</span><span class="sxs-lookup"><span data-stu-id="44308-414">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="44308-415">Se o tamanho do token for muito grande, o código poderá falhar com uma <xref:System.OutOfMemoryException> exceção.</span><span class="sxs-lookup"><span data-stu-id="44308-415">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="44308-416">Isso pode acontecer se o JSON contiver um token com cerca de 1 GB ou mais de tamanho, porque dobrar o tamanho de 1 GB resulta em um tamanho muito grande para caber em um `int32` buffer.</span><span class="sxs-lookup"><span data-stu-id="44308-416">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="44308-417">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="44308-417">Additional resources</span></span>

* <span data-ttu-id="44308-418">[System.Text.Jsonsobre](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="44308-418">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="44308-419">Como gravar conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="44308-419">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="44308-420">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="44308-420">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="44308-421">[Suporte a DateTime e DateTimeOffset emSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="44308-421">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="44308-422">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="44308-422">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
