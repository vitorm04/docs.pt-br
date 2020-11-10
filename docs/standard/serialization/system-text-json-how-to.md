---
title: Como serializar e desserializar JSON usando C#-.NET
description: 'Saiba como usar o System.Text.Json namespace para serializar e desserializar do JSON no .net. Inclui o código de exemplo.'
ms.date: 11/05/2020
no-loc:
- 'System.Text.Json'
- 'Newtonsoft.Json'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c1358b2b63a92cb50b853043adbfaae23ccd897
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329866"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="6a6b8-104">Como serializar e desserializar (empacotar e desempacotar) JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="6a6b8-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="6a6b8-105">Este artigo mostra como usar o <xref:System.Text.Json?displayProperty=fullName> namespace para serializar e desserializar de JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="6a6b8-106">Se você estiver portando um código existente do `Newtonsoft.Json` , consulte [como migrar `System.Text.Json` para o ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="6a6b8-107">As direções e o código de exemplo usam a biblioteca diretamente, não por meio de uma estrutura como [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="6a6b8-108">A maior parte do código de exemplo de serialização define <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` "muito impresso" o JSON (com recuo e espaço em branco para legibilidade humana).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="6a6b8-109">Para uso em produção, você normalmente aceitaria o valor padrão de `false` para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="6a6b8-110">Os exemplos de código referem-se à seguinte classe e variantes dela:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="6a6b8-111">Namespaces</span><span class="sxs-lookup"><span data-stu-id="6a6b8-111">Namespaces</span></span>

<span data-ttu-id="6a6b8-112">O <xref:System.Text.Json> namespace contém todos os pontos de entrada e os tipos principais.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="6a6b8-113">O <xref:System.Text.Json.Serialization> namespace contém atributos e APIs para cenários avançados e personalização específicas para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="6a6b8-114">Os exemplos de código mostrados neste artigo exigem `using` diretivas para um ou ambos os namespaces:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="6a6b8-115"><xref:System.Runtime.Serialization>Não há suporte para atributos do namespace no `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="6a6b8-116">Como gravar objetos .NET em JSON (Serialize)</span><span class="sxs-lookup"><span data-stu-id="6a6b8-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="6a6b8-117">Para gravar JSON em uma cadeia de caracteres ou em um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6a6b8-118">O exemplo a seguir cria JSON como uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-119">O exemplo a seguir usa código síncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-120">O exemplo a seguir usa código assíncrono para criar um arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-121">Os exemplos anteriores usam a inferência de tipos para o tipo que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="6a6b8-122">Uma sobrecarga de `Serialize()` usa um parâmetro de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="6a6b8-123">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="6a6b8-123">Serialization example</span></span>

<span data-ttu-id="6a6b8-124">Aqui está uma classe de exemplo que contém propriedades de tipo de coleção e um tipo definido pelo usuário:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="6a6b8-125">"POCO" significa [objeto CLR antigo](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="6a6b8-126">Um POCO é um tipo .NET que não depende de nenhum tipo específico de estrutura, por exemplo, por meio de herança ou atributos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="6a6b8-127">A saída JSON da serialização de uma instância do tipo anterior é semelhante ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="6a6b8-128">A saída JSON é reduzidos por padrão:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="6a6b8-129">O exemplo a seguir mostra o mesmo JSON, mas formatado (ou seja, muito impresso com espaço em branco e recuo):</span><span class="sxs-lookup"><span data-stu-id="6a6b8-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="6a6b8-130">Serializar para UTF-8</span><span class="sxs-lookup"><span data-stu-id="6a6b8-130">Serialize to UTF-8</span></span>

<span data-ttu-id="6a6b8-131">Para serializar para UTF-8, chame o <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> método:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-132">Uma <xref:System.Text.Json.JsonSerializer.Serialize%2A> sobrecarga que usa um <xref:System.Text.Json.Utf8JsonWriter> também está disponível.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="6a6b8-133">A serialização para UTF-8 é de cerca de 5-10% mais rápida do que usar os métodos baseados em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="6a6b8-134">A diferença é porque os bytes (como UTF-8) não precisam ser convertidos em cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="6a6b8-135">Comportamento de serialização</span><span class="sxs-lookup"><span data-stu-id="6a6b8-135">Serialization behavior</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6a6b8-136">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="6a6b8-137">Você pode [especificar propriedades a serem ignoradas](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-137">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="6a6b8-138">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="6a6b8-139">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-139">By default, JSON is minified.</span></span> <span data-ttu-id="6a6b8-140">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="6a6b8-141">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="6a6b8-142">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="6a6b8-143">Por padrão, referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="6a6b8-144">Você pode [preservar referências e manipular referências circulares](#preserve-references-and-handle-circular-references).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-144">You can [preserve references and handle circular references](#preserve-references-and-handle-circular-references).</span></span>
* <span data-ttu-id="6a6b8-145">Por padrão, os [campos](../../csharp/programming-guide/classes-and-structs/fields.md) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="6a6b8-146">Você pode [incluir campos](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="6a6b8-147">Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6a6b8-148">Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-148">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6a6b8-149">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="6a6b8-150">Você pode [especificar propriedades a serem ignoradas](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-150">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="6a6b8-151">O [codificador padrão](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapa caracteres não ASCII, caracteres sensíveis a HTML dentro do intervalo ASCII e caracteres que devem ser ignorados de acordo com [a especificação JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="6a6b8-152">Por padrão, o JSON é reduzidos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-152">By default, JSON is minified.</span></span> <span data-ttu-id="6a6b8-153">Você pode [muito imprimir o JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="6a6b8-154">Por padrão, a capitalização de nomes JSON corresponde aos nomes .NET.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="6a6b8-155">Você pode personalizar o uso de [maiúsculas e minúsculas de nomes](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-155">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="6a6b8-156">Referências circulares são detectadas e exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="6a6b8-157">Os [campos](../../csharp/programming-guide/classes-and-structs/fields.md) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="6a6b8-158">Os tipos com suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6a6b8-159">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="6a6b8-160">[Pocos (objetos CLR antigos)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="6a6b8-161">Matrizes unidimensionais e denteadas ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="6a6b8-162">Coleções e dicionários dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6a6b8-163">Primitivos .NET que mapeiam para primitivos JavaScript, como tipos numéricos, cadeias de caracteres e booliano.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="6a6b8-164">[Pocos (objetos CLR antigos)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="6a6b8-165">Matrizes unidimensionais e denteadas ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="6a6b8-166">`Dictionary<string,TValue>` onde `TValue` é `object` , `JsonElement` , ou um poco.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="6a6b8-167">Coleções dos namespaces a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="6a6b8-168">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para lidar com tipos adicionais ou para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="6a6b8-169">Como ler JSON em objetos .NET (desserializar)</span><span class="sxs-lookup"><span data-stu-id="6a6b8-169">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="6a6b8-170">Para desserializar de uma cadeia de caracteres ou de um arquivo, chame o <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6a6b8-171">O exemplo a seguir lê JSON de uma cadeia de caracteres e cria uma instância da `WeatherForecastWithPOCOs` classe mostrada anteriormente para o [exemplo de serialização](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="6a6b8-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="6a6b8-172">Para desserializar de um arquivo usando código síncrono, leia o arquivo em uma cadeia de caracteres, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="6a6b8-173">Para desserializar de um arquivo usando código assíncrono, chame o <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> método:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="6a6b8-174">Desserializar de UTF-8</span><span class="sxs-lookup"><span data-stu-id="6a6b8-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="6a6b8-175">Para desserializar do UTF-8, chame uma <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> sobrecarga que usa um `Utf8JsonReader` ou um `ReadOnlySpan<byte>` , conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="6a6b8-176">Os exemplos pressupõem que o JSON esteja em uma matriz de bytes chamada jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="6a6b8-177">Comportamento de desserialização</span><span class="sxs-lookup"><span data-stu-id="6a6b8-177">Deserialization behavior</span></span>

<span data-ttu-id="6a6b8-178">Os seguintes comportamentos se aplicam ao desserializar JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="6a6b8-179">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="6a6b8-180">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-180">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="6a6b8-181">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="6a6b8-182">Os construtores não públicos são ignorados pelo serializador.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="6a6b8-183">Há suporte para desserialização para objetos imutáveis ou propriedades somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="6a6b8-184">Consulte [tipos e registros imutáveis](#immutable-types-and-records).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-184">See [Immutable types and Records](#immutable-types-and-records).</span></span>
* <span data-ttu-id="6a6b8-185">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="6a6b8-186">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-186">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="6a6b8-187">Por padrão, os campos são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-187">By default, fields are ignored.</span></span> <span data-ttu-id="6a6b8-188">Você pode [incluir campos](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="6a6b8-189">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="6a6b8-190">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-190">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="6a6b8-191">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="6a6b8-192">Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6a6b8-193">Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-193">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="6a6b8-194">Por padrão, a correspondência de nome de propriedade diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="6a6b8-195">Você pode [especificar a não diferenciação de maiúsculas e minúsculas](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-195">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span> <span data-ttu-id="6a6b8-196">ASP.NET Core aplicativos [especificam a diferenciação de maiúsculas e minúsculas por padrão](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-196">ASP.NET Core apps [specify case-insensitivity by default](#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="6a6b8-197">Se o JSON contiver um valor para uma propriedade somente leitura, o valor será ignorado e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="6a6b8-198">Um construtor sem parâmetros, que pode ser público, interno ou privado, é usado para desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="6a6b8-199">A desserialização para objetos imutáveis ou propriedades somente leitura não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="6a6b8-200">Por padrão, há suporte para enums como números.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="6a6b8-201">Você pode [serializar nomes de enumeração como cadeias de caracteres](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-201">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="6a6b8-202">Não há suporte para campos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-202">Fields aren't supported.</span></span>
* <span data-ttu-id="6a6b8-203">Por padrão, comentários ou vírgulas à direita nas exceções do JSON throw.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="6a6b8-204">Você pode [permitir comentários e vírgulas à direita](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-204">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="6a6b8-205">A [profundidade máxima padrão](xref:System.Text.Json.JsonReaderOptions.MaxDepth) é 64.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="6a6b8-206">Quando você usa System.Text.Json indiretamente em um aplicativo ASP.NET Core, alguns comportamentos padrão são diferentes.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="6a6b8-207">Para obter mais informações, consulte [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-207">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="6a6b8-208">Você pode [implementar conversores personalizados](system-text-json-converters-how-to.md) para fornecer funcionalidade que não é suportada pelos conversores internos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="6a6b8-209">Serializar para JSON formatado</span><span class="sxs-lookup"><span data-stu-id="6a6b8-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="6a6b8-210">Para imprimir a saída JSON com muita impressão, defina <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> como `true` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="6a6b8-211">Aqui está um tipo de exemplo a ser serializado e a saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="6a6b8-212">Incluir campos</span><span class="sxs-lookup"><span data-stu-id="6a6b8-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-213">Use a <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> configuração global ou o atributo [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) para incluir campos ao serializar ou desserializar, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-213">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

<span data-ttu-id="6a6b8-214">Para ignorar campos somente leitura, use a <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> configuração global.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-214">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-215">Não há suporte para campos no System.Text.Json no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-215">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="6a6b8-216">[Conversores personalizados](system-text-json-converters-how-to.md) podem fornecer essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="customize-json-names-and-values"></a><span data-ttu-id="6a6b8-217">Personalizar nomes e valores JSON</span><span class="sxs-lookup"><span data-stu-id="6a6b8-217">Customize JSON names and values</span></span>

<span data-ttu-id="6a6b8-218">Por padrão, os nomes de propriedade e as chaves de dicionário são inalterados na saída JSON, incluindo maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-218">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="6a6b8-219">Os valores de enumeração são representados como números.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-219">Enum values are represented as numbers.</span></span> <span data-ttu-id="6a6b8-220">Esta seção explica como:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-220">This section explains how to:</span></span>

* [<span data-ttu-id="6a6b8-221">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-221">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="6a6b8-222">Converter todos os nomes de propriedade em camel case</span><span class="sxs-lookup"><span data-stu-id="6a6b8-222">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="6a6b8-223">Implementar uma política de nomenclatura de propriedade personalizada</span><span class="sxs-lookup"><span data-stu-id="6a6b8-223">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="6a6b8-224">Converter chaves de dicionário em camel case</span><span class="sxs-lookup"><span data-stu-id="6a6b8-224">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="6a6b8-225">Converter enums em cadeias de caracteres e camel case</span><span class="sxs-lookup"><span data-stu-id="6a6b8-225">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="6a6b8-226">Para outros cenários que exigem tratamento especial de valores e nomes de propriedade JSON, você pode [implementar conversores personalizados](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-226">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="6a6b8-227">Personalizar nomes de propriedade individuais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-227">Customize individual property names</span></span>

<span data-ttu-id="6a6b8-228">Para definir o nome de propriedades individuais, use o atributo [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-228">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="6a6b8-229">Veja um exemplo de tipo para serializar e o JSON resultante:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-229">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="6a6b8-230">O nome da propriedade definido por este atributo:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-230">The property name set by this attribute:</span></span>

* <span data-ttu-id="6a6b8-231">Aplica-se em ambas as direções, para serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-231">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="6a6b8-232">Tem precedência sobre as políticas de nomenclatura de propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-232">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="6a6b8-233">Usar o camel case para todos os nomes de propriedade JSON</span><span class="sxs-lookup"><span data-stu-id="6a6b8-233">Use camel case for all JSON property names</span></span>

<span data-ttu-id="6a6b8-234">Para usar o camel case para todos os nomes de propriedade JSON, defina como <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-234">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="6a6b8-235">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-235">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="6a6b8-236">A política de nomenclatura de Propriedade do camel case:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-236">The camel case property naming policy:</span></span>

* <span data-ttu-id="6a6b8-237">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-237">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="6a6b8-238">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-238">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="6a6b8-239">É por isso que o nome da propriedade JSON `Wind` no exemplo não é camel case.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-239">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="6a6b8-240">Usar uma política de nomenclatura de propriedade JSON personalizada</span><span class="sxs-lookup"><span data-stu-id="6a6b8-240">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="6a6b8-241">Para usar uma política de nomenclatura de propriedade JSON personalizada, crie uma classe derivada de <xref:System.Text.Json.JsonNamingPolicy> e substitua o <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> método, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-241">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="6a6b8-242">Em seguida, defina a <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> propriedade como uma instância da sua classe de política de nomenclatura:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-242">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-243">Aqui está uma classe de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-243">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="6a6b8-244">A política de nomenclatura de propriedade JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-244">The JSON property naming policy:</span></span>

* <span data-ttu-id="6a6b8-245">Aplica-se à serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-245">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="6a6b8-246">É substituído por `[JsonPropertyName]` atributos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-246">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="6a6b8-247">É por isso que o nome da propriedade JSON `Wind` no exemplo não é maiúscula.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-247">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="6a6b8-248">Chaves de dicionário do camel case</span><span class="sxs-lookup"><span data-stu-id="6a6b8-248">Camel case dictionary keys</span></span>

<span data-ttu-id="6a6b8-249">Se uma propriedade de um objeto a ser serializado for do tipo `Dictionary<string,TValue>` , as `string` chaves poderão ser convertidas em camel case.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-249">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="6a6b8-250">Para fazer isso, defina <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> como `JsonNamingPolicy.CamelCase` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-250">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-251">Serializar um objeto com um dicionário chamado `TemperatureRanges` que tem pares chave-valor `"ColdMinTemp", 20` e `"HotMinTemp", 40` resultaria em uma saída JSON como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-251">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="6a6b8-252">A política de nomenclatura do camel case para chaves de dicionário se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-252">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="6a6b8-253">Se você desserializar um dicionário, as chaves corresponderão ao arquivo JSON mesmo que você especifique `JsonNamingPolicy.CamelCase` para o `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-253">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="6a6b8-254">Enumerações como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="6a6b8-254">Enums as strings</span></span>

<span data-ttu-id="6a6b8-255">Por padrão, as enumerações são serializadas como números.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-255">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="6a6b8-256">Para serializar nomes de enumeração como cadeias de caracteres, use o <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-256">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="6a6b8-257">Por exemplo, suponha que você precise serializar a seguinte classe que tem uma enumeração:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-257">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="6a6b8-258">Se o resumo for `Hot` , por padrão, o JSON serializado terá o valor numérico 3:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-258">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="6a6b8-259">O código de exemplo a seguir serializa os nomes de enumeração em vez dos valores numéricos e converte os nomes em camel case:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-259">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-260">O JSON resultante é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-260">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="6a6b8-261">Os nomes de cadeias de caracteres de enumeração também podem ser desserializados, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-261">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a><span data-ttu-id="6a6b8-262">Ignorar Propriedades</span><span class="sxs-lookup"><span data-stu-id="6a6b8-262">Ignore properties</span></span>

<span data-ttu-id="6a6b8-263">Por padrão, todas as propriedades públicas são serializadas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-263">By default, all public properties are serialized.</span></span> <span data-ttu-id="6a6b8-264">Se você não quiser que alguns deles apareçam na saída JSON, terá várias opções.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-264">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="6a6b8-265">Esta seção explica como ignorar:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-265">This section explains how to ignore:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="6a6b8-266">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-266">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="6a6b8-267">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6b8-267">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="6a6b8-268">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="6a6b8-268">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="6a6b8-269">Todas as propriedades de valor padrão</span><span class="sxs-lookup"><span data-stu-id="6a6b8-269">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="6a6b8-270">Propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-270">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="6a6b8-271">Todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6b8-271">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="6a6b8-272">Todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="6a6b8-272">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a><span data-ttu-id="6a6b8-273">Ignorar propriedades individuais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-273">Ignore individual properties</span></span>

<span data-ttu-id="6a6b8-274">Para ignorar as propriedades individuais, use o atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-274">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="6a6b8-275">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-275">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-276">Você pode especificar a exclusão condicional definindo a propriedade do atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-276">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="6a6b8-277">A <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enumeração fornece as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-277">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="6a6b8-278">`Always` -A propriedade é sempre ignorada.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-278">`Always` - The property is always ignored.</span></span> <span data-ttu-id="6a6b8-279">Se não `Condition` for especificado, essa opção será assumida.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-279">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="6a6b8-280">`Never` -A propriedade é sempre serializada e desserializada, independentemente das `DefaultIgnoreCondition` `IgnoreReadOnlyProperties` `IgnoreReadOnlyFields` configurações globais, e.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-280">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="6a6b8-281">`WhenWritingDefault` -A propriedade será ignorada na serialização se for um tipo de referência `null` ou um tipo de valor `default` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-281">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null` or a value type `default`.</span></span>
* <span data-ttu-id="6a6b8-282">`WhenWritingNull` -A propriedade será ignorada na serialização se for um tipo de referência `null` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-282">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`.</span></span>

<span data-ttu-id="6a6b8-283">O exemplo a seguir ilustra o uso da Propriedade do atributo [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) `Condition` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-283">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a><span data-ttu-id="6a6b8-284">Ignorar todas as propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="6a6b8-284">Ignore all read-only properties</span></span>

<span data-ttu-id="6a6b8-285">Uma propriedade será somente leitura se ela contiver um getter público, mas não um setter público.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-285">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="6a6b8-286">Para ignorar todas as propriedades somente leitura ao serializar, defina <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> como `true` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-286">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-287">Aqui está um tipo de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-287">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="6a6b8-288">Essa opção se aplica somente à serialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-288">This option applies only to serialization.</span></span> <span data-ttu-id="6a6b8-289">Durante a desserialização, as propriedades somente leitura são ignoradas por padrão.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-289">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-290">Essa opção se aplica somente a propriedades.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-290">This option applies only to properties.</span></span> <span data-ttu-id="6a6b8-291">Para ignorar campos somente leitura ao [serializar campos](#include-fields), use a <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> configuração global.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-291">To ignore read-only fields when [serializing fields](#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

### <a name="ignore-all-null-value-properties"></a><span data-ttu-id="6a6b8-292">Ignorar todas as propriedades de valor nulo</span><span class="sxs-lookup"><span data-stu-id="6a6b8-292">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-293">Para ignorar todas as propriedades de valor nulo, defina a <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> propriedade como <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-293">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-294">Para ignorar todas as propriedades de valor nulo ao serializar, defina a <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> propriedade como `true` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-294">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-295">Aqui está um objeto de exemplo para serializar e a saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-295">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="6a6b8-296">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6a6b8-296">Property</span></span> |<span data-ttu-id="6a6b8-297">Valor</span><span class="sxs-lookup"><span data-stu-id="6a6b8-297">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="6a6b8-298">Data</span><span class="sxs-lookup"><span data-stu-id="6a6b8-298">Date</span></span>    | <span data-ttu-id="6a6b8-299">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="6a6b8-299">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="6a6b8-300">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="6a6b8-300">TemperatureCelsius</span></span>| <span data-ttu-id="6a6b8-301">25</span><span class="sxs-lookup"><span data-stu-id="6a6b8-301">25</span></span> |
| <span data-ttu-id="6a6b8-302">Resumo</span><span class="sxs-lookup"><span data-stu-id="6a6b8-302">Summary</span></span>| <span data-ttu-id="6a6b8-303">null</span><span class="sxs-lookup"><span data-stu-id="6a6b8-303">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a><span data-ttu-id="6a6b8-304">Ignorar todas as propriedades de valor padrão</span><span class="sxs-lookup"><span data-stu-id="6a6b8-304">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-305">Para evitar a serialização de valores padrão em Propriedades de tipo de valor, defina a <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> propriedade como <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-305">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="6a6b8-306">A `WhenWritingDefault` configuração também impede a serialização de propriedades de tipo de referência de valor nulo.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-306">The `WhenWritingDefault` setting also prevents serialization of null-value reference type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-307">Não há uma maneira interna de impedir a serialização de propriedades com padrões de tipo de valor no System.Text.Json .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-307">There is no built-in way to prevent serialization of properties with value type defaults in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="customize-character-encoding"></a><span data-ttu-id="6a6b8-308">Personalizar codificação de caracteres</span><span class="sxs-lookup"><span data-stu-id="6a6b8-308">Customize character encoding</span></span>

<span data-ttu-id="6a6b8-309">Por padrão, o serializador escapa todos os caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-309">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="6a6b8-310">Ou seja, ele substitui por `\uxxxx` onde `xxxx` está o código Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-310">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="6a6b8-311">Por exemplo, se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-311">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="6a6b8-312">Serializar conjuntos de caracteres de idioma</span><span class="sxs-lookup"><span data-stu-id="6a6b8-312">Serialize language character sets</span></span>

<span data-ttu-id="6a6b8-313">Para serializar os conjuntos de caracteres de um ou mais idiomas sem saída, especifique os [intervalos Unicode](xref:System.Text.Unicode.UnicodeRanges) ao criar uma instância do <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-313">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="6a6b8-314">Este código não sai de escape de caracteres cirílico ou grego.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-314">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="6a6b8-315">Se a `Summary` propriedade for definida como cirílico жарко, o `WeatherForecast` objeto será serializado, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-315">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="6a6b8-316">Para serializar todos os conjuntos de idiomas sem saída, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-316">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="6a6b8-317">Serializar caracteres específicos</span><span class="sxs-lookup"><span data-stu-id="6a6b8-317">Serialize specific characters</span></span>

<span data-ttu-id="6a6b8-318">Uma alternativa é especificar os caracteres individuais que você deseja permitir sem ter escape.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-318">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="6a6b8-319">O exemplo a seguir serializa apenas os dois primeiros caracteres de жарко:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-319">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="6a6b8-320">Aqui está um exemplo de JSON produzido pelo código anterior:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-320">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="6a6b8-321">Serializar todos os caracteres</span><span class="sxs-lookup"><span data-stu-id="6a6b8-321">Serialize all characters</span></span>

<span data-ttu-id="6a6b8-322">Para minimizar a saída, você pode usar <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-322">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="6a6b8-323">Em comparação com o codificador padrão, o `UnsafeRelaxedJsonEscaping` codificador é mais permissivo de permitir que os caracteres passem sem escape:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-323">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="6a6b8-324">Ele não sai de caracteres sensíveis a HTML, como `<` ,, `>` `&` e `'` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-324">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="6a6b8-325">Ele não oferece nenhuma proteção adicional de defesa profunda contra ataques XSS ou de divulgação de informações, como aqueles que podem resultar do cliente e do servidor que estão descordando no conjunto de *caracteres*.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-325">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="6a6b8-326">Use o codificador não seguro somente quando for conhecido que o cliente irá interpretar a carga resultante como JSON codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-326">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="6a6b8-327">Por exemplo, você pode usá-lo se o servidor estiver enviando o cabeçalho de resposta `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-327">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="6a6b8-328">Nunca permita que a `UnsafeRelaxedJsonEscaping` saída bruta seja emitida em uma página HTML ou em um `<script>` elemento.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-328">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="6a6b8-329">Serializar Propriedades de classes derivadas</span><span class="sxs-lookup"><span data-stu-id="6a6b8-329">Serialize properties of derived classes</span></span>

<span data-ttu-id="6a6b8-330">Não há suporte para a serialização de uma hierarquia de tipo polimórfico.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-330">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="6a6b8-331">Por exemplo, se uma propriedade for definida como uma interface ou uma classe abstrata, somente as propriedades definidas na interface ou na classe abstrata serão serializadas, mesmo que o tipo de tempo de execução tenha propriedades adicionais.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-331">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="6a6b8-332">As exceções a esse comportamento são explicadas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-332">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="6a6b8-333">Por exemplo, suponha que você tenha uma `WeatherForecast` classe e uma classe derivada `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-333">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="6a6b8-334">E suponha que o argumento de tipo do `Serialize` método em tempo de compilação seja `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-334">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="6a6b8-335">Nesse cenário, a `WindSpeed` propriedade não é serializada, mesmo que o `weatherForecast` objeto seja, na verdade, um `WeatherForecastDerived` objeto.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-335">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="6a6b8-336">Somente as propriedades da classe base são serializadas:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-336">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="6a6b8-337">Esse comportamento destina-se a ajudar a evitar a exposição acidental de dados em um tipo criado de tempo de execução derivado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-337">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="6a6b8-338">Para serializar as propriedades do tipo derivado no exemplo anterior, use uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-338">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="6a6b8-339">Chame uma sobrecarga de <xref:System.Text.Json.JsonSerializer.Serialize%2A> que permite especificar o tipo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-339">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="6a6b8-340">Declare o objeto a ser serializado como `object` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-340">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="6a6b8-341">No cenário de exemplo anterior, ambas as abordagens fazem com que a `WindSpeed` propriedade seja incluída na saída JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-341">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="6a6b8-342">Essas abordagens fornecem serialização polimórfica somente para o objeto raiz a ser serializado, não para propriedades desse objeto raiz.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-342">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="6a6b8-343">Você pode obter a serialização polimórfica para objetos de nível inferior se defini-los como tipo `object` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-343">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="6a6b8-344">Por exemplo, suponha que sua `WeatherForecast` classe tenha uma propriedade chamada `PreviousForecast` que possa ser definida como tipo `WeatherForecast` ou `object` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-344">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="6a6b8-345">Se a `PreviousForecast` Propriedade contiver uma instância de `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-345">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="6a6b8-346">A saída JSON da serialização `WeatherForecastWithPrevious` **não inclui** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-346">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="6a6b8-347">A saída JSON da serialização `WeatherForecastWithPreviousAsObject` **inclui** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-347">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="6a6b8-348">Para serializar `WeatherForecastWithPreviousAsObject` , não é necessário chamar `Serialize<object>` ou `GetType` porque o objeto raiz não é aquele que pode ser de um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-348">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="6a6b8-349">O exemplo de código a seguir não chama `Serialize<object>` ou `GetType` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-349">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="6a6b8-350">O código anterior serializa corretamente `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-350">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="6a6b8-351">A mesma abordagem de definir propriedades como `object` funciona com interfaces.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-351">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="6a6b8-352">Suponha que você tenha a seguinte interface e implementação e queira serializar uma classe com propriedades que contêm instâncias de implementação:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-352">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="6a6b8-353">Quando você serializa uma instância do `Forecasts` , `Tuesday` o mostra apenas a `WindSpeed` propriedade, porque `Tuesday` é definido como `object` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-353">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="6a6b8-354">O exemplo a seguir mostra o JSON que resulta do código anterior:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-354">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="6a6b8-355">Para obter mais informações sobre a **serialização** polimórfica e informações sobre a **desserialização** , consulte [como migrar do Newtonsoft.Json para System.Text.Json o](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-355">For more information about polymorphic **serialization** , and for information about **deserialization** , see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="6a6b8-356">Permitir comentários e vírgulas à direita</span><span class="sxs-lookup"><span data-stu-id="6a6b8-356">Allow comments and trailing commas</span></span>

<span data-ttu-id="6a6b8-357">Por padrão, comentários e vírgulas à direita não são permitidos em JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-357">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="6a6b8-358">Para permitir comentários no JSON, defina a <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> propriedade como `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-358">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="6a6b8-359">E para permitir vírgulas à direita, defina a <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-359">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="6a6b8-360">O exemplo a seguir mostra como permitir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-360">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="6a6b8-361">Aqui está um exemplo de JSON com comentários e uma vírgula à direita:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-361">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="6a6b8-362">Correspondência de propriedade que não diferencia maiúsculas de minúsculas</span><span class="sxs-lookup"><span data-stu-id="6a6b8-362">Case-insensitive property matching</span></span>

<span data-ttu-id="6a6b8-363">Por padrão, a desserialização procura as correspondências de nome de propriedade que diferenciam maiúsculas de minúsculas entre JSON e as propriedades do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-363">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="6a6b8-364">Para alterar esse comportamento, defina <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> como `true` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-364">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="6a6b8-365">Aqui está um exemplo de JSON com nomes de Propriedade do camel case.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-365">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="6a6b8-366">Ele pode ser desserializado no seguinte tipo que tem nomes de propriedade de caso de Pascal.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-366">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="6a6b8-367">Processar JSON de estouro</span><span class="sxs-lookup"><span data-stu-id="6a6b8-367">Handle overflow JSON</span></span>

<span data-ttu-id="6a6b8-368">Durante a desserialização, você pode receber dados no JSON que não são representados pelas propriedades do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-368">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="6a6b8-369">Por exemplo, suponha que o tipo de destino seja o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-369">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="6a6b8-370">E o JSON a ser desserializado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-370">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="6a6b8-371">Se você desserializar o JSON mostrado no tipo mostrado, as `DatesAvailable` Propriedades e `SummaryWords` ficarão sem lugar e serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-371">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="6a6b8-372">Para capturar dados adicionais, como essas propriedades, aplique o atributo [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) a uma propriedade do tipo `Dictionary<string,object>` ou `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-372">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="6a6b8-373">Quando você desserializar o JSON mostrado anteriormente neste tipo de exemplo, os dados extras se tornarão pares de chave-valor da `ExtensionData` Propriedade:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-373">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="6a6b8-374">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6a6b8-374">Property</span></span> |<span data-ttu-id="6a6b8-375">Valor</span><span class="sxs-lookup"><span data-stu-id="6a6b8-375">Value</span></span>  |<span data-ttu-id="6a6b8-376">Observações</span><span class="sxs-lookup"><span data-stu-id="6a6b8-376">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="6a6b8-377">Data</span><span class="sxs-lookup"><span data-stu-id="6a6b8-377">Date</span></span>    | <span data-ttu-id="6a6b8-378">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="6a6b8-378">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="6a6b8-379">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="6a6b8-379">TemperatureCelsius</span></span>| <span data-ttu-id="6a6b8-380">0</span><span class="sxs-lookup"><span data-stu-id="6a6b8-380">0</span></span> | <span data-ttu-id="6a6b8-381">Incompatibilidade de maiúsculas e minúsculas ( `temperatureCelsius` no JSON), portanto, a propriedade não está definida.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-381">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="6a6b8-382">Resumo</span><span class="sxs-lookup"><span data-stu-id="6a6b8-382">Summary</span></span> | <span data-ttu-id="6a6b8-383">Frequente</span><span class="sxs-lookup"><span data-stu-id="6a6b8-383">Hot</span></span> ||
| <span data-ttu-id="6a6b8-384">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="6a6b8-384">ExtensionData</span></span> | <span data-ttu-id="6a6b8-385">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="6a6b8-385">temperatureCelsius: 25</span></span> |<span data-ttu-id="6a6b8-386">Como o caso não corresponde, essa propriedade JSON é um extra e se torna um par chave-valor no dicionário.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-386">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="6a6b8-387">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-387">DatesAvailable:</span></span><br>  <span data-ttu-id="6a6b8-388">8/1/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="6a6b8-388">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="6a6b8-389">8/2/2019 12:00:00 AM-07:00</span><span class="sxs-lookup"><span data-stu-id="6a6b8-389">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="6a6b8-390">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-390">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="6a6b8-391">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-391">SummaryWords:</span></span><br><span data-ttu-id="6a6b8-392">Esporádico</span><span class="sxs-lookup"><span data-stu-id="6a6b8-392">Cool</span></span><br><span data-ttu-id="6a6b8-393">Vento</span><span class="sxs-lookup"><span data-stu-id="6a6b8-393">Windy</span></span><br><span data-ttu-id="6a6b8-394">Humid</span><span class="sxs-lookup"><span data-stu-id="6a6b8-394">Humid</span></span> |<span data-ttu-id="6a6b8-395">A propriedade extra do JSON torna-se um par chave-valor, com uma matriz como o objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-395">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="6a6b8-396">Quando o objeto de destino é serializado, os pares de valor de chave de dados de extensão se tornam propriedades JSON, assim como no JSON de entrada:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-396">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="6a6b8-397">Observe que o `ExtensionData` nome da propriedade não aparece no JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-397">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="6a6b8-398">Esse comportamento permite que o JSON faça uma viagem de ida e volta sem perder nenhum dado extra que, de outra forma, não seria desserializado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-398">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="6a6b8-399">Preservar referências e manipular referências circulares</span><span class="sxs-lookup"><span data-stu-id="6a6b8-399">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="6a6b8-400">Para preservar referências e manipular referências circulares, defina <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> como <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-400">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="6a6b8-401">Essa configuração causa o seguinte comportamento:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-401">This setting causes the following behavior:</span></span>

* <span data-ttu-id="6a6b8-402">Em serializar:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-402">On serialize:</span></span>

  <span data-ttu-id="6a6b8-403">Ao escrever tipos complexos, o serializador também grava Propriedades de metadados ( `$id` , `$values` e `$ref` ).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-403">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="6a6b8-404">Ao desserializar:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-404">On deserialize:</span></span>

  <span data-ttu-id="6a6b8-405">Os metadados são esperados (embora não obrigatórios) e o desserializador tenta compreendê-lo.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-405">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="6a6b8-406">O código a seguir ilustra o uso da `Preserve` configuração.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-406">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="6a6b8-407">Esse recurso não pode ser usado para preservar tipos de valor ou tipos imutáveis.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-407">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="6a6b8-408">Na desserialização, a instância de um tipo imutável é criada depois que a carga inteira é lida.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-408">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="6a6b8-409">Portanto, seria impossível desserializar a mesma instância se uma referência a ela aparecer dentro da carga JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-409">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="6a6b8-410">Para tipos de valor, tipos imutáveis e matrizes, nenhum metadado de referência é serializado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-410">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="6a6b8-411">Na desserialização, uma exceção será lançada se `$ref` ou `$id` for encontrada.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-411">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="6a6b8-412">No entanto, os tipos de valor ignoram `$id` (e, `$values` no caso de coleções) para possibilitar a desserialização de cargas que foram serializadas usando Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-412">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="6a6b8-413">Newtonsoft.Json Serializa metadados para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-413">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="6a6b8-414">Para determinar se os objetos são iguais, System.Text.Json usa <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> , que usa igualdade de referência ( <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> ) em vez de igualdade de valor ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> ao comparar duas instâncias de objeto.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-414">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="6a6b8-415">Para obter mais informações sobre como as referências são serializadas e desserializadas, consulte <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-415">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6a6b8-416">A <xref:System.Text.Json.Serialization.ReferenceResolver> classe define o comportamento de preservar referências na serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-416">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="6a6b8-417">Crie uma classe derivada para especificar o comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-417">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="6a6b8-418">Para obter um exemplo, consulte [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-418">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-419">System.Text.Json no .NET Core 3,1 dá suporte apenas a serialização por valor e gera uma exceção para referências circulares.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-419">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="6a6b8-420">Permitir ou gravar números entre aspas</span><span class="sxs-lookup"><span data-stu-id="6a6b8-420">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="6a6b8-421">Alguns serializadores codificam números como cadeias de caracteres JSON (entre aspas).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-421">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="6a6b8-422">Por exemplo: `{"DegreesCelsius":"23"}` em vez de `{"DegreesCelsius":23}` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-422">For example: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="6a6b8-423">Para serializar números entre aspas ou aceitar números entre aspas em todo o grafo de objeto de entrada, defina <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-423">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

<span data-ttu-id="6a6b8-424">Quando você usa System.Text.Json indiretamente por meio de ASP.NET Core, são permitidos números entre aspas ao desserializar porque ASP.NET Core especifica [opções padrão da Web](xref:System.Text.Json.JsonSerializerDefaults.Web).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-424">When you use System.Text.Json indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="6a6b8-425">Para permitir ou gravar números entre aspas para propriedades, campos ou tipos específicos, use o atributo [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-425">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-426">System.Text.Json no .NET Core 3,1 não dá suporte à serialização ou desserialização de números entre aspas.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-426">System.Text.Json in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="6a6b8-427">Para obter mais informações, consulte [permitir ou gravar números entre aspas](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-427">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="immutable-types-and-records"></a><span data-ttu-id="6a6b8-428">Tipos e registros imutáveis</span><span class="sxs-lookup"><span data-stu-id="6a6b8-428">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-429">System.Text.Json pode usar um construtor com parâmetros, o que torna possível desserializar uma classe ou estrutura imutável.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-429">System.Text.Json can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="6a6b8-430">Para uma classe, se o único Construtor for um parametrizado, esse construtor será usado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-430">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="6a6b8-431">Para uma struct ou uma classe com vários construtores, especifique o que deve ser usado aplicando o atributo [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-431">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="6a6b8-432">Quando o atributo não é usado, um construtor público sem parâmetros é sempre usado, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-432">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="6a6b8-433">O atributo só pode ser usado com construtores públicos.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-433">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="6a6b8-434">O exemplo a seguir usa o `[JsonConstructor]` atributo:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-434">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="6a6b8-435">Também há suporte para registros no C# 9, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-435">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="6a6b8-436">Para tipos que são imutáveis porque todos os seus setters de propriedade são não públicos, consulte a seção a seguir sobre [acessadores de propriedade não pública](#non-public-property-accessors).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-436">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-437">`JsonConstructorAttribute` e o suporte a registros do C# 9 não está disponível no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-437">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="6a6b8-438">Acessadores de propriedade não pública</span><span class="sxs-lookup"><span data-stu-id="6a6b8-438">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-439">Para habilitar o uso de um acessador de propriedade não público, use o atributo [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-439">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-440">Não há suporte para acessadores de propriedade não pública no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-440">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="6a6b8-441">Para obter mais informações, consulte [o Newtonsoft.Json artigo migrar de](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-441">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="6a6b8-442">Copiar JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="6a6b8-442">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-443">Há um [Construtor JsonSerializerOptions] (xref: System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)) que permite criar uma nova instância com as mesmas opções de uma instância existente, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-443">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-444">Um `JsonSerializerOptions` Construtor que usa uma instância existente não está disponível no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-444">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="6a6b8-445">Padrões da Web para JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="6a6b8-445">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="6a6b8-446">Aqui estão as opções que têm padrões diferentes para aplicativos Web:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-446">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="6a6b8-447">Há um [Construtor JsonSerializerOptions] (xref: System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = NET-5,0&preserve-View = true) que permite criar uma nova instância com as opções padrão que ASP.NET Core usa para aplicativos Web, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-447">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-448">Aqui estão as opções que têm padrões diferentes para aplicativos Web:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-448">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="6a6b8-449">Um `JsonSerializerOptions` Construtor que especifica um conjunto de padrões não está disponível no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-449">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="6a6b8-450">Métodos de extensão HttpClient e HttpContent</span><span class="sxs-lookup"><span data-stu-id="6a6b8-450">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="6a6b8-451">A serialização e a desserialização de cargas JSON da rede são operações comuns.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-451">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="6a6b8-452">Os métodos de extensão em [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) e [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) permitem que você execute essas operações em uma única linha de código.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-452">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="6a6b8-453">Esses métodos de extensão usam [padrões da Web para JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-453">These extension methods use [web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="6a6b8-454">O exemplo a seguir ilustra o uso de <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> e <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-454">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

<span data-ttu-id="6a6b8-455">Também há métodos de extensão para System.Text.Json em [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span><span class="sxs-lookup"><span data-stu-id="6a6b8-455">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="6a6b8-456">Métodos de extensão em `HttpClient` e `HttpContent` não estão disponíveis no System.Text.Json no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-456">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="6a6b8-457">Utf8JsonReader, Utf8JsonWriter e JsonDocument</span><span class="sxs-lookup"><span data-stu-id="6a6b8-457">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="6a6b8-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> é um leitor de alto desempenho, de baixa alocação e somente de encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>` ou `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="6a6b8-459">O `Utf8JsonReader` é um tipo de baixo nível que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-459">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="6a6b8-460">O <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> método usa `Utf8JsonReader` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-460">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="6a6b8-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> é uma maneira de alto desempenho para escrever texto JSON codificado em UTF-8 de tipos comuns do .NET como `String` , `Int32` e `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="6a6b8-462">O gravador é um tipo de baixo nível que pode ser usado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-462">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="6a6b8-463">O <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> método usa `Utf8JsonWriter` nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-463">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="6a6b8-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> fornece a capacidade de criar um Modelo de Objeto do Documento somente leitura (DOM) usando o `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="6a6b8-465">O DOM fornece acesso aleatório aos dados em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-465">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="6a6b8-466">Os elementos JSON que compõem a carga podem ser acessados por meio do <xref:System.Text.Json.JsonElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-466">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="6a6b8-467">O `JsonElement` tipo fornece enumeradores de matriz e de objeto juntamente com APIs para converter texto JSON em tipos .net comuns.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-467">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="6a6b8-468">`JsonDocument` expõe uma <xref:System.Text.Json.JsonDocument.RootElement> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-468">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="6a6b8-469">As seções a seguir mostram como usar essas ferramentas para ler e gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-469">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="6a6b8-470">Usar o JsonDocument para acessar dados</span><span class="sxs-lookup"><span data-stu-id="6a6b8-470">Use JsonDocument for access to data</span></span>

<span data-ttu-id="6a6b8-471">O exemplo a seguir mostra como usar a <xref:System.Text.Json.JsonDocument> classe para acesso aleatório a dados em uma cadeia de caracteres JSON:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-471">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="6a6b8-472">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-472">The preceding code:</span></span>

* <span data-ttu-id="6a6b8-473">Assume que o JSON a ser analisado está em uma cadeia de caracteres chamada `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-473">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="6a6b8-474">Calcula uma classificação média para objetos em uma `Students` matriz que tem uma `Grade` propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-474">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="6a6b8-475">Atribui uma classificação padrão de 70 para alunos que não têm uma classificação.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-475">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="6a6b8-476">Conta os alunos incrementando uma `count` variável com cada iteração.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-476">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="6a6b8-477">Uma alternativa é chamar <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-477">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="6a6b8-478">Veja um exemplo do JSON que esse código processa:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-478">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="6a6b8-479">Usar JsonDocument para gravar JSON</span><span class="sxs-lookup"><span data-stu-id="6a6b8-479">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="6a6b8-480">O exemplo a seguir mostra como gravar JSON de um <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="6a6b8-480">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="6a6b8-481">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-481">The preceding code:</span></span>

* <span data-ttu-id="6a6b8-482">Lê um arquivo JSON, carrega os dados em um `JsonDocument` e grava JSON formatado (bem-impresso) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-482">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="6a6b8-483">Usa <xref:System.Text.Json.JsonDocumentOptions> para especificar que os comentários no JSON de entrada são permitidos, mas ignorados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-483">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="6a6b8-484">Quando terminar, chama <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> o gravador.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-484">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="6a6b8-485">Uma alternativa é deixar o gravador AutoFlush quando ele é Descartado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-485">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="6a6b8-486">Aqui está um exemplo de entrada JSON a ser processada pelo código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-486">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="6a6b8-487">O resultado é a seguinte saída JSON bem impressa:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-487">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="6a6b8-488">Usar Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="6a6b8-488">Use Utf8JsonWriter</span></span>

<span data-ttu-id="6a6b8-489">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonWriter> classe:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-489">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="6a6b8-490">Usar Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="6a6b8-490">Use Utf8JsonReader</span></span>

<span data-ttu-id="6a6b8-491">O exemplo a seguir mostra como usar a <xref:System.Text.Json.Utf8JsonReader> classe:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-491">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="6a6b8-492">O código anterior pressupõe que a `jsonUtf8` variável é uma matriz de bytes que contém um JSON válido, codificado como UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-492">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="6a6b8-493">Filtrar dados usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="6a6b8-493">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="6a6b8-494">O exemplo a seguir mostra como ler um arquivo de forma síncrona e procurar um valor:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-494">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="6a6b8-495">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-495">The preceding code:</span></span>

* <span data-ttu-id="6a6b8-496">Assume que o JSON contém uma matriz de objetos e cada objeto pode conter uma propriedade "Name" do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-496">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="6a6b8-497">Conta objetos e valores de propriedade "Name" que terminam com "University".</span><span class="sxs-lookup"><span data-stu-id="6a6b8-497">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="6a6b8-498">Pressupõe que o arquivo é codificado como UTF-16 e o codifica em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-498">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="6a6b8-499">Um arquivo codificado como UTF-8 pode ser lido diretamente em um `ReadOnlySpan<byte>` , usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-499">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="6a6b8-500">Se o arquivo contiver uma marca de ordem de byte (BOM) UTF-8, remova-a antes de passar os bytes para o `Utf8JsonReader` , uma vez que o leitor espera o texto.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-500">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="6a6b8-501">Caso contrário, a BOM será considerada JSON inválido e o leitor lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-501">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="6a6b8-502">Aqui está um exemplo de JSON que o código anterior pode ler.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-502">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="6a6b8-503">A mensagem de resumo resultante é "2 de 4 têm nomes que terminam com" University "":</span><span class="sxs-lookup"><span data-stu-id="6a6b8-503">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="6a6b8-504">Ler de um fluxo usando Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="6a6b8-504">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="6a6b8-505">Ao ler um arquivo grande (um gigabyte ou mais, por exemplo), talvez você queira evitar ter que carregar todo o arquivo na memória de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-505">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="6a6b8-506">Para esse cenário, você pode usar um <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-506">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="6a6b8-507">Ao usar o `Utf8JsonReader` para ler de um fluxo, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="6a6b8-507">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="6a6b8-508">O buffer que contém a carga JSON parcial deve ser pelo menos tão grande quanto o maior token JSON dentro dele, de modo que o leitor possa progredir em encaminhar.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-508">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="6a6b8-509">O buffer deve ser pelo menos tão grande quanto a maior sequência de espaços em branco dentro do JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-509">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="6a6b8-510">O leitor não mantém o controle dos dados lidos até que ele leia completamente o próximo <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> na carga JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-510">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="6a6b8-511">Assim, quando houver bytes restantes no buffer, você precisa passá-los para o leitor novamente.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-511">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="6a6b8-512">Você pode usar <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> para determinar quantos bytes serão deixados.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-512">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="6a6b8-513">O código a seguir ilustra como ler de um fluxo.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-513">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="6a6b8-514">O exemplo mostra um <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-514">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="6a6b8-515">O código semelhante funcionará com um <xref:System.IO.FileStream> , exceto quando o `FileStream` contiver uma bom UTF-8 no início.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-515">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="6a6b8-516">Nesse caso, você precisa remover esses três bytes do buffer antes de passar os bytes restantes para o `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="6a6b8-516">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="6a6b8-517">Caso contrário, o leitor lançaria uma exceção, uma vez que a BOM não é considerada uma parte válida do JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-517">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="6a6b8-518">O código de exemplo começa com um buffer de 4 KB e dobra o tamanho do buffer sempre que ele descobre que o tamanho não é grande o suficiente para se ajustar a um token JSON completo, que é necessário para que o leitor faça o progresso no conteúdo JSON.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-518">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="6a6b8-519">O exemplo de JSON fornecido no trecho de código dispara um aumento de tamanho de buffer somente se você definir um tamanho de buffer inicial muito pequeno, por exemplo, 10 bytes.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-519">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="6a6b8-520">Se você definir o tamanho do buffer inicial como 10, as `Console.WriteLine` instruções ilustrarão a causa e o efeito do tamanho do buffer aumentará.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-520">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="6a6b8-521">No tamanho do buffer inicial de 4 KB, o JSON de exemplo inteiro é mostrado por cada um `Console.WriteLine` , e o tamanho do buffer nunca precisa ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-521">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="6a6b8-522">O exemplo anterior não define nenhum limite quanto ao tamanho do buffer pode crescer.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-522">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="6a6b8-523">Se o tamanho do token for muito grande, o código poderá falhar com uma <xref:System.OutOfMemoryException> exceção.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-523">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="6a6b8-524">Isso pode acontecer se o JSON contiver um token com cerca de 1 GB ou mais de tamanho, porque dobrar o tamanho de 1 GB resulta em um tamanho muito grande para caber em um `int32` buffer.</span><span class="sxs-lookup"><span data-stu-id="6a6b8-524">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6a6b8-525">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="6a6b8-525">Additional resources</span></span>

* [<span data-ttu-id="6a6b8-526">System.Text.Json sobre</span><span class="sxs-lookup"><span data-stu-id="6a6b8-526">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="6a6b8-527">Como gravar conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="6a6b8-527">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="6a6b8-528">Como migrar do Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="6a6b8-528">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="6a6b8-529">Suporte a DateTime e DateTimeOffset em System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="6a6b8-529">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="6a6b8-530">[System.Text.Json Referência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6a6b8-530">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
