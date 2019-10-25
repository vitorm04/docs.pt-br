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
# <a name="protobuf-nested-types"></a>Tipos aninhados de Protobuf

Assim como C# permite que você declare classes dentro de outras classes, o Protobuf permite aninhar definições de mensagens dentro de outras mensagens. O exemplo a seguir mostra como criar tipos de mensagens aninhadas:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

No código gerado C# , o tipo de`Inner`será declarado em uma classe de`Types`estática aninhada dentro da classe`HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Anterior](protobuf-data-types.md)
>[Próximo](protobuf-repeated.md)
