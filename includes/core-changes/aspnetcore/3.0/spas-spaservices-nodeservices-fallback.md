---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522667"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="e44f3-101">SPAs: SpaServices e NodeServices não voltam mais para o logger do console</span><span class="sxs-lookup"><span data-stu-id="e44f3-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="e44f3-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>e <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> não exibirá registros do console a menos que o registro esteja configurado.</span><span class="sxs-lookup"><span data-stu-id="e44f3-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e44f3-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e44f3-103">Version introduced</span></span>

<span data-ttu-id="e44f3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e44f3-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e44f3-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="e44f3-105">Old behavior</span></span>

<span data-ttu-id="e44f3-106">`Microsoft.AspNetCore.SpaServices`e `Microsoft.AspNetCore.NodeServices` usado para criar automaticamente um logger de console quando o registro não é configurado.</span><span class="sxs-lookup"><span data-stu-id="e44f3-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e44f3-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="e44f3-107">New behavior</span></span>

<span data-ttu-id="e44f3-108">`Microsoft.AspNetCore.SpaServices`e `Microsoft.AspNetCore.NodeServices` não exibirá registros do console a menos que o registro esteja configurado.</span><span class="sxs-lookup"><span data-stu-id="e44f3-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e44f3-109">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="e44f3-109">Reason for change</span></span>

<span data-ttu-id="e44f3-110">Há uma necessidade de se alinhar com a forma como outros pacotes ASP.NET Core implementam o registro.</span><span class="sxs-lookup"><span data-stu-id="e44f3-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e44f3-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e44f3-111">Recommended action</span></span>

<span data-ttu-id="e44f3-112">Se o comportamento antigo for necessário, para `services.AddLogging(builder => builder.AddConsole())` configurar `Setup.ConfigureServices` o registro do console, adicione ao seu método.</span><span class="sxs-lookup"><span data-stu-id="e44f3-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="e44f3-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="e44f3-113">Category</span></span>

<span data-ttu-id="e44f3-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e44f3-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e44f3-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e44f3-115">Affected APIs</span></span>

<span data-ttu-id="e44f3-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e44f3-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
