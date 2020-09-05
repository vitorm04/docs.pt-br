---
ms.openlocfilehash: 26c50ac8b0e570e31a38b1913f73acbe21fae08b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497288"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="c2358-101">AppDomainSetup.DynamicBase não é mais randomizado por UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="c2358-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="c2358-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c2358-102">Details</span></span>

<span data-ttu-id="c2358-103">Antes do .NET Framework 4.6, o valor de <xref:System.AppDomainSetup.DynamicBase> seria randomizado entre domínios de aplicativos ou entre processos se UseRandomizedStringHashAlgorithm estivesse habilitado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2358-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="c2358-104">A partir do .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retornará um resultado estável entre instâncias diferentes de um aplicativo em execução e entre diferentes domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2358-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="c2358-105">Bases dinâmicas ainda serão diferentes para diferentes aplicativos. Essa alteração remove apenas o elemento de nomenclatura aleatório para instâncias diferentes do mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2358-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2358-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c2358-106">Suggestion</span></span>

<span data-ttu-id="c2358-107">Lembre-se de que habilitar <code>UseRandomizedStringHashAlgorithm</code> não fará com que <xref:System.AppDomainSetup.DynamicBase> seja randomizado.</span><span class="sxs-lookup"><span data-stu-id="c2358-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="c2358-108">Se for necessária uma base aleatória, ela deverá ser produzida no código do aplicativo, e não por meio dessa API.</span><span class="sxs-lookup"><span data-stu-id="c2358-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="c2358-109">Nome</span><span class="sxs-lookup"><span data-stu-id="c2358-109">Name</span></span>    | <span data-ttu-id="c2358-110">Valor</span><span class="sxs-lookup"><span data-stu-id="c2358-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2358-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="c2358-111">Scope</span></span>   |<span data-ttu-id="c2358-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c2358-112">Edge</span></span>|
|<span data-ttu-id="c2358-113">Versão</span><span class="sxs-lookup"><span data-stu-id="c2358-113">Version</span></span>|<span data-ttu-id="c2358-114">4.6</span><span class="sxs-lookup"><span data-stu-id="c2358-114">4.6</span></span>|
|<span data-ttu-id="c2358-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="c2358-115">Type</span></span>|<span data-ttu-id="c2358-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="c2358-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c2358-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c2358-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.DynamicBase`

-->
