---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607780"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="8c57b-101">A criação de perfil de aplicativos ASP.NET MVC4 pode levar a um erro fatal do mecanismo de execução</span><span class="sxs-lookup"><span data-stu-id="8c57b-101">Profiling ASP.NET MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="8c57b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8c57b-102">Details</span></span>

<span data-ttu-id="8c57b-103">Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".</span><span class="sxs-lookup"><span data-stu-id="8c57b-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8c57b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8c57b-104">Suggestion</span></span>

<span data-ttu-id="8c57b-105">Esse problema foi corrigido no .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="8c57b-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="8c57b-106">Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.</span><span class="sxs-lookup"><span data-stu-id="8c57b-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="8c57b-107">Nome</span><span class="sxs-lookup"><span data-stu-id="8c57b-107">Name</span></span>    | <span data-ttu-id="8c57b-108">Valor</span><span class="sxs-lookup"><span data-stu-id="8c57b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8c57b-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="8c57b-109">Scope</span></span>   |<span data-ttu-id="8c57b-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8c57b-110">Edge</span></span>|
|<span data-ttu-id="8c57b-111">Versão</span><span class="sxs-lookup"><span data-stu-id="8c57b-111">Version</span></span>|<span data-ttu-id="8c57b-112">4.5</span><span class="sxs-lookup"><span data-stu-id="8c57b-112">4.5</span></span>|
|<span data-ttu-id="8c57b-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="8c57b-113">Type</span></span>|<span data-ttu-id="8c57b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8c57b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8c57b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8c57b-115">Affected APIs</span></span>

<span data-ttu-id="8c57b-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="8c57b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
