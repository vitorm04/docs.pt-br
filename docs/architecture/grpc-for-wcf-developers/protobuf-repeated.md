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
# <a name="repeated-fields-for-lists-and-arrays"></a>Campos repetidos para listas e matrizes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

As listas são especificadas em Protobuf usando `repeated` a palavra-chave Prefix. O exemplo a seguir mostra como criar uma lista:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

No código gerado, `repeated` os campos são representados `Google.Protobuf.Collections.RepeatedField<T>` pelo tipo genérico em vez de qualquer um dos tipos de coleção .net internos. O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fiação binária. Ele implementa todas as interfaces de coleção do .NET padrão <xref:System.Collections.Generic.IList%601> , <xref:System.Collections.Generic.IEnumerable%601>como e, para que você possa usar consultas LINQ ou convertê-las em uma matriz ou uma lista facilmente.

>[!div class="step-by-step"]
>[Anterior](protobuf-nested-types.md)
>[Próximo](protobuf-reserved.md)
