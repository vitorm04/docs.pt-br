---
title: Inicialização do aplicativo
description: Saiba como definir a lógica de inicialização para seu aplicativo.
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: ea2ea458011d8351a834aa12db02e5d2bac2dc65
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267692"
---
# <a name="app-startup"></a><span data-ttu-id="1463c-103">Inicialização do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1463c-103">App startup</span></span>

<span data-ttu-id="1463c-104">Os aplicativos escritos para ASP.NET normalmente têm um `global.asax.cs` arquivo que define o `Application_Start` evento que controla quais serviços são configurados e disponibilizados para processamento em HTML e .net.</span><span class="sxs-lookup"><span data-stu-id="1463c-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="1463c-105">Este capítulo analisa como as coisas são ligeiramente diferentes com ASP.NET Core e um servidor mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="1463c-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="1463c-106">Application_Start e Web Forms</span><span class="sxs-lookup"><span data-stu-id="1463c-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="1463c-107">O método padrão de formulários da Web aumentou com a `Application_Start` finalidade de anos para lidar com muitas tarefas de configuração.</span><span class="sxs-lookup"><span data-stu-id="1463c-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="1463c-108">Um novo projeto Web Forms com o modelo padrão no Visual Studio 2019 agora contém a seguinte lógica de configuração:</span><span class="sxs-lookup"><span data-stu-id="1463c-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="1463c-109">`RouteConfig` -Roteamento de URL de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1463c-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="1463c-110">`BundleConfig` -Agrupamento e minificação do CSS e do JavaScript</span><span class="sxs-lookup"><span data-stu-id="1463c-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="1463c-111">Cada um desses arquivos individuais reside na `App_Start` pasta e é executado apenas uma vez no início do nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1463c-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="1463c-112">`RouteConfig` no modelo de projeto padrão, o adiciona o `FriendlyUrlSettings` para Web Forms para permitir que as URLs de aplicativo omitam a `.ASPX` extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1463c-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="1463c-113">O modelo padrão também contém uma diretiva que fornece códigos de status de redirecionamento HTTP permanentes (HTTP 301) para as `.ASPX` páginas para a URL amigável com o nome do arquivo que omite a extensão.</span><span class="sxs-lookup"><span data-stu-id="1463c-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="1463c-114">Com o ASP.NET Core e o mais claro, esses métodos são simplificados e consolidados na `Startup` classe ou são eliminados em favor de tecnologias da Web comuns.</span><span class="sxs-lookup"><span data-stu-id="1463c-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="1463c-115">Estrutura de inicialização de servidor mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="1463c-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="1463c-116">Os aplicativos de servidor mais recentes residem na parte superior de um aplicativo ASP.NET Core 3,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1463c-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="1463c-117">ASP.NET Core aplicativos Web são configurados por meio de um par de métodos na `Startup.cs` classe na pasta raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1463c-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="1463c-118">O conteúdo padrão da classe de inicialização está listado abaixo</span><span class="sxs-lookup"><span data-stu-id="1463c-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="1463c-119">Como o restante do ASP.NET Core, a classe de inicialização é criada com princípios de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="1463c-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="1463c-120">O `IConfiguration` é fornecido ao construtor e Stash em uma propriedade pública para acesso posterior durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="1463c-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="1463c-121">O `ConfigureServices` método introduzido no ASP.NET Core permite que vários serviços do ASP.NET Core Framework sejam configurados para o contêiner de injeção de dependência interna da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1463c-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="1463c-122">Os vários `services.Add*` métodos adicionam serviços que habilitam recursos como autenticação, páginas do Razor, roteamento do controlador MVC, signalr e interações de servidor mais incrivelmente entre muitos outros.</span><span class="sxs-lookup"><span data-stu-id="1463c-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="1463c-123">Esse método não era necessário em Web Forms, pois a análise e o manuseio dos arquivos ASPX, ASCX, ASHX e ASMX foram definidos por meio da referência a ASP.NET no arquivo de configuração web.config.</span><span class="sxs-lookup"><span data-stu-id="1463c-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="1463c-124">Mais informações sobre injeção de dependência no ASP.NET Core estão disponíveis na [documentação online](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="1463c-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="1463c-125">O `Configure` método apresenta o conceito do pipeline http para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1463c-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="1463c-126">Nesse método, declaramos de cima para baixo o [middleware](middleware.md) que tratará cada solicitação enviada ao nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1463c-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="1463c-127">A maioria desses recursos na configuração padrão foi espalhada pelos arquivos de configuração do Web Forms e agora está em um único lugar para facilitar a referência.</span><span class="sxs-lookup"><span data-stu-id="1463c-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="1463c-128">Não é mais a configuração da página de erro personalizada colocada em um `web.config` arquivo, mas agora está configurada para ser sempre exibida se o ambiente do aplicativo não estiver rotulado `Development` .</span><span class="sxs-lookup"><span data-stu-id="1463c-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="1463c-129">Além disso, ASP.NET Core aplicativos agora estão configurados para servir páginas seguras com o TLS por padrão com a `UseHttpsRedirection` chamada de método.</span><span class="sxs-lookup"><span data-stu-id="1463c-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="1463c-130">Em seguida, um método de configuração inesperado é listado para `UseStaticFiles` .</span><span class="sxs-lookup"><span data-stu-id="1463c-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="1463c-131">No ASP.NET Core, o suporte para solicitações de arquivos estáticos (como JavaScript, CSS e arquivos de imagem) deve ser explicitamente habilitado e somente os arquivos na pasta *wwwroot* do aplicativo são publicamente endereçáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="1463c-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="1463c-132">A próxima linha é a primeira que replica uma das opções de configuração do Web Forms: `UseRouting` .</span><span class="sxs-lookup"><span data-stu-id="1463c-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="1463c-133">Esse método adiciona o ASP.NET Core roteador ao pipeline e pode ser configurado aqui ou nos arquivos individuais aos quais ele pode considerar o roteamento.</span><span class="sxs-lookup"><span data-stu-id="1463c-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="1463c-134">Mais informações sobre a configuração de roteamento podem ser encontradas na [seção roteamento](pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="1463c-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="1463c-135">A instrução final nesse método define os pontos de extremidade que ASP.NET Core está escutando.</span><span class="sxs-lookup"><span data-stu-id="1463c-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="1463c-136">Esses são os locais acessíveis pela Web que você pode acessar no servidor Web e receber algum conteúdo manipulado pelo .NET e retornado a você.</span><span class="sxs-lookup"><span data-stu-id="1463c-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="1463c-137">A primeira entrada, `MapBlazorHub` configura um Hub do signalr para uso no fornecimento da conexão em tempo real e persistente ao servidor onde o estado e a renderização de componentes mais fáceis são tratados.</span><span class="sxs-lookup"><span data-stu-id="1463c-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="1463c-138">A `MapFallbackToPage` chamada do método indica o local acessível pela Web da página que inicia o aplicativo mais sincero e também configura o aplicativo para lidar com solicitações de vinculação profunda do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="1463c-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="1463c-139">Você verá esse recurso no trabalho se abrir um navegador e navegar diretamente para uma rota manipulada mais incrivelmente em seu aplicativo, como `/counter` no modelo de projeto padrão.</span><span class="sxs-lookup"><span data-stu-id="1463c-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="1463c-140">A solicitação é manipulada pela página de fallback *_Host. cshtml* , que, em seguida, executa o roteador mais incrivelmente e renderiza a página do contador.</span><span class="sxs-lookup"><span data-stu-id="1463c-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="1463c-141">Atualizando o processo BundleConfig</span><span class="sxs-lookup"><span data-stu-id="1463c-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="1463c-142">As tecnologias para agrupar ativos como folhas de estilo CSS e arquivos JavaScript evoluíram significativamente, com outras tecnologias que fornecem ferramentas e técnicas rapidamente em evolução para o gerenciamento desses recursos.</span><span class="sxs-lookup"><span data-stu-id="1463c-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="1463c-143">Para esse fim, é recomendável usar uma ferramenta de linha de comando de nó, como Grunt/Gulp/webpack, para empacotar seus ativos estáticos.</span><span class="sxs-lookup"><span data-stu-id="1463c-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="1463c-144">As ferramentas de linha de comando Grunt, Gulp e webpack e suas configurações associadas podem ser adicionadas ao seu aplicativo e ASP.NET Core ignorarão silenciosamente esses arquivos durante o processo de compilação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1463c-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="1463c-145">Você pode adicionar uma chamada para executar suas tarefas adicionando um `Target` dentro do arquivo de projeto com sintaxe semelhante à seguinte que dispararia um script Gulp e o `min` destino dentro desse script</span><span class="sxs-lookup"><span data-stu-id="1463c-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="1463c-146">Mais detalhes sobre as duas estratégias para gerenciar seus arquivos CSS e JavaScript estão disponíveis no [pacote e reduzir ativos estáticos na documentação ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) .</span><span class="sxs-lookup"><span data-stu-id="1463c-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1463c-147">[Anterior](project-structure.md) 
> [Avançar](components.md)</span><span class="sxs-lookup"><span data-stu-id="1463c-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
