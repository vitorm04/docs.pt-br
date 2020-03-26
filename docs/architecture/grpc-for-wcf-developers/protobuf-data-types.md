---
title: Tipos de dados escalares protobuf - gRPC para desenvolvedores WCF
description: Conheça os tipos de dados básicos e conhecidos que o Protobuf e o gRPC suportam no .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249429"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="7530e-103">Tipos de dados escalares de Protobuf</span><span class="sxs-lookup"><span data-stu-id="7530e-103">Protobuf scalar data types</span></span>

<span data-ttu-id="7530e-104">O Buffer de Protocolo (Protobuf) suporta uma gama de tipos de valor escalar nativo.</span><span class="sxs-lookup"><span data-stu-id="7530e-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="7530e-105">A tabela a seguir lista todos eles com seu tipo C# equivalente:</span><span class="sxs-lookup"><span data-stu-id="7530e-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="7530e-106">Tipo protobuf</span><span class="sxs-lookup"><span data-stu-id="7530e-106">Protobuf type</span></span> | <span data-ttu-id="7530e-107">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="7530e-107">C# type</span></span>      | <span data-ttu-id="7530e-108">Observações</span><span class="sxs-lookup"><span data-stu-id="7530e-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="7530e-109">1</span><span class="sxs-lookup"><span data-stu-id="7530e-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="7530e-110">1</span><span class="sxs-lookup"><span data-stu-id="7530e-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="7530e-111">1</span><span class="sxs-lookup"><span data-stu-id="7530e-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="7530e-112">1</span><span class="sxs-lookup"><span data-stu-id="7530e-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="7530e-113">2</span><span class="sxs-lookup"><span data-stu-id="7530e-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="7530e-114">2</span><span class="sxs-lookup"><span data-stu-id="7530e-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="7530e-115">2</span><span class="sxs-lookup"><span data-stu-id="7530e-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="7530e-116">2</span><span class="sxs-lookup"><span data-stu-id="7530e-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="7530e-117">3</span><span class="sxs-lookup"><span data-stu-id="7530e-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="7530e-118">4</span><span class="sxs-lookup"><span data-stu-id="7530e-118">4</span></span>     |

<span data-ttu-id="7530e-119">Observações:</span><span class="sxs-lookup"><span data-stu-id="7530e-119">Notes:</span></span>

1. <span data-ttu-id="7530e-120">A codificação `int32` padrão `int64` para e é ineficiente quando você está trabalhando com valores assinados.</span><span class="sxs-lookup"><span data-stu-id="7530e-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="7530e-121">Se o seu campo provavelmente `sint32` contiver números negativos, use ou `sint64` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7530e-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="7530e-122">Esses tipos mapeiam `int` `long` para o C# e tipos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7530e-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="7530e-123">Os `fixed` campos sempre usam o mesmo número de bytes, não importa qual seja o valor.</span><span class="sxs-lookup"><span data-stu-id="7530e-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="7530e-124">Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="7530e-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="7530e-125">As seqüências protobuf são UTF-8 (ou ASCII de 7 bits) codificadas.</span><span class="sxs-lookup"><span data-stu-id="7530e-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="7530e-126">O comprimento codificado não pode ser maior que 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="7530e-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="7530e-127">O tempo de execução `ByteString` do Protobuf fornece `byte[]` um tipo que mapeia facilmente para e a partir de matrizes C#.</span><span class="sxs-lookup"><span data-stu-id="7530e-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="7530e-128">Outros tipos primitivos .NET</span><span class="sxs-lookup"><span data-stu-id="7530e-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="7530e-129">Datas e horas</span><span class="sxs-lookup"><span data-stu-id="7530e-129">Dates and times</span></span>

<span data-ttu-id="7530e-130">Os tipos de escalar nativo não fornecem valores de data <xref:System.DateTimeOffset>e <xref:System.DateTime>hora, equivalentes a C#'s , e <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="7530e-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="7530e-131">Você pode especificar esses tipos usando algumas das extensões "Tipos Bem Conhecidos" do Google.</span><span class="sxs-lookup"><span data-stu-id="7530e-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="7530e-132">Essas extensões fornecem suporte à geração de código e tempo de execução para tipos de campo complexos em todas as plataformas suportadas.</span><span class="sxs-lookup"><span data-stu-id="7530e-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="7530e-133">A tabela a seguir mostra os tipos de data e hora:</span><span class="sxs-lookup"><span data-stu-id="7530e-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="7530e-134">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="7530e-134">C# type</span></span> | <span data-ttu-id="7530e-135">Protobuf tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="7530e-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="7530e-136">As propriedades geradas na classe C# não são os tipos de data e hora .NET.</span><span class="sxs-lookup"><span data-stu-id="7530e-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="7530e-137">As propriedades `Timestamp` usam `Duration` o `Google.Protobuf.WellKnownTypes` e classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="7530e-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="7530e-138">Essas classes fornecem métodos para `DateTimeOffset`converter `DateTime`de `TimeSpan`e para , e .</span><span class="sxs-lookup"><span data-stu-id="7530e-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="7530e-139">O `Timestamp` tipo funciona com os horários UTC.</span><span class="sxs-lookup"><span data-stu-id="7530e-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="7530e-140">`DateTimeOffset`valores sempre têm um deslocamento `DateTime.Kind` de `DateTimeKind.Utc`zero, e a propriedade é sempre .</span><span class="sxs-lookup"><span data-stu-id="7530e-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="7530e-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="7530e-141">System.Guid</span></span>

<span data-ttu-id="7530e-142">O Protobuf não suporta <xref:System.Guid> diretamente o `UUID` tipo, conhecido como em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="7530e-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="7530e-143">Não há nenhum tipo bem conhecido para isso.</span><span class="sxs-lookup"><span data-stu-id="7530e-143">There's no well-known type for it.</span></span>

<span data-ttu-id="7530e-144">A melhor abordagem `Guid` é `string` lidar com valores `8-4-4-4-12` como campo, usando o formato `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`hexadecimal padrão (por exemplo, ).</span><span class="sxs-lookup"><span data-stu-id="7530e-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="7530e-145">Todos os idiomas e plataformas podem analisar esse formato.</span><span class="sxs-lookup"><span data-stu-id="7530e-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="7530e-146">Não use um `bytes` campo `Guid` para valores.</span><span class="sxs-lookup"><span data-stu-id="7530e-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="7530e-147">Problemas com *endianness* [(definição da Wikipédia)](https://en.wikipedia.org/wiki/Endianness)podem resultar em comportamento errático quando Protobuf está interagindo com outras plataformas, como Java.</span><span class="sxs-lookup"><span data-stu-id="7530e-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="7530e-148">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="7530e-148">Nullable types</span></span>

<span data-ttu-id="7530e-149">A geração de código Protobuf para C# `int` `int32`usa os tipos nativos, como para .</span><span class="sxs-lookup"><span data-stu-id="7530e-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="7530e-150">Assim, os valores estão sempre incluídos e não podem ser nulos.</span><span class="sxs-lookup"><span data-stu-id="7530e-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="7530e-151">Para valores que requerem nulidade explícita, como usar `int?` em seu código C#, os "Tipos Bem Conhecidos" do Protobuf incluem invólucros que são compilados para tipos C# anulados.</span><span class="sxs-lookup"><span data-stu-id="7530e-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="7530e-152">Para usá-los, `wrappers.proto` `.proto` importe em seu arquivo, assim:</span><span class="sxs-lookup"><span data-stu-id="7530e-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="7530e-153">O Protobuf usará `T?` o simples `int?`(por exemplo) para a propriedade de mensagem gerada.</span><span class="sxs-lookup"><span data-stu-id="7530e-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="7530e-154">A tabela a seguir mostra a lista completa de tipos de invólucros com seu tipo C# equivalente:</span><span class="sxs-lookup"><span data-stu-id="7530e-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="7530e-155">Tipo de C#</span><span class="sxs-lookup"><span data-stu-id="7530e-155">C# type</span></span>   | <span data-ttu-id="7530e-156">Invólucro tipo bem conhecido</span><span class="sxs-lookup"><span data-stu-id="7530e-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="7530e-157">Os tipos `Timestamp` conhecidos `Duration` são representados em .NET como classes.</span><span class="sxs-lookup"><span data-stu-id="7530e-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="7530e-158">Em C # 8 e além, você pode usar tipos de referência anulados.</span><span class="sxs-lookup"><span data-stu-id="7530e-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="7530e-159">Mas é importante verificar se há nulidade em propriedades desses `DateTimeOffset` `TimeSpan`tipos quando você está se convertendo para ou .</span><span class="sxs-lookup"><span data-stu-id="7530e-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="7530e-160">Decimais</span><span class="sxs-lookup"><span data-stu-id="7530e-160">Decimals</span></span>

<span data-ttu-id="7530e-161">Protobuf não suporta nativamente o `decimal` tipo `double` .NET, apenas e `float`.</span><span class="sxs-lookup"><span data-stu-id="7530e-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="7530e-162">Há uma discussão em andamento no projeto Protobuf sobre `Decimal` a possibilidade de adicionar um tipo padrão aos tipos conhecidos, com suporte de plataforma para idiomas e frameworks que o apoiam.</span><span class="sxs-lookup"><span data-stu-id="7530e-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="7530e-163">Nada foi implementado ainda.</span><span class="sxs-lookup"><span data-stu-id="7530e-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="7530e-164">É possível criar uma definição de `decimal` mensagem para representar o tipo que funcionaria para uma serialização segura entre clientes .NET e servidores.</span><span class="sxs-lookup"><span data-stu-id="7530e-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="7530e-165">Mas os desenvolvedores de outras plataformas teriam que entender o formato que está sendo usado e implementar seu próprio manuseio para ele.</span><span class="sxs-lookup"><span data-stu-id="7530e-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="7530e-166">Criando um tipo decimal personalizado para Protobuf</span><span class="sxs-lookup"><span data-stu-id="7530e-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="7530e-167">Uma implementação simples pode ser `Money` semelhante ao tipo não padrão `currency` que algumas APIs do Google usam, sem o campo.</span><span class="sxs-lookup"><span data-stu-id="7530e-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="7530e-168">O `nanos` campo representa `0.999_999_999` valores de até `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="7530e-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="7530e-169">Por exemplo, `decimal` `1.5m` o valor `{ units = 1, nanos = 500_000_000 }`seria representado como .</span><span class="sxs-lookup"><span data-stu-id="7530e-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="7530e-170">É por `nanos` isso que o `sfixed32` campo neste exemplo usa o `int32` tipo, que codifica de forma mais eficiente do que para valores maiores.</span><span class="sxs-lookup"><span data-stu-id="7530e-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="7530e-171">Se `units` o campo for `nanos` negativo, o campo também deve ser negativo.</span><span class="sxs-lookup"><span data-stu-id="7530e-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="7530e-172">Existem vários outros algoritmos `decimal` para codificar valores como strings de byte, mas esta mensagem é mais fácil de entender do que qualquer um deles.</span><span class="sxs-lookup"><span data-stu-id="7530e-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="7530e-173">Os valores não são afetados pela endianidade em diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="7530e-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="7530e-174">A conversão entre este `decimal` tipo e o tipo BCL pode ser implementada em C# assim:</span><span class="sxs-lookup"><span data-stu-id="7530e-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="7530e-175">Sempre que você usar tipos de mensagens personalizadas como esta, você *deve* documentá-los com comentários em `.proto`.</span><span class="sxs-lookup"><span data-stu-id="7530e-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="7530e-176">Outros desenvolvedores podem então implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="7530e-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7530e-177">[Próximo](protobuf-messages.md)
>[anterior](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="7530e-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
