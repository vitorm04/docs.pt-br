---
title: Tipos de dados escalares Protobuf-gRPC para desenvolvedores do WCF
description: Saiba mais sobre os tipos de dados básico e conhecido que Protobuf e gRPC dão suporte ao .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543151"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="5ba4a-103">Tipos de dados escalares de Protobuf</span><span class="sxs-lookup"><span data-stu-id="5ba4a-103">Protobuf scalar data types</span></span>

<span data-ttu-id="5ba4a-104">O buffer de protocolo (Protobuf) dá suporte a um intervalo de tipos de valores escalares nativos.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="5ba4a-105">A tabela a seguir lista todos eles com seu C# tipo equivalente:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="5ba4a-106">Tipo de Protobuf</span><span class="sxs-lookup"><span data-stu-id="5ba4a-106">Protobuf type</span></span> | <span data-ttu-id="5ba4a-107">Tipo C#</span><span class="sxs-lookup"><span data-stu-id="5ba4a-107">C# type</span></span>      | <span data-ttu-id="5ba4a-108">Observações</span><span class="sxs-lookup"><span data-stu-id="5ba4a-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="5ba4a-109">1</span><span class="sxs-lookup"><span data-stu-id="5ba4a-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="5ba4a-110">1</span><span class="sxs-lookup"><span data-stu-id="5ba4a-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="5ba4a-111">1</span><span class="sxs-lookup"><span data-stu-id="5ba4a-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="5ba4a-112">1</span><span class="sxs-lookup"><span data-stu-id="5ba4a-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="5ba4a-113">2</span><span class="sxs-lookup"><span data-stu-id="5ba4a-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="5ba4a-114">2</span><span class="sxs-lookup"><span data-stu-id="5ba4a-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="5ba4a-115">2</span><span class="sxs-lookup"><span data-stu-id="5ba4a-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="5ba4a-116">2</span><span class="sxs-lookup"><span data-stu-id="5ba4a-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="5ba4a-117">3</span><span class="sxs-lookup"><span data-stu-id="5ba4a-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="5ba4a-118">4</span><span class="sxs-lookup"><span data-stu-id="5ba4a-118">4</span></span>     |

<span data-ttu-id="5ba4a-119">Observações:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-119">Notes:</span></span>

1. <span data-ttu-id="5ba4a-120">A codificação padrão para `int32` e `int64` é ineficiente quando você está trabalhando com valores assinados.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="5ba4a-121">Se for provável que o campo contenha números negativos, use `sint32` ou `sint64` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="5ba4a-122">Esses tipos são mapeados C# para os tipos `int` e `long`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="5ba4a-123">Os campos de `fixed` sempre usam o mesmo número de bytes, independentemente do valor.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="5ba4a-124">Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="5ba4a-125">As cadeias de caracteres Protobuf são codificadas em UTF-8 (ou ASCII de 7 bits).</span><span class="sxs-lookup"><span data-stu-id="5ba4a-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="5ba4a-126">O comprimento codificado não pode ser maior que 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="5ba4a-127">O tempo de execução do Protobuf fornece um tipo de `ByteString` que mapeia C# facilmente de e para `byte[]` matrizes.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="5ba4a-128">Outros tipos primitivos .NET</span><span class="sxs-lookup"><span data-stu-id="5ba4a-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="5ba4a-129">Datas e horas</span><span class="sxs-lookup"><span data-stu-id="5ba4a-129">Dates and times</span></span>

<span data-ttu-id="5ba4a-130">Os tipos escalares nativos não fornecem valores de data e hora, equivalentes a C#<xref:System.DateTimeOffset>, <xref:System.DateTime>e <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="5ba4a-131">Você pode especificar esses tipos usando algumas das extensões "tipos conhecidos" do Google.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="5ba4a-132">Essas extensões fornecem geração de código e suporte a tempo de execução para tipos de campo complexos em plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="5ba4a-133">A tabela a seguir mostra os tipos de data e hora:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="5ba4a-134">Tipo C#</span><span class="sxs-lookup"><span data-stu-id="5ba4a-134">C# type</span></span> | <span data-ttu-id="5ba4a-135">Protobuf tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="5ba4a-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="5ba4a-136">As propriedades geradas na C# classe não são os tipos de data e hora do .net.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="5ba4a-137">As propriedades usam as classes `Timestamp` e `Duration` no namespace `Google.Protobuf.WellKnownTypes`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="5ba4a-138">Essas classes fornecem métodos para converter de e para `DateTimeOffset`, `DateTime`e `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="5ba4a-139">O tipo de `Timestamp` funciona com horas UTC.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="5ba4a-140">`DateTimeOffset` valores sempre têm um deslocamento de zero e a propriedade `DateTime.Kind` sempre é `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="5ba4a-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="5ba4a-141">System.Guid</span></span>

<span data-ttu-id="5ba4a-142">O Protobuf não dá suporte direto ao tipo de <xref:System.Guid>, conhecido como `UUID` em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="5ba4a-143">Não há um tipo bem conhecido para ele.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="5ba4a-144">A melhor abordagem é manipular valores de `Guid` como um campo de `string`, usando o formato hexadecimal de `8-4-4-4-12` padrão (por exemplo, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span><span class="sxs-lookup"><span data-stu-id="5ba4a-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="5ba4a-145">Todas as linguagens e plataformas podem analisar esse formato.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="5ba4a-146">Não use um campo `bytes` para `Guid` valores.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="5ba4a-147">Problemas com a *endian* ([definição da Wikipédia](https://en.wikipedia.org/wiki/Endianness)) podem resultar em comportamento irregular quando o Protobuf está interagindo com outras plataformas, como Java.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="5ba4a-148">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="5ba4a-148">Nullable types</span></span>

<span data-ttu-id="5ba4a-149">A geração de código Protobuf C# para o usa os tipos nativos, como `int` para `int32`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="5ba4a-150">Portanto, os valores são sempre incluídos e não podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="5ba4a-151">Para valores que exigem NULL explícito, como usar `int?` em seu código C# , os "tipos bem conhecidos" de Protobuf incluem wrappers que são compilados para C# tipos anuláveis.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="5ba4a-152">Para usá-los, importe `wrappers.proto` para o arquivo `.proto`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="5ba4a-153">Protobuf usará o `T?` simples (por exemplo, `int?`) para a propriedade de mensagem gerada.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="5ba4a-154">A tabela a seguir mostra a lista completa de tipos de wrapper com C# seu tipo equivalente:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="5ba4a-155">Tipo C#</span><span class="sxs-lookup"><span data-stu-id="5ba4a-155">C# type</span></span>   | <span data-ttu-id="5ba4a-156">Wrapper de tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="5ba4a-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="5ba4a-157">Os tipos bem conhecidos `Timestamp` e `Duration` são representados no .NET como classes, portanto, não há necessidade de uma versão anulável.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="5ba4a-158">Mas é importante verificar se há nulo nas propriedades desses tipos quando você estiver convertendo para `DateTimeOffset` ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="5ba4a-159">Decimais</span><span class="sxs-lookup"><span data-stu-id="5ba4a-159">Decimals</span></span>

<span data-ttu-id="5ba4a-160">O Protobuf não dá suporte nativo ao tipo de `decimal` .NET, apenas `double` e `float`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="5ba4a-161">Há uma discussão contínua no projeto Protobuf sobre a possibilidade de adicionar um tipo de `Decimal` padrão aos tipos conhecidos, com suporte de plataforma para linguagens e estruturas que dão suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="5ba4a-162">Nada foi implementado ainda.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="5ba4a-163">É possível criar uma definição de mensagem para representar o tipo de `decimal` que funcionaria para a serialização segura entre clientes e servidores .NET.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="5ba4a-164">Mas os desenvolvedores de outras plataformas teriam que entender o formato que está sendo usado e implementar sua própria manipulação.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="5ba4a-165">Criando um tipo decimal personalizado para Protobuf</span><span class="sxs-lookup"><span data-stu-id="5ba4a-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="5ba4a-166">Uma implementação simples pode ser semelhante ao tipo de `Money` não padrão que algumas APIs do Google usam, sem o campo `currency`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="5ba4a-167">O campo `nanos` representa os valores de `0.999_999_999` para `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="5ba4a-168">Por exemplo, o valor `decimal` `1.5m` seria representado como `{ units = 1, nanos = 500_000_000 }`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="5ba4a-169">É por isso que o campo `nanos` neste exemplo usa o tipo `sfixed32`, que codifica de forma mais eficiente do que `int32` para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="5ba4a-170">Se o campo `units` for negativo, o campo `nanos` também deverá ser negativo.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="5ba4a-171">Há vários outros algoritmos para codificar valores de `decimal` como cadeias de caracteres de byte, mas essa mensagem é mais fácil de entender do que qualquer um deles.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="5ba4a-172">Os valores não são afetados pela endian em plataformas diferentes.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="5ba4a-173">A conversão entre esse tipo e o tipo de `decimal` BCL pode ser C# implementada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5ba4a-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="5ba4a-174">Sempre que usar tipos de mensagem personalizados como este, você *deve* documentá-los com comentários em `.proto`.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="5ba4a-175">Outros desenvolvedores podem então implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5ba4a-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5ba4a-176">[Anterior](protobuf-messages.md)
>[Próximo](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="5ba4a-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
