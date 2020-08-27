---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957674"
---
### <a name="razor-razortemplateengine-api-removed"></a><span data-ttu-id="ff2d3-101">Razor: API RazorTemplateEngine removida</span><span class="sxs-lookup"><span data-stu-id="ff2d3-101">Razor: RazorTemplateEngine API removed</span></span>

<span data-ttu-id="ff2d3-102">A API [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) foi removida e substituída por <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> .</span><span class="sxs-lookup"><span data-stu-id="ff2d3-102">The [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API was removed and replaced with <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span></span>

<span data-ttu-id="ff2d3-103">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 25215](https://github.com/dotnet/aspnetcore/issues/25215).</span><span class="sxs-lookup"><span data-stu-id="ff2d3-103">For discussion, see GitHub issue [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ff2d3-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ff2d3-104">Version introduced</span></span>

<span data-ttu-id="ff2d3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="ff2d3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ff2d3-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ff2d3-106">Old behavior</span></span>

<span data-ttu-id="ff2d3-107">Um mecanismo de modelo pode ser criado e usado para analisar e gerar código para arquivos Razor.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-107">A template engine can be created and used to parse and generate code for Razor files.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ff2d3-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ff2d3-108">New behavior</span></span>

<span data-ttu-id="ff2d3-109">`RazorProjectEngine` pode ser criado e fornecido o mesmo tipo de informação `RazorTemplateEngine` para analisar e gerar código para arquivos Razor.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-109">`RazorProjectEngine` can be created and provided the same type of information as `RazorTemplateEngine` to parse and generate code for Razor files.</span></span> <span data-ttu-id="ff2d3-110">`RazorProjectEngine` também fornece níveis extras de configuração.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-110">`RazorProjectEngine` also provides extra levels of configuration.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ff2d3-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ff2d3-111">Reason for change</span></span>

<span data-ttu-id="ff2d3-112">`RazorTemplateEngine` estava intimamente acoplado às implementações existentes.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-112">`RazorTemplateEngine` was too tightly coupled to the existing implementations.</span></span> <span data-ttu-id="ff2d3-113">Esse acoplamento rígido levou a mais perguntas ao tentar configurar corretamente um pipeline de análise/geração do Razor.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-113">This tight coupling led to more questions when trying to properly configure a Razor parsing/generation pipeline.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ff2d3-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ff2d3-114">Recommended action</span></span>

<span data-ttu-id="ff2d3-115">Use `RazorProjectEngine` em vez de `RazorTemplateEngine`.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-115">Use `RazorProjectEngine` instead of `RazorTemplateEngine`.</span></span> <span data-ttu-id="ff2d3-116">Considere os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff2d3-116">Consider the following examples.</span></span>

##### <a name="create-and-configure-the-razorprojectengine"></a><span data-ttu-id="ff2d3-117">Criar e configurar o RazorProjectEngine</span><span class="sxs-lookup"><span data-stu-id="ff2d3-117">Create and configure the RazorProjectEngine</span></span>

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a><span data-ttu-id="ff2d3-118">Gerar código para um arquivo Razor</span><span class="sxs-lookup"><span data-stu-id="ff2d3-118">Generate code for a Razor file</span></span>

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a><span data-ttu-id="ff2d3-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="ff2d3-119">Category</span></span>

<span data-ttu-id="ff2d3-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ff2d3-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ff2d3-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ff2d3-121">Affected APIs</span></span>

- [<span data-ttu-id="ff2d3-122">RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="ff2d3-122">RazorTemplateEngine</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [<span data-ttu-id="ff2d3-123">RazorTemplateEngineOptions</span><span class="sxs-lookup"><span data-stu-id="ff2d3-123">RazorTemplateEngineOptions</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
