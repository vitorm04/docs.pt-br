---
title: Protobuf any e oneof Fields for Variant Types-gRPC for WCF Developers
description: Saiba como usar o tipo any e a palavra-chave oneof para representar tipos de objeto Variant em mensagens.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543190"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf os campos any e oneof para tipos Variant

A manipulação de tipos de propriedade dinâmica (ou seja, propriedades do tipo `object`) no Windows Communication Foundation (WCF) é complicada. Por exemplo, você deve especificar serializadores e fornecer atributos [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .

O buffer de protocolo (Protobuf) fornece duas opções mais simples para lidar com valores que podem ser de mais de um tipo. O tipo de `Any` pode representar qualquer tipo de mensagem Protobuf conhecido. E você pode usar a palavra-chave `oneof` para especificar que apenas um de vários campos pode ser definido em qualquer mensagem.

## <a name="any"></a>Qualquer

`Any` é um dos "tipos bem conhecidos" de Protobuf: uma coleção de tipos de mensagens úteis e reutilizáveis com implementações em todos os idiomas com suporte. Para usar o tipo de `Any`, você deve importar a definição de `google/protobuf/any.proto`.

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

No C# código, a classe `Any` fornece métodos para definir o campo, extrair a mensagem e verificar o tipo.

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

O código de reflexão interno de Protobuf usa o campo estático `Descriptor` em cada tipo gerado para resolver `Any` tipos de campo. Também há um método `TryUnpack<T>`, mas isso cria uma instância não inicializada de `T` mesmo quando ela falha. É melhor usar o método `Is`, conforme mostrado anteriormente.

## <a name="oneof"></a>Oneof

Os campos oneof são um recurso de linguagem: o compilador manipula a palavra-chave `oneof` quando gera a classe de mensagem. Usar `oneof` para especificar a mensagem de `ChangeNotification` pode ser assim:

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

Os campos dentro do conjunto de `oneof` devem ter números de campo exclusivos na declaração de mensagem geral.

Quando você usa `oneof`, o código C# gerado inclui uma enumeração que especifica quais dos campos foram definidos. Você pode testar a enumeração para localizar qual campo está definido. Os campos que não estão definidos retornam `null` ou o valor padrão, em vez de gerar uma exceção.

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

Definir qualquer campo que faça parte de um conjunto de `oneof` limpará automaticamente todos os outros campos no conjunto. Você não pode usar `repeated` com `oneof`. Em vez disso, você pode criar uma mensagem aninhada com o campo repetido ou o `oneof` definido como contornar essa limitação.

>[!div class="step-by-step"]
>[Anterior](protobuf-reserved.md)
>[Próximo](protobuf-enums.md)
