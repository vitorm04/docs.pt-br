---
title: Como escrever conversores personalizados para serialização JSON-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 0f8b89ec7d7b1677de085631958b888e154aa4fa
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116716"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="45094-102">Como escrever conversores personalizados para serialização JSON (Marshalling) no .NET</span><span class="sxs-lookup"><span data-stu-id="45094-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="45094-103">Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no namespace <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="45094-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="45094-104">Para obter uma introdução ao `System.Text.Json`, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="45094-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="45094-105">Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="45094-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="45094-106">O namespace `System.Text.Json` tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivos JavaScript.</span><span class="sxs-lookup"><span data-stu-id="45094-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="45094-107">Você pode escrever conversores personalizados:</span><span class="sxs-lookup"><span data-stu-id="45094-107">You can write custom converters:</span></span>

* <span data-ttu-id="45094-108">Para substituir o comportamento padrão de um conversor interno.</span><span class="sxs-lookup"><span data-stu-id="45094-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="45094-109">Por exemplo, talvez você queira `DateTime` valores a serem representados pelo formato mm/dd/aaaa em vez do formato ISO 8601-1:2019 padrão.</span><span class="sxs-lookup"><span data-stu-id="45094-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="45094-110">Para dar suporte a um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="45094-110">To support a custom value type.</span></span> <span data-ttu-id="45094-111">Por exemplo, um struct `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="45094-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="45094-112">Você também pode escrever conversores personalizados para personalizar ou estender `System.Text.Json` com funcionalidade não incluída na versão atual.</span><span class="sxs-lookup"><span data-stu-id="45094-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="45094-113">Os cenários a seguir serão abordados posteriormente neste artigo:</span><span class="sxs-lookup"><span data-stu-id="45094-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="45094-114">[Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="45094-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="45094-115">[Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="45094-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="45094-116">[Suporte à desserialização polimórfico](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="45094-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="45094-117">Padrões de conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="45094-117">Custom converter patterns</span></span>

<span data-ttu-id="45094-118">Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="45094-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="45094-119">O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="45094-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="45094-120">O padrão básico é para tipos genéricos não genéricos e fechados.</span><span class="sxs-lookup"><span data-stu-id="45094-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="45094-121">Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="45094-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="45094-122">Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:</span><span class="sxs-lookup"><span data-stu-id="45094-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="45094-123">O padrão básico cria uma classe que pode manipular um tipo.</span><span class="sxs-lookup"><span data-stu-id="45094-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="45094-124">O padrão de fábrica cria uma classe que determina no tempo de execução qual tipo específico é necessário e cria dinamicamente o conversor apropriado.</span><span class="sxs-lookup"><span data-stu-id="45094-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="45094-125">Conversor básico de exemplo</span><span class="sxs-lookup"><span data-stu-id="45094-125">Sample basic converter</span></span>

<span data-ttu-id="45094-126">O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente.</span><span class="sxs-lookup"><span data-stu-id="45094-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="45094-127">O conversor usa o formato mm/dd/aaaa para propriedades de `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="45094-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="45094-128">Conversor de padrão de fábrica de exemplo</span><span class="sxs-lookup"><span data-stu-id="45094-128">Sample factory pattern converter</span></span>

<span data-ttu-id="45094-129">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="45094-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="45094-130">O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto.</span><span class="sxs-lookup"><span data-stu-id="45094-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="45094-131">O método `CanConvert` retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um tipo `Enum`.</span><span class="sxs-lookup"><span data-stu-id="45094-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="45094-132">O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue`.</span><span class="sxs-lookup"><span data-stu-id="45094-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="45094-133">O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="45094-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="45094-134">Etapas para seguir o padrão básico</span><span class="sxs-lookup"><span data-stu-id="45094-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="45094-135">As etapas a seguir explicam como criar um conversor seguindo o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="45094-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="45094-136">Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.</span><span class="sxs-lookup"><span data-stu-id="45094-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="45094-137">Substitua o método `Read` para desserializar o JSON de entrada e convertê-lo no tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="45094-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="45094-138">Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.</span><span class="sxs-lookup"><span data-stu-id="45094-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="45094-139">Substitua o método `Write` para serializar o objeto de entrada do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="45094-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="45094-140">Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="45094-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="45094-141">Substitua o método `CanConvert` somente se necessário.</span><span class="sxs-lookup"><span data-stu-id="45094-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="45094-142">A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="45094-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="45094-143">Portanto, os conversores que dão suporte apenas ao tipo `T` não precisam substituir esse método.</span><span class="sxs-lookup"><span data-stu-id="45094-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="45094-144">Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="45094-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="45094-145">Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="45094-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="45094-146">Etapas para seguir o padrão de fábrica</span><span class="sxs-lookup"><span data-stu-id="45094-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="45094-147">As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="45094-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="45094-148">Crie uma classe derivada de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="45094-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="45094-149">Substitua o método `CanConvert` para retornar true quando o tipo a ser convertido for aquele que o conversor possa manipular.</span><span class="sxs-lookup"><span data-stu-id="45094-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="45094-150">Por exemplo, se o conversor for para `List<T>` ele pode manipular apenas `List<int>`, `List<string>`e `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="45094-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="45094-151">Substitua o método `CreateConverter` para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45094-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="45094-152">Crie a classe de conversor que o método de `CreateConverter` instancia.</span><span class="sxs-lookup"><span data-stu-id="45094-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="45094-153">O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="45094-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="45094-154">Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="45094-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="45094-155">O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="45094-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="45094-156">O tipo de `Enum` é semelhante a um tipo genérico aberto: um conversor para `Enum` tem que criar um conversor para um `Enum` específico (`WeekdaysEnum`, por exemplo) nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="45094-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="45094-157">Manipulação de erros</span><span class="sxs-lookup"><span data-stu-id="45094-157">Error handling</span></span>

<span data-ttu-id="45094-158">Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="45094-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="45094-159">Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="45094-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="45094-160">Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="45094-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="45094-161">Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred")`, a exceção ainda fornecerá o caminho na propriedade <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="45094-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="45094-162">Registrar um conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="45094-162">Register a custom converter</span></span>

<span data-ttu-id="45094-163">*Registre* um conversor personalizado para fazer com que os métodos `Serialize` e `Deserialize` o usem.</span><span class="sxs-lookup"><span data-stu-id="45094-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="45094-164">Escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="45094-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="45094-165">Adicione uma instância da classe converter à coleção de <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45094-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="45094-166">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="45094-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="45094-167">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="45094-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="45094-168">Amostra de registro – coleção de conversores</span><span class="sxs-lookup"><span data-stu-id="45094-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="45094-169">Veja um exemplo que torna o <xref:System.ComponentModel.DateTimeOffsetConverter> o padrão para propriedades do tipo <xref:System.DateTimeOffset>:</span><span class="sxs-lookup"><span data-stu-id="45094-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="45094-170">Suponha que você Serialize uma instância do seguinte tipo:</span><span class="sxs-lookup"><span data-stu-id="45094-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="45094-171">Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:</span><span class="sxs-lookup"><span data-stu-id="45094-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="45094-172">O código a seguir usa a mesma abordagem para desserializar usando o conversor de `DateTimeOffset` personalizado:</span><span class="sxs-lookup"><span data-stu-id="45094-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="45094-173">Exemplo de registro-[Jsonconverter] em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="45094-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="45094-174">O código a seguir seleciona um conversor personalizado para a propriedade `Date`:</span><span class="sxs-lookup"><span data-stu-id="45094-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="45094-175">O código para serializar `WeatherForecastWithConverterAttribute` não requer o uso de `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="45094-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="45094-176">O código para desserializar também não requer o uso de `Converters`:</span><span class="sxs-lookup"><span data-stu-id="45094-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="45094-177">Exemplo de registro-[Jsonconverter] em um tipo</span><span class="sxs-lookup"><span data-stu-id="45094-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="45094-178">Aqui está o código que cria um struct e aplica o atributo `[JsonConverter]` a ele:</span><span class="sxs-lookup"><span data-stu-id="45094-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="45094-179">Este é o conversor personalizado para o struct anterior:</span><span class="sxs-lookup"><span data-stu-id="45094-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="45094-180">O atributo `[JsonConvert]` na struct registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="45094-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="45094-181">O conversor é usado automaticamente na propriedade `TemperatureCelsius` do seguinte tipo ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="45094-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="45094-182">Precedência de registro do conversor</span><span class="sxs-lookup"><span data-stu-id="45094-182">Converter registration precedence</span></span>

<span data-ttu-id="45094-183">Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="45094-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="45094-184">`[JsonConverter]` aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="45094-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="45094-185">Um conversor adicionado à coleção de `Converters`.</span><span class="sxs-lookup"><span data-stu-id="45094-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="45094-186">`[JsonConverter]` aplicado a um tipo de valor personalizado ou POCO.</span><span class="sxs-lookup"><span data-stu-id="45094-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="45094-187">Se vários conversores personalizados para um tipo forem registrados na coleção de `Converters`, o primeiro conversor que retorna true para `CanConvert` será usado.</span><span class="sxs-lookup"><span data-stu-id="45094-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="45094-188">Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.</span><span class="sxs-lookup"><span data-stu-id="45094-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="45094-189">Exemplos de conversor para cenários comuns</span><span class="sxs-lookup"><span data-stu-id="45094-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="45094-190">As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.</span><span class="sxs-lookup"><span data-stu-id="45094-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="45094-191">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="45094-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="45094-192">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="45094-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="45094-193">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="45094-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="45094-194">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="45094-194">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="45094-195">Ao desserializar para uma propriedade do tipo `object`, um objeto `JsonElement` é criado.</span><span class="sxs-lookup"><span data-stu-id="45094-195">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="45094-196">O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar.</span><span class="sxs-lookup"><span data-stu-id="45094-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="45094-197">Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é um `Boolean`e, se um elemento tiver "01/01/2019", o desserializador não inferirá que se trata de um `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="45094-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="45094-198">A inferência de tipos pode ser imprecisa.</span><span class="sxs-lookup"><span data-stu-id="45094-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="45094-199">Se o desserializador analisar um número JSON que não tenha um ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="45094-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="45094-200">A análise de um número que tenha um ponto decimal como um `double` poderá perder a precisão se o número tiver sido originalmente serializado como um `decimal`.</span><span class="sxs-lookup"><span data-stu-id="45094-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="45094-201">Para cenários que exigem inferência de tipos, o código a seguir mostra um conversor personalizado para propriedades de `object`.</span><span class="sxs-lookup"><span data-stu-id="45094-201">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="45094-202">O código converte:</span><span class="sxs-lookup"><span data-stu-id="45094-202">The code converts:</span></span>

* <span data-ttu-id="45094-203">`true` e `false` para `Boolean`</span><span class="sxs-lookup"><span data-stu-id="45094-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="45094-204">Números sem um decimal para `long`</span><span class="sxs-lookup"><span data-stu-id="45094-204">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="45094-205">Números com um decimal para `double`</span><span class="sxs-lookup"><span data-stu-id="45094-205">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="45094-206">Datas para `DateTime`</span><span class="sxs-lookup"><span data-stu-id="45094-206">Dates to `DateTime`</span></span>
* <span data-ttu-id="45094-207">Cadeias de caracteres para `string`</span><span class="sxs-lookup"><span data-stu-id="45094-207">Strings to `string`</span></span>
* <span data-ttu-id="45094-208">Tudo o mais a ser `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="45094-208">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="45094-209">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="45094-209">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="45094-210">Aqui está um tipo de exemplo com propriedades de `object`:</span><span class="sxs-lookup"><span data-stu-id="45094-210">Here's an example type with `object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="45094-211">O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:</span><span class="sxs-lookup"><span data-stu-id="45094-211">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="45094-212">Sem o conversor personalizado, a desserialização coloca uma `JsonElement` em cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="45094-212">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="45094-213">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam a desserialização para `object` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="45094-213">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="45094-214">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="45094-214">Support Dictionary with non-string key</span></span>

<span data-ttu-id="45094-215">O suporte interno para coleções de dicionários é para `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="45094-215">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="45094-216">Ou seja, a chave deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="45094-216">That is, the key must be a string.</span></span> <span data-ttu-id="45094-217">Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="45094-217">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="45094-218">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="45094-218">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="45094-219">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="45094-219">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="45094-220">O conversor pode serializar e desserializar a propriedade `TemperatureRanges` da seguinte classe que usa os seguintes `Enum`:</span><span class="sxs-lookup"><span data-stu-id="45094-220">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="45094-221">A saída JSON da serialização é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="45094-221">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="45094-222">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="45094-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="45094-223">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="45094-223">Support polymorphic deserialization</span></span>

<span data-ttu-id="45094-224">Os recursos internos fornecem um intervalo limitado de [serialização polimórfico](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mas não há suporte para desserialização.</span><span class="sxs-lookup"><span data-stu-id="45094-224">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="45094-225">A desserialização requer um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="45094-225">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="45094-226">Suponha, por exemplo, que você tenha uma classe base abstrata `Person`, com `Employee` e `Customer` classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="45094-226">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="45094-227">A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` e `Employee` objetos no JSON são corretamente desserializados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45094-227">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="45094-228">Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON.</span><span class="sxs-lookup"><span data-stu-id="45094-228">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="45094-229">Os tipos de pistas disponíveis variam de acordo com cada cenário.</span><span class="sxs-lookup"><span data-stu-id="45094-229">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="45094-230">Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="45094-230">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="45094-231">A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="45094-231">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="45094-232">O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas.</span><span class="sxs-lookup"><span data-stu-id="45094-232">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="45094-233">O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica.</span><span class="sxs-lookup"><span data-stu-id="45094-233">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="45094-234">O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="45094-234">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="45094-235">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="45094-235">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="45094-236">O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="45094-236">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="45094-237">O código do conversor no exemplo anterior lê e grava cada propriedade manualmente.</span><span class="sxs-lookup"><span data-stu-id="45094-237">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="45094-238">Uma alternativa é chamar `Deserialize` ou `Serialize` fazer parte do trabalho.</span><span class="sxs-lookup"><span data-stu-id="45094-238">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="45094-239">Para obter um exemplo, consulte [esta postagem de StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="45094-239">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

## <a name="other-custom-converter-samples"></a><span data-ttu-id="45094-240">Outras amostras de conversor personalizadas</span><span class="sxs-lookup"><span data-stu-id="45094-240">Other custom converter samples</span></span>

<span data-ttu-id="45094-241">O artigo [migrar do Newtonsoft. JSON para System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md) contém exemplos adicionais de conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="45094-241">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="45094-242">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no código-fonte `System.Text.Json.Serialization` inclui outras amostras de conversores personalizados, como:</span><span class="sxs-lookup"><span data-stu-id="45094-242">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* [<span data-ttu-id="45094-243">Conversor de Int32 que converte NULL para 0 em desserializar</span><span class="sxs-lookup"><span data-stu-id="45094-243">Int32 converter that converts null to 0 on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [<span data-ttu-id="45094-244">Conversor de Int32 que permite valores de cadeia de caracteres e de número na desserialização</span><span class="sxs-lookup"><span data-stu-id="45094-244">Int32 converter that allows both string and number values on deserialize</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [<span data-ttu-id="45094-245">Conversor de enumeração</span><span class="sxs-lookup"><span data-stu-id="45094-245">Enum converter</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [<span data-ttu-id="45094-246">List\<T > converter que aceita dados externos</span><span class="sxs-lookup"><span data-stu-id="45094-246">List\<T> converter that accepts external data</span></span>](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* <span data-ttu-id="45094-247">[Conversor Long [] que funciona com uma lista de números delimitada por vírgulas](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="45094-247">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span> 

<span data-ttu-id="45094-248">Se você precisar criar um conversor que modifique o comportamento de um conversor interno existente, poderá obter [o código-fonte do conversor existente](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) para servir como ponto de partida para personalização.</span><span class="sxs-lookup"><span data-stu-id="45094-248">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="45094-249">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="45094-249">Additional resources</span></span>

* [<span data-ttu-id="45094-250">Código-fonte para conversores internos</span><span class="sxs-lookup"><span data-stu-id="45094-250">Source code for built-in converters</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [<span data-ttu-id="45094-251">Suporte a DateTime e DateTimeOffset em System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="45094-251">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="45094-252">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="45094-252">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="45094-253">Como usar System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="45094-253">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="45094-254">Como migrar do Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="45094-254">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="45094-255">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="45094-255">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="45094-256">Referência da API System. Text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="45094-256">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
