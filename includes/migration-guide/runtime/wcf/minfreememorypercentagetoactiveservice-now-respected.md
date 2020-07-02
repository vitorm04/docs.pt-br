---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619807"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="04efa-101">MinFreeMemoryPercentageToActiveService agora é respeitado</span><span class="sxs-lookup"><span data-stu-id="04efa-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="04efa-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="04efa-102">Details</span></span>

<span data-ttu-id="04efa-103">Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado.</span><span class="sxs-lookup"><span data-stu-id="04efa-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="04efa-104">Ela foi projetada para evitar exceções <xref:System.OutOfMemoryException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="04efa-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="04efa-105">No .NET Framework 4.5, essa configuração não tinha nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="04efa-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="04efa-106">No .NET Framework 4.5.1, essa configuração é observada.</span><span class="sxs-lookup"><span data-stu-id="04efa-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="04efa-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="04efa-107">Suggestion</span></span>

<span data-ttu-id="04efa-108">Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração.</span><span class="sxs-lookup"><span data-stu-id="04efa-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="04efa-109">Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.</span><span class="sxs-lookup"><span data-stu-id="04efa-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="04efa-110">Name</span><span class="sxs-lookup"><span data-stu-id="04efa-110">Name</span></span>    | <span data-ttu-id="04efa-111">Valor</span><span class="sxs-lookup"><span data-stu-id="04efa-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="04efa-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="04efa-112">Scope</span></span>   |<span data-ttu-id="04efa-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="04efa-113">Minor</span></span>|
|<span data-ttu-id="04efa-114">Versão</span><span class="sxs-lookup"><span data-stu-id="04efa-114">Version</span></span>|<span data-ttu-id="04efa-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="04efa-115">4.5.1</span></span>|
|<span data-ttu-id="04efa-116">Type</span><span class="sxs-lookup"><span data-stu-id="04efa-116">Type</span></span>|<span data-ttu-id="04efa-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="04efa-117">Runtime</span></span>|
