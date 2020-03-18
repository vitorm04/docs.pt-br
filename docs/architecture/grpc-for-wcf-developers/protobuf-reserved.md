---
title: Protobuf campos reservados - gRPC para desenvolvedores WCF
description: Saiba mais sobre campos reservados para compatibilidade entre versões.
ms.date: 09/09/2019
ms.openlocfilehash: bde658c671e970b7ec841d71d5b4284eb91195f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147939"
---
# <a name="protobuf-reserved-fields"></a>Campos reservados de Protobuf

As garantias de retrocompatibilidade no Buffer de Protocolo (Protobuf) dependem de números de campo sempre representando o mesmo item de dados. Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deve ser reutilizado. Você pode se içar `reserved` isso usando a palavra-chave.

Se `displayName` os `marketId` campos e `Stock` campos foram removidos da mensagem definida anteriormente, seus números de campo devem ser reservados como no exemplo a seguir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Você também pode `reserved` usar a palavra-chave como um espaço reservado para campos que podem ser adicionados no futuro. Você pode expressar números de campo contíguos como um intervalo usando a `to` palavra-chave.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Próximo](protobuf-repeated.md)
>[anterior](protobuf-any-oneof.md)
