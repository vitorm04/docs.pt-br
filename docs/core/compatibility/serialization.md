---
title: Alterações significativas de serialização
description: Lista as alterações significativas na categoria de serialização no .NET Core e no .NET 5,0 e posterior.
ms.date: 07/30/2020
ms.openlocfilehash: d68bb95f4ee2b21a5a5bf002a46a3904543cd4a7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844493"
---
# <a name="serialization-breaking-changes"></a>Alterações significativas de serialização

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | - |
| [JsonSerializer. Desserialize requer cadeia de caracteres de caractere único](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
