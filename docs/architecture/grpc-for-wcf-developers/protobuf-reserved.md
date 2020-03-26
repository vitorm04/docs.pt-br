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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="aa6dd-103">Campos reservados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="aa6dd-103">Protobuf reserved fields</span></span>

<span data-ttu-id="aa6dd-104">As garantias de retrocompatibilidade no Buffer de Protocolo (Protobuf) dependem de números de campo sempre representando o mesmo item de dados.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="aa6dd-105">Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deve ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="aa6dd-106">Você pode impor isso `reserved` usando a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-106">You can enforce this by using the `reserved` keyword.</span></span>

<span data-ttu-id="aa6dd-107">Se `displayName` os `marketId` campos e `Stock` campos foram removidos da mensagem definida anteriormente, seus números de campo devem ser reservados como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="aa6dd-108">Você também pode `reserved` usar a palavra-chave como um espaço reservado para campos que podem ser adicionados no futuro.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="aa6dd-109">Você pode expressar números de campo contíguos como um intervalo usando a `to` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="aa6dd-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="aa6dd-110">[Próximo](protobuf-repeated.md)
>[anterior](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="aa6dd-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
