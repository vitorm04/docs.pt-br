---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901774"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="60afa-101">Hospedagem: AspNetCoreModule V1 removido do Pacote de Hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="60afa-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="60afa-102">Começando com ASP.NET Core 3.0, o Pacote de Hospedagem do Windows não conterá OAspNetCoreModule (ANCM) V1.</span><span class="sxs-lookup"><span data-stu-id="60afa-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="60afa-103">O ANCM V2 é retrocompatível com o ANCM OutOfProcess e é recomendado para uso com aplicativos ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="60afa-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="60afa-104">Para discussão, consulte [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="60afa-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="60afa-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="60afa-105">Version introduced</span></span>

<span data-ttu-id="60afa-106">3.0</span><span class="sxs-lookup"><span data-stu-id="60afa-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="60afa-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="60afa-107">Old behavior</span></span>

<span data-ttu-id="60afa-108">Ancm V1 está incluído no Pacote de Hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="60afa-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="60afa-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="60afa-109">New behavior</span></span>

<span data-ttu-id="60afa-110">O ANCM V1 não está incluído no Pacote de Hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="60afa-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="60afa-111">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="60afa-111">Reason for change</span></span>

<span data-ttu-id="60afa-112">O ANCM V2 é retrocompatível com o ANCM OutOfProcess e é recomendado para uso com aplicativos ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="60afa-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60afa-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="60afa-113">Recommended action</span></span>

<span data-ttu-id="60afa-114">Use ancm V2 com aplicativos ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="60afa-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="60afa-115">Se o ANCM V1 for necessário, ele pode ser instalado usando o ASP.NET Core 2.1 ou 2.2 Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="60afa-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="60afa-116">Essa alteração quebrará ASP.NET aplicativos Core 3.0 que:</span><span class="sxs-lookup"><span data-stu-id="60afa-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="60afa-117">Optou explicitamente pelo uso do `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`ANCM V1 com .</span><span class="sxs-lookup"><span data-stu-id="60afa-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="60afa-118">Tenha um arquivo *web.config* personalizado com `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span><span class="sxs-lookup"><span data-stu-id="60afa-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="60afa-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="60afa-119">Category</span></span>

<span data-ttu-id="60afa-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="60afa-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60afa-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="60afa-121">Affected APIs</span></span>

<span data-ttu-id="60afa-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="60afa-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
