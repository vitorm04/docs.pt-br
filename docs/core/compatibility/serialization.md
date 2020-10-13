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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="1d2ca-103">Alterações significativas de serialização</span><span class="sxs-lookup"><span data-stu-id="1d2ca-103">Serialization breaking changes</span></span>

<span data-ttu-id="1d2ca-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="1d2ca-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1d2ca-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="1d2ca-105">Breaking change</span></span> | <span data-ttu-id="1d2ca-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1d2ca-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="1d2ca-107">Construtores não públicos sem parâmetros não usados para desserialização</span><span class="sxs-lookup"><span data-stu-id="1d2ca-107">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="1d2ca-108">5.0</span><span class="sxs-lookup"><span data-stu-id="1d2ca-108">5.0</span></span> |
| [<span data-ttu-id="1d2ca-109">JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo</span><span class="sxs-lookup"><span data-stu-id="1d2ca-109">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="1d2ca-110">5.0</span><span class="sxs-lookup"><span data-stu-id="1d2ca-110">5.0</span></span> |
| [<span data-ttu-id="1d2ca-111">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="1d2ca-111">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="1d2ca-112">5.0</span><span class="sxs-lookup"><span data-stu-id="1d2ca-112">5.0</span></span> |
| [<span data-ttu-id="1d2ca-113">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="1d2ca-113">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="1d2ca-114">5.0</span><span class="sxs-lookup"><span data-stu-id="1d2ca-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1d2ca-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1d2ca-115">.NET 5.0</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
