---
ms.openlocfilehash: 10521759d31c3183232cdb1793d78d139f13ce41
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077560"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="55841-101">Middleware: página de erro do banco de dados marcada como obsoleta</span><span class="sxs-lookup"><span data-stu-id="55841-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="55841-102">O [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) e seus métodos de extensão associados foram marcados como obsoletos no ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="55841-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="55841-103">Os métodos de middleware e de extensão serão removidos no ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="55841-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="55841-104">Em vez disso, a funcionalidade será fornecida por `DatabaseDeveloperPageExceptionFilter` e seus métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="55841-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="55841-105">Para obter uma discussão, consulte o problema do GitHub em [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="55841-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="55841-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="55841-106">Version introduced</span></span>

<span data-ttu-id="55841-107">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="55841-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="55841-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="55841-108">Old behavior</span></span>

<span data-ttu-id="55841-109">`DatabaseErrorPageMiddleware` e seus métodos de extensão associados não estavam obsoletos.</span><span class="sxs-lookup"><span data-stu-id="55841-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="55841-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="55841-110">New behavior</span></span>

<span data-ttu-id="55841-111">`DatabaseErrorPageMiddleware` e seus métodos de extensão associados são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="55841-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="55841-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="55841-112">Reason for change</span></span>

<span data-ttu-id="55841-113">`DatabaseErrorPageMiddleware` foi migrado para uma API extensível para a [página de exceção do desenvolvedor](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="55841-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="55841-114">Para obter mais informações sobre a API extensível, consulte o problema do GitHub [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="55841-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="55841-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="55841-115">Recommended action</span></span>

<span data-ttu-id="55841-116">Concluir as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="55841-116">Complete the following steps:</span></span>

1. <span data-ttu-id="55841-117">Pare `DatabaseErrorPageMiddleware` de usar no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="55841-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="55841-118">Por exemplo, remova a `UseDatabaseErrorPage` chamada de método de `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="55841-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="55841-119">Adicione a página de exceção do desenvolvedor ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="55841-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="55841-120">Por exemplo, chame o <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> método em `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="55841-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="55841-121">Adicione o pacote NuGet [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="55841-121">Add the [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet package to the project file.</span></span>

1. <span data-ttu-id="55841-122">Adicione o filtro de exceção da página do desenvolvedor de banco de dados à coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="55841-122">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="55841-123">Por exemplo, chame o `AddDatabaseDeveloperPageExceptionFilter` método em `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="55841-123">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="55841-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="55841-124">Category</span></span>

<span data-ttu-id="55841-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="55841-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="55841-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="55841-126">Affected APIs</span></span>

- [<span data-ttu-id="55841-127">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="55841-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="55841-128">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="55841-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
