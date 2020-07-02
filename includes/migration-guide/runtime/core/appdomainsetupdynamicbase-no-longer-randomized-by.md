---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621030"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="f7f5f-101">AppDomainSetup.DynamicBase não é mais randomizado por UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="f7f5f-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="f7f5f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f7f5f-102">Details</span></span>

<span data-ttu-id="f7f5f-103">Antes do .NET Framework 4.6, o valor de <xref:System.AppDomainSetup.DynamicBase> seria randomizado entre domínios de aplicativos ou entre processos se UseRandomizedStringHashAlgorithm estivesse habilitado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="f7f5f-104">A partir do .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retornará um resultado estável entre instâncias diferentes de um aplicativo em execução e entre diferentes domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="f7f5f-105">Bases dinâmicas ainda serão diferentes para diferentes aplicativos. Essa alteração remove apenas o elemento de nomenclatura aleatório para instâncias diferentes do mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7f5f-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f7f5f-106">Suggestion</span></span>

<span data-ttu-id="f7f5f-107">Lembre-se de que habilitar <code>UseRandomizedStringHashAlgorithm</code> não fará com que <xref:System.AppDomainSetup.DynamicBase> seja randomizado.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="f7f5f-108">Se for necessária uma base aleatória, ela deverá ser produzida no código do aplicativo, e não por meio dessa API.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="f7f5f-109">Name</span><span class="sxs-lookup"><span data-stu-id="f7f5f-109">Name</span></span>    | <span data-ttu-id="f7f5f-110">Valor</span><span class="sxs-lookup"><span data-stu-id="f7f5f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7f5f-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="f7f5f-111">Scope</span></span>   |<span data-ttu-id="f7f5f-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f7f5f-112">Edge</span></span>|
|<span data-ttu-id="f7f5f-113">Versão</span><span class="sxs-lookup"><span data-stu-id="f7f5f-113">Version</span></span>|<span data-ttu-id="f7f5f-114">4.6</span><span class="sxs-lookup"><span data-stu-id="f7f5f-114">4.6</span></span>|
|<span data-ttu-id="f7f5f-115">Type</span><span class="sxs-lookup"><span data-stu-id="f7f5f-115">Type</span></span>|<span data-ttu-id="f7f5f-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="f7f5f-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7f5f-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f7f5f-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
