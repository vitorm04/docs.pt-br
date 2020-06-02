---
title: Como escrever conversores personalizados para serialização JSON-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: abda23ea538c2c0da6ada4f359ce745602dca45d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279757"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="972f6-102">Como escrever conversores personalizados para serialização JSON (Marshalling) no .NET</span><span class="sxs-lookup"><span data-stu-id="972f6-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="972f6-103">Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no <xref:System.Text.Json> namespace.</span><span class="sxs-lookup"><span data-stu-id="972f6-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="972f6-104">Para obter uma introdução ao `System.Text.Json` , consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="972f6-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="972f6-105">Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="972f6-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="972f6-106">O `System.Text.Json` namespace tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivas de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="972f6-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="972f6-107">Você pode escrever conversores personalizados:</span><span class="sxs-lookup"><span data-stu-id="972f6-107">You can write custom converters:</span></span>

* <span data-ttu-id="972f6-108">Para substituir o comportamento padrão de um conversor interno.</span><span class="sxs-lookup"><span data-stu-id="972f6-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="972f6-109">Por exemplo, talvez você queira que `DateTime` os valores sejam representados pelo formato mm/dd/aaaa em vez do formato padrão ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="972f6-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="972f6-110">Para dar suporte a um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="972f6-110">To support a custom value type.</span></span> <span data-ttu-id="972f6-111">Por exemplo, um `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="972f6-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="972f6-112">Você também pode escrever conversores personalizados para personalizar ou estender `System.Text.Json` com funcionalidade não incluída na versão atual.</span><span class="sxs-lookup"><span data-stu-id="972f6-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="972f6-113">Os cenários a seguir serão abordados posteriormente neste artigo:</span><span class="sxs-lookup"><span data-stu-id="972f6-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="972f6-114">[Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="972f6-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="972f6-115">[Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="972f6-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="972f6-116">[Suporte à desserialização polimórfico](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="972f6-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="972f6-117">[Dar suporte à viagem de ida \<T> e volta para pilha](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="972f6-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="972f6-118">Padrões de conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="972f6-118">Custom converter patterns</span></span>

<span data-ttu-id="972f6-119">Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="972f6-119">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="972f6-120">O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="972f6-120">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="972f6-121">O padrão básico é para tipos genéricos não genéricos e fechados.</span><span class="sxs-lookup"><span data-stu-id="972f6-121">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="972f6-122">Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="972f6-122">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="972f6-123">Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:</span><span class="sxs-lookup"><span data-stu-id="972f6-123">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="972f6-124">O padrão básico cria uma classe que pode manipular um tipo.</span><span class="sxs-lookup"><span data-stu-id="972f6-124">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="972f6-125">O padrão de fábrica cria uma classe que determina, em tempo de execução, qual tipo específico é necessário e cria dinamicamente o conversor apropriado.</span><span class="sxs-lookup"><span data-stu-id="972f6-125">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="972f6-126">Conversor básico de exemplo</span><span class="sxs-lookup"><span data-stu-id="972f6-126">Sample basic converter</span></span>

<span data-ttu-id="972f6-127">O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente.</span><span class="sxs-lookup"><span data-stu-id="972f6-127">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="972f6-128">O conversor usa o formato mm/dd/aaaa para `DateTimeOffset` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="972f6-128">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="972f6-129">Conversor de padrão de fábrica de exemplo</span><span class="sxs-lookup"><span data-stu-id="972f6-129">Sample factory pattern converter</span></span>

<span data-ttu-id="972f6-130">O código a seguir mostra um conversor personalizado que funciona com o `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="972f6-130">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="972f6-131">O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto.</span><span class="sxs-lookup"><span data-stu-id="972f6-131">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="972f6-132">O `CanConvert` método retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="972f6-132">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="972f6-133">O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue` .</span><span class="sxs-lookup"><span data-stu-id="972f6-133">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="972f6-134">O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="972f6-134">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="972f6-135">Etapas para seguir o padrão básico</span><span class="sxs-lookup"><span data-stu-id="972f6-135">Steps to follow the basic pattern</span></span>

<span data-ttu-id="972f6-136">As etapas a seguir explicam como criar um conversor seguindo o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="972f6-136">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="972f6-137">Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.</span><span class="sxs-lookup"><span data-stu-id="972f6-137">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="972f6-138">Substitua o `Read` método para desserializar o JSON de entrada e convertê-lo no tipo `T` .</span><span class="sxs-lookup"><span data-stu-id="972f6-138">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="972f6-139">Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.</span><span class="sxs-lookup"><span data-stu-id="972f6-139">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="972f6-140">Substitua o `Write` método para serializar o objeto de entrada do tipo `T` .</span><span class="sxs-lookup"><span data-stu-id="972f6-140">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="972f6-141">Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="972f6-141">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="972f6-142">Substitua o `CanConvert` método somente se necessário.</span><span class="sxs-lookup"><span data-stu-id="972f6-142">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="972f6-143">A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T` .</span><span class="sxs-lookup"><span data-stu-id="972f6-143">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="972f6-144">Portanto, os conversores que suportam apenas `T` o tipo não precisam substituir esse método.</span><span class="sxs-lookup"><span data-stu-id="972f6-144">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="972f6-145">Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="972f6-145">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="972f6-146">Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="972f6-146">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="972f6-147">Etapas para seguir o padrão de fábrica</span><span class="sxs-lookup"><span data-stu-id="972f6-147">Steps to follow the factory pattern</span></span>

<span data-ttu-id="972f6-148">As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="972f6-148">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="972f6-149">Crie uma classe que deriva de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="972f6-149">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="972f6-150">Substitua o `CanConvert` método para retornar true quando o tipo a ser convertido for aquele que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="972f6-150">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="972f6-151">Por exemplo, se o conversor for para `List<T>` ele, ele só poderá manipular `List<int>` , `List<string>` e `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="972f6-151">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="972f6-152">Substitua o `CreateConverter` método para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="972f6-152">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="972f6-153">Crie a classe de conversor `CreateConverter` instanciada pelo método.</span><span class="sxs-lookup"><span data-stu-id="972f6-153">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="972f6-154">O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="972f6-154">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="972f6-155">Um conversor para um tipo genérico aberto ( `List<T>` , por exemplo) precisa criar um conversor para um tipo genérico fechado ( `List<DateTime>` , por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="972f6-155">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="972f6-156">O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="972f6-156">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="972f6-157">O `Enum` tipo é semelhante a um tipo genérico aberto: um conversor de `Enum` deve criar um conversor para um específico `Enum` ( `WeekdaysEnum` , por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="972f6-157">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="972f6-158">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="972f6-158">Error handling</span></span>

<span data-ttu-id="972f6-159">Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="972f6-159">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="972f6-160">Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="972f6-160">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="972f6-161">Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="972f6-161">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="972f6-162">Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred")` , a exceção ainda fornecerá o caminho na <xref:System.Text.Json.JsonException.Path> propriedade.</span><span class="sxs-lookup"><span data-stu-id="972f6-162">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="972f6-163">Registrar um conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="972f6-163">Register a custom converter</span></span>

<span data-ttu-id="972f6-164">*Registre* um conversor personalizado para fazer com `Serialize` que os métodos e o `Deserialize` usem.</span><span class="sxs-lookup"><span data-stu-id="972f6-164">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="972f6-165">Escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="972f6-165">Choose one of the following approaches:</span></span>

* <span data-ttu-id="972f6-166">Adicione uma instância da classe converter à <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> coleção.</span><span class="sxs-lookup"><span data-stu-id="972f6-166">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="972f6-167">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="972f6-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="972f6-168">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="972f6-168">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="972f6-169">Amostra de registro – coleção de conversores</span><span class="sxs-lookup"><span data-stu-id="972f6-169">Registration sample - Converters collection</span></span>

<span data-ttu-id="972f6-170">Veja um exemplo que torna o <xref:System.ComponentModel.DateTimeOffsetConverter> padrão para propriedades do tipo <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="972f6-170">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="972f6-171">Suponha que você Serialize uma instância do seguinte tipo:</span><span class="sxs-lookup"><span data-stu-id="972f6-171">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="972f6-172">Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:</span><span class="sxs-lookup"><span data-stu-id="972f6-172">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="972f6-173">O código a seguir usa a mesma abordagem para desserializar usando o `DateTimeOffset` conversor personalizado:</span><span class="sxs-lookup"><span data-stu-id="972f6-173">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="972f6-174">Exemplo de registro-[Jsonconverter] em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="972f6-174">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="972f6-175">O código a seguir seleciona um conversor personalizado para a `Date` Propriedade:</span><span class="sxs-lookup"><span data-stu-id="972f6-175">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="972f6-176">O código a ser serializado `WeatherForecastWithConverterAttribute` não exige o uso de `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="972f6-176">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="972f6-177">O código para desserializar também não exige o uso de `Converters` :</span><span class="sxs-lookup"><span data-stu-id="972f6-177">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="972f6-178">Exemplo de registro-[Jsonconverter] em um tipo</span><span class="sxs-lookup"><span data-stu-id="972f6-178">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="972f6-179">Aqui está o código que cria uma struct e aplica o `[JsonConverter]` atributo a ela:</span><span class="sxs-lookup"><span data-stu-id="972f6-179">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="972f6-180">Este é o conversor personalizado para o struct anterior:</span><span class="sxs-lookup"><span data-stu-id="972f6-180">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="972f6-181">O `[JsonConvert]` atributo na estrutura registra o conversor personalizado como o padrão para propriedades do tipo `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="972f6-181">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="972f6-182">O conversor é usado automaticamente na `TemperatureCelsius` Propriedade do seguinte tipo ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="972f6-182">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="972f6-183">Precedência de registro do conversor</span><span class="sxs-lookup"><span data-stu-id="972f6-183">Converter registration precedence</span></span>

<span data-ttu-id="972f6-184">Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="972f6-184">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="972f6-185">`[JsonConverter]`aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="972f6-185">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="972f6-186">Um conversor adicionado à `Converters` coleção.</span><span class="sxs-lookup"><span data-stu-id="972f6-186">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="972f6-187">`[JsonConverter]`aplicado a um tipo de valor personalizado ou POCO.</span><span class="sxs-lookup"><span data-stu-id="972f6-187">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="972f6-188">Se vários conversores personalizados para um tipo forem registrados na `Converters` coleção, o primeiro conversor que retorna true para `CanConvert` será usado.</span><span class="sxs-lookup"><span data-stu-id="972f6-188">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="972f6-189">Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.</span><span class="sxs-lookup"><span data-stu-id="972f6-189">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="972f6-190">Exemplos de conversor para cenários comuns</span><span class="sxs-lookup"><span data-stu-id="972f6-190">Converter samples for common scenarios</span></span>

<span data-ttu-id="972f6-191">As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.</span><span class="sxs-lookup"><span data-stu-id="972f6-191">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="972f6-192">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="972f6-192">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="972f6-193">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="972f6-193">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="972f6-194">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="972f6-194">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)
* <span data-ttu-id="972f6-195">[Dar suporte à viagem de ida \<T> e volta para pilha](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="972f6-195">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="972f6-196">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="972f6-196">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="972f6-197">Ao desserializar para uma propriedade do tipo `object` , um `JsonElement` objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="972f6-197">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="972f6-198">O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar.</span><span class="sxs-lookup"><span data-stu-id="972f6-198">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="972f6-199">Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é a `Boolean` e, se um elemento tiver "01/01/2019", o desserializador não inferirá que é um `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="972f6-199">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="972f6-200">A inferência de tipos pode ser imprecisa.</span><span class="sxs-lookup"><span data-stu-id="972f6-200">Type inference can be inaccurate.</span></span> <span data-ttu-id="972f6-201">Se o desserializador analisar um número JSON que não tenha nenhum ponto decimal como um `long` , isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="972f6-201">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="972f6-202">A análise de um número que tenha um ponto decimal como `double` pode perder a precisão se o número tiver sido originalmente serializado como um `decimal` .</span><span class="sxs-lookup"><span data-stu-id="972f6-202">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="972f6-203">Para cenários que exigem a inferência de tipos, o código a seguir mostra um conversor personalizado para `object` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="972f6-203">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="972f6-204">O código converte:</span><span class="sxs-lookup"><span data-stu-id="972f6-204">The code converts:</span></span>

* <span data-ttu-id="972f6-205">`true`e `false` para`Boolean`</span><span class="sxs-lookup"><span data-stu-id="972f6-205">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="972f6-206">Números sem um decimal para`long`</span><span class="sxs-lookup"><span data-stu-id="972f6-206">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="972f6-207">Números com um decimal para`double`</span><span class="sxs-lookup"><span data-stu-id="972f6-207">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="972f6-208">Datas para`DateTime`</span><span class="sxs-lookup"><span data-stu-id="972f6-208">Dates to `DateTime`</span></span>
* <span data-ttu-id="972f6-209">Cadeias de caracteres para`string`</span><span class="sxs-lookup"><span data-stu-id="972f6-209">Strings to `string`</span></span>
* <span data-ttu-id="972f6-210">Tudo o mais a`JsonElement`</span><span class="sxs-lookup"><span data-stu-id="972f6-210">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="972f6-211">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="972f6-211">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="972f6-212">Aqui está um tipo de exemplo com `object` Propriedades:</span><span class="sxs-lookup"><span data-stu-id="972f6-212">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="972f6-213">O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime` , `long` e `string` :</span><span class="sxs-lookup"><span data-stu-id="972f6-213">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="972f6-214">Sem o conversor personalizado, a desserialização coloca um `JsonElement` em cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="972f6-214">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="972f6-215">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no `System.Text.Json.Serialization` namespace tem mais exemplos de conversores personalizados que manipulam a desserialização para `object` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="972f6-215">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="972f6-216">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="972f6-216">Support Dictionary with non-string key</span></span>

<span data-ttu-id="972f6-217">O suporte interno para coleções de dicionário é para o `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="972f6-217">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="972f6-218">Ou seja, a chave deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="972f6-218">That is, the key must be a string.</span></span> <span data-ttu-id="972f6-219">Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="972f6-219">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="972f6-220">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="972f6-220">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="972f6-221">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="972f6-221">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="972f6-222">O conversor pode serializar e desserializar a `TemperatureRanges` propriedade da seguinte classe que usa o seguinte `Enum` :</span><span class="sxs-lookup"><span data-stu-id="972f6-222">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="972f6-223">A saída JSON da serialização é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="972f6-223">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="972f6-224">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no `System.Text.Json.Serialization` namespace tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="972f6-224">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="972f6-225">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="972f6-225">Support polymorphic deserialization</span></span>

<span data-ttu-id="972f6-226">Os recursos internos fornecem um intervalo limitado de [serialização polimórfico](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mas não há suporte para desserialização.</span><span class="sxs-lookup"><span data-stu-id="972f6-226">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="972f6-227">A desserialização requer um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="972f6-227">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="972f6-228">Suponha, por exemplo, que você tenha uma `Person` classe base abstrata, `Employee` com `Customer` classes derivadas e.</span><span class="sxs-lookup"><span data-stu-id="972f6-228">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="972f6-229">A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` `Employee` os objetos no JSON são corretamente desserializados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="972f6-229">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="972f6-230">Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON.</span><span class="sxs-lookup"><span data-stu-id="972f6-230">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="972f6-231">Os tipos de pistas disponíveis variam de acordo com cada cenário.</span><span class="sxs-lookup"><span data-stu-id="972f6-231">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="972f6-232">Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="972f6-232">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="972f6-233">A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="972f6-233">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="972f6-234">O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas.</span><span class="sxs-lookup"><span data-stu-id="972f6-234">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="972f6-235">O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica.</span><span class="sxs-lookup"><span data-stu-id="972f6-235">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="972f6-236">O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="972f6-236">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="972f6-237">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="972f6-237">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="972f6-238">O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="972f6-238">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="972f6-239">O código do conversor no exemplo anterior lê e grava cada propriedade manualmente.</span><span class="sxs-lookup"><span data-stu-id="972f6-239">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="972f6-240">Uma alternativa é chamar `Deserialize` ou `Serialize` fazer parte do trabalho.</span><span class="sxs-lookup"><span data-stu-id="972f6-240">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="972f6-241">Para obter um exemplo, consulte [esta postagem de StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="972f6-241">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="972f6-242">Dar suporte à viagem de ida e volta para pilha\<T></span><span class="sxs-lookup"><span data-stu-id="972f6-242">Support round-trip for Stack\<T></span></span>

<span data-ttu-id="972f6-243">Se você desserializar uma cadeia de caracteres JSON em um <xref:System.Collections.Generic.Stack%601> objeto e, em seguida, serializar esse objeto, o conteúdo da pilha estará na ordem inversa.</span><span class="sxs-lookup"><span data-stu-id="972f6-243">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="972f6-244">Esse comportamento se aplica aos tipos e à interface a seguir e aos tipos definidos pelo usuário que derivam deles:</span><span class="sxs-lookup"><span data-stu-id="972f6-244">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="972f6-245">Para dar suporte à serialização e desserialização que retém o pedido original na pilha, é necessário um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="972f6-245">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="972f6-246">O código a seguir mostra um conversor personalizado que permite a passagem de ida e volta de `Stack<T>` objetos:</span><span class="sxs-lookup"><span data-stu-id="972f6-246">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="972f6-247">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="972f6-247">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a><span data-ttu-id="972f6-248">Outras amostras de conversor personalizadas</span><span class="sxs-lookup"><span data-stu-id="972f6-248">Other custom converter samples</span></span>

<span data-ttu-id="972f6-249">O artigo [migrar de Newtonsoft.Json para System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) contém exemplos adicionais de conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="972f6-249">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="972f6-250">A [pasta de testes de unidade](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) no `System.Text.Json.Serialization` código-fonte inclui outras amostras de conversores personalizadas, como:</span><span class="sxs-lookup"><span data-stu-id="972f6-250">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="972f6-251">[Conversor de Int32 que converte NULL para 0 em desserializar](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="972f6-251">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="972f6-252">[Conversor de Int32 que permite valores de cadeia de caracteres e de número na desserialização](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="972f6-252">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="972f6-253">[Conversor de enumeração](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="972f6-253">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="972f6-254">[\<T>Conversor de lista que aceita dados externos](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="972f6-254">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="972f6-255">[Conversor Long [] que funciona com uma lista de números delimitada por vírgulas](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="972f6-255">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="972f6-256">Se você precisar criar um conversor que modifique o comportamento de um conversor interno existente, poderá obter [o código-fonte do conversor existente](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) para servir como ponto de partida para personalização.</span><span class="sxs-lookup"><span data-stu-id="972f6-256">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="972f6-257">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="972f6-257">Additional resources</span></span>

* <span data-ttu-id="972f6-258">[Código-fonte para conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="972f6-258">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* <span data-ttu-id="972f6-259">[Suporte a DateTime e DateTimeOffset emSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="972f6-259">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="972f6-260">[System.Text.Jsonsobre](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="972f6-260">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* <span data-ttu-id="972f6-261">[Como usarSystem.Text.Json](system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="972f6-261">[How to use System.Text.Json](system-text-json-how-to.md)</span></span>
* <span data-ttu-id="972f6-262">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="972f6-262">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="972f6-263">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="972f6-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="972f6-264">[System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="972f6-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
