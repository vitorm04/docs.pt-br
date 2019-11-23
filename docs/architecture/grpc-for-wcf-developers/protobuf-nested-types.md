---
title: Protobuf tipos aninhados-gRPC para desenvolvedores do WCF
description: Saiba mais sobre tipos de mensagens aninhadas em Protobuf e gRPC e como elas C#são geradas no.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967395"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="d1b8d-103">Tipos aninhados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="d1b8d-103">Protobuf nested types</span></span>

<span data-ttu-id="d1b8d-104">Assim como C# permite que você declare classes dentro de outras classes, o Protobuf permite aninhar definições de mensagens dentro de outras mensagens.</span><span class="sxs-lookup"><span data-stu-id="d1b8d-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="d1b8d-105">O exemplo a seguir mostra como criar tipos de mensagens aninhadas:</span><span class="sxs-lookup"><span data-stu-id="d1b8d-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="d1b8d-106">No código gerado C# , o tipo de `Inner` será declarado em uma classe de `Types` estática aninhada dentro da classe `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="d1b8d-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="d1b8d-107">[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="d1b8d-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
