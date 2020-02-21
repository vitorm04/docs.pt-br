---
title: Campos repetidos para listas e matrizes-gRPC para desenvolvedores do WCF
description: Entenda como o Protobuf lida com as coleções e como elas se relacionam com as coleções do .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542953"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="a6bf3-103">Campos repetidos para listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="a6bf3-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="a6bf3-104">Você especifica listas no buffer de protocolo (Protobuf) usando a palavra-chave prefixo `repeated`.</span><span class="sxs-lookup"><span data-stu-id="a6bf3-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="a6bf3-105">O exemplo a seguir mostra como criar uma lista:</span><span class="sxs-lookup"><span data-stu-id="a6bf3-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="a6bf3-106">No código gerado, `repeated` campos são representados pelo tipo genérico `Google.Protobuf.Collections.RepeatedField<T>` em vez de qualquer um dos tipos de coleção .NET internos.</span><span class="sxs-lookup"><span data-stu-id="a6bf3-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="a6bf3-107">O tipo de `RepeatedField<T>` inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária.</span><span class="sxs-lookup"><span data-stu-id="a6bf3-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="a6bf3-108">Ele implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="a6bf3-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="a6bf3-109">Portanto, você pode usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.</span><span class="sxs-lookup"><span data-stu-id="a6bf3-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6bf3-110">[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="a6bf3-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
