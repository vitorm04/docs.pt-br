---
title: Alterações significativas de serialização
description: Lista as alterações significativas na categoria de serialização no .NET Core e no .NET 5,0 e posterior.
ms.date: 07/30/2020
ms.openlocfilehash: 67608c8e7a9745c060b7eb179fe5a956ede9f80f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332868"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="4a426-103">Alterações significativas de serialização</span><span class="sxs-lookup"><span data-stu-id="4a426-103">Serialization breaking changes</span></span>

<span data-ttu-id="4a426-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="4a426-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4a426-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="4a426-105">Breaking change</span></span> | <span data-ttu-id="4a426-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4a426-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="4a426-107">ASP.NET Core aplicativos permitem a desserialização de números entre aspas</span><span class="sxs-lookup"><span data-stu-id="4a426-107">ASP.NET Core apps allow deserializing quoted numbers</span></span>](#aspnet-core-apps-allow-deserializing-quoted-numbers) | <span data-ttu-id="4a426-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-108">5.0</span></span> |
| [<span data-ttu-id="4a426-109">As opções PropertyNamingPolicy, PropertyNameCaseInsensitive e Encoder são respeitadas ao serializar e desserializar pares chave-valor</span><span class="sxs-lookup"><span data-stu-id="4a426-109">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="4a426-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-110">5.0</span></span> |
| [<span data-ttu-id="4a426-111">Construtores não públicos sem parâmetros não usados para desserialização</span><span class="sxs-lookup"><span data-stu-id="4a426-111">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="4a426-112">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-112">5.0</span></span> |
| [<span data-ttu-id="4a426-113">JsonSerializer. Serialize gera ArgumentNullException quando o parâmetro de tipo é nulo</span><span class="sxs-lookup"><span data-stu-id="4a426-113">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="4a426-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-114">5.0</span></span> |
| [<span data-ttu-id="4a426-115">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="4a426-115">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="4a426-116">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-116">5.0</span></span> |
| [<span data-ttu-id="4a426-117">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="4a426-117">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="4a426-118">5.0</span><span class="sxs-lookup"><span data-stu-id="4a426-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4a426-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="4a426-119">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

<span data-ttu-id="4a426-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="4a426-120">\*\*_</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

<span data-ttu-id="4a426-121">_\*\*</span><span class="sxs-lookup"><span data-stu-id="4a426-121">_\*\*</span></span>
