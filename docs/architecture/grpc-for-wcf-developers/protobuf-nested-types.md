---
title: Protobuf tipos aninhados-gRPC para desenvolvedores do WCF
description: Saiba mais sobre tipos de mensagens aninhadas em Protobuf e gRPC e como elas C#são geradas no.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846311"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="b934b-103">Tipos aninhados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="b934b-103">Protobuf nested types</span></span>

<span data-ttu-id="b934b-104">Assim como C# permite que você declare classes dentro de outras classes, o Protobuf permite aninhar definições de mensagens dentro de outras mensagens.</span><span class="sxs-lookup"><span data-stu-id="b934b-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="b934b-105">O exemplo a seguir mostra como criar tipos de mensagens aninhadas:</span><span class="sxs-lookup"><span data-stu-id="b934b-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="b934b-106">No código gerado C# , o tipo de`Inner`será declarado em uma classe de`Types`estática aninhada dentro da classe`HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="b934b-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="b934b-107">[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="b934b-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
