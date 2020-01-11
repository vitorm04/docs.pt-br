---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901638"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="0c4ab-101">MVC: sufixo assíncrono cortado dos nomes de ação do controlador</span><span class="sxs-lookup"><span data-stu-id="0c4ab-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="0c4ab-102">Como parte do endereçamento [dotnet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC apara o sufixo `Async` de nomes de ação por padrão.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="0c4ab-103">A partir do ASP.NET Core 3,0, essa alteração afeta o roteamento e a geração de link.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c4ab-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0c4ab-104">Version introduced</span></span>

<span data-ttu-id="0c4ab-105">3.0</span><span class="sxs-lookup"><span data-stu-id="0c4ab-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0c4ab-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0c4ab-106">Old behavior</span></span>

<span data-ttu-id="0c4ab-107">Considere o seguinte controlador MVC ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="0c4ab-108">A ação é roteável via `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="0c4ab-109">A geração de link requer a especificação do sufixo de `Async`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="0c4ab-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="0c4ab-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0c4ab-111">New behavior</span></span>

<span data-ttu-id="0c4ab-112">No ASP.NET Core 3,0, a ação é roteável via `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="0c4ab-113">O código de geração de link deve omitir o sufixo de `Async`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="0c4ab-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="0c4ab-115">Essa alteração não afeta os nomes especificados usando o atributo `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="0c4ab-116">O novo comportamento pode ser desabilitado definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` no `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="0c4ab-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0c4ab-117">Reason for change</span></span>

<span data-ttu-id="0c4ab-118">Por convenção, os métodos .NET assíncronos têm um sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="0c4ab-119">No entanto, quando um método define uma ação MVC, não é desejável usar o sufixo `Async`.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c4ab-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0c4ab-120">Recommended action</span></span>

<span data-ttu-id="0c4ab-121">Se seu aplicativo depende de ações do MVC preservando o sufixo de `Async` do nome, escolha uma das seguintes atenuações:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="0c4ab-122">Use o atributo `[ActionName]` para preservar o nome original.</span><span class="sxs-lookup"><span data-stu-id="0c4ab-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="0c4ab-123">Desabilite a renomeação total definindo `MvcOptions.SuppressAsyncSuffixInActionNames` como `false` no `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="0c4ab-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="0c4ab-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="0c4ab-124">Category</span></span>

<span data-ttu-id="0c4ab-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0c4ab-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c4ab-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0c4ab-126">Affected APIs</span></span>

<span data-ttu-id="0c4ab-127">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0c4ab-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
