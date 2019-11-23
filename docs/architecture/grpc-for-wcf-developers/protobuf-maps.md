---
title: Mapas do Protobuf para dicionários-gRPC para desenvolvedores do WCF
description: Entenda como usar o Protobuf Maps para representar. Tipos de dicionário de rede.
ms.date: 09/09/2019
ms.openlocfilehash: 8b4f29daa263f329dc533d3ddc596d0f47c1b6e0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967423"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="c83cb-103">Mapas de Protobuf para dicionários</span><span class="sxs-lookup"><span data-stu-id="c83cb-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="c83cb-104">É importante poder representar coleções arbitrárias de valores nomeados em mensagens.</span><span class="sxs-lookup"><span data-stu-id="c83cb-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="c83cb-105">No .NET, isso é normalmente Tratado usando tipos de dicionário.</span><span class="sxs-lookup"><span data-stu-id="c83cb-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="c83cb-106">O equivalente do Protobuf do tipo .NET <xref:System.Collections.Generic.IDictionary%602> é o tipo de `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="c83cb-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="c83cb-107">Esta seção mostra como declarar uma `map` no Protobuf e como usar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c83cb-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="c83cb-108">No código gerado, `map` campos usam a classe `Google.Protobuf.Collections.MapField<TKey, TValue>`, que implementa as interfaces de coleção do .NET padrão, incluindo <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="c83cb-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="c83cb-109">Os campos de mapa não podem ser repetidos diretamente em uma definição de mensagem, mas você pode criar uma mensagem aninhada contendo um mapa e usar `repeated` no tipo de mensagem, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c83cb-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="c83cb-110">Usando Propriedades MapField no código</span><span class="sxs-lookup"><span data-stu-id="c83cb-110">Using MapField properties in code</span></span>

<span data-ttu-id="c83cb-111">As propriedades `MapField` geradas de `map` campos são somente leitura e nunca serão `null`das.</span><span class="sxs-lookup"><span data-stu-id="c83cb-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="c83cb-112">Para definir uma propriedade de mapa, use o método `Add(IDictionary<TKey,TValue> values)` na propriedade `MapField` vazia para copiar valores de qualquer dicionário .NET.</span><span class="sxs-lookup"><span data-stu-id="c83cb-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="c83cb-113">Leitura adicional</span><span class="sxs-lookup"><span data-stu-id="c83cb-113">Further reading</span></span>

<span data-ttu-id="c83cb-114">Para obter mais informações sobre o Protobuf, consulte a documentação oficial do [Protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="c83cb-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c83cb-115">[Anterior](protobuf-enums.md)
>[Próximo](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="c83cb-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
