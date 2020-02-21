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
# <a name="repeated-fields-for-lists-and-arrays"></a>Campos repetidos para listas e matrizes

Você especifica listas no buffer de protocolo (Protobuf) usando a palavra-chave prefixo `repeated`. O exemplo a seguir mostra como criar uma lista:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

No código gerado, `repeated` campos são representados pelo tipo genérico `Google.Protobuf.Collections.RepeatedField<T>` em vez de qualquer um dos tipos de coleção .NET internos. 

O tipo de `RepeatedField<T>` inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária. Ele implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601>. Portanto, você pode usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.

>[!div class="step-by-step"]
>[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)
