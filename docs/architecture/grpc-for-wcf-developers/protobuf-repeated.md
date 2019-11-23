---
title: Campos repetidos para listas e matrizes-gRPC para desenvolvedores do WCF
description: Entenda como as coleções são tratadas pelo Protobuf e como elas se relacionam com as coleções do .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967361"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="801fb-103">Campos repetidos para listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="801fb-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="801fb-104">As listas são especificadas em Protobuf usando a palavra-chave de prefixo `repeated`.</span><span class="sxs-lookup"><span data-stu-id="801fb-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="801fb-105">O exemplo a seguir mostra como criar uma lista:</span><span class="sxs-lookup"><span data-stu-id="801fb-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="801fb-106">No código gerado, `repeated` campos são representados pelo tipo genérico `Google.Protobuf.Collections.RepeatedField<T>` em vez de qualquer um dos tipos de coleção .NET internos.</span><span class="sxs-lookup"><span data-stu-id="801fb-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="801fb-107">O tipo de `RepeatedField<T>` inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária.</span><span class="sxs-lookup"><span data-stu-id="801fb-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="801fb-108">Ele implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601>, para que você possa usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.</span><span class="sxs-lookup"><span data-stu-id="801fb-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="801fb-109">[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="801fb-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
