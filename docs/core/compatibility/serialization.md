---
title: Alterações significativas de serialização
description: Lista as alterações significativas na categoria de serialização no .NET Core e no .NET 5,0 e posterior.
ms.date: 07/30/2020
ms.openlocfilehash: 6902ef8eb2dc23610ef532ff57b755456648ffb0
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997713"
---
# <a name="serialization-breaking-changes"></a>Alterações significativas de serialização

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | - |
| [Construtores não públicos sem parâmetros não usados para desserialização](#non-public-parameterless-constructors-not-used-for-deserialization) | 5.0 |
| [JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer. Desserialize requer cadeia de caracteres de caractere único](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
