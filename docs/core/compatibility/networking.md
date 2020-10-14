---
title: Alterações de quebra de rede
description: Lista as alterações significativas na rede no .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050501"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="09f81-103">Alterações de quebra de rede</span><span class="sxs-lookup"><span data-stu-id="09f81-103">Networking breaking changes</span></span>

<span data-ttu-id="09f81-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="09f81-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="09f81-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="09f81-105">Breaking change</span></span> | <span data-ttu-id="09f81-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="09f81-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="09f81-107">NegotiateStream e SslStream permitem operações de início sucessivas</span><span class="sxs-lookup"><span data-stu-id="09f81-107">NegotiateStream and SslStream allow successive Begin operations</span></span>](#negotiatestream-and-sslstream-allow-successive-begin-operations) | <span data-ttu-id="09f81-108">5.0</span><span class="sxs-lookup"><span data-stu-id="09f81-108">5.0</span></span> |
| [<span data-ttu-id="09f81-109">Socket. LocalEndPoint é atualizado após chamar SendToAsync</span><span class="sxs-lookup"><span data-stu-id="09f81-109">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | <span data-ttu-id="09f81-110">5.0</span><span class="sxs-lookup"><span data-stu-id="09f81-110">5.0</span></span> |
| [<span data-ttu-id="09f81-111">WinHttpHandler removido do tempo de execução do .NET</span><span class="sxs-lookup"><span data-stu-id="09f81-111">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="09f81-112">5.0</span><span class="sxs-lookup"><span data-stu-id="09f81-112">5.0</span></span> |
| [<span data-ttu-id="09f81-113">MulticastOption. Group não aceita um valor nulo</span><span class="sxs-lookup"><span data-stu-id="09f81-113">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="09f81-114">5.0</span><span class="sxs-lookup"><span data-stu-id="09f81-114">5.0</span></span> |
| [<span data-ttu-id="09f81-115">O tratamento de caminho de cookie agora está em conformidade com RFC 6265</span><span class="sxs-lookup"><span data-stu-id="09f81-115">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="09f81-116">5.0</span><span class="sxs-lookup"><span data-stu-id="09f81-116">5.0</span></span> |
| [<span data-ttu-id="09f81-117">Valor padrão de HttpRequestMessage. Version alterado para 1,1</span><span class="sxs-lookup"><span data-stu-id="09f81-117">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="09f81-118">3.0</span><span class="sxs-lookup"><span data-stu-id="09f81-118">3.0</span></span> |
| [<span data-ttu-id="09f81-119">WebClient. CancelAsync nem sempre cancela imediatamente</span><span class="sxs-lookup"><span data-stu-id="09f81-119">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="09f81-120">2,0</span><span class="sxs-lookup"><span data-stu-id="09f81-120">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="09f81-121">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="09f81-121">.NET 5.0</span></span>

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="09f81-122">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="09f81-122">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="09f81-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="09f81-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
