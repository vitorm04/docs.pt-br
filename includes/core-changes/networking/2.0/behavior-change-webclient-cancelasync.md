---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859631"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="024d5-101">WebClient. CancelAsync nem sempre cancela imediatamente</span><span class="sxs-lookup"><span data-stu-id="024d5-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="024d5-102">A partir do .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> a chamada não cancelará a solicitação imediatamente se a resposta tiver começado a ser buscada.</span><span class="sxs-lookup"><span data-stu-id="024d5-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="024d5-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="024d5-103">Change description</span></span>

<span data-ttu-id="024d5-104">Anteriormente, chamar <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancelou a solicitação imediatamente.</span><span class="sxs-lookup"><span data-stu-id="024d5-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="024d5-105">A partir do .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> chamar cancelará a solicitação imediatamente somente se a resposta não tiver começado a busca.</span><span class="sxs-lookup"><span data-stu-id="024d5-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="024d5-106">Se a resposta tiver começado a ser buscada, a solicitação será cancelada somente depois que uma resposta completa for lida.</span><span class="sxs-lookup"><span data-stu-id="024d5-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="024d5-107">Essa alteração foi implementada porque <xref:System.Net.WebClient> a API foi preterida em <xref:System.Net.Http.HttpClient>favor de.</span><span class="sxs-lookup"><span data-stu-id="024d5-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="024d5-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="024d5-108">Version introduced</span></span>

<span data-ttu-id="024d5-109">2,0</span><span class="sxs-lookup"><span data-stu-id="024d5-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="024d5-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="024d5-110">Recommended action</span></span>

<span data-ttu-id="024d5-111">Use a <xref:System.Net.Http.HttpClient?displayProperty=fullName> classe em vez <xref:System.Net.WebClient?displayProperty=fullName>de, que é preterida.</span><span class="sxs-lookup"><span data-stu-id="024d5-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="024d5-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="024d5-112">Category</span></span>

<span data-ttu-id="024d5-113">Rede</span><span class="sxs-lookup"><span data-stu-id="024d5-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="024d5-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="024d5-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
