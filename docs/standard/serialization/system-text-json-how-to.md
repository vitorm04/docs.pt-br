---
title: Como serializar e desserializar JSON usando C#-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6324fe28b23e4df74bcf3fd1dbb7e0c14d5e3d1b
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135796"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="79551-102">Como serializar e desserializar (empacotar e desempacotar) JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="79551-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="79551-103">Este artigo mostra como usar o <xref:System.Text.Json> namespace para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="79551-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="79551-104">Se você estiver portando um código existente `Newtonsoft.Json`do, consulte [como migrar `System.Text.Json`para o ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="79551-104">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="79551-105">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="79551-105">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="79551-106">A maior parte do código de exemplo <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> de `true` serialização define como "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana).</span><span class="sxs-lookup"><span data-stu-id="79551-106">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="79551-107">Para uso em produção, você normalmente aceitaria o valor padrão `false` de para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="79551-107">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="79551-108">Os exemplos de código referem-se à seguinte classe e variantes dela:</span><span class="sxs-lookup"><span data-stu-id="79551-108">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="79551-109">Namespaces</span><span class="sxs-lookup"><span data-stu-id="79551-109">Namespaces</span></span>

<span data-ttu-id="79551-110">O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="79551-110">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="79551-111">O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-111">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="79551-112">Os exemplos de código mostrados neste artigo `using` exigem diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="79551-112">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="79551-113">Atualmente, não <xref:System.Runtime.Serialization> há suporte para atributos do `System.Text.Json`namespace no.</span><span class="sxs-lookup"><span data-stu-id="79551-113">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="79551-114">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="79551-114">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="79551-115">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> chame o método.</span><span class="sxs-lookup"><span data-stu-id="79551-115">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="79551-116">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="79551-116">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-117">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-117">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-118">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-118">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-119">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="79551-119">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="79551-120">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="79551-120">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="79551-121">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="79551-121">Serialization example</span></span>

<span data-ttu-id="79551-122">Aqui está uma classe de exemplo que contém coleções e uma classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="79551-122">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="79551-123">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="79551-123">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="79551-124">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="79551-124">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="79551-125">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="79551-125">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="79551-126">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="79551-126">Serialize to UTF-8</span></span>

<span data-ttu-id="79551-127">Para serializar para UTF-8, chame <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> o método:</span><span class="sxs-lookup"><span data-stu-id="79551-127">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-128">Uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="79551-128">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="79551-129">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="79551-129">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="79551-130">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="79551-130">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="79551-131">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="79551-131">Serialization behavior</span></span>

* <span data-ttu-id="79551-132">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="79551-132">By default, all public properties are serialized.</span></span> <span data-ttu-id="79551-133">Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="79551-133">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="79551-134">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="79551-134">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="79551-135">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="79551-135">By default, JSON is minified.</span></span> <span data-ttu-id="79551-136">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="79551-136">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="79551-137">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="79551-137">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="79551-138">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="79551-138">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="79551-139">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="79551-139">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="79551-140">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="79551-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="79551-141">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="79551-141">Supported types include:</span></span>

* <span data-ttu-id="79551-142">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="79551-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="79551-143">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="79551-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="79551-144">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="79551-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="79551-145">`Dictionary<string,TValue>`onde `TValue` é `object`, `JsonElement`, ou um poco.</span><span class="sxs-lookup"><span data-stu-id="79551-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="79551-146">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="79551-146">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="79551-147">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="79551-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="79551-148">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="79551-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="79551-149">Para desserializar de uma cadeia de caracteres ou de um arquivo <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> , chame o método.</span><span class="sxs-lookup"><span data-stu-id="79551-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="79551-150">O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma `WeatherForecast` instância da classe mostrada anteriormente para o [exemplo de serialização](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="79551-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-151">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-152">Para desserializar de um arquivo usando código assíncrono, chame o <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> método:</span><span class="sxs-lookup"><span data-stu-id="79551-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="79551-153">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="79551-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="79551-154">Para desserializar do UTF-8, chame uma <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> sobrecarga que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="79551-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="79551-155">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="79551-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="79551-156">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="79551-156">Deserialization behavior</span></span>

* <span data-ttu-id="79551-157">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="79551-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="79551-158">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="79551-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="79551-159">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="79551-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="79551-160">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="79551-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="79551-161">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="79551-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="79551-162">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="79551-162">By default, enums are supported as numbers.</span></span> <span data-ttu-id="79551-163">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="79551-163">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="79551-164">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="79551-164">Fields aren't supported.</span></span>
* <span data-ttu-id="79551-165">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="79551-165">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="79551-166">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="79551-166">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="79551-167">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="79551-167">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="79551-168">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="79551-168">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="79551-169">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="79551-169">Serialize to formatted JSON</span></span>

<span data-ttu-id="79551-170">Para imprimir a saída JSON com muita impressão, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> defina `true`como:</span><span class="sxs-lookup"><span data-stu-id="79551-170">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="79551-171">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="79551-171">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="79551-172">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="79551-172">Customize JSON names and values</span></span>

<span data-ttu-id="79551-173">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="79551-173">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="79551-174">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="79551-174">Enum values are represented as numbers.</span></span> <span data-ttu-id="79551-175">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="79551-175">This section explains how to:</span></span>

* [<span data-ttu-id="79551-176">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="79551-176">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="79551-177">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="79551-177">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="79551-178">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="79551-178">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="79551-179">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="79551-179">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="79551-180">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="79551-180">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="79551-181">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="79551-181">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="79551-182">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="79551-182">Customize individual property names</span></span>

<span data-ttu-id="79551-183">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="79551-183">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="79551-184">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="79551-184">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="79551-185">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="79551-185">The property name set by this attribute:</span></span>

* <span data-ttu-id="79551-186">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-186">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="79551-187">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="79551-187">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="79551-188">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="79551-188">Use camel case for all JSON property names</span></span>

<span data-ttu-id="79551-189">Para usar o camel case para todos os nomes de propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> JSON `JsonNamingPolicy.CamelCase`, defina como, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-189">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="79551-190">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-190">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="79551-191">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="79551-191">The camel case property naming policy:</span></span>

* <span data-ttu-id="79551-192">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-192">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="79551-193">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="79551-193">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="79551-194">É por isso que o nome `Wind` da propriedade JSON no exemplo não é camel case.</span><span class="sxs-lookup"><span data-stu-id="79551-194">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="79551-195">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="79551-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="79551-196">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> método, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="79551-197">Em seguida, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> defina a propriedade como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="79551-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-198">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-198">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="79551-199">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="79551-200">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="79551-201">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="79551-201">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="79551-202">É por isso que o nome `Wind` da propriedade JSON no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="79551-202">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="79551-203">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="79551-203">Camel case dictionary keys</span></span>

<span data-ttu-id="79551-204">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as `string` chaves poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="79551-204">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="79551-205">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-205">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-206">Serializar um objeto com um dicionário `TemperatureRanges` chamado que tem pares `"ColdMinTemp", 20` chave-valor `"HotMinTemp", 40` e resultaria em uma saída JSON como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-206">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="79551-207">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="79551-207">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="79551-208">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo que você `JsonNamingPolicy.CamelCase` especifique para `DictionaryKeyPolicy`o.</span><span class="sxs-lookup"><span data-stu-id="79551-208">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="79551-209">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="79551-209">Enums as strings</span></span>

<span data-ttu-id="79551-210">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="79551-210">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="79551-211">Para serializar nomes de enumeração como cadeias <xref:System.Text.Json.Serialization.JsonStringEnumConverter>de caracteres, use o.</span><span class="sxs-lookup"><span data-stu-id="79551-211">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="79551-212">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="79551-212">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="79551-213">Se o resumo for `Hot`, por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="79551-213">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="79551-214">O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:</span><span class="sxs-lookup"><span data-stu-id="79551-214">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-215">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-215">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="79551-216">Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-216">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="79551-217">Excluir propriedades da serialização</span><span class="sxs-lookup"><span data-stu-id="79551-217">Exclude properties from serialization</span></span>

<span data-ttu-id="79551-218">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="79551-218">By default, all public properties are serialized.</span></span> <span data-ttu-id="79551-219">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="79551-219">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="79551-220">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="79551-220">This section explains how to exclude:</span></span>

* [<span data-ttu-id="79551-221">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="79551-221">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="79551-222">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="79551-222">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="79551-223">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="79551-223">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="79551-224">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="79551-224">Exclude individual properties</span></span>

<span data-ttu-id="79551-225">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="79551-225">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="79551-226">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-226">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="79551-227">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="79551-227">Exclude all read-only properties</span></span>

<span data-ttu-id="79551-228">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="79551-228">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="79551-229">Para excluir todas as propriedades somente leitura, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-230">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-230">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="79551-231">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="79551-231">This option applies only to serialization.</span></span> <span data-ttu-id="79551-232">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="79551-232">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="79551-233">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="79551-233">Exclude all null value properties</span></span>

<span data-ttu-id="79551-234">Para excluir todas as propriedades de valor nulo, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> defina a `true`Propriedade como, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-234">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-235">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-235">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="79551-236">Propriedade</span><span class="sxs-lookup"><span data-stu-id="79551-236">Property</span></span> |<span data-ttu-id="79551-237">Valor</span><span class="sxs-lookup"><span data-stu-id="79551-237">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="79551-238">Data</span><span class="sxs-lookup"><span data-stu-id="79551-238">Date</span></span>    | <span data-ttu-id="79551-239">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="79551-239">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="79551-240">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="79551-240">TemperatureCelsius</span></span>| <span data-ttu-id="79551-241">25</span><span class="sxs-lookup"><span data-stu-id="79551-241">25</span></span> |
| <span data-ttu-id="79551-242">Resumo</span><span class="sxs-lookup"><span data-stu-id="79551-242">Summary</span></span>| <span data-ttu-id="79551-243">nulo</span><span class="sxs-lookup"><span data-stu-id="79551-243">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="79551-244">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-244">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="79551-245">Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="79551-245">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="79551-246">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="79551-246">Customize character encoding</span></span>

<span data-ttu-id="79551-247">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="79551-247">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="79551-248">Ou seja, ele substitui por `\uxxxx` onde `xxxx` está o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="79551-248">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="79551-249">Por exemplo, se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="79551-249">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="79551-250">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="79551-250">Serialize language character sets</span></span>

<span data-ttu-id="79551-251">Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique os [intervalos Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância do <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-251">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="79551-252">Este código não sai de escape de caracteres cirílico ou grego.</span><span class="sxs-lookup"><span data-stu-id="79551-252">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="79551-253">Se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="79551-253">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="79551-254">Para serializar todos os conjuntos de idiomas sem saída <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>, use.</span><span class="sxs-lookup"><span data-stu-id="79551-254">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="79551-255">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="79551-255">Serialize specific characters</span></span>

<span data-ttu-id="79551-256">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="79551-256">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="79551-257">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="79551-257">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="79551-258">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="79551-258">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="79551-259">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="79551-259">Serialize all characters</span></span>

<span data-ttu-id="79551-260">Para minimizar a saída, você pode <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>usar, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-260">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="79551-261">Em comparação com o codificador padrão `UnsafeRelaxedJsonEscaping` , o codificador é mais permissivo de permitir que os caracteres passem sem escape:</span><span class="sxs-lookup"><span data-stu-id="79551-261">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="79551-262">Ele não sai de caracteres sensíveis a HTML, `<`como `>`, `&`, e `'`.</span><span class="sxs-lookup"><span data-stu-id="79551-262">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="79551-263">Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="79551-263">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="79551-264">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="79551-264">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="79551-265">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho `Content-Type: application/json; charset=utf-8`de resposta.</span><span class="sxs-lookup"><span data-stu-id="79551-265">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="79551-266">Nunca permita que a `UnsafeRelaxedJsonEscaping` saída bruta seja emitida em uma página HTML ou em `<script>` um elemento.</span><span class="sxs-lookup"><span data-stu-id="79551-266">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="79551-267">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="79551-267">Serialize properties of derived classes</span></span>

<span data-ttu-id="79551-268">Não há suporte para a serialização de uma hierarquia de tipo polimórfico.</span><span class="sxs-lookup"><span data-stu-id="79551-268">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="79551-269">Por exemplo, se uma propriedade for definida como uma interface ou uma classe abstrata, somente as propriedades definidas na interface ou na classe abstrata serão serializadas, mesmo que o tipo de tempo de execução tenha propriedades adicionais.</span><span class="sxs-lookup"><span data-stu-id="79551-269">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="79551-270">As exceções a esse comportamento são explicadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="79551-270">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="79551-271">Por exemplo, suponha que você tenha `WeatherForecast` uma classe e uma classe `WeatherForecastDerived`derivada:</span><span class="sxs-lookup"><span data-stu-id="79551-271">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="79551-272">E suponha que o argumento de tipo `Serialize` do método em tempo de `WeatherForecast`compilação seja:</span><span class="sxs-lookup"><span data-stu-id="79551-272">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="79551-273">Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que `weatherForecast` o objeto seja, `WeatherForecastDerived` na verdade, um objeto.</span><span class="sxs-lookup"><span data-stu-id="79551-273">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="79551-274">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="79551-274">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="79551-275">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="79551-275">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="79551-276">Para serializar as propriedades do tipo derivado no exemplo anterior, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="79551-276">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="79551-277">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="79551-277">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="79551-278">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="79551-278">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="79551-279">No cenário de exemplo anterior, ambas as abordagens fazem `WindSpeed` com que a propriedade seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-279">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="79551-280">Essas abordagens fornecem serialização polimórfica somente para o objeto raiz a ser serializado, não para propriedades desse objeto raiz.</span><span class="sxs-lookup"><span data-stu-id="79551-280">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="79551-281">Você pode obter a serialização polimórfica para objetos de nível inferior se defini-los como tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="79551-281">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="79551-282">Por exemplo, suponha que `WeatherForecast` sua classe tenha uma propriedade `PreviousForecast` chamada que possa ser definida como `WeatherForecast` tipo `object`ou:</span><span class="sxs-lookup"><span data-stu-id="79551-282">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="79551-283">Se a `PreviousForecast` Propriedade contiver uma instância `WeatherForecastDerived`de:</span><span class="sxs-lookup"><span data-stu-id="79551-283">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="79551-284">A saída JSON da serialização `WeatherForecastWithPrevious` **não inclui** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="79551-284">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="79551-285">A saída JSON da serialização `WeatherForecastWithPreviousAsObject` **inclui** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="79551-285">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="79551-286">Para serializar `WeatherForecastWithPreviousAsObject`, não é necessário chamar `Serialize<object>` ou `GetType` porque o objeto raiz não é aquele que pode ser de um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="79551-286">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="79551-287">O exemplo de código a seguir `Serialize<object>` não `GetType`chama ou:</span><span class="sxs-lookup"><span data-stu-id="79551-287">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="79551-288">O código anterior serializa corretamente `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="79551-288">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="79551-289">A mesma abordagem de definir propriedades como `object` funciona com interfaces.</span><span class="sxs-lookup"><span data-stu-id="79551-289">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="79551-290">Suponha que você tenha a seguinte interface e implementação e queira serializar uma classe com propriedades que contêm instâncias de implementação:</span><span class="sxs-lookup"><span data-stu-id="79551-290">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="79551-291">Quando você serializa uma instância do `Forecasts`, o `Tuesday` mostra apenas `WindSpeed` a propriedade, `Tuesday` porque é definido `object`como:</span><span class="sxs-lookup"><span data-stu-id="79551-291">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="79551-292">O exemplo a seguir mostra o JSON que resulta do código anterior:</span><span class="sxs-lookup"><span data-stu-id="79551-292">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="79551-293">Para obter mais informações sobre **serialização**polimórfica e informações sobre **desserialização**, consulte [como migrar de Newtonsoft. JSON para System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="79551-293">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="79551-294">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="79551-294">Allow comments and trailing commas</span></span>

<span data-ttu-id="79551-295">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="79551-295">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="79551-296">Para permitir comentários no JSON, defina a <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> Propriedade como. `JsonCommentHandling.Skip`</span><span class="sxs-lookup"><span data-stu-id="79551-296">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="79551-297">E para permitir vírgulas à direita, defina a <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> Propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="79551-297">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="79551-298">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="79551-298">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-299">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="79551-299">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="79551-300">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="79551-300">Case-insensitive property matching</span></span>

<span data-ttu-id="79551-301">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="79551-301">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="79551-302">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="79551-302">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-303">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="79551-303">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="79551-304">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="79551-304">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="79551-305">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="79551-305">Handle overflow JSON</span></span>

<span data-ttu-id="79551-306">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="79551-306">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="79551-307">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79551-307">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="79551-308">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79551-308">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="79551-309">Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="79551-309">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="79551-310">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="79551-310">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="79551-311">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave- `ExtensionData` valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="79551-311">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="79551-312">Propriedade</span><span class="sxs-lookup"><span data-stu-id="79551-312">Property</span></span> |<span data-ttu-id="79551-313">Valor</span><span class="sxs-lookup"><span data-stu-id="79551-313">Value</span></span>  |<span data-ttu-id="79551-314">Observações</span><span class="sxs-lookup"><span data-stu-id="79551-314">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="79551-315">Data</span><span class="sxs-lookup"><span data-stu-id="79551-315">Date</span></span>    | <span data-ttu-id="79551-316">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="79551-316">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="79551-317">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="79551-317">TemperatureCelsius</span></span>| <span data-ttu-id="79551-318">0</span><span class="sxs-lookup"><span data-stu-id="79551-318">0</span></span> | <span data-ttu-id="79551-319">Incompatibilidade de maiúsculas`temperatureCelsius` e minúsculas (no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="79551-319">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="79551-320">Resumo</span><span class="sxs-lookup"><span data-stu-id="79551-320">Summary</span></span> | <span data-ttu-id="79551-321">Dinâmica</span><span class="sxs-lookup"><span data-stu-id="79551-321">Hot</span></span> ||
| <span data-ttu-id="79551-322">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="79551-322">ExtensionData</span></span> | <span data-ttu-id="79551-323">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="79551-323">temperatureCelsius: 25</span></span> |<span data-ttu-id="79551-324">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="79551-324">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="79551-325">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="79551-325">DatesAvailable:</span></span><br>  <span data-ttu-id="79551-326">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="79551-326">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="79551-327">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="79551-327">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="79551-328">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="79551-328">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="79551-329">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="79551-329">SummaryWords:</span></span><br><span data-ttu-id="79551-330">Estática</span><span class="sxs-lookup"><span data-stu-id="79551-330">Cool</span></span><br><span data-ttu-id="79551-331">Vento</span><span class="sxs-lookup"><span data-stu-id="79551-331">Windy</span></span><br><span data-ttu-id="79551-332">Humid</span><span class="sxs-lookup"><span data-stu-id="79551-332">Humid</span></span> |<span data-ttu-id="79551-333">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="79551-333">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="79551-334">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="79551-334">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="79551-335">Observe que o `ExtensionData` nome da propriedade não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="79551-335">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="79551-336">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="79551-336">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="79551-337">Ignorar nulo ao desserializar</span><span class="sxs-lookup"><span data-stu-id="79551-337">Ignore null when deserializing</span></span>

<span data-ttu-id="79551-338">Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL.</span><span class="sxs-lookup"><span data-stu-id="79551-338">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="79551-339">Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.</span><span class="sxs-lookup"><span data-stu-id="79551-339">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="79551-340">Por exemplo, suponha que o código a seguir represente o objeto de destino:</span><span class="sxs-lookup"><span data-stu-id="79551-340">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="79551-341">E suponha que o JSON a seguir seja desserializado:</span><span class="sxs-lookup"><span data-stu-id="79551-341">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="79551-342">Após a desserialização, `Summary` a propriedade do `WeatherForecastWithDefault` objeto é nula.</span><span class="sxs-lookup"><span data-stu-id="79551-342">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="79551-343">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-343">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-344">Com essa opção, a `Summary` Propriedade do `WeatherForecastWithDefault` objeto é o valor padrão "sem Resumo" após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="79551-344">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="79551-345">Os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="79551-345">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="79551-346">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="79551-346">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="79551-347">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="79551-347">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="79551-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>é um leitor de alto desempenho, de baixa alocação e somente de encaminhamento para texto JSON codificado em UTF-8, `ReadOnlySpan<byte>` lido `ReadOnlySequence<byte>`de um ou.</span><span class="sxs-lookup"><span data-stu-id="79551-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="79551-349">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="79551-349">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="79551-350">O <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="79551-350">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="79551-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do `String`.NET `Int32`como, `DateTime`e.</span><span class="sxs-lookup"><span data-stu-id="79551-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="79551-352">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="79551-352">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="79551-353">O <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="79551-353">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="79551-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>fornece a capacidade de criar um Modelo de Objeto do Documento somente leitura (DOM) usando `Utf8JsonReader`o.</span><span class="sxs-lookup"><span data-stu-id="79551-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="79551-355">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="79551-355">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="79551-356">Os elementos JSON que compõem a carga podem ser acessados <xref:System.Text.Json.JsonElement> por meio do tipo.</span><span class="sxs-lookup"><span data-stu-id="79551-356">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="79551-357">O `JsonElement` tipo fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .net comuns.</span><span class="sxs-lookup"><span data-stu-id="79551-357">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="79551-358">`JsonDocument`expõe uma <xref:System.Text.Json.JsonDocument.RootElement> propriedade.</span><span class="sxs-lookup"><span data-stu-id="79551-358">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="79551-359">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="79551-359">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="79551-360">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="79551-360">Use JsonDocument for access to data</span></span>

<span data-ttu-id="79551-361">O exemplo a seguir mostra como usar a <xref:System.Text.Json.JsonDocument> classe para acesso aleatório a dados em uma cadeia de caracteres JSON:</span><span class="sxs-lookup"><span data-stu-id="79551-361">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="79551-362">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="79551-362">The preceding code:</span></span>

* <span data-ttu-id="79551-363">Assume que o JSON a ser analisado está em `jsonString`uma cadeia de caracteres chamada.</span><span class="sxs-lookup"><span data-stu-id="79551-363">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="79551-364">Calcula uma classificação média para objetos em uma `Students` matriz que tem uma `Grade` propriedade.</span><span class="sxs-lookup"><span data-stu-id="79551-364">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="79551-365">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="79551-365">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="79551-366">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="79551-366">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="79551-367">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="79551-367">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="79551-368">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="79551-368">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="79551-369">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="79551-369">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="79551-370">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="79551-370">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="79551-371">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="79551-371">The preceding code:</span></span>

* <span data-ttu-id="79551-372">Lê um arquivo JSON, carrega os dados em um `JsonDocument`e grava JSON formatado (bem-impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="79551-372">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="79551-373">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="79551-373">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="79551-374">Quando terminar, chama <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> o gravador.</span><span class="sxs-lookup"><span data-stu-id="79551-374">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="79551-375">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="79551-375">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="79551-376">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="79551-376">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="79551-377">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="79551-377">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="79551-378">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="79551-378">Use Utf8JsonWriter</span></span>

<span data-ttu-id="79551-379">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe:</span><span class="sxs-lookup"><span data-stu-id="79551-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="79551-380">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="79551-380">Use Utf8JsonReader</span></span>

<span data-ttu-id="79551-381">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe:</span><span class="sxs-lookup"><span data-stu-id="79551-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="79551-382">O código anterior pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="79551-382">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="79551-383">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="79551-383">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="79551-384">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="79551-384">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="79551-385">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="79551-385">The preceding code:</span></span>

* <span data-ttu-id="79551-386">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="79551-386">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="79551-387">Conta objetos e valores de propriedade "Name" que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="79551-387">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="79551-388">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="79551-388">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="79551-389">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="79551-389">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="79551-390">Se o arquivo contiver uma marca de ordem de byte (BOM) UTF-8, remova-a antes de `Utf8JsonReader`passar os bytes para o, uma vez que o leitor espera o texto.</span><span class="sxs-lookup"><span data-stu-id="79551-390">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="79551-391">Caso contrário, a BOM será considerada JSON inválido e o leitor lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="79551-391">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="79551-392">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="79551-392">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="79551-393">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="79551-393">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="79551-394">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="79551-394">Additional resources</span></span>

* <span data-ttu-id="79551-395">[System.Text.Jsonsobre](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="79551-395">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="79551-396">Como gravar conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="79551-396">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="79551-397">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="79551-397">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="79551-398">[Suporte a DateTime e DateTimeOffset emSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="79551-398">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="79551-399">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="79551-399">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
