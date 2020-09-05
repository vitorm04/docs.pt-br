---
ms.openlocfilehash: 76425ca03c98cd6a23b8366257f9e0d53b486edb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497773"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="8aa06-101">Compartilhamento de estado de sessão com StateServer Asp.Net exige que todos os servidores no web farm usem a mesma versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8aa06-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="8aa06-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8aa06-102">Details</span></span>

<span data-ttu-id="8aa06-103">Ao habilitar o estado de sessão <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, todos os servidores no web farm fornecido devem usar a mesma versão do .NET Framework para o estado ser compartilhado corretamente.</span><span class="sxs-lookup"><span data-stu-id="8aa06-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8aa06-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8aa06-104">Suggestion</span></span>

<span data-ttu-id="8aa06-105">Certifique-se de atualizar as versões do .NET Framework em servidores Web que compartilham o estado ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8aa06-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="8aa06-106">Nome</span><span class="sxs-lookup"><span data-stu-id="8aa06-106">Name</span></span>    | <span data-ttu-id="8aa06-107">Valor</span><span class="sxs-lookup"><span data-stu-id="8aa06-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8aa06-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="8aa06-108">Scope</span></span>   |<span data-ttu-id="8aa06-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8aa06-109">Edge</span></span>|
|<span data-ttu-id="8aa06-110">Versão</span><span class="sxs-lookup"><span data-stu-id="8aa06-110">Version</span></span>|<span data-ttu-id="8aa06-111">4.5</span><span class="sxs-lookup"><span data-stu-id="8aa06-111">4.5</span></span>|
|<span data-ttu-id="8aa06-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="8aa06-112">Type</span></span>|<span data-ttu-id="8aa06-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="8aa06-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8aa06-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8aa06-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
