---
title: Protobuf campos reservados - gRPC para desenvolvedores WCF
description: Saiba mais sobre campos reservados para compatibilidade entre versões.
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111030"
---
# <a name="protobuf-reserved-fields"></a>Campos reservados de Protobuf

As garantias de retrocompatibilidade no Buffer de Protocolo (Protobuf) dependem de números de campo sempre representando o mesmo item de dados. Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deve ser reutilizado. Você pode impor isso `reserved` usando a palavra-chave.

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
