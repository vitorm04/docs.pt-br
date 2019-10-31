---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235087"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="c530f-101">MinFreeMemoryPercentageToActiveService agora é respeitado</span><span class="sxs-lookup"><span data-stu-id="c530f-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c530f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c530f-102">Details</span></span>|<span data-ttu-id="c530f-103">Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado.</span><span class="sxs-lookup"><span data-stu-id="c530f-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="c530f-104">Ela foi projetada para evitar exceções <xref:System.OutOfMemoryException?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c530f-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="c530f-105">No .NET Framework 4.5, essa configuração não tinha nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="c530f-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="c530f-106">No .NET Framework 4.5.1, essa configuração é observada.</span><span class="sxs-lookup"><span data-stu-id="c530f-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="c530f-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c530f-107">Suggestion</span></span>|<span data-ttu-id="c530f-108">Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração.</span><span class="sxs-lookup"><span data-stu-id="c530f-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="c530f-109">Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.</span><span class="sxs-lookup"><span data-stu-id="c530f-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="c530f-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="c530f-110">Scope</span></span>|<span data-ttu-id="c530f-111">Secundário</span><span class="sxs-lookup"><span data-stu-id="c530f-111">Minor</span></span>|
|<span data-ttu-id="c530f-112">Versão</span><span class="sxs-lookup"><span data-stu-id="c530f-112">Version</span></span>|<span data-ttu-id="c530f-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c530f-113">4.5.1</span></span>|
|<span data-ttu-id="c530f-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="c530f-114">Type</span></span>|<span data-ttu-id="c530f-115">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c530f-115">Runtime</span></span>|
