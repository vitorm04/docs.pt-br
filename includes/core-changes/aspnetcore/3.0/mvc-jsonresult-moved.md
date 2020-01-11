---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901613"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="10d38-101">MVC: JsonResult movido para Microsoft. AspNetCore. Mvc. Core</span><span class="sxs-lookup"><span data-stu-id="10d38-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="10d38-102">`JsonResult` foi movido para o assembly `Microsoft.AspNetCore.Mvc.Core`.</span><span class="sxs-lookup"><span data-stu-id="10d38-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="10d38-103">Esse tipo costumava ser definido em [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="10d38-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="10d38-104">Um atributo de nível de assembly [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) foi adicionado ao `Microsoft.AspNetCore.Mvc.Formatters.Json` para resolver esse problema para a maioria dos usuários.</span><span class="sxs-lookup"><span data-stu-id="10d38-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="10d38-105">Aplicativos que usam bibliotecas de terceiros podem encontrar problemas.</span><span class="sxs-lookup"><span data-stu-id="10d38-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10d38-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="10d38-106">Version introduced</span></span>

<span data-ttu-id="10d38-107">3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="10d38-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="10d38-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="10d38-108">Old behavior</span></span>

<span data-ttu-id="10d38-109">Um aplicativo que usa uma biblioteca baseada em 2,2 é compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="10d38-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="10d38-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="10d38-110">New behavior</span></span>

<span data-ttu-id="10d38-111">Um aplicativo que usa uma biblioteca com base em 2,2 falha na compilação.</span><span class="sxs-lookup"><span data-stu-id="10d38-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="10d38-112">Um erro contendo uma variação do texto a seguir é fornecido:</span><span class="sxs-lookup"><span data-stu-id="10d38-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="10d38-113">Para obter um exemplo desse problema, consulte [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="10d38-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="10d38-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="10d38-114">Reason for change</span></span>

<span data-ttu-id="10d38-115">Alterações no nível da plataforma para a composição de ASP.NET Core conforme descrito em [ASPNET/comunicados # 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="10d38-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10d38-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="10d38-116">Recommended action</span></span>

<span data-ttu-id="10d38-117">Bibliotecas compiladas na versão 2,2 do `Microsoft.AspNetCore.Mvc.Formatters.Json` talvez precisem ser recompiladas para resolver o problema de todos os consumidores.</span><span class="sxs-lookup"><span data-stu-id="10d38-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="10d38-118">Se for afetado, contate o autor da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="10d38-118">If affected, contact the library author.</span></span> <span data-ttu-id="10d38-119">Solicite a recompilação da biblioteca para o destino ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="10d38-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="10d38-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="10d38-120">Category</span></span>

<span data-ttu-id="10d38-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10d38-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10d38-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="10d38-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
