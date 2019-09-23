---
title: Protobuf tipos aninhados-gRPC para desenvolvedores do WCF
description: Saiba mais sobre tipos de mensagens aninhadas em Protobuf e gRPC e como elas C#são geradas no.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184186"
---
# <a name="protobuf-nested-types"></a>Protobuf tipos aninhados

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Assim como C# permite que você declare classes dentro de outras classes, o Protobuf permite aninhar definições de mensagens dentro de outras mensagens. O exemplo a seguir mostra como criar tipos de mensagens aninhadas:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

No código gerado C# , o `Inner` tipo será declarado em uma classe estática `Types` aninhada dentro da `HelloRequest` classe:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)
