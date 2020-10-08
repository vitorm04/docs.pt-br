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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="7c552-103">Alterações significativas de serialização</span><span class="sxs-lookup"><span data-stu-id="7c552-103">Serialization breaking changes</span></span>

<span data-ttu-id="7c552-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="7c552-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7c552-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="7c552-105">Breaking change</span></span> | <span data-ttu-id="7c552-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7c552-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="7c552-107">JsonSerializer. Desserialize requer cadeia de caracteres de caractere único</span><span class="sxs-lookup"><span data-stu-id="7c552-107">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="7c552-108">5.0</span><span class="sxs-lookup"><span data-stu-id="7c552-108">5.0</span></span> |
| [<span data-ttu-id="7c552-109">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="7c552-109">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="7c552-110">5.0</span><span class="sxs-lookup"><span data-stu-id="7c552-110">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="7c552-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7c552-111">.NET 5.0</span></span>

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
