---
title: Protobuf tipos aninhados-gRPC para desenvolvedores do WCF
description: Saiba mais sobre tipos de mensagens aninhadas em Protobuf e gRPC e como elas C#são geradas no.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542840"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="25ac8-103">Tipos aninhados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="25ac8-103">Protobuf nested types</span></span>

<span data-ttu-id="25ac8-104">Assim como C# permite que você declare classes dentro de outras classes, o buffer de protocolo (Protobuf) permite aninhar definições de mensagens em outras mensagens.</span><span class="sxs-lookup"><span data-stu-id="25ac8-104">Just as C# allows you to declare classes inside other classes, Protocol Buffer (Protobuf) allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="25ac8-105">O exemplo a seguir mostra como criar tipos de mensagens aninhadas:</span><span class="sxs-lookup"><span data-stu-id="25ac8-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="25ac8-106">No código gerado C# , o tipo de `Inner` será declarado em uma classe de `Types` estática aninhada dentro da classe `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="25ac8-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="25ac8-107">[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="25ac8-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
