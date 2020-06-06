---
ms.openlocfilehash: b1fb9647091cecb80b9c2f04ec9b6bb156eb39ba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84466830"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="194c9-101">APIs "Pubternal" removidas</span><span class="sxs-lookup"><span data-stu-id="194c9-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="194c9-102">Para manter a superfície da API pública de ASP.NET Core, a maioria dos tipos em `*.Internal` namespaces (conhecidos como :::no-loc text="\"pubternal\""::: APIs) se tornou verdadeiramente interna.</span><span class="sxs-lookup"><span data-stu-id="194c9-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="194c9-103">Os membros desses namespaces nunca devem ter suporte como APIs voltadas para o público.</span><span class="sxs-lookup"><span data-stu-id="194c9-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="194c9-104">As APIs podem ser interrompidas em versões secundárias e com frequência.</span><span class="sxs-lookup"><span data-stu-id="194c9-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="194c9-105">O código que depende dessas APIs é interrompido ao atualizar para ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="194c9-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="194c9-106">Para obter mais informações, consulte [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) e [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="194c9-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="194c9-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="194c9-107">Version introduced</span></span>

<span data-ttu-id="194c9-108">3.0</span><span class="sxs-lookup"><span data-stu-id="194c9-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="194c9-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="194c9-109">Old behavior</span></span>

<span data-ttu-id="194c9-110">As APIs afetadas são marcadas com o `public` modificador de acesso e existem em `*.Internal` namespaces.</span><span class="sxs-lookup"><span data-stu-id="194c9-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="194c9-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="194c9-111">New behavior</span></span>

<span data-ttu-id="194c9-112">As APIs afetadas são marcadas com o modificador de acesso [interno](/dotnet/csharp/language-reference/keywords/internal) e não podem mais ser usadas pelo código fora desse assembly.</span><span class="sxs-lookup"><span data-stu-id="194c9-112">The affected APIs are marked with the [internal](/dotnet/csharp/language-reference/keywords/internal) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="194c9-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="194c9-113">Reason for change</span></span>

<span data-ttu-id="194c9-114">As diretrizes para essas :::no-loc text="\"pubternal\""::: APIs eram:</span><span class="sxs-lookup"><span data-stu-id="194c9-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="194c9-115">Pode ser alterado sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="194c9-115">Could change without notice.</span></span>
* <span data-ttu-id="194c9-116">Não estavam sujeitos às políticas do .NET para evitar alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="194c9-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="194c9-117">Deixar as APIs `public` (mesmo nos `*.Internal` namespaces) era confusa para os clientes.</span><span class="sxs-lookup"><span data-stu-id="194c9-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="194c9-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="194c9-118">Recommended action</span></span>

<span data-ttu-id="194c9-119">Pare de usar essas :::no-loc text="\"pubternal\""::: APIs.</span><span class="sxs-lookup"><span data-stu-id="194c9-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="194c9-120">Se você tiver dúvidas sobre APIs alternativas, abra um problema no repositório [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .</span><span class="sxs-lookup"><span data-stu-id="194c9-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="194c9-121">Por exemplo, considere o seguinte código de buffer de solicitação HTTP em um projeto ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="194c9-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="194c9-122">O `EnableRewind` método de extensão existe no `Microsoft.AspNetCore.Http.Internal` namespace.</span><span class="sxs-lookup"><span data-stu-id="194c9-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="194c9-123">Em um projeto ASP.NET Core 3,0, substitua a `EnableRewind` chamada por uma chamada para o `EnableBuffering` método de extensão.</span><span class="sxs-lookup"><span data-stu-id="194c9-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="194c9-124">O recurso de buffer de solicitação funciona como fazia no passado.</span><span class="sxs-lookup"><span data-stu-id="194c9-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="194c9-125">`EnableBuffering`chama a `internal` API Now.</span><span class="sxs-lookup"><span data-stu-id="194c9-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="194c9-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="194c9-126">Category</span></span>

<span data-ttu-id="194c9-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="194c9-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="194c9-128">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="194c9-128">Affected APIs</span></span>

<span data-ttu-id="194c9-129">Todas as APIs nos `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` namespaces e que têm um `Internal` segmento no nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="194c9-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="194c9-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="194c9-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
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
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
