---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621920"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="47846-101">Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução</span><span class="sxs-lookup"><span data-stu-id="47846-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="47846-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="47846-102">Details</span></span>

<span data-ttu-id="47846-103">Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".</span><span class="sxs-lookup"><span data-stu-id="47846-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="47846-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="47846-104">Suggestion</span></span>

<span data-ttu-id="47846-105">Esse problema foi corrigido no .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="47846-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="47846-106">Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.</span><span class="sxs-lookup"><span data-stu-id="47846-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="47846-107">Name</span><span class="sxs-lookup"><span data-stu-id="47846-107">Name</span></span>    | <span data-ttu-id="47846-108">Valor</span><span class="sxs-lookup"><span data-stu-id="47846-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="47846-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="47846-109">Scope</span></span>   |<span data-ttu-id="47846-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="47846-110">Edge</span></span>|
|<span data-ttu-id="47846-111">Versão</span><span class="sxs-lookup"><span data-stu-id="47846-111">Version</span></span>|<span data-ttu-id="47846-112">4.5</span><span class="sxs-lookup"><span data-stu-id="47846-112">4.5</span></span>|
|<span data-ttu-id="47846-113">Type</span><span class="sxs-lookup"><span data-stu-id="47846-113">Type</span></span>|<span data-ttu-id="47846-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="47846-114">Runtime</span></span>|
