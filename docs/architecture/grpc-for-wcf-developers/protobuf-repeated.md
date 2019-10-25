---
title: Campos repetidos para listas e matrizes-gRPC para desenvolvedores do WCF
description: Entenda como as coleções são tratadas pelo Protobuf e como elas se relacionam com as coleções do .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846316"
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
