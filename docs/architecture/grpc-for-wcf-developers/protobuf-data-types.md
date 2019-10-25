---
title: Tipos de dados escalares Protobuf-gRPC para desenvolvedores do WCF
description: Saiba mais sobre os tipos de dados básico e bem conhecido com suporte do Protobuf e do gRPC no .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: cae9cc483ffb791a9b53e6a2d9d7c0924d725a67
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846355"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="f29bd-103">Tipos de dados escalares de Protobuf</span><span class="sxs-lookup"><span data-stu-id="f29bd-103">Protobuf scalar data types</span></span>

<span data-ttu-id="f29bd-104">Protobuf dá suporte a um intervalo de tipos de valor escalar nativos.</span><span class="sxs-lookup"><span data-stu-id="f29bd-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="f29bd-105">A tabela a seguir lista todos eles com seu C# tipo equivalente:</span><span class="sxs-lookup"><span data-stu-id="f29bd-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="f29bd-106">Tipo de Protobuf</span><span class="sxs-lookup"><span data-stu-id="f29bd-106">Protobuf type</span></span> | <span data-ttu-id="f29bd-107">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="f29bd-107">C# type</span></span>      | <span data-ttu-id="f29bd-108">Anotações</span><span class="sxs-lookup"><span data-stu-id="f29bd-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="f29bd-109">1</span><span class="sxs-lookup"><span data-stu-id="f29bd-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="f29bd-110">1</span><span class="sxs-lookup"><span data-stu-id="f29bd-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="f29bd-111">1</span><span class="sxs-lookup"><span data-stu-id="f29bd-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="f29bd-112">1</span><span class="sxs-lookup"><span data-stu-id="f29bd-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="f29bd-113">2</span><span class="sxs-lookup"><span data-stu-id="f29bd-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="f29bd-114">2</span><span class="sxs-lookup"><span data-stu-id="f29bd-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="f29bd-115">2</span><span class="sxs-lookup"><span data-stu-id="f29bd-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="f29bd-116">2</span><span class="sxs-lookup"><span data-stu-id="f29bd-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="f29bd-117">3</span><span class="sxs-lookup"><span data-stu-id="f29bd-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="f29bd-118">4</span><span class="sxs-lookup"><span data-stu-id="f29bd-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="f29bd-119">Anotações</span><span class="sxs-lookup"><span data-stu-id="f29bd-119">Notes</span></span>

1. <span data-ttu-id="f29bd-120">A codificação padrão para `int32` e `int64` é ineficiente ao trabalhar com valores assinados.</span><span class="sxs-lookup"><span data-stu-id="f29bd-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="f29bd-121">Se for provável que o campo contenha números negativos, use `sint32` ou `sint64` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f29bd-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="f29bd-122">Os dois tipos são mapeados para os C# tipos`int`e`long`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f29bd-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="f29bd-123">Os campos de `fixed` sempre usam o mesmo número de bytes, independentemente do valor.</span><span class="sxs-lookup"><span data-stu-id="f29bd-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="f29bd-124">Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="f29bd-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="f29bd-125">As cadeias de caracteres Protobuf são codificadas em UTF-8 (ou ASCII de 7 bits) e o comprimento codificado não pode ser maior que 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="f29bd-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="f29bd-126">O tempo de execução do Protobuf fornece um tipo de `ByteString` que mapeia C# facilmente de e para`byte[]`matrizes.</span><span class="sxs-lookup"><span data-stu-id="f29bd-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="f29bd-127">Outros tipos primitivos .NET</span><span class="sxs-lookup"><span data-stu-id="f29bd-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="f29bd-128">Datas e horas</span><span class="sxs-lookup"><span data-stu-id="f29bd-128">Dates and times</span></span>

<span data-ttu-id="f29bd-129">Os tipos escalares nativos não fornecem valores de data e hora, equivalentes a C#<xref:System.DateTimeOffset>,<xref:System.DateTime>e<xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f29bd-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="f29bd-130">Esses tipos podem ser especificados usando algumas extensões de "tipos conhecidos" do Google, que fornecem geração de código e suporte a tempo de execução para tipos de campo mais complexos em todas as plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="f29bd-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="f29bd-131">A tabela a seguir mostra os tipos de data e hora:</span><span class="sxs-lookup"><span data-stu-id="f29bd-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="f29bd-132">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="f29bd-132">C# type</span></span> | <span data-ttu-id="f29bd-133">Protobuf tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="f29bd-133">Protobuf well-known type</span></span> |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

<span data-ttu-id="f29bd-134">As propriedades geradas na C# classe não são os tipos de data e hora do .net.</span><span class="sxs-lookup"><span data-stu-id="f29bd-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="f29bd-135">As propriedades usam as classes `Timestamp` e `Duration` no namespace `Google.Protobuf.WellKnownTypes`, que fornecem métodos para converter de e para `DateTimeOffset`, `DateTime`e `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> <span data-ttu-id="f29bd-136">O tipo de `Timestamp` funciona com horários UTC; `DateTimeOffset` valores sempre têm um deslocamento de zero e a propriedade `DateTime.Kind` sempre será `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="f29bd-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="f29bd-137">System.Guid</span></span>

<span data-ttu-id="f29bd-138">O tipo de <xref:System.Guid>, conhecido como `UUID` em outras plataformas, não tem suporte direto de Protobuf e não há um tipo conhecido para ele.</span><span class="sxs-lookup"><span data-stu-id="f29bd-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="f29bd-139">A melhor abordagem é manipular `Guid` valores como `string` campo, usando o formato hexadecimal `8-4-4-4-12` padrão (por exemplo, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), que pode ser analisado por todas as linguagens e plataformas.</span><span class="sxs-lookup"><span data-stu-id="f29bd-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="f29bd-140">Não use um campo de `bytes` para valores de `Guid`, já que problemas com a endian podem resultar em comportamento irregular ao interagir com outras plataformas, como Java.</span><span class="sxs-lookup"><span data-stu-id="f29bd-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="f29bd-141">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="f29bd-141">Nullable types</span></span>

<span data-ttu-id="f29bd-142">A geração de código Protobuf C# para o usa os tipos nativos, como`int`para`int32`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="f29bd-143">Isso significa que os valores são sempre incluídos e não podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="f29bd-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="f29bd-144">Para valores que exigem NULL explícito, como usar `int?` em seu código C# , os "tipos bem conhecidos" de Protobuf incluem wrappers que são compilados para C# tipos anuláveis.</span><span class="sxs-lookup"><span data-stu-id="f29bd-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="f29bd-145">Para usá-los, importe `wrappers.proto` para o arquivo `.proto`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f29bd-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="f29bd-146">Protobuf usará o `T?` simples (por exemplo, `int?`) para a propriedade de mensagem gerada.</span><span class="sxs-lookup"><span data-stu-id="f29bd-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="f29bd-147">A tabela a seguir mostra a lista completa de tipos de wrapper com C# seu tipo equivalente:</span><span class="sxs-lookup"><span data-stu-id="f29bd-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="f29bd-148">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="f29bd-148">C# type</span></span>   | <span data-ttu-id="f29bd-149">Wrapper de tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="f29bd-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="f29bd-150">Os tipos bem conhecidos `Timestamp` e `Duration` são representados no .NET como classes, portanto, não há necessidade de uma versão anulável, mas é importante verificar se há nulo nas propriedades desses tipos ao converter para `DateTimeOffset` ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="f29bd-151">decimais</span><span class="sxs-lookup"><span data-stu-id="f29bd-151">Decimals</span></span>

<span data-ttu-id="f29bd-152">O Protobuf não dá suporte nativo ao tipo de `decimal` .NET, apenas `double` e `float`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="f29bd-153">Há uma discussão em andamento no projeto Protobuf sobre a possibilidade de adicionar um tipo de `Decimal` padrão aos tipos conhecidos, com suporte de plataforma para linguagens e estruturas que dão suporte a ele, mas nada foi implementado ainda.</span><span class="sxs-lookup"><span data-stu-id="f29bd-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="f29bd-154">É possível criar uma definição de mensagem para representar o tipo de `decimal` que funcionaria para a serialização segura entre clientes e servidores .NET, mas os desenvolvedores em outras plataformas teriam que entender o formato usado e implementar sua própria manipulação para ele.</span><span class="sxs-lookup"><span data-stu-id="f29bd-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="f29bd-155">Criando um tipo decimal personalizado para Protobuf</span><span class="sxs-lookup"><span data-stu-id="f29bd-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="f29bd-156">Uma implementação muito simples pode ser semelhante ao tipo de `Money` não padrão usado por algumas APIs do Google, sem o campo `currency`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

<span data-ttu-id="f29bd-157">O campo `nanos` representa os valores de `0.999_999_999` para `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="f29bd-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="f29bd-158">Por exemplo, o valor `decimal` `1.5m` seria representado como `{ units = 1, nanos = 500_000_000 }` (é por isso que o campo `nanos` neste exemplo usa o tipo `sfixed32`, que codifica de forma mais eficiente do que `int32` para valores maiores).</span><span class="sxs-lookup"><span data-stu-id="f29bd-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="f29bd-159">Se o campo `units` for negativo, o campo `nanos` também deverá ser negativo.</span><span class="sxs-lookup"><span data-stu-id="f29bd-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="f29bd-160">Há vários outros algoritmos para codificar valores de `decimal` como cadeias de caracteres de byte, mas essa mensagem é muito mais fácil de entender do que qualquer um deles, e os valores não são afetados pela *[ordenação](https://en.wikipedia.org/wiki/Endianness)* em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="f29bd-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="f29bd-161">A conversão entre esse tipo e o tipo de `decimal` BCL pode ser C# implementada como esta.</span><span class="sxs-lookup"><span data-stu-id="f29bd-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="f29bd-162">Sempre que você usa tipos de mensagem de utilitário personalizados como este, você **deve** documentá-los com comentários no `.proto` para que outros desenvolvedores possam implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f29bd-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f29bd-163">[Anterior](protobuf-messages.md)
>[Próximo](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="f29bd-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
