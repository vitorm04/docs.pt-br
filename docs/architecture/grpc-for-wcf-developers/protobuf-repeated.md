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
# <a name="repeated-fields-for-lists-and-arrays"></a>Campos repetidos para listas e matrizes

As listas são especificadas em Protobuf usando a palavra-chave de prefixo `repeated`. O exemplo a seguir mostra como criar uma lista:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

No código gerado, `repeated` campos são representados pelo tipo genérico `Google.Protobuf.Collections.RepeatedField<T>` em vez de qualquer um dos tipos de coleção .NET internos. O tipo de `RepeatedField<T>` inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária. Ele implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601>, para que você possa usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.

>[!div class="step-by-step"]
>[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)
