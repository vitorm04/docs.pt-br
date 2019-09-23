---
title: Mapas do Protobuf para dicionários-gRPC para desenvolvedores do WCF
description: Entenda como usar o Protobuf Maps para representar. Tipos de dicionário de rede.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184207"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mapas do Protobuf para dicionários

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

É importante poder representar coleções arbitrárias de valores nomeados em mensagens. No .NET, isso é normalmente Tratado usando tipos de dicionário. O equivalente de Protobuf do tipo <xref:System.Collections.Generic.IDictionary%602> .net é o `map<key_type, value_type>` tipo. Esta seção mostra como declarar um `map` no Protobuf e como usar o código gerado.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

No código gerado, `map` os campos usam a `Google.Protobuf.Collections.MapField<TKey, TValue>` classe, que implementa as interfaces de coleção do .NET padrão, incluindo. <xref:System.Collections.Generic.IDictionary%602>

Os campos de mapa não podem ser repetidos diretamente em uma definição de mensagem, mas você pode criar uma mensagem aninhada contendo um mapa e usar `repeated` no tipo de mensagem, como no exemplo a seguir:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Usando Propriedades MapField no código

As `MapField` Propriedades geradas `map` a partir de campos são somente leitura e nunca `null`serão. Para definir uma propriedade de mapa, use `Add(IDictionary<TKey,TValue> values)` o método na propriedade `MapField` Empty para copiar valores de qualquer dicionário .net.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Leitura adicional

Para obter mais informações sobre o Protobuf, consulte a documentação oficial do [Protobuf](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Anterior](protobuf-enums.md)
>[Próximo](wcf-services-to-grpc-comparison.md)
