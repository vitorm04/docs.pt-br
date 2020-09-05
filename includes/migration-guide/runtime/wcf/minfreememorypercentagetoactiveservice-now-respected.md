---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496998"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="e1051-101">MinFreeMemoryPercentageToActiveService agora é respeitado</span><span class="sxs-lookup"><span data-stu-id="e1051-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="e1051-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e1051-102">Details</span></span>

<span data-ttu-id="e1051-103">Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado.</span><span class="sxs-lookup"><span data-stu-id="e1051-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="e1051-104">Ela foi projetada para evitar exceções <xref:System.OutOfMemoryException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="e1051-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="e1051-105">No .NET Framework 4.5, essa configuração não tinha nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="e1051-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="e1051-106">No .NET Framework 4.5.1, essa configuração é observada.</span><span class="sxs-lookup"><span data-stu-id="e1051-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1051-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e1051-107">Suggestion</span></span>

<span data-ttu-id="e1051-108">Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração.</span><span class="sxs-lookup"><span data-stu-id="e1051-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="e1051-109">Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.</span><span class="sxs-lookup"><span data-stu-id="e1051-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="e1051-110">Nome</span><span class="sxs-lookup"><span data-stu-id="e1051-110">Name</span></span>    | <span data-ttu-id="e1051-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e1051-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1051-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="e1051-112">Scope</span></span>   |<span data-ttu-id="e1051-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="e1051-113">Minor</span></span>|
|<span data-ttu-id="e1051-114">Versão</span><span class="sxs-lookup"><span data-stu-id="e1051-114">Version</span></span>|<span data-ttu-id="e1051-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e1051-115">4.5.1</span></span>|
|<span data-ttu-id="e1051-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="e1051-116">Type</span></span>|<span data-ttu-id="e1051-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="e1051-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e1051-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e1051-118">Affected APIs</span></span>

<span data-ttu-id="e1051-119">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="e1051-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
