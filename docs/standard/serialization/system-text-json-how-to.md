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
ms.openlocfilehash: 3d3dc0011562e25854938aff857f2832a5978b49
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283329"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="f915b-102">Como serializar e desserializar JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="f915b-102">How to serialize and deserialize JSON in .NET</span></span>

<span data-ttu-id="f915b-103">Este artigo mostra como usar o namespace <xref:System.Text.Json> para serializar e desserializar de e para o JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="f915b-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="f915b-104">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="f915b-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="f915b-105">A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> a `true` como "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana).</span><span class="sxs-lookup"><span data-stu-id="f915b-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="f915b-106">Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="f915b-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="f915b-107">Namespaces</span><span class="sxs-lookup"><span data-stu-id="f915b-107">Namespaces</span></span>

<span data-ttu-id="f915b-108">O namespace <xref:System.Text.Json> contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="f915b-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="f915b-109">O namespace <xref:System.Text.Json.Serialization> contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="f915b-110">Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="f915b-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="f915b-111">Atualmente, não há suporte para atributos do namespace <xref:System.Runtime.Serialization> no `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="f915b-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="f915b-112">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="f915b-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="f915b-113">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f915b-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f915b-114">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="f915b-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-115">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-116">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-117">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="f915b-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="f915b-118">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="f915b-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="f915b-119">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="f915b-119">Serialization example</span></span>

<span data-ttu-id="f915b-120">Aqui está uma classe de exemplo que contém coleções e uma classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="f915b-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="f915b-121">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f915b-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="f915b-122">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="f915b-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="f915b-123">O exemplo a seguir mostra o mesmo JSON, formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="f915b-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="f915b-124">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="f915b-124">Serialize to UTF-8</span></span>

<span data-ttu-id="f915b-125">Para serializar para UTF-8, chame o método <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="f915b-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-126">Uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que usa uma <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="f915b-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="f915b-127">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f915b-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="f915b-128">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="f915b-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="f915b-129">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="f915b-129">Serialization behavior</span></span>

* <span data-ttu-id="f915b-130">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="f915b-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="f915b-131">Você pode [especificar propriedades a serem excluídas](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="f915b-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="f915b-132">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="f915b-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="f915b-133">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="f915b-133">By default, JSON is minified.</span></span> <span data-ttu-id="f915b-134">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="f915b-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="f915b-135">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="f915b-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="f915b-136">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="f915b-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="f915b-137">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="f915b-137">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="f915b-138">Para obter mais informações, consulte [emitir 38579 em referências circulares](https://github.com/dotnet/corefx/issues/38579) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="f915b-138">For more information, see [issue 38579 on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="f915b-139">No momento, os campos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="f915b-139">Currently, fields are excluded.</span></span>

<span data-ttu-id="f915b-140">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="f915b-140">Supported types include:</span></span>

* <span data-ttu-id="f915b-141">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="f915b-141">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="f915b-142">[Pocos (objetos CLR antigos)](https://stackoverflow.com/questions/250001/poco-definition)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f915b-142">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="f915b-143">Matrizes unidimensionais e denteadas (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="f915b-143">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="f915b-144">`Dictionary<string,TValue>` em que `TValue` é `object`, `JsonElement`ou um POCO.</span><span class="sxs-lookup"><span data-stu-id="f915b-144">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="f915b-145">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="f915b-145">Collections from the following namespaces.</span></span> <span data-ttu-id="f915b-146">Para obter mais informações, consulte o [problema no suporte de coleção](https://github.com/dotnet/corefx/issues/36643) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="f915b-146">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="f915b-147">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="f915b-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="f915b-148">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="f915b-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="f915b-149">Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f915b-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f915b-150">O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da classe `WeatherForecast` mostrada anteriormente para o [exemplo de serialização](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="f915b-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-151">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-152">Para desserializar de um arquivo usando código assíncrono, chame o método <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="f915b-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="f915b-153">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="f915b-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="f915b-154">Para desserializar do UTF-8, chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> que usa uma `Utf8JsonReader` ou uma `ReadOnlySpan<byte>`, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="f915b-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="f915b-155">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="f915b-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="f915b-156">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="f915b-156">Deserialization behavior</span></span>

* <span data-ttu-id="f915b-157">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f915b-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="f915b-158">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="f915b-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="f915b-159">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="f915b-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="f915b-160">Não há suporte para desserialização para tipos de referência sem um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f915b-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="f915b-161">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="f915b-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="f915b-162">Para obter mais informações, consulte o [problema do GitHub 38569 no suporte a objetos imutáveis](https://github.com/dotnet/corefx/issues/38569) e o [problema 38163 em suporte à propriedade somente leitura](https://github.com/dotnet/corefx/issues/38163) no repositório dotnet/corefx no github.</span><span class="sxs-lookup"><span data-stu-id="f915b-162">For more information, see GitHub [issue 38569 on immutable object support](https://github.com/dotnet/corefx/issues/38569) and [issue 38163 on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="f915b-163">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="f915b-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="f915b-164">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="f915b-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="f915b-165">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="f915b-165">Fields aren't supported.</span></span>
* <span data-ttu-id="f915b-166">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="f915b-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="f915b-167">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="f915b-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="f915b-168">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="f915b-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="f915b-169">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="f915b-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="f915b-170">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="f915b-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="f915b-171">Para imprimir a saída JSON, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="f915b-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="f915b-172">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="f915b-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="f915b-173">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-173">Customize JSON names and values</span></span>

<span data-ttu-id="f915b-174">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f915b-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="f915b-175">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="f915b-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="f915b-176">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="f915b-176">This section explains how to:</span></span>

* [<span data-ttu-id="f915b-177">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="f915b-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="f915b-178">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="f915b-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="f915b-179">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="f915b-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="f915b-180">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="f915b-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="f915b-181">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="f915b-181">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="f915b-182">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="f915b-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="f915b-183">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="f915b-183">Customize individual property names</span></span>

<span data-ttu-id="f915b-184">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f915b-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="f915b-185">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="f915b-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f915b-186">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="f915b-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="f915b-187">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="f915b-188">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f915b-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="f915b-189">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="f915b-190">Para usar o camel case para todos os nomes de propriedade JSON, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="f915b-191">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f915b-192">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="f915b-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="f915b-193">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="f915b-194">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="f915b-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="f915b-195">É por isso que o nome da propriedade JSON `Wind` no exemplo não é o camel case.</span><span class="sxs-lookup"><span data-stu-id="f915b-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="f915b-196">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="f915b-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="f915b-197">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o método <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="f915b-198">Em seguida, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="f915b-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-199">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f915b-200">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="f915b-201">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="f915b-202">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="f915b-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="f915b-203">É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="f915b-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="f915b-204">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="f915b-204">Camel case dictionary keys</span></span>

<span data-ttu-id="f915b-205">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>`, as chaves de `string` poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="f915b-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="f915b-206">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-207">A serialização de um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria na saída JSON, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="f915b-208">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="f915b-209">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo se você especificar `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="f915b-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="f915b-210">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="f915b-210">Enums as strings</span></span>

<span data-ttu-id="f915b-211">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="f915b-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="f915b-212">Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="f915b-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="f915b-213">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="f915b-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="f915b-214">Se o resumo for `Hot`, por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="f915b-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="f915b-215">O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:</span><span class="sxs-lookup"><span data-stu-id="f915b-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-216">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="f915b-217">Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="f915b-218">Excluir propriedades da serialização</span><span class="sxs-lookup"><span data-stu-id="f915b-218">Exclude properties from serialization</span></span>

<span data-ttu-id="f915b-219">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="f915b-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="f915b-220">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="f915b-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="f915b-221">Esta seção explica como excluir:</span><span class="sxs-lookup"><span data-stu-id="f915b-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="f915b-222">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="f915b-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="f915b-223">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="f915b-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="f915b-224">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="f915b-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="f915b-225">Excluir propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="f915b-225">Exclude individual properties</span></span>

<span data-ttu-id="f915b-226">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f915b-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="f915b-227">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="f915b-228">Excluir todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="f915b-228">Exclude all read-only properties</span></span>

<span data-ttu-id="f915b-229">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="f915b-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="f915b-230">Para excluir todas as propriedades somente leitura, defina o <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-231">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="f915b-232">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-232">This option applies only to serialization.</span></span> <span data-ttu-id="f915b-233">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="f915b-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="f915b-234">Excluir todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="f915b-234">Exclude all null value properties</span></span>

<span data-ttu-id="f915b-235">Para excluir todas as propriedades de valor nulo, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-236">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="f915b-237">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f915b-237">Property</span></span> |<span data-ttu-id="f915b-238">Valor</span><span class="sxs-lookup"><span data-stu-id="f915b-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="f915b-239">Date</span><span class="sxs-lookup"><span data-stu-id="f915b-239">Date</span></span>    | <span data-ttu-id="f915b-240">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="f915b-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="f915b-241">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="f915b-241">TemperatureCelsius</span></span>| <span data-ttu-id="f915b-242">25</span><span class="sxs-lookup"><span data-stu-id="f915b-242">25</span></span> |
| <span data-ttu-id="f915b-243">Resumo</span><span class="sxs-lookup"><span data-stu-id="f915b-243">Summary</span></span>| <span data-ttu-id="f915b-244">nulo</span><span class="sxs-lookup"><span data-stu-id="f915b-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="f915b-245">Essa configuração se aplica à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="f915b-246">Para obter informações sobre o efeito na desserialização, consulte [ignorar nulo ao desserializar](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="f915b-246">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="f915b-247">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="f915b-247">Customize character encoding</span></span>

<span data-ttu-id="f915b-248">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="f915b-248">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="f915b-249">Ou seja, ele os substitui por `\uxxxx` em que `xxxx` é o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="f915b-249">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="f915b-250">Por exemplo, se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="f915b-250">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="f915b-251">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="f915b-251">Serialize language character sets</span></span>

<span data-ttu-id="f915b-252">Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique [intervalo (s) Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância de <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-252">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="f915b-253">Este código não sai de escape de caracteres cirílico ou grego.</span><span class="sxs-lookup"><span data-stu-id="f915b-253">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="f915b-254">Se a propriedade `Summary` for definida como cirílico жарко, o objeto `WeatherForecast` será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="f915b-254">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="f915b-255">Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f915b-255">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="f915b-256">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="f915b-256">Serialize specific characters</span></span>

<span data-ttu-id="f915b-257">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="f915b-257">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="f915b-258">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="f915b-258">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="f915b-259">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="f915b-259">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="f915b-260">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="f915b-260">Serialize all characters</span></span>

<span data-ttu-id="f915b-261">Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-261">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="f915b-262">Em comparação com o codificador padrão, o codificador de `UnsafeRelaxedJsonEscaping` é mais permissivo de permitir que os caracteres passem sem escape:</span><span class="sxs-lookup"><span data-stu-id="f915b-262">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="f915b-263">Ele não sai de caracteres sensíveis a HTML, como `<`, `>`, `&`e `'`.</span><span class="sxs-lookup"><span data-stu-id="f915b-263">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="f915b-264">Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="f915b-264">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="f915b-265">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f915b-265">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="f915b-266">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="f915b-266">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="f915b-267">Nunca permita que a saída de `UnsafeRelaxedJsonEscaping` bruta seja emitida em uma página HTML ou em um elemento `<script>`.</span><span class="sxs-lookup"><span data-stu-id="f915b-267">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="f915b-268">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="f915b-268">Serialize properties of derived classes</span></span>

<span data-ttu-id="f915b-269">Não há suporte para a serialização polimórfica quando você especifica no momento da compilação o tipo a ser serializado.</span><span class="sxs-lookup"><span data-stu-id="f915b-269">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="f915b-270">Por exemplo, suponha que você tenha uma classe `WeatherForecast` e uma classe derivada `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="f915b-270">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="f915b-271">E suponha que o argumento de tipo do método de `Serialize` em tempo de compilação seja `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="f915b-271">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="f915b-272">Nesse cenário, a propriedade `WindSpeed` não é serializada, mesmo que o objeto `weatherForecast` seja, na verdade, um objeto `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="f915b-272">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="f915b-273">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="f915b-273">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="f915b-274">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="f915b-274">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="f915b-275">Para serializar as propriedades do tipo derivado, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="f915b-275">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="f915b-276">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="f915b-276">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="f915b-277">Declare o objeto a ser serializado como `object`.</span><span class="sxs-lookup"><span data-stu-id="f915b-277">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="f915b-278">No cenário de exemplo anterior, ambas as abordagens fazem com que a propriedade `WindSpeed` seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-278">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="f915b-279">Para obter informações sobre desserialização polimórfica, consulte [dar suporte à desserialização polimórfica](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="f915b-279">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="f915b-280">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="f915b-280">Allow comments and trailing commas</span></span>

<span data-ttu-id="f915b-281">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="f915b-281">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="f915b-282">Para permitir comentários no JSON, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> como `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="f915b-282">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="f915b-283">E para permitir vírgulas à direita, defina a propriedade <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="f915b-283">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f915b-284">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="f915b-284">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-285">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="f915b-285">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="f915b-286">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="f915b-286">Case-insensitive property matching</span></span>

<span data-ttu-id="f915b-287">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="f915b-287">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="f915b-288">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true`:</span><span class="sxs-lookup"><span data-stu-id="f915b-288">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-289">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="f915b-289">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="f915b-290">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="f915b-290">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="f915b-291">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="f915b-291">Handle overflow JSON</span></span>

<span data-ttu-id="f915b-292">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="f915b-292">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="f915b-293">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f915b-293">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="f915b-294">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f915b-294">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="f915b-295">Se você desserializar o JSON mostrado no tipo mostrado, as propriedades `DatesAvailable` e `SummaryWords` ficarão em qualquer lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="f915b-295">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="f915b-296">Para capturar dados adicionais, como essas propriedades, aplique o atributo [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="f915b-296">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="f915b-297">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares chave-valor da propriedade `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="f915b-297">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="f915b-298">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f915b-298">Property</span></span> |<span data-ttu-id="f915b-299">Valor</span><span class="sxs-lookup"><span data-stu-id="f915b-299">Value</span></span>  |<span data-ttu-id="f915b-300">Observações</span><span class="sxs-lookup"><span data-stu-id="f915b-300">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="f915b-301">Date</span><span class="sxs-lookup"><span data-stu-id="f915b-301">Date</span></span>    | <span data-ttu-id="f915b-302">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="f915b-302">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="f915b-303">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="f915b-303">TemperatureCelsius</span></span>| <span data-ttu-id="f915b-304">0</span><span class="sxs-lookup"><span data-stu-id="f915b-304">0</span></span> | <span data-ttu-id="f915b-305">Incompatibilidade de maiúsculas e minúsculas (`temperatureCelsius` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="f915b-305">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="f915b-306">Resumo</span><span class="sxs-lookup"><span data-stu-id="f915b-306">Summary</span></span> | <span data-ttu-id="f915b-307">Pontos</span><span class="sxs-lookup"><span data-stu-id="f915b-307">Hot</span></span> ||
| <span data-ttu-id="f915b-308">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="f915b-308">ExtensionData</span></span> | <span data-ttu-id="f915b-309">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="f915b-309">temperatureCelsius: 25</span></span> |<span data-ttu-id="f915b-310">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="f915b-310">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="f915b-311">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="f915b-311">DatesAvailable:</span></span><br>  <span data-ttu-id="f915b-312">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="f915b-312">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="f915b-313">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="f915b-313">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="f915b-314">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="f915b-314">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="f915b-315">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="f915b-315">SummaryWords:</span></span><br><span data-ttu-id="f915b-316">Legais</span><span class="sxs-lookup"><span data-stu-id="f915b-316">Cool</span></span><br><span data-ttu-id="f915b-317">Vento</span><span class="sxs-lookup"><span data-stu-id="f915b-317">Windy</span></span><br><span data-ttu-id="f915b-318">Humid</span><span class="sxs-lookup"><span data-stu-id="f915b-318">Humid</span></span> |<span data-ttu-id="f915b-319">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="f915b-319">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="f915b-320">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="f915b-320">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="f915b-321">Observe que o nome da propriedade `ExtensionData` não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="f915b-321">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="f915b-322">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="f915b-322">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="f915b-323">Ignorar nulo ao desserializar</span><span class="sxs-lookup"><span data-stu-id="f915b-323">Ignore null when deserializing</span></span>

<span data-ttu-id="f915b-324">Por padrão, se uma propriedade em JSON for nula, a propriedade correspondente no objeto de destino será definida como NULL.</span><span class="sxs-lookup"><span data-stu-id="f915b-324">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="f915b-325">Em alguns cenários, a propriedade de destino pode ter um valor padrão e você não quer um valor nulo para substituir o padrão.</span><span class="sxs-lookup"><span data-stu-id="f915b-325">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="f915b-326">Por exemplo, suponha que o código a seguir represente o objeto de destino:</span><span class="sxs-lookup"><span data-stu-id="f915b-326">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="f915b-327">E suponha que o JSON a seguir seja desserializado:</span><span class="sxs-lookup"><span data-stu-id="f915b-327">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="f915b-328">Após a desserialização, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é nula.</span><span class="sxs-lookup"><span data-stu-id="f915b-328">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="f915b-329">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> como `true`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-329">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-330">Com essa opção, a propriedade `Summary` do objeto `WeatherForecastWithDefault` é o valor padrão "sem Resumo" após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="f915b-330">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="f915b-331">Os valores nulos no JSON serão ignorados somente se forem válidos.</span><span class="sxs-lookup"><span data-stu-id="f915b-331">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="f915b-332">Valores nulos para tipos de valores não anuláveis causam exceções.</span><span class="sxs-lookup"><span data-stu-id="f915b-332">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="f915b-333">Para obter mais informações, consulte [emitir 40922 em tipos de valores não anuláveis](https://github.com/dotnet/corefx/issues/40922) no repositório dotnet/Corefx no github.</span><span class="sxs-lookup"><span data-stu-id="f915b-333">For more information, see [issue 40922 on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="f915b-334">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="f915b-334">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="f915b-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="f915b-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="f915b-336">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="f915b-336">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="f915b-337">O método <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="f915b-337">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="f915b-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET, como `String`, `Int32`e `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="f915b-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="f915b-339">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="f915b-339">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="f915b-340">O método <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="f915b-340">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="f915b-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento (DOM) somente leitura usando `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="f915b-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="f915b-342">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="f915b-342">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="f915b-343">Os elementos JSON que compõem a carga podem ser acessados por meio do tipo de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="f915b-343">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="f915b-344">O tipo de `JsonElement` fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="f915b-344">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="f915b-345">`JsonDocument` expõe uma propriedade <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="f915b-345">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="f915b-346">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="f915b-346">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="f915b-347">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="f915b-347">Use JsonDocument for access to data</span></span>

<span data-ttu-id="f915b-348">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.JsonDocument> para acesso aleatório a dados em uma cadeia de caracteres JSON:</span><span class="sxs-lookup"><span data-stu-id="f915b-348">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="f915b-349">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="f915b-349">The preceding code:</span></span>

* <span data-ttu-id="f915b-350">Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="f915b-350">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="f915b-351">Calcula uma classificação média para objetos em uma matriz de `Students` que têm uma propriedade `Grade`.</span><span class="sxs-lookup"><span data-stu-id="f915b-351">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="f915b-352">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="f915b-352">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="f915b-353">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="f915b-353">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="f915b-354">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f915b-354">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="f915b-355">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="f915b-355">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="f915b-356">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-356">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="f915b-357">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="f915b-357">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="f915b-358">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="f915b-358">The preceding code:</span></span>

* <span data-ttu-id="f915b-359">Lê um arquivo JSON, carrega os dados em um `JsonDocument`e grava JSON formatado (bem impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f915b-359">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="f915b-360">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="f915b-360">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="f915b-361">Quando terminar, o chamará <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> no gravador.</span><span class="sxs-lookup"><span data-stu-id="f915b-361">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="f915b-362">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="f915b-362">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="f915b-363">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="f915b-363">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="f915b-364">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="f915b-364">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="f915b-365">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="f915b-365">Use Utf8JsonWriter</span></span>

<span data-ttu-id="f915b-366">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="f915b-366">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="f915b-367">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="f915b-367">Use Utf8JsonReader</span></span>

<span data-ttu-id="f915b-368">O exemplo a seguir mostra como usar a classe <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="f915b-368">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="f915b-369">O código anterior pressupõe que a variável `jsonUtf8` é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f915b-369">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="f915b-370">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="f915b-370">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="f915b-371">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="f915b-371">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="f915b-372">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="f915b-372">The preceding code:</span></span>

* <span data-ttu-id="f915b-373">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f915b-373">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="f915b-374">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="f915b-374">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="f915b-375">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f915b-375">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="f915b-376">Conta objetos e `name` valores de propriedade que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="f915b-376">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="f915b-377">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="f915b-377">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="f915b-378">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="f915b-378">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="f915b-379">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f915b-379">Additional resources</span></span>

* [<span data-ttu-id="f915b-380">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-380">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f915b-381">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-381">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="f915b-382">Gravar conversores personalizados para System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-382">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f915b-383">Suporte a DateTime e DateTimeOffset em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f915b-383">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="f915b-384">Problemas do GitHub no repositório dotnet/corefx rotulados como JSON-funcionalidade-doc</span><span class="sxs-lookup"><span data-stu-id="f915b-384">GitHub issues in the dotnet/corefx repository labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
