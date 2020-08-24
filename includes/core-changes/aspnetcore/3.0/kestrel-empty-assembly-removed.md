---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394127"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="38749-101">Kestrel: assembly HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="38749-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="38749-102">O assembly foi <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> removido.</span><span class="sxs-lookup"><span data-stu-id="38749-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38749-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="38749-103">Version introduced</span></span>

<span data-ttu-id="38749-104">3,0</span><span class="sxs-lookup"><span data-stu-id="38749-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="38749-105">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="38749-105">Reason for change</span></span>

<span data-ttu-id="38749-106">No ASP.NET Core 2,1, o conteúdo de `Microsoft.AspNetCore.Server.Kestrel.Https` foi movido para <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="38749-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="38749-107">Essa alteração foi feita de forma não-significativa usando `[TypeForwardedTo]` atributos.</span><span class="sxs-lookup"><span data-stu-id="38749-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38749-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="38749-108">Recommended action</span></span>

- <span data-ttu-id="38749-109">As bibliotecas `Microsoft.AspNetCore.Server.Kestrel.Https` que fazem referência a 2,0 devem atualizar todas as dependências de ASP.NET Core para 2,1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="38749-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="38749-110">Caso contrário, eles poderão ser interrompidos quando forem carregados em um aplicativo ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="38749-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="38749-111">Os aplicativos e bibliotecas destinados a ASP.NET Core 2,1 e posterior devem remover todas as referências diretas ao `Microsoft.AspNetCore.Server.Kestrel.Https` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="38749-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="38749-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="38749-112">Category</span></span>

<span data-ttu-id="38749-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38749-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38749-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="38749-114">Affected APIs</span></span>

<span data-ttu-id="38749-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="38749-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
