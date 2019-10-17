---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394215"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="af2d1-101">SPAs: SpaServices e Nodeservices não retornam mais para o agente do console</span><span class="sxs-lookup"><span data-stu-id="af2d1-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="af2d1-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> e <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> não exibirão logs do console, a menos que o log esteja configurado.</span><span class="sxs-lookup"><span data-stu-id="af2d1-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="af2d1-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="af2d1-103">Version introduced</span></span>

<span data-ttu-id="af2d1-104">3.0</span><span class="sxs-lookup"><span data-stu-id="af2d1-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="af2d1-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="af2d1-105">Old behavior</span></span>

<span data-ttu-id="af2d1-106">`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` usados para criar automaticamente um agente de log do console quando o registro não estiver configurado.</span><span class="sxs-lookup"><span data-stu-id="af2d1-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span> 

#### <a name="new-behavior"></a><span data-ttu-id="af2d1-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="af2d1-107">New behavior</span></span>

<span data-ttu-id="af2d1-108">`Microsoft.AspNetCore.SpaServices` e `Microsoft.AspNetCore.NodeServices` não exibirão logs do console, a menos que o log esteja configurado.</span><span class="sxs-lookup"><span data-stu-id="af2d1-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="af2d1-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="af2d1-109">Reason for change</span></span>

<span data-ttu-id="af2d1-110">Há a necessidade de se alinhar com o modo como outros pacotes de ASP.NET Core implementam o registro em log.</span><span class="sxs-lookup"><span data-stu-id="af2d1-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="af2d1-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="af2d1-111">Recommended action</span></span>

<span data-ttu-id="af2d1-112">Se o comportamento antigo for necessário, para configurar o log do console, adicione `services.AddLogging(builder => builder.AddConsole())` ao seu método `Setup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="af2d1-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="af2d1-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="af2d1-113">Category</span></span>

<span data-ttu-id="af2d1-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="af2d1-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af2d1-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="af2d1-115">Affected APIs</span></span>

<span data-ttu-id="af2d1-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="af2d1-116">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
