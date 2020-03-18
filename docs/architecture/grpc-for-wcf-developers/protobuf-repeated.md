---
title: Campos repetidos para listas e matrizes - gRPC para desenvolvedores WCF
description: Entenda como a Protobuf lida com as coleções e como elas se relacionam com as coleções .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147965"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="9d299-103">Campos repetidos para listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="9d299-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="9d299-104">Você especifica listas no Protobuf (Protocol `repeated` Buffer) usando a palavra-chave prefixo.</span><span class="sxs-lookup"><span data-stu-id="9d299-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="9d299-105">O exemplo a seguir mostra como criar uma lista:</span><span class="sxs-lookup"><span data-stu-id="9d299-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="9d299-106">No código gerado, `repeated` os campos `Google.Protobuf.Collections.RepeatedField<T>` são representados pelo tipo genérico em vez de qualquer um dos tipos de coleta .NET incorporados.</span><span class="sxs-lookup"><span data-stu-id="9d299-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="9d299-107">O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fio binário.</span><span class="sxs-lookup"><span data-stu-id="9d299-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="9d299-108">Ele implementa todas as interfaces de <xref:System.Collections.Generic.IList%601> coleta <xref:System.Collections.Generic.IEnumerable%601>padrão .NET, tais como e .</span><span class="sxs-lookup"><span data-stu-id="9d299-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="9d299-109">Assim, você pode usar consultas LINQ ou convertê-lo para uma matriz ou uma lista facilmente.</span><span class="sxs-lookup"><span data-stu-id="9d299-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9d299-110">[Próximo](protobuf-nested-types.md)
>[anterior](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="9d299-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
