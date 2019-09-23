---
title: Campos repetidos para listas e matrizes-gRPC para desenvolvedores do WCF
description: Entenda como as coleções são tratadas pelo Protobuf e como elas se relacionam com as coleções do .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184179"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="92cb4-103">Campos repetidos para listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="92cb4-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="92cb4-104">As listas são especificadas em Protobuf usando `repeated` a palavra-chave Prefix.</span><span class="sxs-lookup"><span data-stu-id="92cb4-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="92cb4-105">O exemplo a seguir mostra como criar uma lista:</span><span class="sxs-lookup"><span data-stu-id="92cb4-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="92cb4-106">No código gerado, `repeated` os campos são representados `Google.Protobuf.Collections.RepeatedField<T>` pelo tipo genérico em vez de qualquer um dos tipos de coleção .net internos.</span><span class="sxs-lookup"><span data-stu-id="92cb4-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="92cb4-107">O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária.</span><span class="sxs-lookup"><span data-stu-id="92cb4-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="92cb4-108">Ele implementa todas as interfaces de coleção do .NET padrão <xref:System.Collections.Generic.IList%601> , <xref:System.Collections.Generic.IEnumerable%601>como e, para que você possa usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.</span><span class="sxs-lookup"><span data-stu-id="92cb4-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="92cb4-109">[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="92cb4-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
