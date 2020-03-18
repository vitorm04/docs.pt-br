---
title: Tipos de dados escalares protobuf - gRPC para desenvolvedores WCF
description: Conheça os tipos de dados básicos e conhecidos que o Protobuf e o gRPC suportam no .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: a40f51fa32ddb97ba417ec01f31e1f0187f0d544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148121"
---
# <a name="protobuf-scalar-data-types"></a>Tipos de dados escalares de Protobuf

O Buffer de Protocolo (Protobuf) suporta uma gama de tipos de valor escalar nativo. A tabela a seguir lista todos eles com seu tipo C# equivalente:

| Tipo protobuf | Tipo de C#      | Observações |
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

Observações:

1. A codificação `int32` padrão `int64` para e é ineficiente quando você está trabalhando com valores assinados. Se o seu campo provavelmente `sint32` contiver números negativos, use ou `sint64` em vez disso. Esses tipos mapeiam `int` `long` para o C# e tipos, respectivamente.
2. Os `fixed` campos sempre usam o mesmo número de bytes, não importa qual seja o valor. Esse comportamento torna a serialização e a desserialização mais rápidas para valores maiores.
3. As seqüências protobuf são UTF-8 (ou ASCII de 7 bits) codificadas. O comprimento codificado não pode ser maior que 2<sup>32</sup>.
4. O tempo de execução `ByteString` do Protobuf fornece `byte[]` um tipo que mapeia facilmente para e a partir de matrizes C#.

## <a name="other-net-primitive-types"></a>Outros tipos primitivos .NET

### <a name="dates-and-times"></a>Datas e horas

Os tipos de escalar nativo não fornecem valores de data <xref:System.DateTimeOffset>e <xref:System.DateTime>hora, equivalentes a C#'s , e <xref:System.TimeSpan>. Você pode especificar esses tipos usando algumas das extensões "Tipos Bem Conhecidos" do Google. Essas extensões fornecem suporte à geração de código e tempo de execução para tipos de campo complexos em todas as plataformas suportadas.

A tabela a seguir mostra os tipos de data e hora:

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

As propriedades geradas na classe C# não são os tipos de data e hora .NET. As propriedades `Timestamp` usam `Duration` o `Google.Protobuf.WellKnownTypes` e classes no namespace. Essas classes fornecem métodos para `DateTimeOffset`converter `DateTime`de `TimeSpan`e para , e .

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
> O `Timestamp` tipo funciona com os horários UTC. `DateTimeOffset`valores sempre têm um deslocamento `DateTime.Kind` de `DateTimeKind.Utc`zero, e a propriedade é sempre .

### <a name="systemguid"></a>System.Guid

O Protobuf não suporta <xref:System.Guid> diretamente o `UUID` tipo, conhecido como em outras plataformas. Não há nenhum tipo bem conhecido para isso.

A melhor abordagem `Guid` é `string` lidar com valores `8-4-4-4-12` como campo, usando o formato `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`hexadecimal padrão (por exemplo, ). Todos os idiomas e plataformas podem analisar esse formato.

Não use um `bytes` campo `Guid` para valores. Problemas com *endianness* [(definição da Wikipédia)](https://en.wikipedia.org/wiki/Endianness)podem resultar em comportamento errático quando Protobuf está interagindo com outras plataformas, como Java.

### <a name="nullable-types"></a>Tipos que permitem valor nulo

A geração de código Protobuf para C# `int` `int32`usa os tipos nativos, como para . Assim, os valores estão sempre incluídos e não podem ser nulos.

Para valores que requerem nulidade explícita, como usar `int?` em seu código C#, os "Tipos Bem Conhecidos" do Protobuf incluem invólucros que são compilados para tipos C# anulados. Para usá-los, `wrappers.proto` `.proto` importe em seu arquivo, assim:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

O Protobuf usará `T?` o simples `int?`(por exemplo) para a propriedade de mensagem gerada.

A tabela a seguir mostra a lista completa de tipos de invólucros com seu tipo C# equivalente:

| Tipo de C#   | Invólucro tipo bem conhecido       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Os tipos `Timestamp` conhecidos `Duration` são representados em .NET como classes, portanto não há necessidade de uma versão anulada. Mas é importante verificar se há nulidade em propriedades desses `DateTimeOffset` `TimeSpan`tipos quando você está se convertendo para ou .

## <a name="decimals"></a>Decimais

Protobuf não suporta nativamente o `decimal` tipo `double` .NET, apenas e `float`. Há uma discussão em andamento no projeto Protobuf sobre `Decimal` a possibilidade de adicionar um tipo padrão aos tipos conhecidos, com suporte de plataforma para idiomas e frameworks que o apoiam. Nada foi implementado ainda.

É possível criar uma definição de `decimal` mensagem para representar o tipo que funcionaria para uma serialização segura entre clientes .NET e servidores. Mas os desenvolvedores de outras plataformas teriam que entender o formato que está sendo usado e implementar seu próprio manuseio para ele.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Criando um tipo decimal personalizado para Protobuf

Uma implementação simples pode ser `Money` semelhante ao tipo não padrão `currency` que algumas APIs do Google usam, sem o campo.

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

O `nanos` campo representa `0.999_999_999` valores de até `-0.999_999_999`. Por exemplo, `decimal` `1.5m` o valor `{ units = 1, nanos = 500_000_000 }`seria representado como . É por `nanos` isso que o `sfixed32` campo neste exemplo usa o `int32` tipo, que codifica de forma mais eficiente do que para valores maiores. Se `units` o campo for `nanos` negativo, o campo também deve ser negativo.

> [!NOTE]
> Existem vários outros algoritmos `decimal` para codificar valores como strings de byte, mas esta mensagem é mais fácil de entender do que qualquer um deles. Os valores não são afetados pela endianidade em diferentes plataformas.

A conversão entre este `decimal` tipo e o tipo BCL pode ser implementada em C# assim:

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
> Sempre que você usar tipos de mensagens personalizadas como esta, você *deve* documentá-los com comentários em `.proto`. Outros desenvolvedores podem então implementar a conversão de e para o tipo equivalente em seu próprio idioma ou estrutura.

>[!div class="step-by-step"]
>[Próximo](protobuf-messages.md)
>[anterior](protobuf-nested-types.md)
