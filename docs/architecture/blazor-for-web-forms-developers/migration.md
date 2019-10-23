---
title: Migrar do ASP.NET Web Forms para o mais incrivelmente
description: Saiba como abordar a migração de um aplicativo ASP.NET Web Forms existente para um mais incrivelmente.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 78742fc0d998a70c6e3992041d1fa62f2fe53f39
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520275"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="0daf1-103">Migrar do ASP.NET Web Forms para o mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="0daf1-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0daf1-104">A migração de uma base de código do ASP.NET Web Forms para o mais alto é uma tarefa demorada que requer planejamento.</span><span class="sxs-lookup"><span data-stu-id="0daf1-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="0daf1-105">Este capítulo descreve o processo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-105">This chapter outlines the process.</span></span> <span data-ttu-id="0daf1-106">Algo que pode facilitar a transição é garantir que o aplicativo obedeça a uma arquitetura de *N camadas* , na qual o modelo de aplicativo (nesse caso, Web Forms) é separado da lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="0daf1-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="0daf1-107">Essa separação lógica de camadas torna claro o que precisa mudar para o .NET Core e o mais simples.</span><span class="sxs-lookup"><span data-stu-id="0daf1-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="0daf1-108">Para este exemplo, o aplicativo eShop disponível no [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) é usado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="0daf1-109">eShop é um serviço de catálogo que fornece recursos CRUD por meio de entrada e validação de formulário.</span><span class="sxs-lookup"><span data-stu-id="0daf1-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="0daf1-110">Por que um aplicativo de trabalho deve ser migrado para um mais incrivelmente?</span><span class="sxs-lookup"><span data-stu-id="0daf1-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="0daf1-111">Muitas vezes, não há necessidade.</span><span class="sxs-lookup"><span data-stu-id="0daf1-111">Many times, there's no need.</span></span> <span data-ttu-id="0daf1-112">O ASP.NET Web Forms continuará a ter suporte por muitos anos.</span><span class="sxs-lookup"><span data-stu-id="0daf1-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="0daf1-113">No entanto, muitos dos recursos que o mais incrivelmente oferece têm suporte apenas em um aplicativo migrado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="0daf1-114">Esses recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="0daf1-114">Such features include:</span></span>

- <span data-ttu-id="0daf1-115">Melhorias de desempenho na estrutura, como `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="0daf1-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="0daf1-116">Capacidade de executar como Webassembly</span><span class="sxs-lookup"><span data-stu-id="0daf1-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="0daf1-117">Suporte de plataforma cruzada para Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="0daf1-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="0daf1-118">Implantação de aplicativo-local ou implantação de estrutura compartilhada sem afetar outros aplicativos</span><span class="sxs-lookup"><span data-stu-id="0daf1-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="0daf1-119">Se esses ou outros novos recursos forem atraentes o suficiente, pode haver um valor na migração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="0daf1-120">A migração pode ter formas diferentes; pode ser o aplicativo inteiro ou apenas determinados pontos de extremidade que exigem as alterações.</span><span class="sxs-lookup"><span data-stu-id="0daf1-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="0daf1-121">A decisão de migrar é, por fim, baseada nos problemas de negócios a serem resolvidos pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="0daf1-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="0daf1-122">Hospedagem do lado do servidor em comparação com o lado do cliente</span><span class="sxs-lookup"><span data-stu-id="0daf1-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="0daf1-123">Conforme descrito no capítulo [modelos de hospedagem](hosting-models.md) , um aplicativo mais incrivelmente pode ser hospedado de duas maneiras diferentes: lado do servidor e do cliente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="0daf1-124">O modelo do lado do servidor usa ASP.NET Core conexões de sinalização para gerenciar as atualizações do DOM durante a execução de qualquer código real no servidor.</span><span class="sxs-lookup"><span data-stu-id="0daf1-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="0daf1-125">O modelo do lado do cliente é executado como Webassembly em um navegador e não requer conexões de servidor.</span><span class="sxs-lookup"><span data-stu-id="0daf1-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="0daf1-126">Há várias diferenças que podem afetar o que é melhor para um aplicativo específico:</span><span class="sxs-lookup"><span data-stu-id="0daf1-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="0daf1-127">A execução como Webassembly ainda está em desenvolvimento e pode não dar suporte a todos os recursos (como Threading) no momento atual</span><span class="sxs-lookup"><span data-stu-id="0daf1-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="0daf1-128">A comunicação informal entre o cliente e o servidor pode causar problemas de latência no modo do servidor</span><span class="sxs-lookup"><span data-stu-id="0daf1-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="0daf1-129">O acesso a bancos de dados e serviços internos ou protegidos requer um serviço separado com hospedagem do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="0daf1-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="0daf1-130">No momento da elaboração do artigo, o modelo do lado do servidor se assemelha mais à Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0daf1-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="0daf1-131">A maior parte deste capítulo se concentra no modelo de hospedagem do lado do servidor, pois ele está pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="0daf1-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="0daf1-132">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="0daf1-132">Create a new project</span></span>

<span data-ttu-id="0daf1-133">Essa etapa inicial de migração é criar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="0daf1-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="0daf1-134">Esse tipo de projeto se baseia nos projetos de estilo do SDK do .NET Core e simplifica grande parte do timbre que foi usado em formatos de projeto anteriores.</span><span class="sxs-lookup"><span data-stu-id="0daf1-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="0daf1-135">Para obter mais detalhes, consulte o capítulo sobre [estrutura do projeto](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="0daf1-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="0daf1-136">Depois que o projeto tiver sido criado, instale as bibliotecas que foram usadas no projeto anterior.</span><span class="sxs-lookup"><span data-stu-id="0daf1-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="0daf1-137">Em projetos de Web Forms mais antigos, você pode ter usado o arquivo *Packages. config* para listar os pacotes NuGet necessários.</span><span class="sxs-lookup"><span data-stu-id="0daf1-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="0daf1-138">No novo projeto no estilo SDK, *Packages. config* foi substituído por `<PackageReference>` elementos no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0daf1-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="0daf1-139">Um benefício para essa abordagem é que todas as dependências são instaladas de maneira transitiva.</span><span class="sxs-lookup"><span data-stu-id="0daf1-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="0daf1-140">Você só lista as dependências de nível superior que se preocupam.</span><span class="sxs-lookup"><span data-stu-id="0daf1-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="0daf1-141">Muitas das dependências que você está usando estão disponíveis para o .NET Core, incluindo Entity Framework 6 e log4net.</span><span class="sxs-lookup"><span data-stu-id="0daf1-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="0daf1-142">Se não houver nenhuma versão do .NET Core ou do .NET Standard disponível, a versão .NET Framework poderá ser usada com frequência.</span><span class="sxs-lookup"><span data-stu-id="0daf1-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="0daf1-143">Sua quilometragem pode variar.</span><span class="sxs-lookup"><span data-stu-id="0daf1-143">Your mileage may vary.</span></span> <span data-ttu-id="0daf1-144">Qualquer API usada que não esteja disponível no .NET Core causa um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0daf1-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="0daf1-145">O Visual Studio o notifica sobre esses pacotes.</span><span class="sxs-lookup"><span data-stu-id="0daf1-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="0daf1-146">Um ícone amarelo aparece no nó **referências** do projeto no **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="0daf1-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="0daf1-147">No projeto eShop baseado em mais Altova, você pode ver os pacotes que estão instalados.</span><span class="sxs-lookup"><span data-stu-id="0daf1-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="0daf1-148">Anteriormente, o arquivo *Packages. config* listou cada pacote usado no projeto, resultando em um arquivo com quase 50 linhas de comprimento.</span><span class="sxs-lookup"><span data-stu-id="0daf1-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="0daf1-149">Um trecho de *Packages. config* é:</span><span class="sxs-lookup"><span data-stu-id="0daf1-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="0daf1-150">O elemento `<packages>` inclui todas as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="0daf1-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="0daf1-151">É difícil identificar quais desses pacotes são incluídos porque você precisa deles.</span><span class="sxs-lookup"><span data-stu-id="0daf1-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="0daf1-152">Alguns elementos `<package>` são listados simplesmente para atender às necessidades das dependências que você precisa.</span><span class="sxs-lookup"><span data-stu-id="0daf1-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="0daf1-153">O projeto mais incrivelmente lista as dependências que você precisa dentro de um elemento `<ItemGroup>` no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="0daf1-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="0daf1-154">Um pacote NuGet que simplifica a vida de Web Forms desenvolvedores é o [pacote de compatibilidade do Windows](/dotnet/core/porting/windows-compat-pack).</span><span class="sxs-lookup"><span data-stu-id="0daf1-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](/dotnet/core/porting/windows-compat-pack).</span></span> <span data-ttu-id="0daf1-155">Embora o .NET Core seja uma plataforma cruzada, alguns recursos estão disponíveis apenas no Windows.</span><span class="sxs-lookup"><span data-stu-id="0daf1-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="0daf1-156">Os recursos específicos do Windows são disponibilizados pela instalação do Compatibility Pack.</span><span class="sxs-lookup"><span data-stu-id="0daf1-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="0daf1-157">Exemplos de tais recursos incluem o registro, o WMI e os serviços de diretório.</span><span class="sxs-lookup"><span data-stu-id="0daf1-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="0daf1-158">O pacote acrescenta cerca de 20.000 APIs e ativa muitos serviços com os quais você já deve estar familiarizado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="0daf1-159">O projeto eShop não requer o Compatibility Pack; Mas se seus projetos usarem recursos específicos do Windows, o pacote facilitará os esforços de migração.</span><span class="sxs-lookup"><span data-stu-id="0daf1-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="0daf1-160">Habilitar processo de inicialização</span><span class="sxs-lookup"><span data-stu-id="0daf1-160">Enable startup process</span></span>

<span data-ttu-id="0daf1-161">O processo de inicialização para o mais baixo mudou de Web Forms e segue uma configuração semelhante para outros serviços de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="0daf1-162">Quando hospedados no lado do servidor, os componentes mais podestas são executados como parte de um aplicativo ASP.NET Core normal.</span><span class="sxs-lookup"><span data-stu-id="0daf1-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="0daf1-163">Quando hospedado no navegador com Webassembly, os componentes mais poseriais usam um modelo de hospedagem semelhante.</span><span class="sxs-lookup"><span data-stu-id="0daf1-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="0daf1-164">A diferença é que os componentes são executados como um serviço separado de qualquer um dos processos de back-end.</span><span class="sxs-lookup"><span data-stu-id="0daf1-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="0daf1-165">De qualquer forma, a inicialização é semelhante.</span><span class="sxs-lookup"><span data-stu-id="0daf1-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="0daf1-166">O arquivo *global.asax.cs* é a página de inicialização padrão para projetos Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0daf1-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="0daf1-167">No projeto eShop, esse arquivo configura o contêiner inversão de controle (IoC) e manipula os vários eventos de ciclo de vida do aplicativo ou da solicitação.</span><span class="sxs-lookup"><span data-stu-id="0daf1-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="0daf1-168">Alguns desses eventos são tratados com middleware (como `Application_BeginRequest`).</span><span class="sxs-lookup"><span data-stu-id="0daf1-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="0daf1-169">Outros eventos exigem a substituição de serviços específicos por meio de injeção de dependência (DI).</span><span class="sxs-lookup"><span data-stu-id="0daf1-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="0daf1-170">Por exemplo, o arquivo *global.asax.cs* para eshop contém o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0daf1-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="0daf1-171">O arquivo anterior torna-se a classe `Startup` no mais alto nível do servidor:</span><span class="sxs-lookup"><span data-stu-id="0daf1-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="0daf1-172">Uma alteração significativa que você pode observar de Web Forms é a proeminência de DI.</span><span class="sxs-lookup"><span data-stu-id="0daf1-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="0daf1-173">DI foi um princípio de orientação no design de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="0daf1-174">Ele dá suporte à personalização de quase todos os aspectos da estrutura de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="0daf1-175">Há até mesmo um provedor de serviços interno que pode ser usado em muitos cenários.</span><span class="sxs-lookup"><span data-stu-id="0daf1-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="0daf1-176">Se for necessária mais personalização, ela poderá ser suportada pelos vários projetos da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="0daf1-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="0daf1-177">Por exemplo, você pode transportar seu investimento de biblioteca de DI de terceiros.</span><span class="sxs-lookup"><span data-stu-id="0daf1-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="0daf1-178">No aplicativo eShop original, há alguma configuração para o gerenciamento de sessão.</span><span class="sxs-lookup"><span data-stu-id="0daf1-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="0daf1-179">Como um amversor do lado do servidor usa ASP.NET Core Signalr para comunicação, o estado da sessão não é suportado, pois as conexões podem ocorrer independentemente de um contexto HTTP.</span><span class="sxs-lookup"><span data-stu-id="0daf1-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="0daf1-180">Um aplicativo que usa o estado de sessão requer a rearquiteturação antes da execução como um aplicativo mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="0daf1-181">Para obter mais informações sobre a inicialização do aplicativo, consulte [inicialização do aplicativo](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="0daf1-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="0daf1-182">Migrar módulos e manipuladores HTTP para middleware</span><span class="sxs-lookup"><span data-stu-id="0daf1-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="0daf1-183">Os módulos e manipuladores HTTP são padrões comuns em Web Forms para controlar o pipeline de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="0daf1-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="0daf1-184">As classes que implementam `IHttpModule` ou `IHttpHandler` podem ser registradas e processar solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="0daf1-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="0daf1-185">Web Forms configura módulos e manipuladores no arquivo *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="0daf1-186">O Web Forms também é muito baseado na manipulação de eventos do ciclo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="0daf1-187">O ASP.NET Core usa o middleware em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0daf1-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="0daf1-188">Middleware são registrados no método `Configure` da classe `Startup`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-188">Middlewares are registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="0daf1-189">A ordem de execução do middleware é determinada pela ordem de registro.</span><span class="sxs-lookup"><span data-stu-id="0daf1-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="0daf1-190">Na seção [habilitar processo de inicialização](#enable-startup-process) , um evento de ciclo de vida foi gerado por Web Forms como o método `Application_BeginRequest`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="0daf1-191">Esse evento não está disponível no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="0daf1-192">Uma maneira de atingir esse comportamento é implementar o middleware como visto no exemplo de arquivo *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="0daf1-193">Esse middleware faz a mesma lógica e, em seguida, transfere o controle para o próximo manipulador no pipeline de middleware.</span><span class="sxs-lookup"><span data-stu-id="0daf1-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="0daf1-194">Para obter mais informações sobre como migrar módulos e manipuladores, consulte [migrar manipuladores e módulos http para ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="0daf1-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="0daf1-195">Migrar arquivos estáticos</span><span class="sxs-lookup"><span data-stu-id="0daf1-195">Migrate static files</span></span>

<span data-ttu-id="0daf1-196">Para servir arquivos estáticos (por exemplo, HTML, CSS, imagens e JavaScript), os arquivos devem ser expostos por middleware.</span><span class="sxs-lookup"><span data-stu-id="0daf1-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="0daf1-197">Chamar o método `UseStaticFiles` permite o serviço de arquivos estáticos do caminho raiz da Web.</span><span class="sxs-lookup"><span data-stu-id="0daf1-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="0daf1-198">O diretório raiz padrão da Web é *wwwroot*, mas pode ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="0daf1-199">Conforme incluído no método `Configure` da classe `Startup` do eShop:</span><span class="sxs-lookup"><span data-stu-id="0daf1-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="0daf1-200">O projeto eShop habilita o acesso básico a arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0daf1-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="0daf1-201">Há muitas personalizações disponíveis para acesso a arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0daf1-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="0daf1-202">Para obter informações sobre como habilitar arquivos padrão ou um navegador de arquivos, consulte [arquivos estáticos em ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="0daf1-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="0daf1-203">Migrar a configuração de agrupamento e minificação de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0daf1-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="0daf1-204">O agrupamento e o minificação são técnicas de otimização de desempenho para reduzir o número e o tamanho das solicitações de servidor para recuperar determinados tipos de arquivo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="0daf1-205">O JavaScript e o CSS geralmente passam por alguma forma de agrupamento ou minificação antes de serem enviados ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="0daf1-206">No ASP.NET Web Forms, essas otimizações são tratadas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0daf1-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="0daf1-207">As convenções de otimização são definidas como um arquivo *App_Start/BundleConfig. cs* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="0daf1-208">No ASP.NET Core, uma abordagem mais declarativa é adotada.</span><span class="sxs-lookup"><span data-stu-id="0daf1-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="0daf1-209">Um arquivo lista os arquivos a serem reduzidosdos, juntamente com configurações específicas de minificação.</span><span class="sxs-lookup"><span data-stu-id="0daf1-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="0daf1-210">Para obter mais informações sobre agrupamento e minificação, consulte [ativos estáticos de pacote e reduzir em ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="0daf1-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="0daf1-211">Migrar páginas ASPX</span><span class="sxs-lookup"><span data-stu-id="0daf1-211">Migrate ASPX pages</span></span>

<span data-ttu-id="0daf1-212">Uma página em um aplicativo Web Forms é um arquivo com a extensão *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="0daf1-213">Uma página de Web Forms geralmente pode ser mapeada para um componente do mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="0daf1-214">Um componente mais incrivelmente é criado em um arquivo com a extensão *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="0daf1-215">Para o projeto eShop, cinco páginas são convertidas em uma página Razor.</span><span class="sxs-lookup"><span data-stu-id="0daf1-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="0daf1-216">Por exemplo, a exibição de detalhes é composta de três arquivos no projeto Web Forms: *Details. aspx*, *Details.aspx.cs*e *Details.aspx.designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="0daf1-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="0daf1-217">Ao converter para mais incrivelmente, o code-behind e a marcação são combinados em *Details. Razor*.</span><span class="sxs-lookup"><span data-stu-id="0daf1-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="0daf1-218">A compilação do Razor (equivalente ao que está nos arquivos *. designer.cs* ) é armazenada no diretório *obj* e não é, por padrão, visível no **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="0daf1-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="0daf1-219">A página Web Forms consiste na seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="0daf1-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="0daf1-220">O code-behind da marcação anterior inclui o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0daf1-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="0daf1-221">Quando convertido para um mais recente, a página Web Forms se traduz no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0daf1-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="0daf1-222">Observe que o código e a marcação estão no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="0daf1-223">Todos os serviços necessários são tornados acessíveis com o atributo `@inject`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="0daf1-224">De acordo com a diretiva de `@page`, essa página pode ser acessada na rota `Catalog/Details/{id}`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="0daf1-225">O valor do espaço reservado de `{id}` da rota foi restrito a um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="0daf1-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="0daf1-226">Conforme descrito na seção de [Roteamento](pages-routing-layouts.md) , ao contrário de Web Forms, um componente Razor declara explicitamente sua rota e quaisquer parâmetros que estejam incluídos.</span><span class="sxs-lookup"><span data-stu-id="0daf1-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="0daf1-227">Muitos controles de Web Forms podem não ter equivalentes exatos no mais grande número.</span><span class="sxs-lookup"><span data-stu-id="0daf1-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="0daf1-228">Geralmente, há um trecho HTML equivalente que terá a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="0daf1-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="0daf1-229">Por exemplo, o controle de `<asp:Label />` pode ser substituído por um elemento de `<label>` HTML.</span><span class="sxs-lookup"><span data-stu-id="0daf1-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="0daf1-230">Validação de modelo no mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="0daf1-230">Model validation in Blazor</span></span>

<span data-ttu-id="0daf1-231">Se seu código de Web Forms inclui validação, você pode transferir grande parte do que tem com pouca ou nenhuma alteração.</span><span class="sxs-lookup"><span data-stu-id="0daf1-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="0daf1-232">Um benefício da execução do mais incrivelmente é que a mesma lógica de validação pode ser executada sem a necessidade de JavaScript personalizado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="0daf1-233">As anotações de dados permitem uma validação fácil de modelo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="0daf1-234">Por exemplo, a página *Create. aspx* tem um formulário de entrada de dados com validação.</span><span class="sxs-lookup"><span data-stu-id="0daf1-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="0daf1-235">Um trecho de código de exemplo ficaria assim:</span><span class="sxs-lookup"><span data-stu-id="0daf1-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="0daf1-236">No mais ou mais, a marcação equivalente é fornecida em um arquivo *Create. Razor* :</span><span class="sxs-lookup"><span data-stu-id="0daf1-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>
    
    ...
</EditForm>
```

<span data-ttu-id="0daf1-237">O contexto de `EditForm` inclui suporte à validação e pode ser disposto em torno da entrada.</span><span class="sxs-lookup"><span data-stu-id="0daf1-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="0daf1-238">As anotações de dados são uma maneira comum de adicionar validação.</span><span class="sxs-lookup"><span data-stu-id="0daf1-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="0daf1-239">Esse suporte à validação pode ser adicionado por meio do componente `DataAnnotationsValidator`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="0daf1-240">Para obter mais informações sobre esse mecanismo, consulte [ASP.NET Core formulários e validação de](/aspnet/core/blazor/forms-validation)mais mais.</span><span class="sxs-lookup"><span data-stu-id="0daf1-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="0daf1-241">Migrar controles de Web Forms internos</span><span class="sxs-lookup"><span data-stu-id="0daf1-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="0daf1-242">*Esse conteúdo será disponibilizado em breve.*</span><span class="sxs-lookup"><span data-stu-id="0daf1-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="0daf1-243">Migrar configuração</span><span class="sxs-lookup"><span data-stu-id="0daf1-243">Migrate configuration</span></span>

<span data-ttu-id="0daf1-244">Em um projeto Web Forms, os dados de configuração são mais comumente armazenados no arquivo *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="0daf1-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="0daf1-245">Os dados de configuração são acessados com `ConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="0daf1-246">Normalmente, os serviços eram necessários para analisar objetos.</span><span class="sxs-lookup"><span data-stu-id="0daf1-246">Services were often required to parse objects.</span></span> <span data-ttu-id="0daf1-247">Com o .NET Framework 4.7.2, a capacidade de composição foi adicionada à configuração via `ConfigurationBuilders`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="0daf1-248">Esses construtores permitiam que os desenvolvedores adicionassem várias fontes de configuração que, em seguida, eram compostas em tempo de execução para recuperar os valores necessários.</span><span class="sxs-lookup"><span data-stu-id="0daf1-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="0daf1-249">ASP.NET Core introduziu um sistema de configuração flexível que permite que você defina a fonte de configuração ou as fontes usadas pelo seu aplicativo e sua implantação.</span><span class="sxs-lookup"><span data-stu-id="0daf1-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="0daf1-250">A infraestrutura de `ConfigurationBuilder` que você pode estar usando em seu aplicativo Web Forms foi modelada após os conceitos usados no sistema de configuração ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="0daf1-251">O trecho a seguir demonstra como o projeto Web Forms eShop usa o *Web. config* para armazenar valores de configuração:</span><span class="sxs-lookup"><span data-stu-id="0daf1-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
```

<span data-ttu-id="0daf1-252">É comum que segredos, como cadeias de conexão de banco de dados, sejam armazenados no *Web. config*. Os segredos são inevitavelmente persistentes em locais não seguros, como o controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0daf1-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="0daf1-253">Com o mais alto ASP.NET Core, a configuração baseada em XML anterior é substituída pelo JSON a seguir:</span><span class="sxs-lookup"><span data-stu-id="0daf1-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="0daf1-254">JSON é o formato de configuração padrão; no entanto, o ASP.NET Core dá suporte a muitos outros formatos, incluindo XML.</span><span class="sxs-lookup"><span data-stu-id="0daf1-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="0daf1-255">Também há vários formatos com suporte da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="0daf1-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="0daf1-256">O Construtor na classe de `Startup` do projeto mais incrivelmente aceita uma instância de `IConfiguration` por meio de uma técnica de DI, conhecida como injeção de construtor:</span><span class="sxs-lookup"><span data-stu-id="0daf1-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="0daf1-257">Por padrão, variáveis de ambiente, arquivos JSON (*appSettings. JSON* e *appSettings. { Environment}. JSON*) e as opções de linha de comando são registradas como fontes de configuração válidas no objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="0daf1-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="0daf1-258">As fontes de configuração podem ser acessadas por meio de `Configuration[key]`.</span><span class="sxs-lookup"><span data-stu-id="0daf1-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="0daf1-259">Uma técnica mais avançada é associar os dados de configuração a objetos usando o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="0daf1-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="0daf1-260">Para obter mais informações sobre configuração e o padrão de opções, consulte [configuração no](/aspnet/core/fundamentals/configuration/) padrão de ASP.NET Core e [opções em ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="0daf1-261">Migrar acesso a dados</span><span class="sxs-lookup"><span data-stu-id="0daf1-261">Migrate data access</span></span>

<span data-ttu-id="0daf1-262">O acesso a dados é um aspecto importante de qualquer aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="0daf1-263">O projeto eShop armazena as informações de catálogo em um banco de dados e recupera os dados com Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="0daf1-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="0daf1-264">Como o EF 6 tem suporte no .NET Core 3,0, o projeto pode continuar a usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0daf1-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="0daf1-265">As seguintes alterações relacionadas ao EF foram necessárias para eShop:</span><span class="sxs-lookup"><span data-stu-id="0daf1-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="0daf1-266">Em .NET Framework, o objeto `DbContext` aceita uma cadeia de caracteres do formato *Name = ConnectionString* e usa a cadeia de conexão de `ConfigurationManager.AppSettings[ConnectionString]` para se conectar.</span><span class="sxs-lookup"><span data-stu-id="0daf1-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="0daf1-267">No .NET Core, não há suporte para isso.</span><span class="sxs-lookup"><span data-stu-id="0daf1-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="0daf1-268">A cadeia de conexão deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="0daf1-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="0daf1-269">O banco de dados foi acessado de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="0daf1-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="0daf1-270">Embora isso funcione, a escalabilidade pode ser afetada.</span><span class="sxs-lookup"><span data-stu-id="0daf1-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="0daf1-271">Essa lógica deve ser movida para um padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0daf1-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="0daf1-272">Embora não haja o mesmo suporte nativo para associação de conjunto de recursos, o mais incrivelmente fornece flexibilidade C# e potência com seu suporte em uma página Razor.</span><span class="sxs-lookup"><span data-stu-id="0daf1-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="0daf1-273">Por exemplo, você pode executar cálculos e exibir o resultado.</span><span class="sxs-lookup"><span data-stu-id="0daf1-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="0daf1-274">Para obter mais informações sobre padrões de dados no mais ou mais, consulte o capítulo de [acesso a dados](data.md) .</span><span class="sxs-lookup"><span data-stu-id="0daf1-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="0daf1-275">Alterações de arquitetura</span><span class="sxs-lookup"><span data-stu-id="0daf1-275">Architectural changes</span></span>

<span data-ttu-id="0daf1-276">Por fim, há algumas diferenças de arquitetura importantes a serem consideradas ao migrar para o mais robusto.</span><span class="sxs-lookup"><span data-stu-id="0daf1-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="0daf1-277">Muitas dessas alterações são aplicáveis a qualquer coisa com base no .NET Core ou ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="0daf1-278">Como o mais elaborado é baseado no .NET Core, há considerações sobre a garantia de suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0daf1-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="0daf1-279">Algumas das principais alterações incluem a remoção dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="0daf1-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="0daf1-280">Vários AppDomains</span><span class="sxs-lookup"><span data-stu-id="0daf1-280">Multiple AppDomains</span></span>
- <span data-ttu-id="0daf1-281">Comunicação Remota</span><span class="sxs-lookup"><span data-stu-id="0daf1-281">Remoting</span></span>
- <span data-ttu-id="0daf1-282">CAS (Segurança de Acesso do Código)</span><span class="sxs-lookup"><span data-stu-id="0daf1-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="0daf1-283">Transparência de Segurança</span><span class="sxs-lookup"><span data-stu-id="0daf1-283">Security Transparency</span></span>

<span data-ttu-id="0daf1-284">Para obter mais informações sobre técnicas para identificar as alterações necessárias para dar suporte à execução no .NET Core, consulte [portar seu código do .NET Framework para o .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="0daf1-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="0daf1-285">ASP.NET Core é uma versão reimaginada do ASP.NET e tem algumas alterações que podem não parecer óbvias inicialmente.</span><span class="sxs-lookup"><span data-stu-id="0daf1-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="0daf1-286">As principais alterações são:</span><span class="sxs-lookup"><span data-stu-id="0daf1-286">The main changes are:</span></span>

- <span data-ttu-id="0daf1-287">Nenhum contexto de sincronização, o que significa que não há `HttpContext.Current`, `Thread.CurrentPrincipal` ou outros acessadores estáticos</span><span class="sxs-lookup"><span data-stu-id="0daf1-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="0daf1-288">Sem cópia de sombra</span><span class="sxs-lookup"><span data-stu-id="0daf1-288">No shadow copying</span></span>
- <span data-ttu-id="0daf1-289">Nenhuma fila de solicitações</span><span class="sxs-lookup"><span data-stu-id="0daf1-289">No request queue</span></span>

<span data-ttu-id="0daf1-290">Muitas operações no ASP.NET Core são assíncronas, o que permite o descarregamento mais fácil de tarefas vinculadas a e/s.</span><span class="sxs-lookup"><span data-stu-id="0daf1-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="0daf1-291">É importante nunca Bloquear usando `Task.Wait()` ou `Task.GetResult()`, o que pode esgotar rapidamente os recursos do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="0daf1-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="0daf1-292">Conclusão da migração</span><span class="sxs-lookup"><span data-stu-id="0daf1-292">Migration conclusion</span></span>

<span data-ttu-id="0daf1-293">Neste ponto, você viu muitos exemplos do que é necessário para mover um projeto Web Forms para um grande número.</span><span class="sxs-lookup"><span data-stu-id="0daf1-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="0daf1-294">Para obter um exemplo completo, consulte o projeto [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="0daf1-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="0daf1-295">Anterior</span><span class="sxs-lookup"><span data-stu-id="0daf1-295">Previous</span></span>](security-authentication-authorization.md)
