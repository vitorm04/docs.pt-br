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
# <a name="repeated-fields-for-lists-and-arrays"></a>Campos repetidos para listas e matrizes

Você especifica listas no Protobuf (Protocol `repeated` Buffer) usando a palavra-chave prefixo. O exemplo a seguir mostra como criar uma lista:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

No código gerado, `repeated` os campos `Google.Protobuf.Collections.RepeatedField<T>` são representados pelo tipo genérico em vez de qualquer um dos tipos de coleta .NET incorporados.

O `RepeatedField<T>` tipo inclui o código necessário para serializar e desserializar a lista para o formato de fio binário. Ele implementa todas as interfaces de <xref:System.Collections.Generic.IList%601> coleta <xref:System.Collections.Generic.IEnumerable%601>padrão .NET, tais como e . Assim, você pode usar consultas LINQ ou convertê-lo para uma matriz ou uma lista facilmente.

>[!div class="step-by-step"]
>[Próximo](protobuf-nested-types.md)
>[anterior](protobuf-reserved.md)
