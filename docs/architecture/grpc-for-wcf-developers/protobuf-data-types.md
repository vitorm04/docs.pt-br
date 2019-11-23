---
title: Tipos de dados escalares Protobuf-gRPC para desenvolvedores do WCF
description: Saiba mais sobre os tipos de dados básico e bem conhecido com suporte do Protobuf e do gRPC no .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ae7f5f48099000dff0eefb36e23cb9b9f2ac517c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971546"
---
# <a name="protobuf-scalar-data-types"></a>Tipos de dados escalares de Protobuf

Protobuf dá suporte a um intervalo de tipos de valor escalar nativos. A tabela a seguir lista todos eles com seu C# tipo equivalente:

| Tipo de Protobuf | Tipo C#      | {1&gt;Observações&lt;1} |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

## <a name="notes"></a>{1&gt;Observações&lt;1}

1. A codificação padrão para `int32` e `int64` é ineficiente ao trabalhar com valores assinados. Se for provável que o campo contenha números negativos, use `sint32` ou `sint64` em vez disso. Os dois tipos são mapeados para os C# tipos `int` e `long`, respectivamente.
2. Os campos de `fixed` sempre usam o mesmo número de bytes, independentemente do valor. Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.
3. As cadeias de caracteres Protobuf são codificadas em UTF-8 (ou ASCII de 7 bits) e o comprimento codificado não pode ser maior que 2<sup>32</sup>.
4. O tempo de execução do Protobuf fornece um tipo de `ByteString` que mapeia C# facilmente de e para `byte[]` matrizes.

## <a name="other-net-primitive-types"></a>Outros tipos primitivos .NET

### <a name="dates-and-times"></a>Datas e horas

Os tipos escalares nativos não fornecem valores de data e hora, equivalentes a C#<xref:System.DateTimeOffset>, <xref:System.DateTime>e <xref:System.TimeSpan>. Esses tipos podem ser especificados usando algumas extensões de "tipos conhecidos" do Google, que fornecem geração de código e suporte a tempo de execução para tipos de campo mais complexos em todas as plataformas com suporte. A tabela a seguir mostra os tipos de data e hora:

| Tipo C# | Protobuf tipo bem conhecido |
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

As propriedades geradas na C# classe não são os tipos de data e hora do .net. As propriedades usam as classes `Timestamp` e `Duration` no namespace `Google.Protobuf.WellKnownTypes`, que fornecem métodos para converter de e para `DateTimeOffset`, `DateTime`e `TimeSpan`.

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
> O tipo de `Timestamp` funciona com horários UTC; `DateTimeOffset` valores sempre têm um deslocamento de zero e a propriedade `DateTime.Kind` sempre será `DateTimeKind.Utc`.

### <a name="systemguid"></a>System.Guid

O tipo de <xref:System.Guid>, conhecido como `UUID` em outras plataformas, não tem suporte direto de Protobuf e não há um tipo conhecido para ele. A melhor abordagem é manipular `Guid` valores como `string` campo, usando o formato hexadecimal `8-4-4-4-12` padrão (por exemplo, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), que pode ser analisado por todas as linguagens e plataformas. Não use um campo de `bytes` para valores de `Guid`, já que problemas com a endian podem resultar em comportamento irregular ao interagir com outras plataformas, como Java.

### <a name="nullable-types"></a>Tipos que permitem valor nulo

A geração de código Protobuf C# para o usa os tipos nativos, como `int` para `int32`. Isso significa que os valores são sempre incluídos e não podem ser nulos. Para valores que exigem NULL explícito, como usar `int?` em seu código C# , os "tipos bem conhecidos" de Protobuf incluem wrappers que são compilados para C# tipos anuláveis. Para usá-los, importe `wrappers.proto` para o arquivo `.proto`, da seguinte maneira:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf usará o `T?` simples (por exemplo, `int?`) para a propriedade de mensagem gerada.

A tabela a seguir mostra a lista completa de tipos de wrapper com C# seu tipo equivalente:

| Tipo C#   | Wrapper de tipo bem conhecido       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Os tipos bem conhecidos `Timestamp` e `Duration` são representados no .NET como classes, portanto, não há necessidade de uma versão anulável, mas é importante verificar se há nulo nas propriedades desses tipos ao converter para `DateTimeOffset` ou `TimeSpan`.

## <a name="decimals"></a>Decimals

O Protobuf não dá suporte nativo ao tipo de `decimal` .NET, apenas `double` e `float`. Há uma discussão em andamento no projeto Protobuf sobre a possibilidade de adicionar um tipo de `Decimal` padrão aos tipos conhecidos, com suporte de plataforma para linguagens e estruturas que dão suporte a ele, mas nada foi implementado ainda.

É possível criar uma definição de mensagem para representar o tipo de `decimal` que funcionaria para a serialização segura entre clientes e servidores .NET, mas os desenvolvedores em outras plataformas teriam que entender o formato usado e implementar sua própria manipulação.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Criando um tipo decimal personalizado para Protobuf

Uma implementação muito simples pode ser semelhante ao tipo de `Money` não padrão usado por algumas APIs do Google, sem o campo `currency`.

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

O campo `nanos` representa os valores de `0.999_999_999` para `-0.999_999_999`. Por exemplo, o valor `decimal` `1.5m` seria representado como `{ units = 1, nanos = 500_000_000 }` (é por isso que o campo `nanos` neste exemplo usa o tipo `sfixed32`, que codifica de forma mais eficiente do que `int32` para valores maiores). Se o campo `units` for negativo, o campo `nanos` também deverá ser negativo.

> [!NOTE]
> Há vários outros algoritmos para codificar valores de `decimal` como cadeias de caracteres de byte, mas essa mensagem é muito mais fácil de entender do que qualquer um deles, e os valores não são afetados pela *[ordenação](https://en.wikipedia.org/wiki/Endianness)* em diferentes plataformas.

A conversão entre esse tipo e o tipo de `decimal` BCL pode ser C# implementada como esta.

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
> Sempre que você usa tipos de mensagem de utilitário personalizados como este, você **deve** documentá-los com comentários no `.proto` para que outros desenvolvedores possam implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.

>[!div class="step-by-step"]
>[Anterior](protobuf-messages.md)
>[Próximo](protobuf-nested-types.md)
