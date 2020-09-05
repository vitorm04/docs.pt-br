---
ms.openlocfilehash: c679cb2603d39f580203d9373d76481e904e6c1d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497026"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="9399d-101">Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução</span><span class="sxs-lookup"><span data-stu-id="9399d-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="9399d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9399d-102">Details</span></span>

<span data-ttu-id="9399d-103">Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".</span><span class="sxs-lookup"><span data-stu-id="9399d-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9399d-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9399d-104">Suggestion</span></span>

<span data-ttu-id="9399d-105">Esse problema foi corrigido no .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="9399d-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="9399d-106">Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.</span><span class="sxs-lookup"><span data-stu-id="9399d-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="9399d-107">Nome</span><span class="sxs-lookup"><span data-stu-id="9399d-107">Name</span></span>    | <span data-ttu-id="9399d-108">Valor</span><span class="sxs-lookup"><span data-stu-id="9399d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9399d-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="9399d-109">Scope</span></span>   |<span data-ttu-id="9399d-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9399d-110">Edge</span></span>|
|<span data-ttu-id="9399d-111">Versão</span><span class="sxs-lookup"><span data-stu-id="9399d-111">Version</span></span>|<span data-ttu-id="9399d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="9399d-112">4.5</span></span>|
|<span data-ttu-id="9399d-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="9399d-113">Type</span></span>|<span data-ttu-id="9399d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="9399d-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9399d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9399d-115">Affected APIs</span></span>

<span data-ttu-id="9399d-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="9399d-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
