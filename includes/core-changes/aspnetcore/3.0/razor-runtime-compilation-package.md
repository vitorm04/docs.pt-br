---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394068"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="aec3a-101">Razor: compilação de tempo de execução movida para um pacote</span><span class="sxs-lookup"><span data-stu-id="aec3a-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="aec3a-102">O suporte para a compilação em tempo de execução de exibições do Razor e Razor Pages foi movido para um pacote separado.</span><span class="sxs-lookup"><span data-stu-id="aec3a-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aec3a-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="aec3a-103">Version introduced</span></span>

<span data-ttu-id="aec3a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="aec3a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="aec3a-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="aec3a-105">Old behavior</span></span>

<span data-ttu-id="aec3a-106">A compilação em tempo de execução está disponível sem a necessidade de pacotes adicionais.</span><span class="sxs-lookup"><span data-stu-id="aec3a-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="aec3a-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="aec3a-107">New behavior</span></span>

<span data-ttu-id="aec3a-108">A funcionalidade foi movida para o pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="aec3a-108">The functionality has been moved to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

<span data-ttu-id="aec3a-109">As APIs a seguir estavam disponíveis anteriormente no `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` para dar suporte à compilação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="aec3a-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="aec3a-110">As APIs agora estão disponíveis por meio de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="aec3a-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

<span data-ttu-id="aec3a-111">Além disso, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` foi removido.</span><span class="sxs-lookup"><span data-stu-id="aec3a-111">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="aec3a-112">A recompilação em alterações de arquivo é habilitada por padrão referenciando o pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="aec3a-112">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aec3a-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="aec3a-113">Reason for change</span></span>

<span data-ttu-id="aec3a-114">Essa alteração foi necessária para remover a dependência de estrutura compartilhada ASP.NET Core em Roslyn.</span><span class="sxs-lookup"><span data-stu-id="aec3a-114">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aec3a-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="aec3a-115">Recommended action</span></span>

<span data-ttu-id="aec3a-116">Aplicativos que exigem compilação em tempo de execução ou recompilação de arquivos Razor devem executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="aec3a-116">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="aec3a-117">Adicione uma referência ao pacote `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="aec3a-117">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="aec3a-118">Atualize o método `Startup.ConfigureServices` do projeto para incluir uma chamada para `AddMvcRazorRuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="aec3a-118">Update the project's `Startup.ConfigureServices` method to include a call to `AddMvcRazorRuntimeCompilation`.</span></span> <span data-ttu-id="aec3a-119">Por exemplo, em `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="aec3a-119">For example, in `Startup.ConfigureServices`:</span></span>

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="aec3a-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="aec3a-120">Category</span></span>

<span data-ttu-id="aec3a-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aec3a-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aec3a-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="aec3a-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
