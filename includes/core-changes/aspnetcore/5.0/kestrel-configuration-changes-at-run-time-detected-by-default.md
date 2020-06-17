---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803256"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="f21aa-101">Kestrel: alterações de configuração em tempo de execução detectadas por padrão</span><span class="sxs-lookup"><span data-stu-id="f21aa-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="f21aa-102">Kestrel agora reage às alterações feitas na `Kestrel` seção da instância do projeto `IConfiguration` (por exemplo, *appsettings.json*) em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f21aa-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="f21aa-103">Para saber mais sobre como configurar o Kestrel usando o *appsettings.jsno*, consulte o *appsettings.jsno* exemplo na [configuração do ponto de extremidade](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span><span class="sxs-lookup"><span data-stu-id="f21aa-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="f21aa-104">Kestrel irá ligar, desassociar e reassociar pontos de extremidade conforme necessário para reagir a essas alterações de configuração.</span><span class="sxs-lookup"><span data-stu-id="f21aa-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="f21aa-105">Para obter uma discussão, veja Issue [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="f21aa-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f21aa-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="f21aa-106">Version introduced</span></span>

<span data-ttu-id="f21aa-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="f21aa-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f21aa-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="f21aa-108">Old behavior</span></span>

<span data-ttu-id="f21aa-109">Antes da ASP.NET Core 5,0 Preview 6, o Kestrel não tinha suporte para alterar a configuração em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f21aa-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="f21aa-110">No ASP.NET Core 5,0 Preview 6, você poderia optar pelo comportamento agora padrão de reagir às alterações de configuração em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f21aa-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="f21aa-111">Optando pela configuração do Kestrel de vinculação necessária manualmente:</span><span class="sxs-lookup"><span data-stu-id="f21aa-111">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a><span data-ttu-id="f21aa-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="f21aa-112">New behavior</span></span>

<span data-ttu-id="f21aa-113">O Kestrel reage às alterações de configuração em tempo de execução por padrão.</span><span class="sxs-lookup"><span data-stu-id="f21aa-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="f21aa-114">Para dar suporte a essa alteração, o <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> chama `KestrelServerOptions.Configure(IConfiguration, bool)` com `reloadOnChange: true` por padrão.</span><span class="sxs-lookup"><span data-stu-id="f21aa-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f21aa-115">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="f21aa-115">Reason for change</span></span>

<span data-ttu-id="f21aa-116">A alteração foi feita para dar suporte à reconfiguração de ponto de extremidade em tempo de execução sem reiniciar completamente o servidor.</span><span class="sxs-lookup"><span data-stu-id="f21aa-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="f21aa-117">Ao contrário de uma reinicialização completa do servidor, os pontos de extremidade inalterados não são desassociados mesmo temporariamente.</span><span class="sxs-lookup"><span data-stu-id="f21aa-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f21aa-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="f21aa-118">Recommended action</span></span>

* <span data-ttu-id="f21aa-119">Para a maioria dos cenários em que a seção de configuração padrão do Kestrel não é alterada em tempo de execução, essa alteração não tem nenhum impacto e nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="f21aa-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="f21aa-120">Para cenários nos quais a seção de configuração padrão do Kestrel é alterada em tempo de execução e Kestrel deve reagir a ela, esse agora é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="f21aa-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="f21aa-121">Para cenários nos quais a seção de configuração padrão do Kestrel é alterada em tempo de execução e Kestrel não deve reagir a ela, você pode recusar da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f21aa-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="f21aa-122">**Observações:**</span><span class="sxs-lookup"><span data-stu-id="f21aa-122">**Notes:**</span></span>

<span data-ttu-id="f21aa-123">Essa alteração não modifica o comportamento da `KestrelServerOptions.Configure(IConfiguration)` sobrecarga, que ainda usa como padrão o `reloadOnChange: false` comportamento.</span><span class="sxs-lookup"><span data-stu-id="f21aa-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="f21aa-124">Também é importante verificar se a fonte de configuração dá suporte ao recarregamento.</span><span class="sxs-lookup"><span data-stu-id="f21aa-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="f21aa-125">Para fontes JSON, o recarregamento é configurado chamando `AddJsonFile(path, reloadOnChange: true)` .</span><span class="sxs-lookup"><span data-stu-id="f21aa-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="f21aa-126">O recarregamento já está configurado por padrão para *appsettings.jsem* e *appSettings. { Ambiente}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="f21aa-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="f21aa-127">Categoria</span><span class="sxs-lookup"><span data-stu-id="f21aa-127">Category</span></span>

<span data-ttu-id="f21aa-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f21aa-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f21aa-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f21aa-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
