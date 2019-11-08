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
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741888"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="e0659-102">Como escrever conversores personalizados para serialização JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="e0659-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="e0659-103">Este artigo mostra como criar conversores personalizados para as classes de serialização JSON que são fornecidas no namespace <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="e0659-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="e0659-104">Para obter uma introdução ao `System.Text.Json`, consulte [como serializar e desserializar JSON no .net](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="e0659-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="e0659-105">Um *conversor* é uma classe que converte um objeto ou um valor de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="e0659-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="e0659-106">O namespace `System.Text.Json` tem conversores internos para a maioria dos tipos primitivos que mapeiam para primitivos JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e0659-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="e0659-107">Você pode escrever conversores personalizados:</span><span class="sxs-lookup"><span data-stu-id="e0659-107">You can write custom converters:</span></span>

* <span data-ttu-id="e0659-108">Para substituir o comportamento padrão de um conversor interno.</span><span class="sxs-lookup"><span data-stu-id="e0659-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="e0659-109">Por exemplo, talvez você queira `DateTime` valores a serem representados pelo formato mm/dd/aaaa em vez do formato ISO 8601-1:2019 padrão.</span><span class="sxs-lookup"><span data-stu-id="e0659-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="e0659-110">Para dar suporte a um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0659-110">To support a custom value type.</span></span> <span data-ttu-id="e0659-111">Por exemplo, um struct `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="e0659-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="e0659-112">Você também pode escrever conversores personalizados para estender `System.Text.Json` com funcionalidade não incluída na versão atual.</span><span class="sxs-lookup"><span data-stu-id="e0659-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="e0659-113">Os cenários a seguir serão abordados posteriormente neste artigo:</span><span class="sxs-lookup"><span data-stu-id="e0659-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="e0659-114">[Desserializar tipos inferidos para propriedades de objeto](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="e0659-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="e0659-115">[Dicionário de suporte com chave não cadeia de caracteres](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="e0659-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="e0659-116">[Suporte à desserialização polimórfico](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="e0659-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="e0659-117">Padrões de conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="e0659-117">Custom converter patterns</span></span>

<span data-ttu-id="e0659-118">Há dois padrões para a criação de um conversor personalizado: o padrão básico e o padrão de fábrica.</span><span class="sxs-lookup"><span data-stu-id="e0659-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="e0659-119">O padrão de fábrica é para conversores que manipulam tipos `Enum` ou genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="e0659-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="e0659-120">O padrão básico é para tipos genéricos não genéricos e fechados.</span><span class="sxs-lookup"><span data-stu-id="e0659-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="e0659-121">Por exemplo, os conversores para os seguintes tipos exigem o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="e0659-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="e0659-122">Alguns exemplos de tipos que podem ser tratados pelo padrão básico incluem:</span><span class="sxs-lookup"><span data-stu-id="e0659-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="e0659-123">O padrão básico cria uma classe que pode manipular um tipo.</span><span class="sxs-lookup"><span data-stu-id="e0659-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="e0659-124">O padrão de fábrica cria uma classe que determina no tempo de execução qual tipo específico é necessário e cria dinamicamente o conversor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e0659-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="e0659-125">Conversor básico de exemplo</span><span class="sxs-lookup"><span data-stu-id="e0659-125">Sample basic converter</span></span>

<span data-ttu-id="e0659-126">O exemplo a seguir é um conversor que substitui a serialização padrão para um tipo de dados existente.</span><span class="sxs-lookup"><span data-stu-id="e0659-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="e0659-127">O conversor usa o formato mm/dd/aaaa para propriedades de `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="e0659-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="e0659-128">Conversor de padrão de fábrica de exemplo</span><span class="sxs-lookup"><span data-stu-id="e0659-128">Sample factory pattern converter</span></span>

<span data-ttu-id="e0659-129">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="e0659-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="e0659-130">O código segue o padrão de fábrica porque o primeiro parâmetro de tipo genérico é `Enum` e o segundo é aberto.</span><span class="sxs-lookup"><span data-stu-id="e0659-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="e0659-131">O método `CanConvert` retorna `true` apenas para um `Dictionary` com dois parâmetros genéricos, o primeiro deles é um tipo `Enum`.</span><span class="sxs-lookup"><span data-stu-id="e0659-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="e0659-132">O conversor interno Obtém um conversor existente para lidar com qualquer tipo fornecido no tempo de execução para `TValue`.</span><span class="sxs-lookup"><span data-stu-id="e0659-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="e0659-133">O código anterior é o mesmo que o mostrado no dicionário de [suporte com uma chave que não seja de cadeia de caracteres](#support-dictionary-with-non-string-key) , mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="e0659-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="e0659-134">Etapas para seguir o padrão básico</span><span class="sxs-lookup"><span data-stu-id="e0659-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="e0659-135">As etapas a seguir explicam como criar um conversor seguindo o padrão básico:</span><span class="sxs-lookup"><span data-stu-id="e0659-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="e0659-136">Crie uma classe que derive de <xref:System.Text.Json.Serialization.JsonConverter%601> onde `T` é o tipo a ser serializado e desserializado.</span><span class="sxs-lookup"><span data-stu-id="e0659-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="e0659-137">Substitua o método `Read` para desserializar o JSON de entrada e convertê-lo no tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="e0659-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="e0659-138">Use o <xref:System.Text.Json.Utf8JsonReader> que é passado para o método para ler o JSON.</span><span class="sxs-lookup"><span data-stu-id="e0659-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="e0659-139">Substitua o método `Write` para serializar o objeto de entrada do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="e0659-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="e0659-140">Use o <xref:System.Text.Json.Utf8JsonWriter> que é passado para o método para gravar o JSON.</span><span class="sxs-lookup"><span data-stu-id="e0659-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="e0659-141">Substitua o método `CanConvert` somente se necessário.</span><span class="sxs-lookup"><span data-stu-id="e0659-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="e0659-142">A implementação padrão retorna `true` quando o tipo a ser convertido é do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="e0659-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="e0659-143">Portanto, os conversores que dão suporte apenas ao tipo `T` não precisam substituir esse método.</span><span class="sxs-lookup"><span data-stu-id="e0659-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="e0659-144">Para obter um exemplo de um conversor que precisa substituir esse método, consulte a seção [desserialização polimórfica](#support-polymorphic-deserialization) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="e0659-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="e0659-145">Você pode consultar o [código-fonte dos conversores internos](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) como implementações de referência para escrever conversores personalizados.</span><span class="sxs-lookup"><span data-stu-id="e0659-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="e0659-146">Etapas para seguir o padrão de fábrica</span><span class="sxs-lookup"><span data-stu-id="e0659-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="e0659-147">As etapas a seguir explicam como criar um conversor seguindo o padrão de fábrica:</span><span class="sxs-lookup"><span data-stu-id="e0659-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="e0659-148">Crie uma classe que deriva de <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="e0659-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="e0659-149">Substitua o método `CanConvert` para retornar true quando o tipo a ser convertido for aquele que o conversor possa manipular.</span><span class="sxs-lookup"><span data-stu-id="e0659-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="e0659-150">Por exemplo, se o conversor for para `List<T>` ele pode manipular apenas `List<int>`, `List<string>`e `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="e0659-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="e0659-151">Substitua o método `CreateConverter` para retornar uma instância de uma classe de conversor que manipulará o tipo a ser convertido que é fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0659-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="e0659-152">Crie a classe de conversor que o método de `CreateConverter` instancia.</span><span class="sxs-lookup"><span data-stu-id="e0659-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="e0659-153">O padrão de fábrica é necessário para os genéricos abertos porque o código para converter um objeto de e para uma cadeia de caracteres não é o mesmo para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="e0659-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="e0659-154">Um conversor para um tipo genérico aberto (`List<T>`, por exemplo) precisa criar um conversor para um tipo genérico fechado (`List<DateTime>`, por exemplo) em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="e0659-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="e0659-155">O código deve ser gravado para lidar com cada tipo fechado genérico que o conversor pode manipular.</span><span class="sxs-lookup"><span data-stu-id="e0659-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="e0659-156">O tipo de `Enum` é semelhante a um tipo genérico aberto: um conversor para `Enum` tem que criar um conversor para um `Enum` específico (`WeekdaysEnum`, por exemplo) nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="e0659-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="e0659-157">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="e0659-157">Error handling</span></span>

<span data-ttu-id="e0659-158">Se você precisar lançar uma exceção no código de tratamento de erros, considere lançar um <xref:System.Text.Json.JsonException> sem uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="e0659-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="e0659-159">Esse tipo de exceção cria automaticamente uma mensagem que inclui o caminho para a parte do JSON que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="e0659-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="e0659-160">Por exemplo, a instrução `throw new JsonException();` produz uma mensagem de erro semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e0659-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="e0659-161">Se você fornecer uma mensagem (por exemplo, `throw new JsonException("Error occurred)`, a exceção ainda fornecerá o caminho na propriedade <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="e0659-161">If you do provide a message (for example, `throw new JsonException("Error occurred)`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="e0659-162">Registrar um conversor personalizado</span><span class="sxs-lookup"><span data-stu-id="e0659-162">Register a custom converter</span></span>

<span data-ttu-id="e0659-163">*Registre* um conversor personalizado para fazer com que os métodos `Serialize` e `Deserialize` o usem.</span><span class="sxs-lookup"><span data-stu-id="e0659-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="e0659-164">Escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="e0659-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="e0659-165">Adicione uma instância da classe converter à coleção de <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0659-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="e0659-166">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) às propriedades que exigem o conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0659-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="e0659-167">Aplique o atributo [[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) a uma classe ou a uma struct que represente um tipo de valor personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0659-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="e0659-168">Amostra de registro – coleção de conversores</span><span class="sxs-lookup"><span data-stu-id="e0659-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="e0659-169">Veja um exemplo que torna o `ExampleDateTimeOffsetConverter` o padrão para propriedades do tipo `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="e0659-169">Here's an example that makes the `ExampleDateTimeOffsetConverter` the default for properties of type `DateTimeOffset`:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0659-170">Suponha que você Serialize o seguinte tipo:</span><span class="sxs-lookup"><span data-stu-id="e0659-170">Suppose you serialize the following type:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="e0659-171">Aqui está um exemplo de saída JSON que mostra que o conversor personalizado foi usado:</span><span class="sxs-lookup"><span data-stu-id="e0659-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="e0659-172">O código a seguir usa a mesma abordagem para desserializar usando o conversor de `DateTimeOffset` personalizado:</span><span class="sxs-lookup"><span data-stu-id="e0659-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="e0659-173">Exemplo de registro-[Jsonconverter] em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e0659-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="e0659-174">O código a seguir seleciona um conversor personalizado para a propriedade `Date`:</span><span class="sxs-lookup"><span data-stu-id="e0659-174">The following code selects a custom converter for the `Date` property:</span></span>

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="e0659-175">O código para serializar e desserializar `WeatherForecastWithConverter` não requer o uso de `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="e0659-175">The code to serialize and deserialize `WeatherForecastWithConverter` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="e0659-176">Exemplo de registro-[Jsonconverter] em um tipo</span><span class="sxs-lookup"><span data-stu-id="e0659-176">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="e0659-177">Aqui está o código que cria um struct e aplica o atributo `[JsonConverter]` a ele:</span><span class="sxs-lookup"><span data-stu-id="e0659-177">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

<span data-ttu-id="e0659-178">Este é o conversor personalizado para o struct anterior:</span><span class="sxs-lookup"><span data-stu-id="e0659-178">Here's the custom converter for the preceding struct:</span></span>

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

<span data-ttu-id="e0659-179">O atributo `[JsonConvert]` na struct registra o conversor personalizado como o padrão para propriedades do tipo `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="e0659-179">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="e0659-180">O conversor é usado automaticamente na propriedade `TemperatureC` do seguinte tipo ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="e0659-180">The converter is automatically used on the `TemperatureC` property of the following type when you serialize or deserialize it:</span></span>

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a><span data-ttu-id="e0659-181">Precedência de registro do conversor</span><span class="sxs-lookup"><span data-stu-id="e0659-181">Converter registration precedence</span></span>

<span data-ttu-id="e0659-182">Durante a serialização ou desserialização, um conversor é escolhido para cada elemento JSON na seguinte ordem, listada da prioridade mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="e0659-182">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="e0659-183">`[JsonConverter]` aplicado a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="e0659-183">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="e0659-184">Um conversor adicionado à coleção de `Converters`.</span><span class="sxs-lookup"><span data-stu-id="e0659-184">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="e0659-185">`[JsonConverter]` aplicado a um tipo de valor personalizado ou POCO.</span><span class="sxs-lookup"><span data-stu-id="e0659-185">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="e0659-186">Se vários conversores personalizados para um tipo forem registrados na coleção de `Converters`, o primeiro conversor que retorna true para `CanConvert` será usado.</span><span class="sxs-lookup"><span data-stu-id="e0659-186">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="e0659-187">Um conversor interno será escolhido somente se nenhum conversor personalizado aplicável for registrado.</span><span class="sxs-lookup"><span data-stu-id="e0659-187">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="e0659-188">Exemplos de conversor para cenários comuns</span><span class="sxs-lookup"><span data-stu-id="e0659-188">Converter samples for common scenarios</span></span>

<span data-ttu-id="e0659-189">As seções a seguir fornecem exemplos de conversor que abordam alguns cenários comuns que a funcionalidade interna não trata.</span><span class="sxs-lookup"><span data-stu-id="e0659-189">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="e0659-190">Desserializar tipos inferidos para propriedades de objeto</span><span class="sxs-lookup"><span data-stu-id="e0659-190">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="e0659-191">Ao desserializar para uma propriedade do tipo `Object`, um objeto `JsonElement` é criado.</span><span class="sxs-lookup"><span data-stu-id="e0659-191">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="e0659-192">O motivo é que o desserializador não sabe qual tipo de CLR deve ser criado e não tenta adivinhar.</span><span class="sxs-lookup"><span data-stu-id="e0659-192">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="e0659-193">Por exemplo, se uma propriedade JSON tiver "true", o desserializador não inferirá que o valor é um `Boolean`e, se um elemento tiver "01/01/2019", o desserializador não inferirá que se trata de um `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="e0659-193">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="e0659-194">A inferência de tipos pode ser imprecisa.</span><span class="sxs-lookup"><span data-stu-id="e0659-194">Type inference can be inaccurate.</span></span> <span data-ttu-id="e0659-195">Se o desserializador analisar um número JSON que não tenha um ponto decimal como um `long`, isso poderá resultar em problemas fora do intervalo se o valor tiver sido originalmente serializado como um `ulong` ou `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="e0659-195">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="e0659-196">A análise de um número que tenha um ponto decimal como um `double` poderá perder a precisão se o número tiver sido originalmente serializado como um `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e0659-196">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="e0659-197">Para cenários que exigem inferência de tipos, o código a seguir mostra um conversor personalizado para propriedades de `Object`.</span><span class="sxs-lookup"><span data-stu-id="e0659-197">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="e0659-198">O código converte:</span><span class="sxs-lookup"><span data-stu-id="e0659-198">The code converts:</span></span>

* <span data-ttu-id="e0659-199">`true` e `false` para `Boolean`</span><span class="sxs-lookup"><span data-stu-id="e0659-199">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="e0659-200">Números para `long` ou `double`</span><span class="sxs-lookup"><span data-stu-id="e0659-200">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="e0659-201">Datas para `DateTime`</span><span class="sxs-lookup"><span data-stu-id="e0659-201">Dates to `DateTime`</span></span>
* <span data-ttu-id="e0659-202">Cadeias de caracteres para `string`</span><span class="sxs-lookup"><span data-stu-id="e0659-202">Strings to `string`</span></span>
* <span data-ttu-id="e0659-203">Tudo o mais a ser `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="e0659-203">Everything else to `JsonElement`</span></span>

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

<span data-ttu-id="e0659-204">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="e0659-204">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

<span data-ttu-id="e0659-205">Aqui está um tipo de exemplo com uma propriedade de objeto:</span><span class="sxs-lookup"><span data-stu-id="e0659-205">Here's an example type with an Object property:</span></span>

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

<span data-ttu-id="e0659-206">O exemplo a seguir de JSON para desserializar contém valores que serão desserializados como `DateTime`, `long`e `string`:</span><span class="sxs-lookup"><span data-stu-id="e0659-206">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="e0659-207">Sem o conversor personalizado, a desserialização coloca uma `JsonElement` em cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="e0659-207">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="e0659-208">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam a desserialização nas propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="e0659-208">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="e0659-209">Dicionário de suporte com chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e0659-209">Support Dictionary with non-string key</span></span>

<span data-ttu-id="e0659-210">O suporte interno para coleções de dicionários é para `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="e0659-210">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="e0659-211">Ou seja, a chave deve ser uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e0659-211">That is, the key must be a string.</span></span> <span data-ttu-id="e0659-212">Para dar suporte a um dicionário com um inteiro ou algum outro tipo como a chave, um conversor personalizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0659-212">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="e0659-213">O código a seguir mostra um conversor personalizado que funciona com `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="e0659-213">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="e0659-214">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="e0659-214">The following code registers the converter:</span></span>

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

<span data-ttu-id="e0659-215">O conversor pode serializar e desserializar a propriedade `TemperatureRanges` da seguinte classe que usa os seguintes `Enum`:</span><span class="sxs-lookup"><span data-stu-id="e0659-215">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

<span data-ttu-id="e0659-216">A saída JSON da serialização é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e0659-216">The JSON output from serialization looks like the following example:</span></span>

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="e0659-217">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no namespace `System.Text.Json.Serialization` tem mais exemplos de conversores personalizados que manipulam dicionários que não são de chave de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e0659-217">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="e0659-218">Suporte à desserialização polimórfico</span><span class="sxs-lookup"><span data-stu-id="e0659-218">Support polymorphic deserialization</span></span>

<span data-ttu-id="e0659-219">A [serialização polimórfica](system-text-json-how-to.md#serialize-properties-of-derived-classes) não requer um conversor personalizado, mas a desserialização requer um conversor personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0659-219">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="e0659-220">Suponha, por exemplo, que você tenha uma classe base abstrata `Person`, com `Employee` e `Customer` classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="e0659-220">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="e0659-221">A desserialização polimórfica significa que, em tempo de design, você pode especificar `Person` como o destino de desserialização e `Customer` e `Employee` objetos no JSON são corretamente desserializados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0659-221">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="e0659-222">Durante a desserialização, você precisa encontrar pistas que identificam o tipo necessário no JSON.</span><span class="sxs-lookup"><span data-stu-id="e0659-222">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="e0659-223">Os tipos de pistas disponíveis variam de acordo com cada cenário.</span><span class="sxs-lookup"><span data-stu-id="e0659-223">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="e0659-224">Por exemplo, uma propriedade discriminadora pode estar disponível ou talvez você precise contar com a presença ou a ausência de uma determinada propriedade.</span><span class="sxs-lookup"><span data-stu-id="e0659-224">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="e0659-225">A versão atual do `System.Text.Json` não fornece atributos para especificar como lidar com cenários de desserialização polimórfico, para que conversores personalizados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="e0659-225">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="e0659-226">O código a seguir mostra uma classe base, duas classes derivadas e um conversor personalizado para elas.</span><span class="sxs-lookup"><span data-stu-id="e0659-226">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="e0659-227">O conversor usa uma propriedade discriminadora para fazer desserialização polimórfica.</span><span class="sxs-lookup"><span data-stu-id="e0659-227">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="e0659-228">O discriminador de tipo não está nas definições de classe, mas é criado durante a serialização e é lido durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="e0659-228">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

<span data-ttu-id="e0659-229">O código a seguir registra o conversor:</span><span class="sxs-lookup"><span data-stu-id="e0659-229">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

<span data-ttu-id="e0659-230">O conversor pode desserializar o JSON criado usando o mesmo conversor para serializar, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e0659-230">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="e0659-231">Outras amostras de conversor personalizadas</span><span class="sxs-lookup"><span data-stu-id="e0659-231">Other custom converter samples</span></span>

<span data-ttu-id="e0659-232">A [pasta de testes de unidade](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) no código-fonte `System.Text.Json.Serialization` inclui outras amostras de conversores personalizados, como:</span><span class="sxs-lookup"><span data-stu-id="e0659-232">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="e0659-233">`Int32` o conversor que converte NULL em 0 em desserializar</span><span class="sxs-lookup"><span data-stu-id="e0659-233">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="e0659-234">`Int32` conversor que permite valores de cadeia de caracteres e de número na desserialização</span><span class="sxs-lookup"><span data-stu-id="e0659-234">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="e0659-235">conversor de `Enum`</span><span class="sxs-lookup"><span data-stu-id="e0659-235">`Enum` converter</span></span>
* <span data-ttu-id="e0659-236">`List<T>` o conversor que aceita dados externos</span><span class="sxs-lookup"><span data-stu-id="e0659-236">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="e0659-237">`Long[]` conversor que funciona com uma lista de números delimitada por vírgulas</span><span class="sxs-lookup"><span data-stu-id="e0659-237">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="e0659-238">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e0659-238">Additional resources</span></span>

* [<span data-ttu-id="e0659-239">Visão geral de System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="e0659-239">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e0659-240">Referência da API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="e0659-240">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="e0659-241">Como usar System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="e0659-241">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e0659-242">Código-fonte para conversores internos</span><span class="sxs-lookup"><span data-stu-id="e0659-242">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="e0659-243">Problemas do GitHub relacionados a conversores personalizados para `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="e0659-243">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="e0659-244">36639 apresentando conversores personalizados</span><span class="sxs-lookup"><span data-stu-id="e0659-244">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="e0659-245">38713 sobre desserialização para objeto</span><span class="sxs-lookup"><span data-stu-id="e0659-245">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="e0659-246">40120 sobre dicionários de chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e0659-246">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="e0659-247">37787 sobre desserialização polimórfica</span><span class="sxs-lookup"><span data-stu-id="e0659-247">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
