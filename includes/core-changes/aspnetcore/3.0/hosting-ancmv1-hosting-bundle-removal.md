---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901774"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="f6861-101">Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows</span><span class="sxs-lookup"><span data-stu-id="f6861-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="f6861-102">A partir do ASP.NET Core 3,0, o grupo de hospedagem do Windows não conterá AspNetCoreModule (ANCM) v1.</span><span class="sxs-lookup"><span data-stu-id="f6861-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="f6861-103">O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.</span><span class="sxs-lookup"><span data-stu-id="f6861-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="f6861-104">Para obter uma discussão, consulte [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="f6861-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f6861-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="f6861-105">Version introduced</span></span>

<span data-ttu-id="f6861-106">3.0</span><span class="sxs-lookup"><span data-stu-id="f6861-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f6861-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="f6861-107">Old behavior</span></span>

<span data-ttu-id="f6861-108">O ANCM v1 está incluído no pacote de hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="f6861-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f6861-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="f6861-109">New behavior</span></span>

<span data-ttu-id="f6861-110">O ANCM v1 não está incluído no pacote de hospedagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="f6861-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f6861-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="f6861-111">Reason for change</span></span>

<span data-ttu-id="f6861-112">O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.</span><span class="sxs-lookup"><span data-stu-id="f6861-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f6861-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="f6861-113">Recommended action</span></span>

<span data-ttu-id="f6861-114">Use o ANCM V2 com aplicativos ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f6861-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="f6861-115">Se o ANCM v1 for necessário, ele poderá ser instalado usando o pacote de hospedagem ASP.NET Core 2,1 ou 2,2 do Windows.</span><span class="sxs-lookup"><span data-stu-id="f6861-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="f6861-116">Essa alteração interromperá ASP.NET Core aplicativos 3,0 que:</span><span class="sxs-lookup"><span data-stu-id="f6861-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="f6861-117">Optamos explicitamente por usar o ANCM v1 com `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span><span class="sxs-lookup"><span data-stu-id="f6861-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="f6861-118">Ter um arquivo *Web. config* personalizado com `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span><span class="sxs-lookup"><span data-stu-id="f6861-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="f6861-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="f6861-119">Category</span></span>

<span data-ttu-id="f6861-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f6861-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f6861-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f6861-121">Affected APIs</span></span>

<span data-ttu-id="f6861-122">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f6861-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
