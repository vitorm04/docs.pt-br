---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621034"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="1715c-101">TargetFrameworkName para o domínio de aplicativo padrão não será mais padronizado como nulo se não for definido</span><span class="sxs-lookup"><span data-stu-id="1715c-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="1715c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1715c-102">Details</span></span>

<span data-ttu-id="1715c-103">O <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> era nulo anteriormente no domínio de aplicativo padrão, a menos que fosse explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="1715c-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="1715c-104">A partir da 4.6, a propriedade <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> para o domínio de aplicativo padrão terá um valor padrão derivado do TargetFrameworkAttribute (se um estiver presente).</span><span class="sxs-lookup"><span data-stu-id="1715c-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="1715c-105">Os domínios de aplicativo não padrão continuarão herdando o respectivo <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> do domínio de aplicativo padrão (que não será padronizado para nulo na 4.6), a menos que sejam explicitamente substituídos.</span><span class="sxs-lookup"><span data-stu-id="1715c-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1715c-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1715c-106">Suggestion</span></span>

<span data-ttu-id="1715c-107">O código deve ser atualizado para não depender do <xref:System.AppDomainSetup.TargetFrameworkName> que padroniza para nulo.</span><span class="sxs-lookup"><span data-stu-id="1715c-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="1715c-108">Se for necessário que essa propriedade continue sendo avaliada como nula, ela poderá ser explicitamente definida para esse valor.</span><span class="sxs-lookup"><span data-stu-id="1715c-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="1715c-109">Name</span><span class="sxs-lookup"><span data-stu-id="1715c-109">Name</span></span>    | <span data-ttu-id="1715c-110">Valor</span><span class="sxs-lookup"><span data-stu-id="1715c-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1715c-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="1715c-111">Scope</span></span>   |<span data-ttu-id="1715c-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1715c-112">Edge</span></span>|
|<span data-ttu-id="1715c-113">Versão</span><span class="sxs-lookup"><span data-stu-id="1715c-113">Version</span></span>|<span data-ttu-id="1715c-114">4.6</span><span class="sxs-lookup"><span data-stu-id="1715c-114">4.6</span></span>|
|<span data-ttu-id="1715c-115">Type</span><span class="sxs-lookup"><span data-stu-id="1715c-115">Type</span></span>|<span data-ttu-id="1715c-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="1715c-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1715c-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1715c-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
