---
title: Mapas do Protobuf para dicionários-gRPC para desenvolvedores do WCF
description: Entenda como usar o Protobuf Maps para representar tipos de dicionário no .NET.
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543125"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="6a3c3-103">Mapas de Protobuf para dicionários</span><span class="sxs-lookup"><span data-stu-id="6a3c3-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="6a3c3-104">É importante poder representar coleções arbitrárias de valores nomeados em mensagens.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="6a3c3-105">No .NET, isso é normalmente tratado por meio de tipos de dicionário.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="6a3c3-106">O equivalente do tipo de <xref:System.Collections.Generic.IDictionary%602> do .NET no buffer de protocolo (Protobuf) é o tipo de `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="6a3c3-107">Esta seção mostra como declarar um tipo de `map` em Protobuf e como usar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="6a3c3-108">No código gerado, `map` campos usam a classe `Google.Protobuf.Collections.MapField<TKey, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="6a3c3-109">Essa classe implementa as interfaces de coleção do .NET padrão, incluindo <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="6a3c3-110">Os campos de mapa não podem ser repetidos diretamente em uma definição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="6a3c3-111">Mas você pode criar uma mensagem aninhada que contém um mapa e usar `repeated` no tipo de mensagem, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6a3c3-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="6a3c3-112">Usando Propriedades MapField no código</span><span class="sxs-lookup"><span data-stu-id="6a3c3-112">Using MapField properties in code</span></span>

<span data-ttu-id="6a3c3-113">As propriedades `MapField` geradas de `map` campos são somente leitura e nunca serão `null`das.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="6a3c3-114">Para definir uma propriedade de mapa, use o método `Add(IDictionary<TKey,TValue> values)` na propriedade `MapField` vazia para copiar valores de qualquer dicionário .NET.</span><span class="sxs-lookup"><span data-stu-id="6a3c3-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="6a3c3-115">Leitura adicional</span><span class="sxs-lookup"><span data-stu-id="6a3c3-115">Further reading</span></span>

<span data-ttu-id="6a3c3-116">Para obter mais informações sobre o Protobuf, consulte a documentação oficial do [Protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="6a3c3-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6a3c3-117">[Anterior](protobuf-enums.md)
>[Próximo](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="6a3c3-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
