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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="289e9-103">Mapas do Protobuf para dicionários</span><span class="sxs-lookup"><span data-stu-id="289e9-103">Protobuf maps for dictionaries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="289e9-104">É importante poder representar coleções arbitrárias de valores nomeados em mensagens.</span><span class="sxs-lookup"><span data-stu-id="289e9-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="289e9-105">No .NET, isso é normalmente Tratado usando tipos de dicionário.</span><span class="sxs-lookup"><span data-stu-id="289e9-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="289e9-106">O equivalente de Protobuf do tipo <xref:System.Collections.Generic.IDictionary%602> .net é o `map<key_type, value_type>` tipo.</span><span class="sxs-lookup"><span data-stu-id="289e9-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="289e9-107">Esta seção mostra como declarar um `map` no Protobuf e como usar o código gerado.</span><span class="sxs-lookup"><span data-stu-id="289e9-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="289e9-108">No código gerado, `map` os campos usam a `Google.Protobuf.Collections.MapField<TKey, TValue>` classe, que implementa as interfaces de coleção do .NET padrão, incluindo. <xref:System.Collections.Generic.IDictionary%602></span><span class="sxs-lookup"><span data-stu-id="289e9-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="289e9-109">Os campos de mapa não podem ser repetidos diretamente em uma definição de mensagem, mas você pode criar uma mensagem aninhada contendo um mapa e usar `repeated` no tipo de mensagem, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="289e9-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="289e9-110">Usando Propriedades MapField no código</span><span class="sxs-lookup"><span data-stu-id="289e9-110">Using MapField properties in code</span></span>

<span data-ttu-id="289e9-111">As `MapField` Propriedades geradas `map` a partir de campos são somente leitura e nunca `null`serão.</span><span class="sxs-lookup"><span data-stu-id="289e9-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="289e9-112">Para definir uma propriedade de mapa, use `Add(IDictionary<TKey,TValue> values)` o método na propriedade `MapField` Empty para copiar valores de qualquer dicionário .net.</span><span class="sxs-lookup"><span data-stu-id="289e9-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="289e9-113">Leitura adicional</span><span class="sxs-lookup"><span data-stu-id="289e9-113">Further reading</span></span>

<span data-ttu-id="289e9-114">Para obter mais informações sobre o Protobuf, consulte a documentação oficial do [Protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="289e9-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="289e9-115">[Anterior](protobuf-enums.md)
>[Próximo](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="289e9-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
