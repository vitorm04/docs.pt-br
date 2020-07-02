---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619770"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="a40b0-101">Compartilhamento de estado de sessão com StateServer Asp.Net exige que todos os servidores no web farm usem a mesma versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a40b0-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="a40b0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a40b0-102">Details</span></span>

<span data-ttu-id="a40b0-103">Ao habilitar o estado de sessão <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, todos os servidores no web farm fornecido devem usar a mesma versão do .NET Framework para o estado ser compartilhado corretamente.</span><span class="sxs-lookup"><span data-stu-id="a40b0-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a40b0-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a40b0-104">Suggestion</span></span>

<span data-ttu-id="a40b0-105">Certifique-se de atualizar as versões do .NET Framework em servidores Web que compartilham o estado ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a40b0-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="a40b0-106">Name</span><span class="sxs-lookup"><span data-stu-id="a40b0-106">Name</span></span>    | <span data-ttu-id="a40b0-107">Valor</span><span class="sxs-lookup"><span data-stu-id="a40b0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a40b0-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="a40b0-108">Scope</span></span>   |<span data-ttu-id="a40b0-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a40b0-109">Edge</span></span>|
|<span data-ttu-id="a40b0-110">Versão</span><span class="sxs-lookup"><span data-stu-id="a40b0-110">Version</span></span>|<span data-ttu-id="a40b0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a40b0-111">4.5</span></span>|
|<span data-ttu-id="a40b0-112">Type</span><span class="sxs-lookup"><span data-stu-id="a40b0-112">Type</span></span>|<span data-ttu-id="a40b0-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="a40b0-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a40b0-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a40b0-114">Affected APIs</span></span>

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
