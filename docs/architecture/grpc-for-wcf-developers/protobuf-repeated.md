---
title: Campos repetidos para listas e matrizes-gRPC para desenvolvedores do WCF
description: Entenda como o Protobuf lida com as coleções e como elas se relacionam com as coleções do .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867497"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="652d2-103">Campos repetidos para listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="652d2-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="652d2-104">Você especifica listas no buffer de protocolo (Protobuf) usando a `repeated` palavra-chave Prefix.</span><span class="sxs-lookup"><span data-stu-id="652d2-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="652d2-105">O exemplo a seguir mostra como criar uma lista:</span><span class="sxs-lookup"><span data-stu-id="652d2-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="652d2-106">No código gerado, os `repeated` campos são representados por propriedades somente leitura do [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] tipo em vez de qualquer um dos tipos de coleção .net internos.</span><span class="sxs-lookup"><span data-stu-id="652d2-106">In the generated code, `repeated` fields are represented by read-only properties of the [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="652d2-107">Esse tipo implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="652d2-107">This type implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="652d2-108">Portanto, você pode usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.</span><span class="sxs-lookup"><span data-stu-id="652d2-108">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

<span data-ttu-id="652d2-109">O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária.</span><span class="sxs-lookup"><span data-stu-id="652d2-109">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span>

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
><span data-ttu-id="652d2-110">[Anterior](protobuf-nested-types.md) 
> [Avançar](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="652d2-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
