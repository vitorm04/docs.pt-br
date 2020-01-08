---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344295"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="c8bbe-101">Razor: compilação de tempo de execução movida para um pacote</span><span class="sxs-lookup"><span data-stu-id="c8bbe-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="c8bbe-102">O suporte para a compilação em tempo de execução de exibições do Razor e Razor Pages foi movido para um pacote separado.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c8bbe-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c8bbe-103">Version introduced</span></span>

<span data-ttu-id="c8bbe-104">3.0</span><span class="sxs-lookup"><span data-stu-id="c8bbe-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c8bbe-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="c8bbe-105">Old behavior</span></span>

<span data-ttu-id="c8bbe-106">A compilação em tempo de execução está disponível sem a necessidade de pacotes adicionais.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c8bbe-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="c8bbe-107">New behavior</span></span>

<span data-ttu-id="c8bbe-108">A funcionalidade foi movida para o pacote [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) .</span><span class="sxs-lookup"><span data-stu-id="c8bbe-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="c8bbe-109">As APIs a seguir estavam disponíveis anteriormente em `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` para dar suporte à compilação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="c8bbe-110">As APIs agora estão disponíveis por meio de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="c8bbe-111">`RazorViewEngineOptions.FileProviders` agora é `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="c8bbe-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="c8bbe-112">`RazorViewEngineOptions.AdditionalCompilationReferences` agora é `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="c8bbe-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="c8bbe-113">Além disso, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` foi removido.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="c8bbe-114">A recompilação em alterações de arquivo é habilitada por padrão referenciando o pacote de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c8bbe-115">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="c8bbe-115">Reason for change</span></span>

<span data-ttu-id="c8bbe-116">Essa alteração foi necessária para remover a dependência de estrutura compartilhada ASP.NET Core em Roslyn.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c8bbe-117">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c8bbe-117">Recommended action</span></span>

<span data-ttu-id="c8bbe-118">Aplicativos que exigem compilação em tempo de execução ou recompilação de arquivos Razor devem executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c8bbe-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="c8bbe-119">Adicione uma referência ao pacote de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="c8bbe-120">Atualize o método de `Startup.ConfigureServices` do projeto para incluir uma chamada para `AddRazorRuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="c8bbe-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="c8bbe-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8bbe-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="c8bbe-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="c8bbe-122">Category</span></span>

<span data-ttu-id="c8bbe-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c8bbe-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c8bbe-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c8bbe-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
