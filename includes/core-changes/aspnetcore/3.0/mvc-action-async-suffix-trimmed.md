---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901638"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="b743d-101">MVC: Sufixo assíncrono aparado a partir de nomes de ação do controlador</span><span class="sxs-lookup"><span data-stu-id="b743d-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="b743d-102">Como parte do endereçamento [do dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), `Async` ASP.NET MVC do Core apara o sufixo dos nomes de ação por padrão.</span><span class="sxs-lookup"><span data-stu-id="b743d-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="b743d-103">Começando com ASP.NET Núcleo 3.0, essa alteração afeta tanto o roteamento quanto a geração de links.</span><span class="sxs-lookup"><span data-stu-id="b743d-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b743d-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b743d-104">Version introduced</span></span>

<span data-ttu-id="b743d-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b743d-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b743d-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="b743d-106">Old behavior</span></span>

<span data-ttu-id="b743d-107">Considere o seguinte controlador ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="b743d-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="b743d-108">A ação é rotável via `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="b743d-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="b743d-109">A geração de `Async` links requer especificação do sufixo.</span><span class="sxs-lookup"><span data-stu-id="b743d-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="b743d-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="b743d-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="b743d-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="b743d-111">New behavior</span></span>

<span data-ttu-id="b743d-112">Em ASP.NET Núcleo 3.0, a ação `Product/List`é roteável via .</span><span class="sxs-lookup"><span data-stu-id="b743d-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="b743d-113">O código de geração `Async` de links deve omitir o sufixo.</span><span class="sxs-lookup"><span data-stu-id="b743d-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="b743d-114">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="b743d-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="b743d-115">Essa alteração não afeta nomes especificados usando o atributo. `[ActionName]`</span><span class="sxs-lookup"><span data-stu-id="b743d-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="b743d-116">O novo comportamento pode `MvcOptions.SuppressAsyncSuffixInActionNames` ser `false` `Startup.ConfigureServices`desativado definindo em :</span><span class="sxs-lookup"><span data-stu-id="b743d-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="b743d-117">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="b743d-117">Reason for change</span></span>

<span data-ttu-id="b743d-118">Por convenção, os métodos assíncronos `Async`.NET são sufixos com .</span><span class="sxs-lookup"><span data-stu-id="b743d-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="b743d-119">No entanto, quando um método define uma ação MVC, é indesejável usar o `Async` sufixo.</span><span class="sxs-lookup"><span data-stu-id="b743d-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b743d-120">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b743d-120">Recommended action</span></span>

<span data-ttu-id="b743d-121">Se o seu aplicativo depender das ações de `Async` MVC que preservam o sufixo do nome, escolha uma das seguintes atenuações:</span><span class="sxs-lookup"><span data-stu-id="b743d-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="b743d-122">Use `[ActionName]` o atributo para preservar o nome original.</span><span class="sxs-lookup"><span data-stu-id="b743d-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="b743d-123">Desativar a renomeação inteiramente `false` `Startup.ConfigureServices`configurando `MvcOptions.SuppressAsyncSuffixInActionNames` para :</span><span class="sxs-lookup"><span data-stu-id="b743d-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="b743d-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="b743d-124">Category</span></span>

<span data-ttu-id="b743d-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b743d-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b743d-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b743d-126">Affected APIs</span></span>

<span data-ttu-id="b743d-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b743d-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
