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
# <a name="repeated-fields-for-lists-and-arrays"></a>Campos repetidos para listas e matrizes

Você especifica listas no buffer de protocolo (Protobuf) usando a `repeated` palavra-chave Prefix. O exemplo a seguir mostra como criar uma lista:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

No código gerado, os `repeated` campos são representados por propriedades somente leitura do [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] tipo em vez de qualquer um dos tipos de coleção .net internos. Esse tipo implementa todas as interfaces de coleção do .NET padrão, como <xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IEnumerable%601> . Portanto, você pode usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.

O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária.

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
>[Anterior](protobuf-nested-types.md) 
> [Avançar](protobuf-reserved.md)
