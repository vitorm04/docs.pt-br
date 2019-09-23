---
title: Protobuf any e oneof Fields for Variant Types-gRPC for WCF Developers
description: Saiba como usar o tipo any e a palavra-chave oneof para representar tipos de objeto Variant em mensagens.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184277"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf os campos any e oneof para tipos Variant

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

A manipulação de tipos de propriedade dinâmica (ou seja, `object`Propriedades do tipo) no WCF é complicada. Os serializadores devem ser especificados, os atributos [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) devem ser fornecidos e assim por diante.

O Protobuf fornece duas opções mais simples para lidar com valores que podem ser de mais de um tipo. O `Any` tipo pode representar qualquer tipo de mensagem Protobuf conhecida, enquanto `oneof` a palavra-chave permite que você especifique que apenas um de vários campos pode ser definido em qualquer mensagem específica.

## <a name="any"></a>Qualquer

`Any`é um dos "tipos bem conhecidos" de Protobuf: uma coleção de tipos de mensagens úteis e reutilizáveis com implementações em todos os idiomas com suporte. Para usar o `Any` tipo, você deve importar a `google/protobuf/any.proto` definição.

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

No C# código, a `Any` classe fornece métodos para definir o campo, extrair a mensagem e verificar o tipo.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

O `Descriptor` campo estático em cada tipo gerado é usado pelo código de reflexão interno de Protobuf para `Any` resolver tipos de campo. Há também um `TryUnpack<T>` método, mas isso cria uma instância não inicializada de `T` mesmo quando ela falha, portanto, é melhor usar o `Is` método, como mostrado acima.

## <a name="oneof"></a>Oneof

Os campos oneof são um recurso de linguagem `oneof` : a palavra-chave é manipulada pelo compilador quando ele gera a classe de mensagem. Usar `oneof` para especificar a `ChangeNotification` mensagem pode ser semelhante a este:

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

Os campos dentro `oneof` do conjunto devem ter números de campo exclusivos dentro da declaração de mensagem geral.

Quando você usa `oneof`, o código C# gerado inclui uma enumeração que especifica quais dos campos foram definidos. Você pode testar a enumeração para localizar qual campo está definido. Campos que não são definidos `null` como Return ou o valor padrão, em vez de lançar uma exceção.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

Definir qualquer campo que faça parte de um `oneof` conjunto limpará automaticamente todos os outros campos no conjunto. Você não pode `repeated` usar `oneof`com. Em vez disso, você pode criar uma mensagem aninhada com o campo repetido ou o `oneof` conjunto para contornar essa limitação.

>[!div class="step-by-step"]
>[Anterior](protobuf-reserved.md)
>[Próximo](protobuf-enums.md)
