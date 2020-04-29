---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507062"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="432ef-101">Tipos de BadHttpRequestException de HTTP: Kestrel e IIS marcados como obsoletos e substituídos</span><span class="sxs-lookup"><span data-stu-id="432ef-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="432ef-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` foram marcados como obsoletos e alterados para derivar de `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span><span class="sxs-lookup"><span data-stu-id="432ef-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="432ef-103">Os servidores Kestrel e IIS ainda lançam seus tipos de exceção antigos para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="432ef-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="432ef-104">Os tipos obsoletos serão removidos em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="432ef-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="432ef-105">Para obter uma discussão, consulte [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="432ef-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="432ef-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="432ef-106">Version introduced</span></span>

<span data-ttu-id="432ef-107">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="432ef-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="432ef-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="432ef-108">Old behavior</span></span>

<span data-ttu-id="432ef-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derivado de <xref:System.IO.IOException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="432ef-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="432ef-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="432ef-110">New behavior</span></span>

<span data-ttu-id="432ef-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="432ef-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="432ef-112">Os tipos também derivam `Microsoft.AspNetCore.Http.BadHttpRequestException`de, que deriva de `System.IO.IOException`.</span><span class="sxs-lookup"><span data-stu-id="432ef-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="432ef-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="432ef-113">Reason for change</span></span>

<span data-ttu-id="432ef-114">A alteração foi feita em:</span><span class="sxs-lookup"><span data-stu-id="432ef-114">The change was made to:</span></span>

* <span data-ttu-id="432ef-115">Consolide tipos duplicados.</span><span class="sxs-lookup"><span data-stu-id="432ef-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="432ef-116">Unificar o comportamento entre implementações do servidor.</span><span class="sxs-lookup"><span data-stu-id="432ef-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="432ef-117">Um aplicativo agora pode capturar a exceção `Microsoft.AspNetCore.Http.BadHttpRequestException` base ao usar o Kestrel ou o IIS.</span><span class="sxs-lookup"><span data-stu-id="432ef-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="432ef-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="432ef-118">Recommended action</span></span>

<span data-ttu-id="432ef-119">Substitua os usos de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` por `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span><span class="sxs-lookup"><span data-stu-id="432ef-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="432ef-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="432ef-120">Category</span></span>

<span data-ttu-id="432ef-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="432ef-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="432ef-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="432ef-122">Affected APIs</span></span>

- [<span data-ttu-id="432ef-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="432ef-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="432ef-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="432ef-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
