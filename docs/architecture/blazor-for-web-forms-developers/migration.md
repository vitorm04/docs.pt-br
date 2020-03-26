---
title: Migrar de ASP.NET Formulários web para Blazor
description: Aprenda a abordar a migração de um aplicativo de Formulários web ASP.NET existente para Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134084"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="6cfe5-103">Migrar de ASP.NET Formulários web para Blazor</span><span class="sxs-lookup"><span data-stu-id="6cfe5-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6cfe5-104">Migrar uma base de código de ASP.NET Formulários web para Blazor é uma tarefa demorada que requer planejamento.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="6cfe5-105">Este capítulo descreve o processo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-105">This chapter outlines the process.</span></span> <span data-ttu-id="6cfe5-106">Algo que pode facilitar a transição é garantir que o aplicativo adere a uma arquitetura *n-tier,* onde o modelo de aplicativo (neste caso, Web Forms) é separado da lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="6cfe5-107">Esta separação lógica de camadas deixa claro o que precisa passar para .NET Core e Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="6cfe5-108">Para este exemplo, o aplicativo eShop disponível no [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) é usado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="6cfe5-109">O eShop é um serviço de catálogo que fornece recursos CRUD via entrada e validação de formulários.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="6cfe5-110">Por que um aplicativo de trabalho deve ser migrado para Blazor?</span><span class="sxs-lookup"><span data-stu-id="6cfe5-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="6cfe5-111">Muitas vezes, não há necessidade.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-111">Many times, there's no need.</span></span> <span data-ttu-id="6cfe5-112">ASP.NET Web Forms continuarão a ser suportados por muitos anos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="6cfe5-113">No entanto, muitos dos recursos que o Blazor fornece são suportados apenas em um aplicativo migrado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="6cfe5-114">Tais características incluem:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-114">Such features include:</span></span>

- <span data-ttu-id="6cfe5-115">Melhorias de desempenho no quadro, como`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="6cfe5-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="6cfe5-116">Capacidade de executar como WebAssembly</span><span class="sxs-lookup"><span data-stu-id="6cfe5-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="6cfe5-117">Suporte multiplataforma para Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="6cfe5-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="6cfe5-118">Implantação local de aplicativos ou implantação de framework compartilhado sem afetar outros aplicativos</span><span class="sxs-lookup"><span data-stu-id="6cfe5-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="6cfe5-119">Se esses ou outros novos recursos forem convincentes o suficiente, pode haver valor na migração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="6cfe5-120">A migração pode tomar diferentes formas; pode ser o aplicativo inteiro, ou apenas certos pontos finais que requerem as alterações.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="6cfe5-121">A decisão de migrar é baseada, em última instância, nos problemas de negócios a serem resolvidos pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="6cfe5-122">Lado do servidor versus hospedagem do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="6cfe5-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="6cfe5-123">Como descrito no capítulo [modelos de hospedagem,](hosting-models.md) um aplicativo Blazor pode ser hospedado de duas maneiras diferentes: lado do servidor e lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="6cfe5-124">O modelo do lado do servidor usa ASP.NET conexões Core SignalR para gerenciar as atualizações do DOM enquanto executa qualquer código real no servidor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="6cfe5-125">O modelo do lado do cliente é executado como WebAssembly dentro de um navegador e não requer conexões de servidor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="6cfe5-126">Há uma série de diferenças que podem afetar o que é melhor para um aplicativo específico:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="6cfe5-127">Executando como WebAssembly ainda está em desenvolvimento e pode não suportar todos os recursos (como threading) no momento atual</span><span class="sxs-lookup"><span data-stu-id="6cfe5-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="6cfe5-128">A comunicação conversada entre o cliente e o servidor pode causar problemas de latência no modo lado do servidor</span><span class="sxs-lookup"><span data-stu-id="6cfe5-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="6cfe5-129">O acesso a bancos de dados e serviços internos ou protegidos exigem um serviço separado com hospedagem do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="6cfe5-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="6cfe5-130">No momento da escrita, o modelo do lado do servidor se assemelha mais aos Formulários da Web.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="6cfe5-131">A maior parte deste capítulo se concentra no modelo de hospedagem do lado do servidor, já que está pronto para a produção.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="6cfe5-132">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="6cfe5-132">Create a new project</span></span>

<span data-ttu-id="6cfe5-133">Este passo inicial de migração é criar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="6cfe5-134">Este tipo de projeto é baseado nos projetos de estilo SDK do .NET Core e simplifica grande parte da caldeira que foi usada em formatos de projeto anteriores.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="6cfe5-135">Para obter mais detalhes, consulte o capítulo sobre [estrutura do projeto.](project-structure.md)</span><span class="sxs-lookup"><span data-stu-id="6cfe5-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="6cfe5-136">Uma vez criado o projeto, instale as bibliotecas que foram utilizadas no projeto anterior.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="6cfe5-137">Em projetos mais antigos da Web Forms, você pode ter usado o arquivo *packages.config* para listar os pacotes NuGet necessários.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="6cfe5-138">No novo projeto no estilo SDK, *o packages.config* foi substituído por `<PackageReference>` elementos no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="6cfe5-139">Um benefício dessa abordagem é que todas as dependências são instaladas transitivamente.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="6cfe5-140">Você só lista as dependências de alto nível que você se importa.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="6cfe5-141">Muitas das dependências que você está usando estão disponíveis para .NET Core, incluindo Entity Framework 6 e log4net.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="6cfe5-142">Se não houver nenhuma versão .NET Core ou .NET Standard disponível, a versão .NET Framework pode ser usada muitas vezes.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="6cfe5-143">Sua quilometragem pode variar.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-143">Your mileage may vary.</span></span> <span data-ttu-id="6cfe5-144">Qualquer API usada que não esteja disponível no .NET Core causa um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="6cfe5-145">Visual Studio notifica você de tais pacotes.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="6cfe5-146">Um ícone amarelo aparece no nó **Referências** do projeto no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="6cfe5-147">No projeto eShop baseado em Blazor, você pode ver os pacotes que estão instalados.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="6cfe5-148">Anteriormente, o arquivo *packages.config* listava todos os pacotes usados no projeto, resultando em um arquivo de quase 50 linhas de comprimento.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="6cfe5-149">Um trecho de *pacotes.config* é:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="6cfe5-150">O `<packages>` elemento inclui todas as dependências necessárias.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="6cfe5-151">É difícil identificar quais desses pacotes estão incluídos porque você os precisa.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="6cfe5-152">Alguns `<package>` elementos são listados simplesmente para satisfazer as necessidades de dependências que você precisa.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="6cfe5-153">O projeto Blazor lista as dependências que você precisa dentro de um `<ItemGroup>` elemento no arquivo do projeto:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="6cfe5-154">Um pacote NuGet que simplifica a vida dos desenvolvedores do Web Forms é o [Pacote de Compatibilidade do Windows](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="6cfe5-155">Embora o .NET Core seja multiplataforma, alguns recursos só estão disponíveis no Windows.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="6cfe5-156">Recursos específicos do Windows são disponibilizados instalando o pacote de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="6cfe5-157">Exemplos desses recursos incluem os Serviços de Registro, WMI e Diretório.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="6cfe5-158">O pacote adiciona cerca de 20.000 APIs e ativa muitos serviços com os quais você pode já estar familiarizado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="6cfe5-159">O projeto eShop não requer o pacote de compatibilidade; mas se seus projetos usarem recursos específicos do Windows, o pacote facilitará os esforços de migração.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="6cfe5-160">Habilitar o processo de inicialização</span><span class="sxs-lookup"><span data-stu-id="6cfe5-160">Enable startup process</span></span>

<span data-ttu-id="6cfe5-161">O processo de inicialização do Blazor mudou de Web Forms e segue uma configuração semelhante para outros serviços ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="6cfe5-162">Quando hospedados do lado do servidor, os componentes Blazor são executados como parte de um aplicativo normal do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="6cfe5-163">Quando hospedados no navegador com webAssembly, os componentes Blazor usam um modelo de hospedagem semelhante.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="6cfe5-164">A diferença é que os componentes são executados como um serviço separado de qualquer um dos processos back-end.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="6cfe5-165">De qualquer forma, a startup é semelhante.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="6cfe5-166">O arquivo *Global.asax.cs* é a página de inicialização padrão para projetos do Web Forms.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="6cfe5-167">No projeto eShop, este arquivo configura o contêiner Inversão de Controle (IoC) e lida com os vários eventos do ciclo de vida do aplicativo ou solicitação.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="6cfe5-168">Alguns desses eventos são tratados com `Application_BeginRequest`middleware (como ).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="6cfe5-169">Outros eventos requerem a substituição de serviços específicos via injeção de dependência (DI).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="6cfe5-170">A propósito, o *arquivo Global.asax.cs* para eShop, contém o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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

<span data-ttu-id="6cfe5-171">O arquivo anterior `Startup` torna-se a classe no lado do servidor Blazor:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="6cfe5-172">Uma mudança significativa que você pode notar a partir de Formulários web é a proeminência do DI.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="6cfe5-173">Di tem sido um princípio norteador no design do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="6cfe5-174">Ele suporta a personalização de quase todos os aspectos da estrutura do Núcleo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="6cfe5-175">Há até um provedor de serviços embutido que pode ser usado para muitos cenários.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="6cfe5-176">Se mais personalização for necessária, ela pode ser apoiada pelos muitos projetos comunitários.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="6cfe5-177">Por exemplo, você pode levar adiante o investimento na biblioteca DI de terceiros.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="6cfe5-178">No aplicativo original da eShop, há alguma configuração para gerenciamento de sessões.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="6cfe5-179">Uma vez que o Blazor do lado do servidor usa ASP.NET Core SignalR para comunicação, o estado de sessão não é suportado, pois as conexões podem ocorrer independentemente de um contexto HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="6cfe5-180">Um aplicativo que usa o estado de sessão requer rearquiteantes antes de ser executado como um aplicativo Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="6cfe5-181">Para obter mais informações sobre a inicialização do aplicativo, consulte [a inicialização do aplicativo](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="6cfe5-182">Migrar módulos HTTP e manipuladores para middleware</span><span class="sxs-lookup"><span data-stu-id="6cfe5-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="6cfe5-183">Módulos HTTP e manipuladores são padrões comuns em Formulários da Web para controlar o pipeline de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="6cfe5-184">Classes que `IHttpModule` `IHttpHandler` implementam ou podem ser registradas e processam solicitações recebidas.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="6cfe5-185">O Web Forms configura módulos e manipuladores no arquivo *Web.config.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="6cfe5-186">O Web Forms também é fortemente baseado no manuseio de eventos do ciclo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="6cfe5-187">ASP.NET Core usa middleware em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="6cfe5-188">Middleware é registrado `Configure` no método `Startup` da classe.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="6cfe5-189">A ordem de execução do middleware é determinada pela ordem de registro.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="6cfe5-190">Na seção [Habilitar processo de inicialização,](#enable-startup-process) um evento `Application_BeginRequest` do ciclo de vida foi levantado pela Web Forms como método.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="6cfe5-191">Este evento não está disponível em ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="6cfe5-192">Uma maneira de alcançar esse comportamento é implementar middleware, como visto no exemplo de arquivo *Startup.cs.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="6cfe5-193">Este middleware faz a mesma lógica e, em seguida, transfere o controle para o próximo manipulador no pipeline de middleware.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="6cfe5-194">Para obter mais informações sobre módulos e manipuladores migratórios, consulte [Migrar manipuladores http e módulos para ASP.NET middleware Core](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="6cfe5-195">Migrar arquivos estáticos</span><span class="sxs-lookup"><span data-stu-id="6cfe5-195">Migrate static files</span></span>

<span data-ttu-id="6cfe5-196">Para servir arquivos estáticos (por exemplo, HTML, CSS, imagens e JavaScript), os arquivos devem ser expostos por middleware.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="6cfe5-197">A `UseStaticFiles` chamada do método permite a saque de arquivos estáticos do caminho raiz da Web.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="6cfe5-198">O diretório raiz da Web padrão é *wwwroot,* mas pode ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="6cfe5-199">Como incluído `Configure` no método de `Startup` classe do eShop:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="6cfe5-200">O projeto eShop permite o acesso básico de arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="6cfe5-201">Existem muitas personalizações disponíveis para acesso a arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="6cfe5-202">Para obter informações sobre como ativar arquivos padrão ou um navegador de arquivos, consulte [arquivos estáticos no ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="6cfe5-203">Migrar agrupamento em tempo de execução e configuração de minificação</span><span class="sxs-lookup"><span data-stu-id="6cfe5-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="6cfe5-204">Agrupamento e minificação são técnicas de otimização de desempenho para reduzir o número e o tamanho das solicitações de servidor para recuperar certos tipos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="6cfe5-205">JavaScript e CSS geralmente passam por algum tipo de agrupamento ou minificação antes de serem enviados ao cliente.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="6cfe5-206">Em ASP.NET Formulários da Web, essas otimizações são tratadas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="6cfe5-207">As convenções de otimização são definidas como um arquivo *App_Start/BundleConfig.cs.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="6cfe5-208">Em ASP.NET Núcleo, adota-se uma abordagem mais declarativa.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="6cfe5-209">Um arquivo lista os arquivos a serem minified, juntamente com configurações específicas de minificação.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="6cfe5-210">Para obter mais informações sobre agrupamento e minificação, consulte [Bundle e minify ativos estáticos em ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="6cfe5-211">Migrar páginas ASPX</span><span class="sxs-lookup"><span data-stu-id="6cfe5-211">Migrate ASPX pages</span></span>

<span data-ttu-id="6cfe5-212">Uma página em um aplicativo Web Forms é um arquivo com a extensão *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="6cfe5-213">Uma página formulários da Web pode muitas vezes ser mapeada para um componente em Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="6cfe5-214">Um componente Blazor é de autoria de um arquivo com a extensão *.razor.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="6cfe5-215">Para o projeto eShop, cinco páginas são convertidas em uma página de Navalha.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="6cfe5-216">Por exemplo, a visualização de detalhes é composta por três arquivos no projeto Formulários da Web: *Details.aspx,* *Details.aspx.cs*e *Details.aspx.designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="6cfe5-217">Ao converter para Blazor, o code-behind e a marcação são combinados em *Details.razor*.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="6cfe5-218">A compilação razor (equivalente ao que está em *arquivos de .designer.cs)* é armazenada no diretório *obj* e não são, por padrão, visível no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="6cfe5-219">A página Formulários da Web consiste na seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="6cfe5-220">O código de configuração anterior inclui o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="6cfe5-221">Quando convertida em Blazor, a página Formulários da Web se traduz para o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="6cfe5-222">Observe que o código e a marcação estão no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="6cfe5-223">Todos os serviços necessários são acessíveis com o atributo. `@inject`</span><span class="sxs-lookup"><span data-stu-id="6cfe5-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="6cfe5-224">De `@page` acordo com a diretiva, esta `Catalog/Details/{id}` página pode ser acessada na rota.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="6cfe5-225">O valor do espaço `{id}` reservado da rota foi constrangido a um inteiro.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="6cfe5-226">Como descrito na seção [de roteamento,](pages-routing-layouts.md) ao contrário do Web Forms, um componente Razor declara explicitamente sua rota e quaisquer parâmetros incluídos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="6cfe5-227">Muitos controles web forms podem não ter contrapartes exatas em Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="6cfe5-228">Muitas vezes há um trecho HTML equivalente que servirá ao mesmo propósito.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="6cfe5-229">Por exemplo, `<asp:Label />` o controle pode ser `<label>` substituído por um elemento HTML.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="6cfe5-230">Validação de modelo em Blazor</span><span class="sxs-lookup"><span data-stu-id="6cfe5-230">Model validation in Blazor</span></span>

<span data-ttu-id="6cfe5-231">Se o código web forms incluir validação, você pode transferir muito do que você tem com poucaou para não alterações.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="6cfe5-232">Um benefício para ser executado em Blazor é que a mesma lógica de validação pode ser executada sem precisar de JavaScript personalizado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="6cfe5-233">As anotações de dados permitem uma validação fácil do modelo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="6cfe5-234">Por exemplo, a página *Create.aspx* tem um formulário de entrada de dados com validação.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="6cfe5-235">Um trecho de exemplo seria assim:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="6cfe5-236">Em Blazor, a marcação equivalente é fornecida em um arquivo *Create.razor:*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="6cfe5-237">O `EditForm` contexto inclui suporte de validação e pode ser enrolado em torno da entrada.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="6cfe5-238">Anotações de dados são uma maneira comum de adicionar validação.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="6cfe5-239">Esse suporte de validação `DataAnnotationsValidator` pode ser adicionado através do componente.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="6cfe5-240">Para obter mais informações sobre este mecanismo, consulte [ASP.NET formulários e validação do Core Blazor](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="6cfe5-241">Migrar controles de Formulários web incorporados</span><span class="sxs-lookup"><span data-stu-id="6cfe5-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="6cfe5-242">*Este conteúdo está chegando.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="6cfe5-243">Migrar configuração</span><span class="sxs-lookup"><span data-stu-id="6cfe5-243">Migrate configuration</span></span>

<span data-ttu-id="6cfe5-244">Em um projeto Web Forms, os dados de configuração são armazenados mais comumente no arquivo *Web.config.*</span><span class="sxs-lookup"><span data-stu-id="6cfe5-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="6cfe5-245">Os dados de configuração são acessados com `ConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="6cfe5-246">Os serviços eram frequentemente necessários para analisar objetos.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-246">Services were often required to parse objects.</span></span> <span data-ttu-id="6cfe5-247">Com o .NET Framework 4.7.2, a composability foi adicionada à configuração via `ConfigurationBuilders`.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="6cfe5-248">Esses construtores permitiram que os desenvolvedores adicionassem várias fontes de configuração que foram então compostas em tempo de execução para recuperar os valores necessários.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="6cfe5-249">ASP.NET Core introduziu um sistema de configuração flexível que permite definir a fonte de configuração ou as fontes usadas pelo seu aplicativo e implantação.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="6cfe5-250">A `ConfigurationBuilder` infra-estrutura que você pode estar usando no aplicativo Web Forms foi modelada após os conceitos usados no sistema de configuração ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="6cfe5-251">O trecho a seguir demonstra como o projeto Web Forms eShop usa *web.config* para armazenar valores de configuração:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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
</configuration>
```

<span data-ttu-id="6cfe5-252">É comum que segredos, como strings de conexão de banco de dados, sejam armazenados dentro da *web.config*. Os segredos são inevitavelmente permaneciados em locais inseguros, como o controle de fontes.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="6cfe5-253">Com o Blazor no ASP.NET Core, a configuração baseada em XML anterior é substituída pelo seguinte JSON:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="6cfe5-254">JSON é o formato de configuração padrão; no entanto, ASP.NET Core suporta muitos outros formatos, incluindo XML.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="6cfe5-255">Há também vários formatos apoiados pela comunidade.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="6cfe5-256">O construtor da classe do `Startup` projeto Blazor `IConfiguration` aceita uma instância através de uma técnica DI conhecida como injeção de construtor:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="6cfe5-257">Por padrão, variáveis de ambiente, arquivos JSON *(appsettings.json* e *appsettings.{ As*opções de configuração e de linha de comando são registradas como fontes de configuração válidas no objeto de configuração.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="6cfe5-258">As fontes de configuração `Configuration[key]`podem ser acessadas via .</span><span class="sxs-lookup"><span data-stu-id="6cfe5-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="6cfe5-259">Uma técnica mais avançada é vincular os dados de configuração a objetos usando o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="6cfe5-260">Para obter mais informações sobre a configuração e o padrão de opções, consulte [Configuração no](/aspnet/core/fundamentals/configuration/) padrão ASP.NET Núcleo e [Opções em ASP.NET Core,](/aspnet/core/fundamentals/configuration/options)respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="6cfe5-261">Migrar acesso a dados</span><span class="sxs-lookup"><span data-stu-id="6cfe5-261">Migrate data access</span></span>

<span data-ttu-id="6cfe5-262">O acesso a dados é um aspecto importante de qualquer aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="6cfe5-263">O projeto eShop armazena informações de catálogo em um banco de dados e recupera os dados com Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="6cfe5-264">Como o EF 6 é suportado no .NET Core 3.0, o projeto pode continuar a usá-lo.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="6cfe5-265">As seguintes alterações relacionadas à EF foram necessárias para o eShop:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="6cfe5-266">No .NET Framework, o `DbContext` objeto aceita uma seqüência do nome do *formulário=ConnectionString* e usa a seqüência de conexão para `ConfigurationManager.AppSettings[ConnectionString]` conectar.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="6cfe5-267">No .NET Core, isso não é suportado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="6cfe5-268">A corda de conexão deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="6cfe5-269">O banco de dados foi acessado de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="6cfe5-270">Embora isso funcione, a escalabilidade pode sofrer.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="6cfe5-271">Essa lógica deve ser movida para um padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="6cfe5-272">Embora não haja o mesmo suporte nativo para vinculação de conjuntos de dados, blazor fornece flexibilidade e poder com seu suporte C# em uma página de Navalha.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="6cfe5-273">Por exemplo, você pode realizar cálculos e exibir o resultado.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="6cfe5-274">Para obter mais informações sobre padrões de dados em Blazor, consulte o capítulo [de acesso a dados.](data.md)</span><span class="sxs-lookup"><span data-stu-id="6cfe5-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="6cfe5-275">Mudanças arquitetônicas</span><span class="sxs-lookup"><span data-stu-id="6cfe5-275">Architectural changes</span></span>

<span data-ttu-id="6cfe5-276">Finalmente, existem algumas diferenças arquitetônicas importantes a considerar ao migrar para Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="6cfe5-277">Muitas dessas alterações são aplicáveis a qualquer coisa baseada no .NET Core ou no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="6cfe5-278">Como o Blazor é construído no .NET Core, existem considerações para garantir o suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="6cfe5-279">Algumas das principais mudanças incluem a remoção dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="6cfe5-280">Vários domínios de aplicativos</span><span class="sxs-lookup"><span data-stu-id="6cfe5-280">Multiple AppDomains</span></span>
- <span data-ttu-id="6cfe5-281">Comunicação remota</span><span class="sxs-lookup"><span data-stu-id="6cfe5-281">Remoting</span></span>
- <span data-ttu-id="6cfe5-282">CAS (segurança de acesso ao código)</span><span class="sxs-lookup"><span data-stu-id="6cfe5-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="6cfe5-283">Transparência de Segurança</span><span class="sxs-lookup"><span data-stu-id="6cfe5-283">Security Transparency</span></span>

<span data-ttu-id="6cfe5-284">Para obter mais informações sobre técnicas para identificar as alterações necessárias para suportar a execução no .NET Core, consulte ['Portar seu código de .NET Framework para .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="6cfe5-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="6cfe5-285">ASP.NET Core é uma versão reimaginada de ASP.NET e tem algumas mudanças que podem inicialmente não parecer óbvias.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="6cfe5-286">As principais mudanças são:</span><span class="sxs-lookup"><span data-stu-id="6cfe5-286">The main changes are:</span></span>

- <span data-ttu-id="6cfe5-287">Sem contexto de sincronização, `HttpContext.Current`o `Thread.CurrentPrincipal`que significa que não há, ou outros acessórios estáticos</span><span class="sxs-lookup"><span data-stu-id="6cfe5-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="6cfe5-288">Sem cópia de sombras</span><span class="sxs-lookup"><span data-stu-id="6cfe5-288">No shadow copying</span></span>
- <span data-ttu-id="6cfe5-289">Sem fila de solicitações</span><span class="sxs-lookup"><span data-stu-id="6cfe5-289">No request queue</span></span>

<span data-ttu-id="6cfe5-290">Muitas operações no ASP.NET Core são assíncronas, o que permite o descarregamento mais fácil de tarefas vinculadas a I/O.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="6cfe5-291">É importante nunca bloquear usando `Task.Wait()` `Task.GetResult()`ou , o que pode esgotar rapidamente os recursos do pool de rosca.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="6cfe5-292">Conclusão da migração</span><span class="sxs-lookup"><span data-stu-id="6cfe5-292">Migration conclusion</span></span>

<span data-ttu-id="6cfe5-293">Neste ponto, você já viu muitos exemplos do que é preciso para mover um projeto de Formulários Web para Blazor.</span><span class="sxs-lookup"><span data-stu-id="6cfe5-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="6cfe5-294">Para um exemplo completo, veja o projeto [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="6cfe5-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="6cfe5-295">Anterior</span><span class="sxs-lookup"><span data-stu-id="6cfe5-295">Previous</span></span>](security-authentication-authorization.md)
