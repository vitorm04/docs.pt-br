---
title: Alterações significativas de serialização
description: Lista as alterações significativas na categoria de serialização no .NET Core e no .NET 5,0 e posterior.
ms.date: 07/30/2020
ms.openlocfilehash: bb6bd650afeba426edc6e102076f05f97f8e0598
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050450"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="d5bdb-103">Alterações significativas de serialização</span><span class="sxs-lookup"><span data-stu-id="d5bdb-103">Serialization breaking changes</span></span>

<span data-ttu-id="d5bdb-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="d5bdb-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d5bdb-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="d5bdb-105">Breaking change</span></span> | <span data-ttu-id="d5bdb-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d5bdb-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="d5bdb-107">As opções PropertyNamingPolicy, PropertyNameCaseInsensitive e Encoder são respeitadas ao serializar e desserializar pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="d5bdb-107">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="d5bdb-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-108">5.0</span></span> |
| [<span data-ttu-id="d5bdb-109">Construtores não públicos sem parâmetros não usados para desserialização</span><span class="sxs-lookup"><span data-stu-id="d5bdb-109">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="d5bdb-110">5.0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-110">5.0</span></span> |
| [<span data-ttu-id="d5bdb-111">JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo</span><span class="sxs-lookup"><span data-stu-id="d5bdb-111">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="d5bdb-112">5.0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-112">5.0</span></span> |
| [<span data-ttu-id="d5bdb-113">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="d5bdb-113">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="d5bdb-114">5.0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-114">5.0</span></span> |
| [<span data-ttu-id="d5bdb-115">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="d5bdb-115">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="d5bdb-116">5.0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-116">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d5bdb-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d5bdb-117">.NET 5.0</span></span>

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

***

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
