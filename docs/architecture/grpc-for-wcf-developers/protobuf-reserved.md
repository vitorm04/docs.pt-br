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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="27ada-103">Protobuf campos reservados</span><span class="sxs-lookup"><span data-stu-id="27ada-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="27ada-104">As garantias de compatibilidade com versões anteriores do Protobuf dependem de números de campo que representam sempre o mesmo item de dados.</span><span class="sxs-lookup"><span data-stu-id="27ada-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="27ada-105">Se um campo for removido de uma mensagem em uma nova versão do serviço, esse número de campo nunca deverá ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="27ada-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="27ada-106">Isso pode ser imposto usando a `reserved` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="27ada-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="27ada-107">Se os `displayName` `marketId`campose tiverem sido removidos da mensagemdefinidaanteriormente,osnúmerosdecamposdeverãoserreservadoscomonoexemploaseguir.`Stock`</span><span class="sxs-lookup"><span data-stu-id="27ada-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="27ada-108">A `reserved` palavra-chave também pode ser usada como um espaço reservado para campos que podem ser adicionados no futuro.</span><span class="sxs-lookup"><span data-stu-id="27ada-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="27ada-109">Números de campo contíguos podem ser expressos como um `to` intervalo usando a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="27ada-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="27ada-110">[Anterior](protobuf-repeated.md)
>[Próximo](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="27ada-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
