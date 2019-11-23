---
title: Protobuf campos reservados – gRPC para desenvolvedores do WCF
description: Saiba mais sobre os campos reservados para compatibilidade entre versões.
ms.date: 09/09/2019
ms.openlocfilehash: e589cd38a712ce014fa2c4d847fbde359d538dd0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967306"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="a52f3-103">Campos reservados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="a52f3-103">Protobuf reserved fields</span></span>

<span data-ttu-id="a52f3-104">As garantias de compatibilidade com versões anteriores do Protobuf dependem de números de campo que representam sempre o mesmo item de dados.</span><span class="sxs-lookup"><span data-stu-id="a52f3-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="a52f3-105">Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="a52f3-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="a52f3-106">Isso pode ser imposto usando a palavra-chave `reserved`.</span><span class="sxs-lookup"><span data-stu-id="a52f3-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="a52f3-107">Se os campos `displayName` e `marketId` foram removidos da mensagem `Stock` definida anteriormente, os números de campos deverão ser reservados como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a52f3-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="a52f3-108">A palavra-chave `reserved` também pode ser usada como um espaço reservado para campos que possam ser adicionados no futuro.</span><span class="sxs-lookup"><span data-stu-id="a52f3-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="a52f3-109">Números de campo contíguos podem ser expressos como um intervalo usando a palavra-chave `to`.</span><span class="sxs-lookup"><span data-stu-id="a52f3-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="a52f3-110">[Anterior](protobuf-repeated.md)
>[Próximo](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="a52f3-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
