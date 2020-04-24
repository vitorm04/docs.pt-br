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
ms.openlocfilehash: 310967f39c3aa7a46d79087bcbf0cb016f7d7284
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159566"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="199f2-102">Como escrever conversores personalizados para serialização JSON (Marshalling) no .NET</span><span class="sxs-lookup"><span data-stu-id="199f2-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="199f2-103">Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no <xref:[!OP.NO-LOC(System.Text.Json)]> namespace.</span><span class="sxs-lookup"><span data-stu-id="199f2-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:[!OP.NO-LOC(System.Text.Json)]> namespace.</span></span> <span data-ttu-id="199f2-104">Para obter uma introdução `[!OP.NO-LOC(System.Text.Json)]`ao, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="199f2-104">For an introduction to `[!OP.NO-LOC(System.Text.Json)]`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="199f2-105">Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="199f2-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="199f2-106">O `[!OP.NO-LOC(System.Text.Json)]` namespace tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivas de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="199f2-106">The `[!OP.NO-LOC(System.Text.Json)]` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="199f2-107">Você pode escrever conversores personalizados:</span><span class="sxs-lookup"><span data-stu-id="199f2-107">You can write custom converters:</span></span>

* <span data-ttu-id="199f2-108">Para substituir o comportamento padrão de um conversor interno.</span><span class="sxs-lookup"><span data-stu-id="199f2-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="199f2-109">Por exemplo, talvez você queira `DateTime` que os valores sejam representados pelo formato mm/dd/aaaa em vez do formato padrão ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="199f2-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="199f2-110">Para dar suporte a um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="199f2-110">To support a custom value type.</span></span> <span data-ttu-id="199f2-111">Por exemplo, um `PhoneNumber` struct.</span><span class="sxs-lookup"><span data-stu-id="199f2-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="199f2-112">Você também pode escrever conversores personalizados para personalizar ou estender `[!OP.NO-LOC(System.Text.Json)]` com funcionalidade não incluída na versão atual.</span><span class="sxs-lookup"><span data-stu-id="199f2-112">You can also write custom converters to customize or extend `[!OP.NO-LOC(System.Text.Json)]` with functionality not included in the current release.</span></span> <span data-ttu-id="199f2-113">Os cenários a seguir serão abordados posteriormente neste artigo:</span><span class="sxs-lookup"><span data-stu-id="199f2-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="199f2-114">[Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="199f2-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="199f2-115">[Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="199f2-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="199f2-116">[Suporte à desserialização polimórfico](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="199f2-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="199f2-117">Padrões de conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="199f2-117">Custom converter patterns</span></span>

<span data-ttu-id="199f2-118">Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="199f2-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="199f2-119">O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="199f2-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="199f2-120">O padrão básico é para tipos genéricos não genéricos e fechados.</span><span class="sxs-lookup"><span data-stu-id="199f2-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="199f2-121">Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="199f2-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="199f2-122">Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:</span><span class="sxs-lookup"><span data-stu-id="199f2-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="199f2-123">O padrão básico cria uma classe que pode manipular um tipo.</span><span class="sxs-lookup"><span data-stu-id="199f2-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="199f2-124">O padrão de fábrica cria uma classe que determina no tempo de execução qual tipo específico é necessário e cria dinamicamente o conversor apropriado.</span><span class="sxs-lookup"><span data-stu-id="199f2-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="199f2-125">Conversor básico de exemplo</span><span class="sxs-lookup"><span data-stu-id="199f2-125">Sample basic converter</span></span>

<span data-ttu-id="199f2-126">O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente.</span><span class="sxs-lookup"><span data-stu-id="199f2-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="199f2-127">O conversor usa o formato mm/dd/aaaa `DateTimeOffset` para propriedades.</span><span class="sxs-lookup"><span data-stu-id="199f2-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="199f2-128">Conversor de padrão de fábrica de exemplo</span><span class="sxs-lookup"><span data-stu-id="199f2-128">Sample factory pattern converter</span></span>

<span data-ttu-id="199f2-129">O código a seguir mostra um conversor personalizado que funciona `Dictionary<Enum,TValue>`com o.</span><span class="sxs-lookup"><span data-stu-id="199f2-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="199f2-130">O código segue o padrão de fábrica porque o primeiro parâmetro de tipo `Enum` genérico é e o segundo é aberto.</span><span class="sxs-lookup"><span data-stu-id="199f2-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="199f2-131">O `CanConvert` método retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="199f2-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="199f2-132">O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de `TValue`execução para.</span><span class="sxs-lookup"><span data-stu-id="199f2-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="199f2-133">O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="199f2-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="199f2-134">Etapas para seguir o padrão básico</span><span class="sxs-lookup"><span data-stu-id="199f2-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="199f2-135">As etapas a seguir explicam como criar um conversor seguindo o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="199f2-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="199f2-136">Crie uma classe que derive de <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.</span><span class="sxs-lookup"><span data-stu-id="199f2-136">Create a class that derives from <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="199f2-137">Substitua o `Read` método para desserializar o JSON de entrada e convertê- `T`lo no tipo.</span><span class="sxs-lookup"><span data-stu-id="199f2-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="199f2-138">Use o <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader> que é passado para o método para ler o JSON.</span><span class="sxs-lookup"><span data-stu-id="199f2-138">Use the <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="199f2-139">Substitua o `Write` método para serializar o objeto de entrada `T`do tipo.</span><span class="sxs-lookup"><span data-stu-id="199f2-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="199f2-140">Use o <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> que é passado para o método para gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="199f2-140">Use the <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="199f2-141">Substitua o `CanConvert` método somente se necessário.</span><span class="sxs-lookup"><span data-stu-id="199f2-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="199f2-142">A implementação padrão retorna `true` quando o tipo a ser convertido é do `T`tipo.</span><span class="sxs-lookup"><span data-stu-id="199f2-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="199f2-143">Portanto, os conversores que suportam apenas o tipo `T` não precisam substituir esse método.</span><span class="sxs-lookup"><span data-stu-id="199f2-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="199f2-144">Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="199f2-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="199f2-145">Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="199f2-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="199f2-146">Etapas para seguir o padrão de fábrica</span><span class="sxs-lookup"><span data-stu-id="199f2-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="199f2-147">As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="199f2-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="199f2-148">Crie uma classe que deriva de <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="199f2-148">Create a class that derives from <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="199f2-149">Substitua o `CanConvert` método para retornar true quando o tipo a ser convertido for aquele que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="199f2-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="199f2-150">Por exemplo, se o conversor for para `List<T>` ele, ele só `List<int>`poderá `List<string>`manipular, `List<DateTime>`e.</span><span class="sxs-lookup"><span data-stu-id="199f2-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="199f2-151">Substitua o `CreateConverter` método para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="199f2-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="199f2-152">Crie a classe de conversor instanciada pelo `CreateConverter` método.</span><span class="sxs-lookup"><span data-stu-id="199f2-152">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="199f2-153">O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="199f2-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="199f2-154">Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="199f2-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="199f2-155">O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="199f2-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="199f2-156">O `Enum` tipo é semelhante a um tipo genérico aberto: um conversor de `Enum` deve criar um conversor para um específico `Enum` (`WeekdaysEnum`, por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="199f2-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="199f2-157">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="199f2-157">Error handling</span></span>

<span data-ttu-id="199f2-158">Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:[!OP.NO-LOC(System.Text.Json)].JsonException> sem uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="199f2-158">If you need to throw an exception in error-handling code, consider throwing a <xref:[!OP.NO-LOC(System.Text.Json)].JsonException> without a message.</span></span> <span data-ttu-id="199f2-159">Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="199f2-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="199f2-160">Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="199f2-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. [!OP.NO-LOC(System.Text.Json)].JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="199f2-161">Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred")`, a exceção ainda fornecerá o caminho na <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path> propriedade.</span><span class="sxs-lookup"><span data-stu-id="199f2-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="199f2-162">Registrar um conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="199f2-162">Register a custom converter</span></span>

<span data-ttu-id="199f2-163">*Registre* um conversor personalizado para fazer com `Serialize` que `Deserialize` os métodos e o usem.</span><span class="sxs-lookup"><span data-stu-id="199f2-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="199f2-164">Escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="199f2-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="199f2-165">Adicione uma instância da classe converter à <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType> coleção.</span><span class="sxs-lookup"><span data-stu-id="199f2-165">Add an instance of the converter class to the <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="199f2-166">Aplique o atributo [[jsonconverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="199f2-166">Apply the [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="199f2-167">Aplique o atributo [[jsonconverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="199f2-167">Apply the [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="199f2-168">Amostra de registro – coleção de conversores</span><span class="sxs-lookup"><span data-stu-id="199f2-168">Registration sample - Converters collection</span></span>

<span data-ttu-id="199f2-169">Veja um exemplo que torna o <xref:System.ComponentModel.DateTimeOffsetConverter> padrão para propriedades do tipo: <xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="199f2-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="199f2-170">Suponha que você Serialize uma instância do seguinte tipo:</span><span class="sxs-lookup"><span data-stu-id="199f2-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="199f2-171">Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:</span><span class="sxs-lookup"><span data-stu-id="199f2-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="199f2-172">O código a seguir usa a mesma abordagem para desserializar usando o `DateTimeOffset` conversor personalizado:</span><span class="sxs-lookup"><span data-stu-id="199f2-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="199f2-173">Exemplo de registro-[Jsonconverter] em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="199f2-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="199f2-174">O código a seguir seleciona um conversor personalizado para `Date` a propriedade:</span><span class="sxs-lookup"><span data-stu-id="199f2-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="199f2-175">O código a ser `WeatherForecastWithConverterAttribute` serializado não exige o uso `JsonSerializeOptions.Converters`de:</span><span class="sxs-lookup"><span data-stu-id="199f2-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="199f2-176">O código para desserializar também não exige o uso de `Converters`:</span><span class="sxs-lookup"><span data-stu-id="199f2-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="199f2-177">Exemplo de registro-[Jsonconverter] em um tipo</span><span class="sxs-lookup"><span data-stu-id="199f2-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="199f2-178">Aqui está o código que cria uma struct e aplica `[JsonConverter]` o atributo a ela:</span><span class="sxs-lookup"><span data-stu-id="199f2-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="199f2-179">Este é o conversor personalizado para o struct anterior:</span><span class="sxs-lookup"><span data-stu-id="199f2-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="199f2-180">O `[JsonConvert]` atributo na estrutura registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="199f2-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="199f2-181">O conversor é usado automaticamente na `TemperatureCelsius` Propriedade do seguinte tipo ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="199f2-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="199f2-182">Precedência de registro do conversor</span><span class="sxs-lookup"><span data-stu-id="199f2-182">Converter registration precedence</span></span>

<span data-ttu-id="199f2-183">Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="199f2-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="199f2-184">`[JsonConverter]`aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="199f2-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="199f2-185">Um conversor adicionado à `Converters` coleção.</span><span class="sxs-lookup"><span data-stu-id="199f2-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="199f2-186">`[JsonConverter]`aplicado a um tipo de valor personalizado ou POCO.</span><span class="sxs-lookup"><span data-stu-id="199f2-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="199f2-187">Se vários conversores personalizados para um tipo forem registrados na `Converters` coleção, o primeiro conversor que retorna true para `CanConvert` será usado.</span><span class="sxs-lookup"><span data-stu-id="199f2-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="199f2-188">Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.</span><span class="sxs-lookup"><span data-stu-id="199f2-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="199f2-189">Exemplos de conversor para cenários comuns</span><span class="sxs-lookup"><span data-stu-id="199f2-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="199f2-190">As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.</span><span class="sxs-lookup"><span data-stu-id="199f2-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="199f2-191">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="199f2-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="199f2-192">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="199f2-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="199f2-193">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="199f2-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="199f2-194">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="199f2-194">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="199f2-195">Ao desserializar para uma propriedade do tipo `object`, um `JsonElement` objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="199f2-195">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="199f2-196">O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar.</span><span class="sxs-lookup"><span data-stu-id="199f2-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="199f2-197">Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor `Boolean`é a e, se um elemento tiver "01/01/2019", o desserializador não inferirá `DateTime`que é um.</span><span class="sxs-lookup"><span data-stu-id="199f2-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="199f2-198">A inferência de tipos pode ser imprecisa.</span><span class="sxs-lookup"><span data-stu-id="199f2-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="199f2-199">Se o desserializador analisar um número JSON que não tenha nenhum ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou. `BigInteger`</span><span class="sxs-lookup"><span data-stu-id="199f2-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="199f2-200">A análise de um número que tenha um ponto decimal como `double` pode perder a precisão se o número tiver sido originalmente serializado `decimal`como um.</span><span class="sxs-lookup"><span data-stu-id="199f2-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="199f2-201">Para cenários que exigem a inferência de tipos, o código a seguir mostra `object` um conversor personalizado para propriedades.</span><span class="sxs-lookup"><span data-stu-id="199f2-201">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="199f2-202">O código converte:</span><span class="sxs-lookup"><span data-stu-id="199f2-202">The code converts:</span></span>

* <span data-ttu-id="199f2-203">`true`e `false` para`Boolean`</span><span class="sxs-lookup"><span data-stu-id="199f2-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="199f2-204">Números sem um decimal para`long`</span><span class="sxs-lookup"><span data-stu-id="199f2-204">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="199f2-205">Números com um decimal para`double`</span><span class="sxs-lookup"><span data-stu-id="199f2-205">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="199f2-206">Datas para`DateTime`</span><span class="sxs-lookup"><span data-stu-id="199f2-206">Dates to `DateTime`</span></span>
* <span data-ttu-id="199f2-207">Cadeias de caracteres para`string`</span><span class="sxs-lookup"><span data-stu-id="199f2-207">Strings to `string`</span></span>
* <span data-ttu-id="199f2-208">Tudo o mais a`JsonElement`</span><span class="sxs-lookup"><span data-stu-id="199f2-208">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="199f2-209">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="199f2-209">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="199f2-210">Aqui está um tipo de exemplo `object` com propriedades:</span><span class="sxs-lookup"><span data-stu-id="199f2-210">Here's an example type with `object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="199f2-211">O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:</span><span class="sxs-lookup"><span data-stu-id="199f2-211">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="199f2-212">Sem o conversor personalizado, a desserialização coloca `JsonElement` um em cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="199f2-212">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="199f2-213">A [pasta de testes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de unidade `System.Text.Json.Serialization` no namespace tem mais exemplos de conversores personalizados que manipulam a desserialização para `object` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="199f2-213">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="199f2-214">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="199f2-214">Support Dictionary with non-string key</span></span>

<span data-ttu-id="199f2-215">O suporte interno para coleções de dicionário é para `Dictionary<string, TValue>`o.</span><span class="sxs-lookup"><span data-stu-id="199f2-215">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="199f2-216">Ou seja, a chave deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="199f2-216">That is, the key must be a string.</span></span> <span data-ttu-id="199f2-217">Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="199f2-217">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="199f2-218">O código a seguir mostra um conversor personalizado que funciona `Dictionary<Enum,TValue>`com:</span><span class="sxs-lookup"><span data-stu-id="199f2-218">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="199f2-219">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="199f2-219">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="199f2-220">O conversor pode serializar e desserializar `TemperatureRanges` a propriedade da seguinte classe que usa o seguinte `Enum`:</span><span class="sxs-lookup"><span data-stu-id="199f2-220">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="199f2-221">A saída JSON da serialização é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="199f2-221">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="199f2-222">A [pasta de testes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de unidade `System.Text.Json.Serialization` no namespace tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="199f2-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="199f2-223">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="199f2-223">Support polymorphic deserialization</span></span>

<span data-ttu-id="199f2-224">Os recursos internos fornecem um intervalo limitado de [serialização polimórfico](system-text-json-how-to.md#serialize-properties-of-derived-classes) , mas não há suporte para desserialização.</span><span class="sxs-lookup"><span data-stu-id="199f2-224">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="199f2-225">A desserialização requer um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="199f2-225">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="199f2-226">Suponha, por exemplo, que você tenha `Person` uma classe base abstrata, `Employee` com `Customer` classes derivadas e.</span><span class="sxs-lookup"><span data-stu-id="199f2-226">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="199f2-227">A desserialização polimórfica significa que, em tempo de design, `Person` `Customer` você pode especificar como o destino de desserialização `Employee` e os objetos no JSON são desserializados corretamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="199f2-227">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="199f2-228">Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON.</span><span class="sxs-lookup"><span data-stu-id="199f2-228">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="199f2-229">Os tipos de pistas disponíveis variam de acordo com cada cenário.</span><span class="sxs-lookup"><span data-stu-id="199f2-229">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="199f2-230">Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="199f2-230">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="199f2-231">A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="199f2-231">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="199f2-232">O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas.</span><span class="sxs-lookup"><span data-stu-id="199f2-232">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="199f2-233">O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica.</span><span class="sxs-lookup"><span data-stu-id="199f2-233">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="199f2-234">O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="199f2-234">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="199f2-235">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="199f2-235">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="199f2-236">O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="199f2-236">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="199f2-237">O código do conversor no exemplo anterior lê e grava cada propriedade manualmente.</span><span class="sxs-lookup"><span data-stu-id="199f2-237">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="199f2-238">Uma alternativa é chamar `Deserialize` ou `Serialize` fazer parte do trabalho.</span><span class="sxs-lookup"><span data-stu-id="199f2-238">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="199f2-239">Para obter um exemplo, consulte [esta postagem de StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="199f2-239">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

## <a name="other-custom-converter-samples"></a><span data-ttu-id="199f2-240">Outras amostras de conversor personalizadas</span><span class="sxs-lookup"><span data-stu-id="199f2-240">Other custom converter samples</span></span>

<span data-ttu-id="199f2-241">O artigo [migrar de Newtonsoft.Json System.Text.Json para](system-text-json-migrate-from-newtonsoft-how-to.md) contém exemplos adicionais de conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="199f2-241">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="199f2-242">A [pasta de testes](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) de unidade `System.Text.Json.Serialization` no código-fonte inclui outras amostras de conversores personalizadas, como:</span><span class="sxs-lookup"><span data-stu-id="199f2-242">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="199f2-243">[Conversor de Int32 que converte NULL para 0 em desserializar](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="199f2-243">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="199f2-244">[Conversor de Int32 que permite valores de cadeia de caracteres e de número na desserialização](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="199f2-244">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="199f2-245">[Conversor de enumeração](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="199f2-245">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="199f2-246">[List\<T> converter que aceita dados externos](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="199f2-246">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="199f2-247">[Conversor Long [] que funciona com uma lista de números delimitada por vírgulas](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="199f2-247">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="199f2-248">Se você precisar criar um conversor que modifique o comportamento de um conversor interno existente, poderá obter [o código-fonte do conversor existente](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) para servir como ponto de partida para personalização.</span><span class="sxs-lookup"><span data-stu-id="199f2-248">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="199f2-249">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="199f2-249">Additional resources</span></span>

* <span data-ttu-id="199f2-250">[Código-fonte para conversores internos](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="199f2-250">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* <span data-ttu-id="199f2-251">[Suporte a DateTime e DateTimeOffset emSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="199f2-251">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="199f2-252">[System.Text.Jsonsobre](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="199f2-252">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* <span data-ttu-id="199f2-253">[Como usarSystem.Text.Json](system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="199f2-253">[How to use System.Text.Json](system-text-json-how-to.md)</span></span>
* <span data-ttu-id="199f2-254">[Como migrar doNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="199f2-254">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="199f2-255">[System.Text.JsonReferência de API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="199f2-255">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="199f2-256">[System.Text.Json. Referência de API de serialização](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="199f2-256">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
