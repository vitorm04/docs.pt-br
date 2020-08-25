---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811245"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a>Middleware: página de erro do banco de dados marcada como obsoleta

O [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) e seus métodos de extensão associados foram marcados como obsoletos no ASP.NET Core 5,0. Os métodos de middleware e de extensão serão removidos no ASP.NET Core 6,0. Em vez disso, a funcionalidade será fornecida por `DatabaseDeveloperPageExceptionFilter` e seus métodos de extensão.

Para obter uma discussão, consulte o problema do GitHub em [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987).

#### <a name="version-introduced"></a>Versão introduzida

5,0 RC 1

#### <a name="old-behavior"></a>Comportamento antigo

`DatabaseErrorPageMiddleware` e seus métodos de extensão associados não estavam obsoletos.

#### <a name="new-behavior"></a>Novo comportamento

`DatabaseErrorPageMiddleware` e seus métodos de extensão associados são obsoletos.

#### <a name="reason-for-change"></a>Motivo da alteração

`DatabaseErrorPageMiddleware` foi migrado para uma API extensível para a [página de exceção do desenvolvedor](/aspnet/core/fundamentals/error-handling#developer-exception-page). Para obter mais informações sobre a API extensível, consulte o problema do GitHub [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).

#### <a name="recommended-action"></a>Ação recomendada

Concluir as seguintes etapas:

1. Pare `DatabaseErrorPageMiddleware` de usar no seu projeto. Por exemplo, remova a `UseDatabaseErrorPage` chamada de método de `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. Adicione a página de exceção do desenvolvedor ao seu projeto. Por exemplo, chame o <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> método em `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. Adicione o filtro de exceção da página do desenvolvedor de banco de dados à coleção de serviços. Por exemplo, chame o `AddDatabaseDeveloperPageExceptionFilter` método em `Startup.ConfigureServices` :

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- [Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
