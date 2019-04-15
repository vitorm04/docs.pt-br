---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235050"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="db1c1-101">Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução</span><span class="sxs-lookup"><span data-stu-id="db1c1-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="db1c1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="db1c1-102">Details</span></span>|<span data-ttu-id="db1c1-103">Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".</span><span class="sxs-lookup"><span data-stu-id="db1c1-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="db1c1-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="db1c1-104">Suggestion</span></span>|<span data-ttu-id="db1c1-105">Esse problema foi corrigido no .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="db1c1-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="db1c1-106">Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.</span><span class="sxs-lookup"><span data-stu-id="db1c1-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="db1c1-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="db1c1-107">Scope</span></span>|<span data-ttu-id="db1c1-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="db1c1-108">Edge</span></span>|
|<span data-ttu-id="db1c1-109">Versão</span><span class="sxs-lookup"><span data-stu-id="db1c1-109">Version</span></span>|<span data-ttu-id="db1c1-110">4.5</span><span class="sxs-lookup"><span data-stu-id="db1c1-110">4.5</span></span>|
|<span data-ttu-id="db1c1-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="db1c1-111">Type</span></span>|<span data-ttu-id="db1c1-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="db1c1-112">Runtime</span></span>|
