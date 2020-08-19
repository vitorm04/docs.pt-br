---
title: Alterações de quebra de rede
description: Lista as alterações significativas na rede no .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 5d27f9663a2c1b79610ab002a03beeafa8b2818e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557952"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="b3d86-103">Alterações de quebra de rede</span><span class="sxs-lookup"><span data-stu-id="b3d86-103">Networking breaking changes</span></span>

<span data-ttu-id="b3d86-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="b3d86-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b3d86-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="b3d86-105">Breaking change</span></span> | <span data-ttu-id="b3d86-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b3d86-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="b3d86-107">MulticastOption. Group não aceita um valor nulo</span><span class="sxs-lookup"><span data-stu-id="b3d86-107">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="b3d86-108">5.0</span><span class="sxs-lookup"><span data-stu-id="b3d86-108">5.0</span></span> |
| [<span data-ttu-id="b3d86-109">Valor padrão de HttpRequestMessage. Version alterado para 1,1</span><span class="sxs-lookup"><span data-stu-id="b3d86-109">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="b3d86-110">3.0</span><span class="sxs-lookup"><span data-stu-id="b3d86-110">3.0</span></span> |
| [<span data-ttu-id="b3d86-111">WebClient. CancelAsync nem sempre cancela imediatamente</span><span class="sxs-lookup"><span data-stu-id="b3d86-111">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="b3d86-112">2.0</span><span class="sxs-lookup"><span data-stu-id="b3d86-112">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b3d86-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b3d86-113">.NET 5.0</span></span>

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b3d86-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b3d86-114">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="b3d86-115">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b3d86-115">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
