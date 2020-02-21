---
title: Protobuf campos reservados – gRPC para desenvolvedores do WCF
description: Saiba mais sobre os campos reservados para compatibilidade entre versões.
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542970"
---
# <a name="protobuf-reserved-fields"></a>Campos reservados de Protobuf

As garantias de compatibilidade com versões anteriores no buffer de protocolo (Protobuf) dependem de números de campo sempre representando o mesmo item de dados. Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado. Você pode usar a palavra-chave `reserved`. 

Se os campos `displayName` e `marketId` foram removidos da mensagem `Stock` definida anteriormente, os números de campos deverão ser reservados como no exemplo a seguir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Você também pode usar a palavra-chave `reserved` como um espaço reservado para campos que podem ser adicionados no futuro. Você pode expressar números de campo contíguos como um intervalo usando a palavra-chave `to`.

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
