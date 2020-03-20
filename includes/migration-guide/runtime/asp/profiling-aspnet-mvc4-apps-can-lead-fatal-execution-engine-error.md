---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803272"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="e4b28-101">Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução</span><span class="sxs-lookup"><span data-stu-id="e4b28-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4b28-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e4b28-102">Details</span></span>|<span data-ttu-id="e4b28-103">Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".</span><span class="sxs-lookup"><span data-stu-id="e4b28-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="e4b28-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e4b28-104">Suggestion</span></span>|<span data-ttu-id="e4b28-105">Esse problema foi corrigido no .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="e4b28-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="e4b28-106">Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.</span><span class="sxs-lookup"><span data-stu-id="e4b28-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="e4b28-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="e4b28-107">Scope</span></span>|<span data-ttu-id="e4b28-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e4b28-108">Edge</span></span>|
|<span data-ttu-id="e4b28-109">Versão</span><span class="sxs-lookup"><span data-stu-id="e4b28-109">Version</span></span>|<span data-ttu-id="e4b28-110">4.5</span><span class="sxs-lookup"><span data-stu-id="e4b28-110">4.5</span></span>|
|<span data-ttu-id="e4b28-111">Type</span><span class="sxs-lookup"><span data-stu-id="e4b28-111">Type</span></span>|<span data-ttu-id="e4b28-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="e4b28-112">Runtime</span></span>|
