---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803115"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="eabf1-101">O método Replace nas URLs do OData é desabilitado por padrão</span><span class="sxs-lookup"><span data-stu-id="eabf1-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="eabf1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="eabf1-102">Details</span></span>|<span data-ttu-id="eabf1-103">A partir do .NET Framework 4.5, o método Replace em URLs do OData é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="eabf1-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="eabf1-104">Quando o Replace do OData está desabilitado (agora por padrão), qualquer solicitação de usuário, incluindo funções de substituição (que são incomuns), falha.</span><span class="sxs-lookup"><span data-stu-id="eabf1-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="eabf1-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="eabf1-105">Suggestion</span></span>|<span data-ttu-id="eabf1-106">Se o método de substituição for necessário (o que é incomum), ele poderá ser reabilitado por meio das configurações (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="eabf1-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="eabf1-107">No entanto, um método de substituição habilitado pode dar abertura para vulnerabilidades de segurança, devendo ser usado somente depois de análise cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="eabf1-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="eabf1-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="eabf1-108">Scope</span></span>|<span data-ttu-id="eabf1-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="eabf1-109">Edge</span></span>|
|<span data-ttu-id="eabf1-110">Versão</span><span class="sxs-lookup"><span data-stu-id="eabf1-110">Version</span></span>|<span data-ttu-id="eabf1-111">4.5</span><span class="sxs-lookup"><span data-stu-id="eabf1-111">4.5</span></span>|
|<span data-ttu-id="eabf1-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="eabf1-112">Type</span></span>|<span data-ttu-id="eabf1-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="eabf1-113">Runtime</span></span>|
|<span data-ttu-id="eabf1-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="eabf1-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
