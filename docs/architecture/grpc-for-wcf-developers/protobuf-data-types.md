---
title: Tipos de dados escalares Protobuf-gRPC para desenvolvedores do WCF
description: Saiba mais sobre os tipos de dados básico e conhecido que Protobuf e gRPC dão suporte ao .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: 5447067b953d257258950d020636e0b38245e20d
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573638"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="40169-103">Tipos de dados escalares de Protobuf</span><span class="sxs-lookup"><span data-stu-id="40169-103">Protobuf scalar data types</span></span>

<span data-ttu-id="40169-104">O buffer de protocolo (Protobuf) dá suporte a um intervalo de tipos de valores escalares nativos.</span><span class="sxs-lookup"><span data-stu-id="40169-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="40169-105">A tabela a seguir lista todos eles com seu tipo C# equivalente:</span><span class="sxs-lookup"><span data-stu-id="40169-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="40169-106">Tipo de Protobuf</span><span class="sxs-lookup"><span data-stu-id="40169-106">Protobuf type</span></span> | <span data-ttu-id="40169-107">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="40169-107">C# type</span></span>      | <span data-ttu-id="40169-108">Observações</span><span class="sxs-lookup"><span data-stu-id="40169-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="40169-109">1</span><span class="sxs-lookup"><span data-stu-id="40169-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="40169-110">1</span><span class="sxs-lookup"><span data-stu-id="40169-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="40169-111">1</span><span class="sxs-lookup"><span data-stu-id="40169-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="40169-112">1</span><span class="sxs-lookup"><span data-stu-id="40169-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="40169-113">2</span><span class="sxs-lookup"><span data-stu-id="40169-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="40169-114">2</span><span class="sxs-lookup"><span data-stu-id="40169-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="40169-115">2</span><span class="sxs-lookup"><span data-stu-id="40169-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="40169-116">2</span><span class="sxs-lookup"><span data-stu-id="40169-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="40169-117">3</span><span class="sxs-lookup"><span data-stu-id="40169-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="40169-118">4</span><span class="sxs-lookup"><span data-stu-id="40169-118">4</span></span>     |

<span data-ttu-id="40169-119">Observações:</span><span class="sxs-lookup"><span data-stu-id="40169-119">Notes:</span></span>

1. <span data-ttu-id="40169-120">A codificação padrão para o `int32` e o `int64` é ineficiente quando você está trabalhando com valores assinados.</span><span class="sxs-lookup"><span data-stu-id="40169-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="40169-121">Se for provável que o campo contenha números negativos, use `sint32` ou `sint64` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="40169-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="40169-122">Esses tipos são mapeados para o C# `int` e `long` tipos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="40169-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="40169-123">Os `fixed` campos sempre usam o mesmo número de bytes, independentemente do valor.</span><span class="sxs-lookup"><span data-stu-id="40169-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="40169-124">Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="40169-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="40169-125">As cadeias de caracteres Protobuf são codificadas em UTF-8 (ou ASCII de 7 bits).</span><span class="sxs-lookup"><span data-stu-id="40169-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="40169-126">O comprimento codificado não pode ser maior que 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="40169-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="40169-127">O tempo de execução do Protobuf fornece um `ByteString` tipo que mapeia facilmente para e de `byte[]` matrizes C#.</span><span class="sxs-lookup"><span data-stu-id="40169-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="40169-128">Outros tipos primitivos .NET</span><span class="sxs-lookup"><span data-stu-id="40169-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="40169-129">Datas e horas</span><span class="sxs-lookup"><span data-stu-id="40169-129">Dates and times</span></span>

<span data-ttu-id="40169-130">Os tipos escalares nativos não fornecem valores de data e hora, equivalentes a C# <xref:System.DateTimeOffset> , <xref:System.DateTime> e <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="40169-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="40169-131">Você pode especificar esses tipos usando algumas das extensões "tipos conhecidos" do Google.</span><span class="sxs-lookup"><span data-stu-id="40169-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="40169-132">Essas extensões fornecem geração de código e suporte a tempo de execução para tipos de campo complexos em plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="40169-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="40169-133">A tabela a seguir mostra os tipos de data e hora:</span><span class="sxs-lookup"><span data-stu-id="40169-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="40169-134">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="40169-134">C# type</span></span> | <span data-ttu-id="40169-135">Protobuf tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="40169-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="40169-136">As propriedades geradas na classe C# não são os tipos de data e hora do .NET.</span><span class="sxs-lookup"><span data-stu-id="40169-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="40169-137">As propriedades usam as `Timestamp` `Duration` classes e no `Google.Protobuf.WellKnownTypes` namespace.</span><span class="sxs-lookup"><span data-stu-id="40169-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="40169-138">Essas classes fornecem métodos para converter de e para `DateTimeOffset` , `DateTime` e `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="40169-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="40169-139">O `Timestamp` tipo funciona com horas UTC.</span><span class="sxs-lookup"><span data-stu-id="40169-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="40169-140">`DateTimeOffset` os valores sempre têm um deslocamento de zero e a `DateTime.Kind` propriedade é sempre `DateTimeKind.Utc` .</span><span class="sxs-lookup"><span data-stu-id="40169-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="40169-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="40169-141">System.Guid</span></span>

<span data-ttu-id="40169-142">O Protobuf não oferece suporte direto ao <xref:System.Guid> tipo, conhecido como `UUID` em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="40169-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="40169-143">Não há um tipo bem conhecido para ele.</span><span class="sxs-lookup"><span data-stu-id="40169-143">There's no well-known type for it.</span></span>

<span data-ttu-id="40169-144">A melhor abordagem é manipular `Guid` valores como um `string` campo, usando o `8-4-4-4-12` formato hexadecimal padrão (por exemplo, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3` ).</span><span class="sxs-lookup"><span data-stu-id="40169-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="40169-145">Todas as linguagens e plataformas podem analisar esse formato.</span><span class="sxs-lookup"><span data-stu-id="40169-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="40169-146">Não use um `bytes` campo para `Guid` valores.</span><span class="sxs-lookup"><span data-stu-id="40169-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="40169-147">Problemas com a *endian* ([definição da Wikipédia](https://en.wikipedia.org/wiki/Endianness)) podem resultar em comportamento irregular quando o Protobuf está interagindo com outras plataformas, como Java.</span><span class="sxs-lookup"><span data-stu-id="40169-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="40169-148">Tipos anuláveis</span><span class="sxs-lookup"><span data-stu-id="40169-148">Nullable types</span></span>

<span data-ttu-id="40169-149">A geração de código Protobuf para C# usa os tipos nativos, como `int` para `int32` .</span><span class="sxs-lookup"><span data-stu-id="40169-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="40169-150">Portanto, os valores são sempre incluídos e não podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="40169-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="40169-151">Para valores que exigem NULL explícito, como usar `int?` em seu código C#, "tipos conhecidos" de Protobuf incluem wrappers que são compilados para tipos em C# anuláveis.</span><span class="sxs-lookup"><span data-stu-id="40169-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="40169-152">Para usá-los, importe `wrappers.proto` para o `.proto` arquivo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="40169-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="40169-153">Protobuf usará o simples `T?` (por exemplo, `int?` ) para a propriedade Message gerada.</span><span class="sxs-lookup"><span data-stu-id="40169-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="40169-154">A tabela a seguir mostra a lista completa de tipos de wrapper com seu tipo C# equivalente:</span><span class="sxs-lookup"><span data-stu-id="40169-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="40169-155">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="40169-155">C# type</span></span>   | <span data-ttu-id="40169-156">Wrapper de tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="40169-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="40169-157">Os tipos bem conhecidos `Timestamp` e `Duration` são representados no .net como classes.</span><span class="sxs-lookup"><span data-stu-id="40169-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="40169-158">No C# 8 e além disso, você pode usar tipos de referência anuláveis.</span><span class="sxs-lookup"><span data-stu-id="40169-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="40169-159">Mas é importante verificar se há nulo nas propriedades desses tipos quando você estiver convertendo para `DateTimeOffset` ou `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="40169-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="40169-160">Decimais</span><span class="sxs-lookup"><span data-stu-id="40169-160">Decimals</span></span>

<span data-ttu-id="40169-161">O Protobuf não dá suporte nativo ao `decimal` tipo .net, apenas `double` e `float` .</span><span class="sxs-lookup"><span data-stu-id="40169-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="40169-162">Há uma discussão contínua no projeto Protobuf sobre a possibilidade de adicionar um `Decimal` tipo padrão aos tipos conhecidos, com suporte de plataforma para linguagens e estruturas que dão suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="40169-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="40169-163">Nada foi implementado ainda.</span><span class="sxs-lookup"><span data-stu-id="40169-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="40169-164">É possível criar uma definição de mensagem para representar o `decimal` tipo que funcionaria para a serialização segura entre clientes e servidores .net.</span><span class="sxs-lookup"><span data-stu-id="40169-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="40169-165">Mas os desenvolvedores de outras plataformas teriam que entender o formato que está sendo usado e implementar sua própria manipulação.</span><span class="sxs-lookup"><span data-stu-id="40169-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="40169-166">Criando um tipo decimal personalizado para Protobuf</span><span class="sxs-lookup"><span data-stu-id="40169-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="40169-167">Uma implementação simples pode ser semelhante ao tipo não padrão `Money` que algumas APIs do Google usam, sem o `currency` campo.</span><span class="sxs-lookup"><span data-stu-id="40169-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message DecimalValue {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

<span data-ttu-id="40169-168">O `nanos` campo representa valores de `0.999_999_999` a `-0.999_999_999` .</span><span class="sxs-lookup"><span data-stu-id="40169-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="40169-169">Por exemplo, o `decimal` valor `1.5m` seria representado como `{ units = 1, nanos = 500_000_000 }` .</span><span class="sxs-lookup"><span data-stu-id="40169-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="40169-170">É por isso que o `nanos` campo neste exemplo usa o `sfixed32` tipo, que codifica com mais eficiência do que `int32` para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="40169-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="40169-171">Se o `units` campo for negativo, o `nanos` campo também deverá ser negativo.</span><span class="sxs-lookup"><span data-stu-id="40169-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="40169-172">Há vários outros algoritmos para codificar `decimal` valores como cadeias de caracteres de byte, mas essa mensagem é mais fácil de entender do que qualquer um deles.</span><span class="sxs-lookup"><span data-stu-id="40169-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="40169-173">Os valores não são afetados pela endian em plataformas diferentes.</span><span class="sxs-lookup"><span data-stu-id="40169-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="40169-174">A conversão entre esse tipo e o `decimal` tipo de BCL pode ser implementada em C# da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="40169-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

```csharp
namespace CustomTypes
{
    public partial class DecimalValue
    {
        private const decimal NanoFactor = 1_000_000_000;
        public DecimalValue(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.DecimalValue grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.DecimalValue(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.DecimalValue(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="40169-175">Sempre que usar tipos de mensagem personalizados como este, você *deve* documentá-los com comentários no `.proto` .</span><span class="sxs-lookup"><span data-stu-id="40169-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="40169-176">Outros desenvolvedores podem então implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="40169-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="40169-177">[Anterior](protobuf-messages.md) 
> [Avançar](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="40169-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
