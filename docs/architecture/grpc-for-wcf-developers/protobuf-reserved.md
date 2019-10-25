---
title: Protobuf campos reservados – gRPC para desenvolvedores do WCF
description: Saiba mais sobre os campos reservados para compatibilidade entre versões.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846325"
---
# <a name="protobuf-reserved-fields"></a>Campos reservados de Protobuf

As garantias de compatibilidade com versões anteriores do Protobuf dependem de números de campo que representam sempre o mesmo item de dados. Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado. Isso pode ser imposto usando a palavra-chave `reserved`. Se os campos `displayName` e `marketId` foram removidos da mensagem `Stock` definida anteriormente, os números de campos deverão ser reservados como no exemplo a seguir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

A palavra-chave `reserved` também pode ser usada como um espaço reservado para campos que possam ser adicionados no futuro. Números de campo contíguos podem ser expressos como um intervalo usando a palavra-chave `to`.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Anterior](protobuf-repeated.md)
>[Próximo](protobuf-any-oneof.md)
