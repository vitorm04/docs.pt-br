---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394127"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="b1b1e-101">Kestrel: Conjunto HTTPS vazio removido</span><span class="sxs-lookup"><span data-stu-id="b1b1e-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="b1b1e-102">A <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> assembléia foi removida.</span><span class="sxs-lookup"><span data-stu-id="b1b1e-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1b1e-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b1b1e-103">Version introduced</span></span>

<span data-ttu-id="b1b1e-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b1b1e-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b1b1e-105">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="b1b1e-105">Reason for change</span></span>

<span data-ttu-id="b1b1e-106">Em ASP.NET Núcleo 2.1, `Microsoft.AspNetCore.Server.Kestrel.Https` o <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>conteúdo foi transferido para .</span><span class="sxs-lookup"><span data-stu-id="b1b1e-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="b1b1e-107">Essa mudança foi feita de forma `[TypeForwardedTo]` não-quebra usando atributos.</span><span class="sxs-lookup"><span data-stu-id="b1b1e-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1b1e-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b1b1e-108">Recommended action</span></span>

- <span data-ttu-id="b1b1e-109">Bibliotecas referentes `Microsoft.AspNetCore.Server.Kestrel.Https` ao 2.0 devem atualizar todas as dependências ASP.NET Core para 2.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b1b1e-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="b1b1e-110">Caso contrário, eles podem quebrar quando carregados em um aplicativo ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b1b1e-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="b1b1e-111">Aplicativos e bibliotecas direcionados ao ASP.NET Core 2.1 e `Microsoft.AspNetCore.Server.Kestrel.Https` posteriores devem remover quaisquer referências diretas ao pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1b1e-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="b1b1e-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="b1b1e-112">Category</span></span>

<span data-ttu-id="b1b1e-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1b1e-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1b1e-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b1b1e-114">Affected APIs</span></span>

<span data-ttu-id="b1b1e-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b1b1e-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
