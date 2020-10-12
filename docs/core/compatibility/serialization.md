---
title: Alterações significativas de serialização
description: Lista as alterações significativas na categoria de serialização no .NET Core e no .NET 5,0 e posterior.
ms.date: 07/30/2020
ms.openlocfilehash: 65006e6fb45ed2d54699c9972e0489e3ac5ac8bc
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955324"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="c1aa2-103">Alterações significativas de serialização</span><span class="sxs-lookup"><span data-stu-id="c1aa2-103">Serialization breaking changes</span></span>

<span data-ttu-id="c1aa2-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="c1aa2-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c1aa2-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="c1aa2-105">Breaking change</span></span> | <span data-ttu-id="c1aa2-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c1aa2-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="c1aa2-107">JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo</span><span class="sxs-lookup"><span data-stu-id="c1aa2-107">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="c1aa2-108">5.0</span><span class="sxs-lookup"><span data-stu-id="c1aa2-108">5.0</span></span> |
| [<span data-ttu-id="c1aa2-109">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="c1aa2-109">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="c1aa2-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c1aa2-110">5.0</span></span> |
| [<span data-ttu-id="c1aa2-111">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="c1aa2-111">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="c1aa2-112">5.0</span><span class="sxs-lookup"><span data-stu-id="c1aa2-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c1aa2-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c1aa2-113">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
