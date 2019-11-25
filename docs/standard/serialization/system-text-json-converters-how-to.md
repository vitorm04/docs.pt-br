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
ms.openlocfilehash: 33d1cd7764e71d9e2fa382c9f3c5feb77e8defb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283344"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="25c61-102">Como escrever conversores personalizados para serialização JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="25c61-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="25c61-103">Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no namespace <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="25c61-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="25c61-104">Para obter uma introdução ao `System.Text.Json`, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="25c61-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="25c61-105">Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="25c61-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="25c61-106">O namespace `System.Text.Json` tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivos JavaScript.</span><span class="sxs-lookup"><span data-stu-id="25c61-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="25c61-107">Você pode escrever conversores personalizados:</span><span class="sxs-lookup"><span data-stu-id="25c61-107">You can write custom converters:</span></span>

* <span data-ttu-id="25c61-108">Para substituir o comportamento padrão de um conversor interno.</span><span class="sxs-lookup"><span data-stu-id="25c61-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="25c61-109">Por exemplo, talvez você queira `DateTime` valores a serem representados pelo formato mm/dd/aaaa em vez do formato ISO 8601-1:2019 padrão.</span><span class="sxs-lookup"><span data-stu-id="25c61-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="25c61-110">Para dar suporte a um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="25c61-110">To support a custom value type.</span></span> <span data-ttu-id="25c61-111">Por exemplo, um struct `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="25c61-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="25c61-112">Você também pode escrever conversores personalizados para estender `System.Text.Json` com funcionalidade não incluída na versão atual.</span><span class="sxs-lookup"><span data-stu-id="25c61-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="25c61-113">Os cenários a seguir serão abordados posteriormente neste artigo:</span><span class="sxs-lookup"><span data-stu-id="25c61-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="25c61-114">[Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="25c61-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="25c61-115">[Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="25c61-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="25c61-116">[Suporte à desserialização polimórfico](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="25c61-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="25c61-117">Padrões de conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="25c61-117">Custom converter patterns</span></span>

<span data-ttu-id="25c61-118">Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="25c61-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="25c61-119">O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="25c61-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="25c61-120">O padrão básico é para tipos genéricos não genéricos e fechados.</span><span class="sxs-lookup"><span data-stu-id="25c61-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="25c61-121">Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="25c61-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="25c61-122">Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:</span><span class="sxs-lookup"><span data-stu-id="25c61-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="25c61-123">O padrão básico cria uma classe que pode manipular um tipo.</span><span class="sxs-lookup"><span data-stu-id="25c61-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="25c61-124">O padrão de fábrica cria uma classe que determina no tempo de execução qual tipo específico é necessário e cria dinamicamente o conversor apropriado.</span><span class="sxs-lookup"><span data-stu-id="25c61-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="25c61-125">Conversor básico de exemplo</span><span class="sxs-lookup"><span data-stu-id="25c61-125">Sample basic converter</span></span>

<span data-ttu-id="25c61-126">O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente.</span><span class="sxs-lookup"><span data-stu-id="25c61-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="25c61-127">O conversor usa o formato mm/dd/aaaa para propriedades de `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="25c61-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="25c61-128">Conversor de padrão de fábrica de exemplo</span><span class="sxs-lookup"><span data-stu-id="25c61-128">Sample factory pattern converter</span></span>

<span data-ttu-id="25c61-129">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="25c61-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="25c61-130">O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto.</span><span class="sxs-lookup"><span data-stu-id="25c61-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="25c61-131">O método `CanConvert` retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um tipo `Enum`.</span><span class="sxs-lookup"><span data-stu-id="25c61-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="25c61-132">O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue`.</span><span class="sxs-lookup"><span data-stu-id="25c61-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="25c61-133">O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="25c61-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="25c61-134">Etapas para seguir o padrão básico</span><span class="sxs-lookup"><span data-stu-id="25c61-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="25c61-135">As etapas a seguir explicam como criar um conversor seguindo o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="25c61-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="25c61-136">Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.</span><span class="sxs-lookup"><span data-stu-id="25c61-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="25c61-137">Substitua o método `Read` para desserializar o JSON de entrada e convertê-lo no tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="25c61-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="25c61-138">Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.</span><span class="sxs-lookup"><span data-stu-id="25c61-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="25c61-139">Substitua o método `Write` para serializar o objeto de entrada do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="25c61-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="25c61-140">Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="25c61-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="25c61-141">Substitua o método `CanConvert` somente se necessário.</span><span class="sxs-lookup"><span data-stu-id="25c61-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="25c61-142">A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="25c61-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="25c61-143">Portanto, os conversores que dão suporte apenas ao tipo `T` não precisam substituir esse método.</span><span class="sxs-lookup"><span data-stu-id="25c61-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="25c61-144">Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="25c61-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="25c61-145">Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="25c61-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="25c61-146">Etapas para seguir o padrão de fábrica</span><span class="sxs-lookup"><span data-stu-id="25c61-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="25c61-147">As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="25c61-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="25c61-148">Crie uma classe que deriva de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="25c61-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="25c61-149">Substitua o método `CanConvert` para retornar true quando o tipo a ser convertido for aquele que o conversor possa manipular.</span><span class="sxs-lookup"><span data-stu-id="25c61-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="25c61-150">Por exemplo, se o conversor for para `List<T>` ele pode manipular apenas `List<int>`, `List<string>`e `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="25c61-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="25c61-151">Substitua o método `CreateConverter` para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25c61-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="25c61-152">Crie a classe de conversor que o método de `CreateConverter` instancia.</span><span class="sxs-lookup"><span data-stu-id="25c61-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="25c61-153">O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="25c61-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="25c61-154">Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="25c61-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="25c61-155">O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="25c61-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="25c61-156">O tipo de `Enum` é semelhante a um tipo genérico aberto: um conversor para `Enum` tem que criar um conversor para um `Enum` específico (`WeekdaysEnum`, por exemplo) nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="25c61-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="25c61-157">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="25c61-157">Error handling</span></span>

<span data-ttu-id="25c61-158">Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="25c61-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="25c61-159">Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="25c61-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="25c61-160">Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="25c61-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="25c61-161">Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred")`, a exceção ainda fornecerá o caminho na propriedade <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="25c61-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="25c61-162">Registrar um conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="25c61-162">Register a custom converter</span></span>

<span data-ttu-id="25c61-163">*Registre* um conversor personalizado para fazer com que os métodos `Serialize` e `Deserialize` o usem.</span><span class="sxs-lookup"><span data-stu-id="25c61-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="25c61-164">Escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="25c61-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="25c61-165">Adicione uma instância da classe converter à coleção de <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25c61-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="25c61-166">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="25c61-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="25c61-167">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="25c61-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="25c61-168">Amostra de registro – coleção de conversores</span><span class="sxs-lookup"><span data-stu-id="25c61-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="25c61-169">Veja um exemplo que torna o <xref:System.ComponentModel.DateTimeOffsetConverter> o padrão para propriedades do tipo <xref:System.DateTimeOffset>:</span><span class="sxs-lookup"><span data-stu-id="25c61-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="25c61-170">Suponha que você Serialize uma instância do seguinte tipo:</span><span class="sxs-lookup"><span data-stu-id="25c61-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="25c61-171">Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:</span><span class="sxs-lookup"><span data-stu-id="25c61-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="25c61-172">O código a seguir usa a mesma abordagem para desserializar usando o conversor de `DateTimeOffset` personalizado:</span><span class="sxs-lookup"><span data-stu-id="25c61-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="25c61-173">Exemplo de registro-[Jsonconverter] em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="25c61-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="25c61-174">O código a seguir seleciona um conversor personalizado para a propriedade `Date`:</span><span class="sxs-lookup"><span data-stu-id="25c61-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="25c61-175">O código para serializar `WeatherForecastWithConverterAttribute` não requer o uso de `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="25c61-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="25c61-176">O código para desserializar também não requer o uso de `Converters`:</span><span class="sxs-lookup"><span data-stu-id="25c61-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="25c61-177">Exemplo de registro-[Jsonconverter] em um tipo</span><span class="sxs-lookup"><span data-stu-id="25c61-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="25c61-178">Aqui está o código que cria um struct e aplica o atributo `[JsonConverter]` a ele:</span><span class="sxs-lookup"><span data-stu-id="25c61-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="25c61-179">Este é o conversor personalizado para o struct anterior:</span><span class="sxs-lookup"><span data-stu-id="25c61-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="25c61-180">O atributo `[JsonConvert]` na struct registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="25c61-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="25c61-181">O conversor é usado automaticamente na propriedade `TemperatureCelsius` do seguinte tipo ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="25c61-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="25c61-182">Precedência de registro do conversor</span><span class="sxs-lookup"><span data-stu-id="25c61-182">Converter registration precedence</span></span>

<span data-ttu-id="25c61-183">Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="25c61-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="25c61-184">`[JsonConverter]` aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="25c61-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="25c61-185">Um conversor adicionado à coleção de `Converters`.</span><span class="sxs-lookup"><span data-stu-id="25c61-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="25c61-186">`[JsonConverter]` aplicado a um tipo de valor personalizado ou POCO.</span><span class="sxs-lookup"><span data-stu-id="25c61-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="25c61-187">Se vários conversores personalizados para um tipo forem registrados na coleção de `Converters`, o primeiro conversor que retorna true para `CanConvert` será usado.</span><span class="sxs-lookup"><span data-stu-id="25c61-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="25c61-188">Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.</span><span class="sxs-lookup"><span data-stu-id="25c61-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="25c61-189">Exemplos de conversor para cenários comuns</span><span class="sxs-lookup"><span data-stu-id="25c61-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="25c61-190">As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.</span><span class="sxs-lookup"><span data-stu-id="25c61-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="25c61-191">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="25c61-191">Deserialize inferred types to Object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="25c61-192">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25c61-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="25c61-193">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="25c61-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="25c61-194">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="25c61-194">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="25c61-195">Ao desserializar para uma propriedade do tipo `Object`, um objeto `JsonElement` é criado.</span><span class="sxs-lookup"><span data-stu-id="25c61-195">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="25c61-196">O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar.</span><span class="sxs-lookup"><span data-stu-id="25c61-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="25c61-197">Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é um `Boolean`e, se um elemento tiver "01/01/2019", o desserializador não inferirá que se trata de um `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="25c61-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="25c61-198">A inferência de tipos pode ser imprecisa.</span><span class="sxs-lookup"><span data-stu-id="25c61-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="25c61-199">Se o desserializador analisar um número JSON que não tenha um ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="25c61-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="25c61-200">A análise de um número que tenha um ponto decimal como um `double` poderá perder a precisão se o número tiver sido originalmente serializado como um `decimal`.</span><span class="sxs-lookup"><span data-stu-id="25c61-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="25c61-201">Para cenários que exigem inferência de tipos, o código a seguir mostra um conversor personalizado para propriedades de `Object`.</span><span class="sxs-lookup"><span data-stu-id="25c61-201">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="25c61-202">O código converte:</span><span class="sxs-lookup"><span data-stu-id="25c61-202">The code converts:</span></span>

* <span data-ttu-id="25c61-203">`true` e `false` para `Boolean`</span><span class="sxs-lookup"><span data-stu-id="25c61-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="25c61-204">Números para `long` ou `double`</span><span class="sxs-lookup"><span data-stu-id="25c61-204">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="25c61-205">Datas para `DateTime`</span><span class="sxs-lookup"><span data-stu-id="25c61-205">Dates to `DateTime`</span></span>
* <span data-ttu-id="25c61-206">Cadeias de caracteres para `string`</span><span class="sxs-lookup"><span data-stu-id="25c61-206">Strings to `string`</span></span>
* <span data-ttu-id="25c61-207">Tudo o mais a ser `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="25c61-207">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="25c61-208">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="25c61-208">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="25c61-209">Aqui está um tipo de exemplo com propriedades de `Object`:</span><span class="sxs-lookup"><span data-stu-id="25c61-209">Here's an example type with `Object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="25c61-210">O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:</span><span class="sxs-lookup"><span data-stu-id="25c61-210">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="25c61-211">Sem o conversor personalizado, a desserialização coloca uma `JsonElement` em cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="25c61-211">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="25c61-212">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam a desserialização nas propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="25c61-212">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="25c61-213">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25c61-213">Support Dictionary with non-string key</span></span>

<span data-ttu-id="25c61-214">O suporte interno para coleções de dicionários é para `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="25c61-214">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="25c61-215">Ou seja, a chave deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25c61-215">That is, the key must be a string.</span></span> <span data-ttu-id="25c61-216">Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="25c61-216">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="25c61-217">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="25c61-217">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="25c61-218">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="25c61-218">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="25c61-219">O conversor pode serializar e desserializar a propriedade `TemperatureRanges` da seguinte classe que usa os seguintes `Enum`:</span><span class="sxs-lookup"><span data-stu-id="25c61-219">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="25c61-220">A saída JSON da serialização é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="25c61-220">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="25c61-221">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25c61-221">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="25c61-222">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="25c61-222">Support polymorphic deserialization</span></span>

<span data-ttu-id="25c61-223">A [serialização polimórfica](system-text-json-how-to.md#serialize-properties-of-derived-classes) não requer um conversor personalizado, mas a desserialização requer um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="25c61-223">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="25c61-224">Suponha, por exemplo, que você tenha uma classe base abstrata `Person`, com `Employee` e `Customer` classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="25c61-224">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="25c61-225">A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` e `Employee` objetos no JSON são corretamente desserializados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25c61-225">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="25c61-226">Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON.</span><span class="sxs-lookup"><span data-stu-id="25c61-226">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="25c61-227">Os tipos de pistas disponíveis variam de acordo com cada cenário.</span><span class="sxs-lookup"><span data-stu-id="25c61-227">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="25c61-228">Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="25c61-228">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="25c61-229">A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="25c61-229">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="25c61-230">O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas.</span><span class="sxs-lookup"><span data-stu-id="25c61-230">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="25c61-231">O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica.</span><span class="sxs-lookup"><span data-stu-id="25c61-231">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="25c61-232">O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="25c61-232">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="25c61-233">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="25c61-233">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="25c61-234">O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="25c61-234">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="25c61-235">Outras amostras de conversor personalizadas</span><span class="sxs-lookup"><span data-stu-id="25c61-235">Other custom converter samples</span></span>

<span data-ttu-id="25c61-236">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no código-fonte `System.Text.Json.Serialization` inclui outras amostras de conversores personalizados, como:</span><span class="sxs-lookup"><span data-stu-id="25c61-236">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="25c61-237">`Int32` o conversor que converte NULL em 0 em desserializar</span><span class="sxs-lookup"><span data-stu-id="25c61-237">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="25c61-238">`Int32` conversor que permite valores de cadeia de caracteres e de número na desserialização</span><span class="sxs-lookup"><span data-stu-id="25c61-238">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="25c61-239">conversor de `Enum`</span><span class="sxs-lookup"><span data-stu-id="25c61-239">`Enum` converter</span></span>
* <span data-ttu-id="25c61-240">`List<T>` o conversor que aceita dados externos</span><span class="sxs-lookup"><span data-stu-id="25c61-240">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="25c61-241">`Long[]` conversor que funciona com uma lista de números delimitada por vírgulas</span><span class="sxs-lookup"><span data-stu-id="25c61-241">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="25c61-242">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="25c61-242">Additional resources</span></span>

* [<span data-ttu-id="25c61-243">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="25c61-243">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="25c61-244">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="25c61-244">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="25c61-245">Como usar System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="25c61-245">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="25c61-246">Código-fonte para conversores internos</span><span class="sxs-lookup"><span data-stu-id="25c61-246">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="25c61-247">Problemas do GitHub relacionados a conversores personalizados para `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="25c61-247">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="25c61-248">36639 apresentando conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="25c61-248">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="25c61-249">38713 sobre desserialização para objeto</span><span class="sxs-lookup"><span data-stu-id="25c61-249">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="25c61-250">40120 sobre dicionários de chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25c61-250">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="25c61-251">37787 sobre desserialização polimórfica</span><span class="sxs-lookup"><span data-stu-id="25c61-251">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
