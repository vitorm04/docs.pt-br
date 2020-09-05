---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496561"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="e2003-101">TargetFrameworkName para o domínio de aplicativo padrão não será mais padronizado como nulo se não for definido</span><span class="sxs-lookup"><span data-stu-id="e2003-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="e2003-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e2003-102">Details</span></span>

<span data-ttu-id="e2003-103">O <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> era nulo anteriormente no domínio de aplicativo padrão, a menos que fosse explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="e2003-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="e2003-104">A partir da 4.6, a propriedade <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> para o domínio de aplicativo padrão terá um valor padrão derivado do TargetFrameworkAttribute (se um estiver presente).</span><span class="sxs-lookup"><span data-stu-id="e2003-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="e2003-105">Os domínios de aplicativo não padrão continuarão herdando o respectivo <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> do domínio de aplicativo padrão (que não será padronizado para nulo na 4.6), a menos que sejam explicitamente substituídos.</span><span class="sxs-lookup"><span data-stu-id="e2003-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2003-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e2003-106">Suggestion</span></span>

<span data-ttu-id="e2003-107">O código deve ser atualizado para não depender do <xref:System.AppDomainSetup.TargetFrameworkName> que padroniza para nulo.</span><span class="sxs-lookup"><span data-stu-id="e2003-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="e2003-108">Se for necessário que essa propriedade continue sendo avaliada como nula, ela poderá ser explicitamente definida para esse valor.</span><span class="sxs-lookup"><span data-stu-id="e2003-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="e2003-109">Nome</span><span class="sxs-lookup"><span data-stu-id="e2003-109">Name</span></span>    | <span data-ttu-id="e2003-110">Valor</span><span class="sxs-lookup"><span data-stu-id="e2003-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2003-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="e2003-111">Scope</span></span>   |<span data-ttu-id="e2003-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e2003-112">Edge</span></span>|
|<span data-ttu-id="e2003-113">Versão</span><span class="sxs-lookup"><span data-stu-id="e2003-113">Version</span></span>|<span data-ttu-id="e2003-114">4.6</span><span class="sxs-lookup"><span data-stu-id="e2003-114">4.6</span></span>|
|<span data-ttu-id="e2003-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="e2003-115">Type</span></span>|<span data-ttu-id="e2003-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="e2003-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e2003-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e2003-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
