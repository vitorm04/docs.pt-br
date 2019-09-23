---
title: Tipos de dados escalares Protobuf-gRPC para desenvolvedores do WCF
description: Saiba mais sobre os tipos de dados básico e bem conhecido com suporte do Protobuf e do gRPC no .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184263"
---
# <a name="protobuf-scalar-data-types"></a>Tipos de dados escalares Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf dá suporte a um intervalo de tipos de valor escalar nativos. A tabela a seguir lista todos eles com seu C# tipo equivalente:

| Tipo de Protobuf | Tipo de C#      | Observações |
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

## <a name="notes"></a>Observações

1. A codificação padrão para `int32` o `int64` e o é ineficiente ao trabalhar com valores assinados. Se for provável que o campo contenha números negativos, `sint32` use `sint64` ou em vez disso. Os dois tipos são mapeados `long` para os C# `int` tipos e, respectivamente.
2. Os `fixed` campos sempre usam o mesmo número de bytes, independentemente do valor. Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.
3. As cadeias de caracteres Protobuf são codificadas em UTF-8 (ou ASCII de 7 bits) e o comprimento codificado não pode ser maior que 2<sup>32</sup>.
4. O tempo de execução do `ByteString` Protobuf fornece um tipo que mapeia facilmente C# `byte[]` de e para matrizes.

## <a name="other-net-primitive-types"></a>Outros tipos primitivos .NET

### <a name="dates-and-times"></a>Datas e horas

Os tipos escalares nativos não fornecem valores de data e hora, equivalentes <xref:System.DateTimeOffset>a <xref:System.DateTime> C#, e <xref:System.TimeSpan>. Esses tipos podem ser especificados usando algumas extensões de "tipos conhecidos" do Google, que fornecem geração de código e suporte a tempo de execução para tipos de campo mais complexos em todas as plataformas com suporte. A tabela a seguir mostra os tipos de data e hora:

| Tipo de C# | Protobuf tipo bem conhecido |
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

As propriedades geradas na C# classe não são os tipos de data e hora do .net. As propriedades usam as `Timestamp` classes `Duration` e no `Google.Protobuf.WellKnownTypes` namespace, `DateTimeOffset`que fornecem métodos para converter de e para, `DateTime`e `TimeSpan`.

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
> O `Timestamp` tipo funciona com horários UTC; os valores sempre têm um deslocamento de zero e a `DateTime.Kind` propriedade sempre `DateTimeKind.Utc`será. `DateTimeOffset`

### <a name="systemguid"></a>System.Guid

O <xref:System.Guid> tipo, conhecido como `UUID` em outras plataformas, não tem suporte direto de Protobuf e não há um tipo conhecido para ele. A melhor `Guid` abordagem é manipular valores como `string` campo, usando o formato hexadecimal `8-4-4-4-12` padrão (por exemplo, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), que pode ser analisado por todas as linguagens e plataformas. Não use um `bytes` campo para `Guid` valores, já que problemas com a endian podem resultar em comportamento irregular ao interagir com outras plataformas, como Java.

### <a name="nullable-types"></a>Tipos que permitem valor nulo

A geração de código Protobuf C# para o usa os tipos nativos, `int` como `int32`para. Isso significa que os valores são sempre incluídos e não podem ser nulos. Para valores que exigem NULL explícito, como usar `int?` em seu código, os C# "tipos bem conhecidos" de Protobuf incluem wrappers que são compilados para C# tipos anuláveis. Para usá-los, `wrappers.proto` importe para `.proto` o arquivo, da seguinte maneira:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf usará o simples `T?` (por exemplo, `int?`) para a propriedade Message gerada.

A tabela a seguir mostra a lista completa de tipos de wrapper com C# seu tipo equivalente:

| Tipo de C#   | Wrapper de tipo bem conhecido       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Os tipos `Timestamp` bem conhecidos e `Duration` são representados no .net como classes, portanto, não há necessidade de uma versão anulável, mas é importante verificar se há nulo nas propriedades desses tipos ao converter para `DateTimeOffset` ou `TimeSpan`.

## <a name="decimals"></a>Decimais

O Protobuf não dá suporte nativo ao `decimal` tipo .net, `double` apenas `float`e. Há uma discussão contínua no projeto Protobuf sobre a possibilidade de adicionar um tipo padrão `Decimal` aos tipos conhecidos, com suporte de plataforma para linguagens e estruturas que dão suporte a ele, mas nada foi implementado ainda.

É possível criar uma definição de mensagem para representar o `decimal` tipo que funcionaria para a serialização segura entre clientes e servidores .net, mas os desenvolvedores em outras plataformas teriam que entender o formato usado e implementar seus próprios lidando com ele.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Criando um tipo decimal personalizado para Protobuf

Uma implementação muito simples pode ser semelhante ao tipo não padrão `Money` usado por algumas APIs do Google, sem o `currency` campo.

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

O `nanos` campo representa valores de `0.999_999_999` a `-0.999_999_999`. Por exemplo, o `decimal` valor `1.5m` seria representado como `{ units = 1, nanos = 500_000_000 }` (é por isso que o `nanos` campo neste exemplo usa o `sfixed32` tipo, que codifica de forma mais eficiente do que `int32` para valores maiores). Se o `units` campo for negativo, o `nanos` campo também deverá ser negativo.

> [!NOTE]
> Há vários outros algoritmos para codificar `decimal` valores como cadeias de caracteres de byte, mas essa mensagem é muito mais fácil de entender do que qualquer um deles, e os valores não são afetados pela *[ordenação](https://en.wikipedia.org/wiki/Endianness)* em diferentes plataformas.

A conversão entre esse tipo e o `decimal` tipo de BCL poderia ser C# implementada como esta.

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
> Sempre que usar tipos de mensagem de utilitário personalizados como este, você **deve** documentá-los `.proto` com comentários no para que outros desenvolvedores possam implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.

>[!div class="step-by-step"]
>[Anterior](protobuf-messages.md)
>[Próximo](protobuf-nested-types.md)
