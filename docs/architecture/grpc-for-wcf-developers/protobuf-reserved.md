---
title: Protobuf campos reservados – gRPC para desenvolvedores do WCF
description: Saiba mais sobre os campos reservados para compatibilidade entre versões.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184172"
---
# <a name="protobuf-reserved-fields"></a>Protobuf campos reservados

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

As garantias de compatibilidade com versões anteriores do Protobuf dependem de números de campo que representam sempre o mesmo item de dados. Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado. Isso pode ser imposto usando a `reserved` palavra-chave. Se os `displayName` `marketId`campose tiverem sido removidos da mensagemdefinidaanteriormente,osnúmerosdecamposdeverãoserreservadoscomonoexemploaseguir.`Stock`

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

A `reserved` palavra-chave também pode ser usada como um espaço reservado para campos que podem ser adicionados no futuro. Números de campo contíguos podem ser expressos como um `to` intervalo usando a palavra-chave.

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
