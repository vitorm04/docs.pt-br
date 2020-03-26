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
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Migrar de ASP.NET Formulários web para Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Migrar uma base de código de ASP.NET Formulários web para Blazor é uma tarefa demorada que requer planejamento. Este capítulo descreve o processo. Algo que pode facilitar a transição é garantir que o aplicativo adere a uma arquitetura *n-tier,* onde o modelo de aplicativo (neste caso, Web Forms) é separado da lógica de negócios. Esta separação lógica de camadas deixa claro o que precisa passar para .NET Core e Blazor.

Para este exemplo, o aplicativo eShop disponível no [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) é usado. O eShop é um serviço de catálogo que fornece recursos CRUD via entrada e validação de formulários.

Por que um aplicativo de trabalho deve ser migrado para Blazor? Muitas vezes, não há necessidade. ASP.NET Web Forms continuarão a ser suportados por muitos anos. No entanto, muitos dos recursos que o Blazor fornece são suportados apenas em um aplicativo migrado. Tais características incluem:

- Melhorias de desempenho no quadro, como`Span<T>`
- Capacidade de executar como WebAssembly
- Suporte multiplataforma para Linux e macOS
- Implantação local de aplicativos ou implantação de framework compartilhado sem afetar outros aplicativos

Se esses ou outros novos recursos forem convincentes o suficiente, pode haver valor na migração do aplicativo. A migração pode tomar diferentes formas; pode ser o aplicativo inteiro, ou apenas certos pontos finais que requerem as alterações. A decisão de migrar é baseada, em última instância, nos problemas de negócios a serem resolvidos pelo desenvolvedor.

## <a name="server-side-versus-client-side-hosting"></a>Lado do servidor versus hospedagem do lado do cliente

Como descrito no capítulo [modelos de hospedagem,](hosting-models.md) um aplicativo Blazor pode ser hospedado de duas maneiras diferentes: lado do servidor e lado do cliente. O modelo do lado do servidor usa ASP.NET conexões Core SignalR para gerenciar as atualizações do DOM enquanto executa qualquer código real no servidor. O modelo do lado do cliente é executado como WebAssembly dentro de um navegador e não requer conexões de servidor. Há uma série de diferenças que podem afetar o que é melhor para um aplicativo específico:

- Executando como WebAssembly ainda está em desenvolvimento e pode não suportar todos os recursos (como threading) no momento atual
- A comunicação conversada entre o cliente e o servidor pode causar problemas de latência no modo lado do servidor
- O acesso a bancos de dados e serviços internos ou protegidos exigem um serviço separado com hospedagem do lado do cliente

No momento da escrita, o modelo do lado do servidor se assemelha mais aos Formulários da Web. A maior parte deste capítulo se concentra no modelo de hospedagem do lado do servidor, já que está pronto para a produção.

## <a name="create-a-new-project"></a>Criar um novo projeto

Este passo inicial de migração é criar um novo projeto. Este tipo de projeto é baseado nos projetos de estilo SDK do .NET Core e simplifica grande parte da caldeira que foi usada em formatos de projeto anteriores. Para obter mais detalhes, consulte o capítulo sobre [estrutura do projeto.](project-structure.md)

Uma vez criado o projeto, instale as bibliotecas que foram utilizadas no projeto anterior. Em projetos mais antigos da Web Forms, você pode ter usado o arquivo *packages.config* para listar os pacotes NuGet necessários. No novo projeto no estilo SDK, *o packages.config* foi substituído por `<PackageReference>` elementos no arquivo do projeto. Um benefício dessa abordagem é que todas as dependências são instaladas transitivamente. Você só lista as dependências de alto nível que você se importa.

Muitas das dependências que você está usando estão disponíveis para .NET Core, incluindo Entity Framework 6 e log4net. Se não houver nenhuma versão .NET Core ou .NET Standard disponível, a versão .NET Framework pode ser usada muitas vezes. Sua quilometragem pode variar. Qualquer API usada que não esteja disponível no .NET Core causa um erro de tempo de execução. Visual Studio notifica você de tais pacotes. Um ícone amarelo aparece no nó **Referências** do projeto no **Solution Explorer**.

No projeto eShop baseado em Blazor, você pode ver os pacotes que estão instalados. Anteriormente, o arquivo *packages.config* listava todos os pacotes usados no projeto, resultando em um arquivo de quase 50 linhas de comprimento. Um trecho de *pacotes.config* é:

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

O `<packages>` elemento inclui todas as dependências necessárias. É difícil identificar quais desses pacotes estão incluídos porque você os precisa. Alguns `<package>` elementos são listados simplesmente para satisfazer as necessidades de dependências que você precisa.

O projeto Blazor lista as dependências que você precisa dentro de um `<ItemGroup>` elemento no arquivo do projeto:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Um pacote NuGet que simplifica a vida dos desenvolvedores do Web Forms é o [Pacote de Compatibilidade do Windows](../../core/porting/windows-compat-pack.md). Embora o .NET Core seja multiplataforma, alguns recursos só estão disponíveis no Windows. Recursos específicos do Windows são disponibilizados instalando o pacote de compatibilidade. Exemplos desses recursos incluem os Serviços de Registro, WMI e Diretório. O pacote adiciona cerca de 20.000 APIs e ativa muitos serviços com os quais você pode já estar familiarizado. O projeto eShop não requer o pacote de compatibilidade; mas se seus projetos usarem recursos específicos do Windows, o pacote facilitará os esforços de migração.

## <a name="enable-startup-process"></a>Habilitar o processo de inicialização

O processo de inicialização do Blazor mudou de Web Forms e segue uma configuração semelhante para outros serviços ASP.NET Core. Quando hospedados do lado do servidor, os componentes Blazor são executados como parte de um aplicativo normal do ASP.NET Core. Quando hospedados no navegador com webAssembly, os componentes Blazor usam um modelo de hospedagem semelhante. A diferença é que os componentes são executados como um serviço separado de qualquer um dos processos back-end. De qualquer forma, a startup é semelhante.

O arquivo *Global.asax.cs* é a página de inicialização padrão para projetos do Web Forms. No projeto eShop, este arquivo configura o contêiner Inversão de Controle (IoC) e lida com os vários eventos do ciclo de vida do aplicativo ou solicitação. Alguns desses eventos são tratados com `Application_BeginRequest`middleware (como ). Outros eventos requerem a substituição de serviços específicos via injeção de dependência (DI).

A propósito, o *arquivo Global.asax.cs* para eShop, contém o seguinte código:

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

O arquivo anterior `Startup` torna-se a classe no lado do servidor Blazor:

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

Uma mudança significativa que você pode notar a partir de Formulários web é a proeminência do DI. Di tem sido um princípio norteador no design do ASP.NET Core. Ele suporta a personalização de quase todos os aspectos da estrutura do Núcleo ASP.NET. Há até um provedor de serviços embutido que pode ser usado para muitos cenários. Se mais personalização for necessária, ela pode ser apoiada pelos muitos projetos comunitários. Por exemplo, você pode levar adiante o investimento na biblioteca DI de terceiros.

No aplicativo original da eShop, há alguma configuração para gerenciamento de sessões. Uma vez que o Blazor do lado do servidor usa ASP.NET Core SignalR para comunicação, o estado de sessão não é suportado, pois as conexões podem ocorrer independentemente de um contexto HTTP. Um aplicativo que usa o estado de sessão requer rearquiteantes antes de ser executado como um aplicativo Blazor.

Para obter mais informações sobre a inicialização do aplicativo, consulte [a inicialização do aplicativo](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrar módulos HTTP e manipuladores para middleware

Módulos HTTP e manipuladores são padrões comuns em Formulários da Web para controlar o pipeline de solicitação HTTP. Classes que `IHttpModule` `IHttpHandler` implementam ou podem ser registradas e processam solicitações recebidas. O Web Forms configura módulos e manipuladores no arquivo *Web.config.* O Web Forms também é fortemente baseado no manuseio de eventos do ciclo de vida do aplicativo. ASP.NET Core usa middleware em vez disso. Middleware é registrado `Configure` no método `Startup` da classe. A ordem de execução do middleware é determinada pela ordem de registro.

Na seção [Habilitar processo de inicialização,](#enable-startup-process) um evento `Application_BeginRequest` do ciclo de vida foi levantado pela Web Forms como método. Este evento não está disponível em ASP.NET Core. Uma maneira de alcançar esse comportamento é implementar middleware, como visto no exemplo de arquivo *Startup.cs.* Este middleware faz a mesma lógica e, em seguida, transfere o controle para o próximo manipulador no pipeline de middleware.

Para obter mais informações sobre módulos e manipuladores migratórios, consulte [Migrar manipuladores http e módulos para ASP.NET middleware Core](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrar arquivos estáticos

Para servir arquivos estáticos (por exemplo, HTML, CSS, imagens e JavaScript), os arquivos devem ser expostos por middleware. A `UseStaticFiles` chamada do método permite a saque de arquivos estáticos do caminho raiz da Web. O diretório raiz da Web padrão é *wwwroot,* mas pode ser personalizado. Como incluído `Configure` no método de `Startup` classe do eShop:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

O projeto eShop permite o acesso básico de arquivos estáticos. Existem muitas personalizações disponíveis para acesso a arquivos estáticos. Para obter informações sobre como ativar arquivos padrão ou um navegador de arquivos, consulte [arquivos estáticos no ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migrar agrupamento em tempo de execução e configuração de minificação

Agrupamento e minificação são técnicas de otimização de desempenho para reduzir o número e o tamanho das solicitações de servidor para recuperar certos tipos de arquivos. JavaScript e CSS geralmente passam por algum tipo de agrupamento ou minificação antes de serem enviados ao cliente. Em ASP.NET Formulários da Web, essas otimizações são tratadas em tempo de execução. As convenções de otimização são definidas como um arquivo *App_Start/BundleConfig.cs.* Em ASP.NET Núcleo, adota-se uma abordagem mais declarativa. Um arquivo lista os arquivos a serem minified, juntamente com configurações específicas de minificação.

Para obter mais informações sobre agrupamento e minificação, consulte [Bundle e minify ativos estáticos em ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrar páginas ASPX

Uma página em um aplicativo Web Forms é um arquivo com a extensão *.aspx.* Uma página formulários da Web pode muitas vezes ser mapeada para um componente em Blazor. Um componente Blazor é de autoria de um arquivo com a extensão *.razor.* Para o projeto eShop, cinco páginas são convertidas em uma página de Navalha.

Por exemplo, a visualização de detalhes é composta por três arquivos no projeto Formulários da Web: *Details.aspx,* *Details.aspx.cs*e *Details.aspx.designer.cs*. Ao converter para Blazor, o code-behind e a marcação são combinados em *Details.razor*. A compilação razor (equivalente ao que está em *arquivos de .designer.cs)* é armazenada no diretório *obj* e não são, por padrão, visível no **Solution Explorer**. A página Formulários da Web consiste na seguinte marcação:

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

O código de configuração anterior inclui o seguinte código:

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

Quando convertida em Blazor, a página Formulários da Web se traduz para o seguinte código:

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

Observe que o código e a marcação estão no mesmo arquivo. Todos os serviços necessários são acessíveis com o atributo. `@inject` De `@page` acordo com a diretiva, esta `Catalog/Details/{id}` página pode ser acessada na rota. O valor do espaço `{id}` reservado da rota foi constrangido a um inteiro. Como descrito na seção [de roteamento,](pages-routing-layouts.md) ao contrário do Web Forms, um componente Razor declara explicitamente sua rota e quaisquer parâmetros incluídos. Muitos controles web forms podem não ter contrapartes exatas em Blazor. Muitas vezes há um trecho HTML equivalente que servirá ao mesmo propósito. Por exemplo, `<asp:Label />` o controle pode ser `<label>` substituído por um elemento HTML.

### <a name="model-validation-in-blazor"></a>Validação de modelo em Blazor

Se o código web forms incluir validação, você pode transferir muito do que você tem com poucaou para não alterações. Um benefício para ser executado em Blazor é que a mesma lógica de validação pode ser executada sem precisar de JavaScript personalizado. As anotações de dados permitem uma validação fácil do modelo.

Por exemplo, a página *Create.aspx* tem um formulário de entrada de dados com validação. Um trecho de exemplo seria assim:

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

Em Blazor, a marcação equivalente é fornecida em um arquivo *Create.razor:*

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

O `EditForm` contexto inclui suporte de validação e pode ser enrolado em torno da entrada. Anotações de dados são uma maneira comum de adicionar validação. Esse suporte de validação `DataAnnotationsValidator` pode ser adicionado através do componente. Para obter mais informações sobre este mecanismo, consulte [ASP.NET formulários e validação do Core Blazor](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrar controles de Formulários web incorporados

*Este conteúdo está chegando.*

## <a name="migrate-configuration"></a>Migrar configuração

Em um projeto Web Forms, os dados de configuração são armazenados mais comumente no arquivo *Web.config.* Os dados de configuração são acessados com `ConfigurationManager`. Os serviços eram frequentemente necessários para analisar objetos. Com o .NET Framework 4.7.2, a composability foi adicionada à configuração via `ConfigurationBuilders`. Esses construtores permitiram que os desenvolvedores adicionassem várias fontes de configuração que foram então compostas em tempo de execução para recuperar os valores necessários.

ASP.NET Core introduziu um sistema de configuração flexível que permite definir a fonte de configuração ou as fontes usadas pelo seu aplicativo e implantação. A `ConfigurationBuilder` infra-estrutura que você pode estar usando no aplicativo Web Forms foi modelada após os conceitos usados no sistema de configuração ASP.NET Core.

O trecho a seguir demonstra como o projeto Web Forms eShop usa *web.config* para armazenar valores de configuração:

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

É comum que segredos, como strings de conexão de banco de dados, sejam armazenados dentro da *web.config*. Os segredos são inevitavelmente permaneciados em locais inseguros, como o controle de fontes. Com o Blazor no ASP.NET Core, a configuração baseada em XML anterior é substituída pelo seguinte JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON é o formato de configuração padrão; no entanto, ASP.NET Core suporta muitos outros formatos, incluindo XML. Há também vários formatos apoiados pela comunidade.

O construtor da classe do `Startup` projeto Blazor `IConfiguration` aceita uma instância através de uma técnica DI conhecida como injeção de construtor:

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

Por padrão, variáveis de ambiente, arquivos JSON *(appsettings.json* e *appsettings.{ As*opções de configuração e de linha de comando são registradas como fontes de configuração válidas no objeto de configuração. As fontes de configuração `Configuration[key]`podem ser acessadas via . Uma técnica mais avançada é vincular os dados de configuração a objetos usando o padrão de opções. Para obter mais informações sobre a configuração e o padrão de opções, consulte [Configuração no](/aspnet/core/fundamentals/configuration/) padrão ASP.NET Núcleo e [Opções em ASP.NET Core,](/aspnet/core/fundamentals/configuration/options)respectivamente.

## <a name="migrate-data-access"></a>Migrar acesso a dados

O acesso a dados é um aspecto importante de qualquer aplicativo. O projeto eShop armazena informações de catálogo em um banco de dados e recupera os dados com Entity Framework (EF) 6. Como o EF 6 é suportado no .NET Core 3.0, o projeto pode continuar a usá-lo.

As seguintes alterações relacionadas à EF foram necessárias para o eShop:

- No .NET Framework, o `DbContext` objeto aceita uma seqüência do nome do *formulário=ConnectionString* e usa a seqüência de conexão para `ConfigurationManager.AppSettings[ConnectionString]` conectar. No .NET Core, isso não é suportado. A corda de conexão deve ser fornecida.
- O banco de dados foi acessado de forma síncrona. Embora isso funcione, a escalabilidade pode sofrer. Essa lógica deve ser movida para um padrão assíncrono.

Embora não haja o mesmo suporte nativo para vinculação de conjuntos de dados, blazor fornece flexibilidade e poder com seu suporte C# em uma página de Navalha. Por exemplo, você pode realizar cálculos e exibir o resultado. Para obter mais informações sobre padrões de dados em Blazor, consulte o capítulo [de acesso a dados.](data.md)

## <a name="architectural-changes"></a>Mudanças arquitetônicas

Finalmente, existem algumas diferenças arquitetônicas importantes a considerar ao migrar para Blazor. Muitas dessas alterações são aplicáveis a qualquer coisa baseada no .NET Core ou no ASP.NET Core.

Como o Blazor é construído no .NET Core, existem considerações para garantir o suporte no .NET Core. Algumas das principais mudanças incluem a remoção dos seguintes recursos:

- Vários domínios de aplicativos
- Comunicação remota
- CAS (segurança de acesso ao código)
- Transparência de Segurança

Para obter mais informações sobre técnicas para identificar as alterações necessárias para suportar a execução no .NET Core, consulte ['Portar seu código de .NET Framework para .NET Core](/dotnet/core/porting).

ASP.NET Core é uma versão reimaginada de ASP.NET e tem algumas mudanças que podem inicialmente não parecer óbvias. As principais mudanças são:

- Sem contexto de sincronização, `HttpContext.Current`o `Thread.CurrentPrincipal`que significa que não há, ou outros acessórios estáticos
- Sem cópia de sombras
- Sem fila de solicitações

Muitas operações no ASP.NET Core são assíncronas, o que permite o descarregamento mais fácil de tarefas vinculadas a I/O. É importante nunca bloquear usando `Task.Wait()` `Task.GetResult()`ou , o que pode esgotar rapidamente os recursos do pool de rosca.

## <a name="migration-conclusion"></a>Conclusão da migração

Neste ponto, você já viu muitos exemplos do que é preciso para mover um projeto de Formulários Web para Blazor. Para um exemplo completo, veja o projeto [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)

>[!div class="step-by-step"]
>[Anterior](security-authentication-authorization.md)
