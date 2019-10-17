---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394425"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="9ad74-101">MVC: tipos "Pubternal" alterados para interno</span><span class="sxs-lookup"><span data-stu-id="9ad74-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="9ad74-102">No ASP.NET Core 3,0, todos os tipos "pubternal" no MVC foram atualizados para `public` em um namespace com suporte ou `internal`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="9ad74-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9ad74-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="9ad74-103">Change description</span></span>

<span data-ttu-id="9ad74-104">Em ASP.NET Core, os tipos "pubternal" são declarados como `public`, mas residem em um namespace `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="9ad74-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="9ad74-105">Embora esses tipos sejam `public`, eles não têm nenhuma política de suporte e estão sujeitos a alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="9ad74-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="9ad74-106">Infelizmente, o uso acidental desses tipos foi comum, resultando em alterações significativas nesses projetos e limitando a capacidade de manter a estrutura.</span><span class="sxs-lookup"><span data-stu-id="9ad74-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9ad74-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9ad74-107">Version introduced</span></span>

<span data-ttu-id="9ad74-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9ad74-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9ad74-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="9ad74-109">Old behavior</span></span>

<span data-ttu-id="9ad74-110">Alguns tipos no MVC foram `public`, mas em um namespace `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="9ad74-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="9ad74-111">Esses tipos não tinham nenhuma política de suporte e estavam sujeitos a alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="9ad74-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9ad74-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="9ad74-112">New behavior</span></span>

<span data-ttu-id="9ad74-113">Todos esses tipos são atualizados para serem `public` em um namespace com suporte ou marcados como `internal`.</span><span class="sxs-lookup"><span data-stu-id="9ad74-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9ad74-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="9ad74-114">Reason for change</span></span>

<span data-ttu-id="9ad74-115">O uso acidental dos tipos "pubternal" é comum, resultando em alterações significativas nesses projetos e limitando a capacidade de manter a estrutura.</span><span class="sxs-lookup"><span data-stu-id="9ad74-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9ad74-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="9ad74-116">Recommended action</span></span>

<span data-ttu-id="9ad74-117">Se você estiver usando tipos que se tornaram verdadeiramente `public` e foram movidos para um novo namespace com suporte, atualize suas referências para que correspondam aos novos namespaces.</span><span class="sxs-lookup"><span data-stu-id="9ad74-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="9ad74-118">Se você estiver usando tipos que se tornaram marcados como `internal`, você precisará encontrar uma alternativa.</span><span class="sxs-lookup"><span data-stu-id="9ad74-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="9ad74-119">Os tipos de "pubternal" anteriormente nunca tinham suporte para uso público.</span><span class="sxs-lookup"><span data-stu-id="9ad74-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="9ad74-120">Se houver tipos específicos nesses namespaces que são críticos para seus aplicativos, execute um problema em [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="9ad74-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span> <span data-ttu-id="9ad74-121">Podem ser feitas considerações para fazer os tipos solicitados `public`.</span><span class="sxs-lookup"><span data-stu-id="9ad74-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="9ad74-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="9ad74-122">Category</span></span>

<span data-ttu-id="9ad74-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ad74-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ad74-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9ad74-124">Affected APIs</span></span>

<span data-ttu-id="9ad74-125">Essa alteração inclui tipos nos seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="9ad74-125">This change includes types in the following namespaces:</span></span>

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
