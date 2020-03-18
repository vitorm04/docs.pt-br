---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901667"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="5aa20-101">MVC: Tipos de "pubternal" alterados para internos</span><span class="sxs-lookup"><span data-stu-id="5aa20-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="5aa20-102">Em ASP.NET Núcleo 3.0, todos os tipos "pubternais" `public` em MVC foram `internal` atualizados para estar em um namespace suportado ou conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="5aa20-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5aa20-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="5aa20-103">Change description</span></span>

<span data-ttu-id="5aa20-104">Em ASP.NET Core, os tipos "pubternais" são declarados como `public` mas residem em um `.Internal`espaço de nome sufixo.</span><span class="sxs-lookup"><span data-stu-id="5aa20-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="5aa20-105">Embora esses `public`tipos sejam, eles não têm política de apoio e estão sujeitos a mudanças.</span><span class="sxs-lookup"><span data-stu-id="5aa20-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="5aa20-106">Infelizmente, o uso acidental desses tipos tem sido comum, resultando em mudanças nesses projetos e limitando a capacidade de manter o quadro.</span><span class="sxs-lookup"><span data-stu-id="5aa20-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5aa20-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5aa20-107">Version introduced</span></span>

<span data-ttu-id="5aa20-108">3.0</span><span class="sxs-lookup"><span data-stu-id="5aa20-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5aa20-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="5aa20-109">Old behavior</span></span>

<span data-ttu-id="5aa20-110">Alguns tipos em `public` MVC `.Internal` estavam em um namespace.</span><span class="sxs-lookup"><span data-stu-id="5aa20-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="5aa20-111">Esses tipos não tinham política de apoio e estavam sujeitos a mudanças.</span><span class="sxs-lookup"><span data-stu-id="5aa20-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5aa20-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="5aa20-112">New behavior</span></span>

<span data-ttu-id="5aa20-113">Todos esses tipos são `public` atualizados para estar em `internal`um namespace suportado ou marcado como .</span><span class="sxs-lookup"><span data-stu-id="5aa20-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5aa20-114">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="5aa20-114">Reason for change</span></span>

<span data-ttu-id="5aa20-115">O uso acidental dos tipos "pubternais" tem sido comum, resultando em mudanças nesses projetos e limitando a capacidade de manutenção da estrutura.</span><span class="sxs-lookup"><span data-stu-id="5aa20-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5aa20-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5aa20-116">Recommended action</span></span>

<span data-ttu-id="5aa20-117">Se você estiver usando tipos `public` que se tornaram verdadeiramente e foram movidos para um novo espaço de nome suportado, atualize suas referências para combinar com os novos namespaces.</span><span class="sxs-lookup"><span data-stu-id="5aa20-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="5aa20-118">Se você estiver usando tipos que `internal`se tornaram marcados como , você precisará encontrar uma alternativa.</span><span class="sxs-lookup"><span data-stu-id="5aa20-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="5aa20-119">Os tipos anteriormente "pubternais" nunca foram apoiados para uso público.</span><span class="sxs-lookup"><span data-stu-id="5aa20-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="5aa20-120">Se houver tipos específicos nesses namespaces que são críticos para seus aplicativos, arquive um problema no [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="5aa20-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="5aa20-121">Podem ser feitas considerações para `public`a realização dos tipos solicitados.</span><span class="sxs-lookup"><span data-stu-id="5aa20-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="5aa20-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="5aa20-122">Category</span></span>

<span data-ttu-id="5aa20-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5aa20-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5aa20-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5aa20-124">Affected APIs</span></span>

<span data-ttu-id="5aa20-125">Essa alteração inclui tipos nos seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="5aa20-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
