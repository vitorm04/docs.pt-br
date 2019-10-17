---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394383"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="950bc-101">MVC: sufixo assíncrono cortado dos nomes de ação do controlador</span><span class="sxs-lookup"><span data-stu-id="950bc-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="950bc-102">Como parte do endereçamento [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC apara o sufixo `Async` dos nomes de ação por padrão.</span><span class="sxs-lookup"><span data-stu-id="950bc-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="950bc-103">A partir do ASP.NET Core 3,0, essa alteração afeta o roteamento e a geração de link.</span><span class="sxs-lookup"><span data-stu-id="950bc-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="950bc-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="950bc-104">Version introduced</span></span>

<span data-ttu-id="950bc-105">3.0</span><span class="sxs-lookup"><span data-stu-id="950bc-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="950bc-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="950bc-106">Old behavior</span></span>

<span data-ttu-id="950bc-107">Considere o seguinte controlador MVC ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="950bc-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="950bc-108">A ação é roteável via `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="950bc-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="950bc-109">A geração de link requer a especificação do sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="950bc-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="950bc-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="950bc-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="950bc-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="950bc-111">New behavior</span></span>

<span data-ttu-id="950bc-112">No ASP.NET Core 3,0, a ação é roteável via `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="950bc-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="950bc-113">O código de geração de link deve omitir o sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="950bc-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="950bc-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="950bc-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="950bc-115">Essa alteração não afeta os nomes especificados usando o atributo `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="950bc-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="950bc-116">O novo comportamento pode ser desabilitado definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` em `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="950bc-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="950bc-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="950bc-117">Reason for change</span></span>

<span data-ttu-id="950bc-118">Por convenção, os métodos .NET assíncronos têm um sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="950bc-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="950bc-119">No entanto, quando um método define uma ação MVC, não é desejável usar o sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="950bc-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="950bc-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="950bc-120">Recommended action</span></span>

<span data-ttu-id="950bc-121">Se seu aplicativo depende de ações do MVC preservando o sufixo `Async` do nome, escolha uma das seguintes atenuações:</span><span class="sxs-lookup"><span data-stu-id="950bc-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="950bc-122">Use o atributo `[ActionName]` para preservar o nome original.</span><span class="sxs-lookup"><span data-stu-id="950bc-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="950bc-123">Desabilite a renomeação total definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` em `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="950bc-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="category"></a><span data-ttu-id="950bc-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="950bc-124">Category</span></span>

<span data-ttu-id="950bc-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="950bc-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="950bc-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="950bc-126">Affected APIs</span></span>

<span data-ttu-id="950bc-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="950bc-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
