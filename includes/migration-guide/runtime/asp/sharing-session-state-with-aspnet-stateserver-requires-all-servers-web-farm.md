---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609122"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="4ae76-101">O compartilhamento do estado de sessão com o ASP.NET StateServer exige que todos os servidores na web farm usem a mesma versão de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ae76-101">Sharing session state with ASP.NET StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="4ae76-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4ae76-102">Details</span></span>

<span data-ttu-id="4ae76-103">Ao habilitar o estado de sessão <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, todos os servidores no web farm fornecido devem usar a mesma versão do .NET Framework para o estado ser compartilhado corretamente.</span><span class="sxs-lookup"><span data-stu-id="4ae76-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ae76-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4ae76-104">Suggestion</span></span>

<span data-ttu-id="4ae76-105">Certifique-se de atualizar as versões do .NET Framework em servidores Web que compartilham o estado ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="4ae76-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="4ae76-106">Nome</span><span class="sxs-lookup"><span data-stu-id="4ae76-106">Name</span></span>    | <span data-ttu-id="4ae76-107">Valor</span><span class="sxs-lookup"><span data-stu-id="4ae76-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ae76-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="4ae76-108">Scope</span></span>   |<span data-ttu-id="4ae76-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4ae76-109">Edge</span></span>|
|<span data-ttu-id="4ae76-110">Versão</span><span class="sxs-lookup"><span data-stu-id="4ae76-110">Version</span></span>|<span data-ttu-id="4ae76-111">4.5</span><span class="sxs-lookup"><span data-stu-id="4ae76-111">4.5</span></span>|
|<span data-ttu-id="4ae76-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="4ae76-112">Type</span></span>|<span data-ttu-id="4ae76-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="4ae76-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ae76-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4ae76-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
