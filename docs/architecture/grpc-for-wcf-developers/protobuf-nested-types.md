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
# <a name="protobuf-nested-types"></a><span data-ttu-id="ceb84-103">Protobuf tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="ceb84-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ceb84-104">Assim como C# permite que você declare classes dentro de outras classes, o Protobuf permite aninhar definições de mensagens dentro de outras mensagens.</span><span class="sxs-lookup"><span data-stu-id="ceb84-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="ceb84-105">O exemplo a seguir mostra como criar tipos de mensagens aninhadas:</span><span class="sxs-lookup"><span data-stu-id="ceb84-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="ceb84-106">No código gerado C# , o `Inner` tipo será declarado em uma classe estática `Types` aninhada dentro da `HelloRequest` classe:</span><span class="sxs-lookup"><span data-stu-id="ceb84-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="ceb84-107">[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="ceb84-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
