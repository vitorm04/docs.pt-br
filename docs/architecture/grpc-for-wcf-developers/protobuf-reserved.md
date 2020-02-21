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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="442f7-103">Campos reservados de Protobuf</span><span class="sxs-lookup"><span data-stu-id="442f7-103">Protobuf reserved fields</span></span>

<span data-ttu-id="442f7-104">As garantias de compatibilidade com versões anteriores no buffer de protocolo (Protobuf) dependem de números de campo sempre representando o mesmo item de dados.</span><span class="sxs-lookup"><span data-stu-id="442f7-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="442f7-105">Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="442f7-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="442f7-106">Você pode usar a palavra-chave `reserved`.</span><span class="sxs-lookup"><span data-stu-id="442f7-106">You can enfore this by using the `reserved` keyword.</span></span> 

<span data-ttu-id="442f7-107">Se os campos `displayName` e `marketId` foram removidos da mensagem `Stock` definida anteriormente, os números de campos deverão ser reservados como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="442f7-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="442f7-108">Você também pode usar a palavra-chave `reserved` como um espaço reservado para campos que podem ser adicionados no futuro.</span><span class="sxs-lookup"><span data-stu-id="442f7-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="442f7-109">Você pode expressar números de campo contíguos como um intervalo usando a palavra-chave `to`.</span><span class="sxs-lookup"><span data-stu-id="442f7-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="442f7-110">[Anterior](protobuf-repeated.md)
>[Próximo](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="442f7-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
