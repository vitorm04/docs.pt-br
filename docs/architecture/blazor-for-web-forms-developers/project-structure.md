---
title: Estrutura do projeto para aplicativos mais Incrivelmenteos
description: Saiba como as estruturas de projeto dos projetos ASP.NET Web Forms e mais incrivelmente comparam.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087859"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="0db8d-103">Estrutura do projeto para aplicativos mais Incrivelmenteos</span><span class="sxs-lookup"><span data-stu-id="0db8d-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0db8d-104">Apesar das diferenças significativas na estrutura do projeto, o ASP.NET Web Forms e o mais grande compartilhamento são muitos conceitos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="0db8d-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="0db8d-105">Aqui, vamos examinar a estrutura de um projeto mais claro e compará-lo a um projeto ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0db8d-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="0db8d-106">Para criar seu primeiro aplicativo mais incrivelmente, siga as instruções nas [etapas de introdução](/aspnet/core/blazor/get-started)do mais ou mais.</span><span class="sxs-lookup"><span data-stu-id="0db8d-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="0db8d-107">Você pode seguir as instruções para criar um aplicativo de servidor mais incrivelmente ou um aplicativo Webassembly mais incrivelmente hospedado no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="0db8d-108">Exceto para a lógica específica do modelo de hospedagem, a maior parte do código em ambos os projetos é a mesma.</span><span class="sxs-lookup"><span data-stu-id="0db8d-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="0db8d-109">Arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="0db8d-109">Project file</span></span>

<span data-ttu-id="0db8d-110">Os aplicativos de servidor de mais incrivelmente são projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="0db8d-111">O arquivo de projeto para o aplicativo de servidor mais incrivelmente é tão simples quanto pode ser:</span><span class="sxs-lookup"><span data-stu-id="0db8d-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0db8d-112">O arquivo de projeto para um aplicativo Webassembly mais complicado parece um pouco mais envolvido (números de versão exatas podem variar):</span><span class="sxs-lookup"><span data-stu-id="0db8d-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="0db8d-113">Os projetos Webassembly de mais alto-alvo .NET Standard em vez do .NET Core porque eles são executados no navegador em um tempo de execução .NET baseado em Webassembly.</span><span class="sxs-lookup"><span data-stu-id="0db8d-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="0db8d-114">Você não pode instalar o .NET em um navegador da Web como você pode em um computador de servidor ou de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="0db8d-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="0db8d-115">Consequentemente, o projeto faz referência à estrutura mais Incrivelmentea usando referências de pacote individuais.</span><span class="sxs-lookup"><span data-stu-id="0db8d-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="0db8d-116">Por comparação, um projeto ASP.NET Web Forms padrão inclui quase 300 linhas de XML em seu arquivo *. csproj* , a maior parte deles está listando explicitamente os vários arquivos de código e conteúdo no projeto.</span><span class="sxs-lookup"><span data-stu-id="0db8d-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="0db8d-117">Muitas das simplificações dos projetos baseados no .NET Core e no .NET Standard são provenientes dos destinos e das propriedades padrão importadas referenciando o SDK do `Microsoft.NET.Sdk.Web`, geralmente conhecido como simplesmente o SDK da Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="0db8d-118">O SDK da Web inclui curingas e outras conveniências que simplificam a inclusão de código e arquivos de conteúdo no projeto.</span><span class="sxs-lookup"><span data-stu-id="0db8d-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="0db8d-119">Você não precisa listar os arquivos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="0db8d-120">Ao direcionar o .NET Core, o Web SDK também adiciona referências de estrutura às estruturas compartilhadas do .NET Core e do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="0db8d-121">As estruturas são visíveis no nó **dependências** > **estruturas** , na janela **Gerenciador de soluções** .</span><span class="sxs-lookup"><span data-stu-id="0db8d-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="0db8d-122">As estruturas compartilhadas são coleções de assemblies que foram instalados no computador durante a instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="0db8d-123">Embora eles tenham suporte, as referências de assembly individuais são menos comuns em projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="0db8d-124">A maioria das dependências do projeto é tratada como referências de pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0db8d-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="0db8d-125">Você só precisa referenciar as dependências de pacote de nível superior em projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="0db8d-126">Dependências transitivas são incluídas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="0db8d-127">Em vez de usar o arquivo *Packages. config* normalmente encontrado em ASP.NET Web Forms projetos para referenciar pacotes, as referências de pacote são adicionadas ao arquivo de projeto usando o elemento `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="0db8d-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="0db8d-128">Ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="0db8d-128">Entry point</span></span>

<span data-ttu-id="0db8d-129">O ponto de entrada do aplicativo de servidor mais incrivelmente é definido no arquivo *Program.cs* , como você veria em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0db8d-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="0db8d-130">Quando o aplicativo é executado, ele cria e executa uma instância de host Web usando padrões específicos para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="0db8d-131">O host da Web gerencia o ciclo de vida do aplicativo de servidor mais novo e configura os serviços de nível de host.</span><span class="sxs-lookup"><span data-stu-id="0db8d-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="0db8d-132">Exemplos desses serviços são configuração, registro em log, injeção de dependência e o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="0db8d-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="0db8d-133">Esse código é basicamente clichê e, muitas vezes, permanece inalterado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-133">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="0db8d-134">Os aplicativos Webassembly mais incrivelmente também definem um ponto de entrada em *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="0db8d-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="0db8d-135">O código parece um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-135">The code looks slightly different.</span></span> <span data-ttu-id="0db8d-136">O código é semelhante, pois está configurando o host de aplicativo para fornecer os mesmos serviços de nível de host para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db8d-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="0db8d-137">No entanto, o host do aplicativo Webassembly não configura um servidor HTTP porque ele é executado diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="0db8d-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="0db8d-138">Os aplicativos mais incrivelmente têm uma classe `Startup` em vez de um arquivo *global. asax* para definir a lógica de inicialização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db8d-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="0db8d-139">A classe `Startup` é usada para configurar o aplicativo e quaisquer serviços específicos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db8d-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="0db8d-140">No aplicativo de servidor mais grande, a classe `Startup` é usada para configurar o ponto de extremidade para a conexão em tempo real usada pelo mais alto nível entre os navegadores de cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="0db8d-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="0db8d-141">No aplicativo Webassembly mais incrivelmente, a classe `Startup` define os componentes raiz para o aplicativo e onde eles devem ser renderizados.</span><span class="sxs-lookup"><span data-stu-id="0db8d-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="0db8d-142">Vamos dar uma olhada mais detalhada na classe `Startup` na seção de [inicialização do aplicativo](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="0db8d-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="0db8d-143">Arquivos estáticos</span><span class="sxs-lookup"><span data-stu-id="0db8d-143">Static files</span></span>

<span data-ttu-id="0db8d-144">Ao contrário dos projetos do ASP.NET Web Forms, nem todos os arquivos em um projeto mais incrivelmente podem ser solicitados como arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0db8d-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="0db8d-145">Somente os arquivos na pasta *wwwroot* são endereçáveis da Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="0db8d-146">Essa pasta é referida na "raiz da Web" do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db8d-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="0db8d-147">Qualquer coisa fora da raiz da Web do aplicativo *não é* endereçável da Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="0db8d-148">Essa configuração fornece um nível adicional de segurança que impede a exposição acidental de arquivos de projeto na Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="0db8d-149">Configuração</span><span class="sxs-lookup"><span data-stu-id="0db8d-149">Configuration</span></span>

<span data-ttu-id="0db8d-150">A configuração no ASP.NET Web Forms aplicativos normalmente é manipulada usando um ou mais arquivos *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="0db8d-151">Os aplicativos mais incrivelmente não normalmente têm arquivos *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="0db8d-152">Se isso for feito, o arquivo será usado apenas para definir configurações específicas do IIS quando hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="0db8d-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="0db8d-153">Em vez disso, aplicativos de servidor mais poseriais usam as abstrações de configuração de ASP.NET Core (aplicativos Webassembly de maior destaque atualmente não dão suporte às mesmas abstrações de configuração, mas que podem ser um recurso adicionado no futuro).</span><span class="sxs-lookup"><span data-stu-id="0db8d-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="0db8d-154">Por exemplo, o aplicativo de servidor padrão de mais incrivelmente armazena algumas configurações em *appSettings. JSON*.</span><span class="sxs-lookup"><span data-stu-id="0db8d-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="0db8d-155">Aprenderemos mais sobre a configuração em projetos ASP.NET Core na seção de [configuração](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="0db8d-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="0db8d-156">Componentes do Razor</span><span class="sxs-lookup"><span data-stu-id="0db8d-156">Razor components</span></span>

<span data-ttu-id="0db8d-157">A maioria dos arquivos em projetos mais podestas são arquivos *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="0db8d-158">O Razor é uma linguagem de modelagem baseada em C# HTML e é usada para gerar dinamicamente a interface do usuário da Web.</span><span class="sxs-lookup"><span data-stu-id="0db8d-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="0db8d-159">Os arquivos *. Razor* definem componentes que compõem a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db8d-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="0db8d-160">Para a maior parte, os componentes são idênticos tanto para os aplicativos do mais grande servidor quanto para o Webassembly.</span><span class="sxs-lookup"><span data-stu-id="0db8d-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="0db8d-161">Os componentes do mais incrivelmente são análogos aos controles de usuário no ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="0db8d-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="0db8d-162">Cada arquivo de componente do Razor é compilado em uma classe do .NET quando o projeto é compilado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="0db8d-163">A classe gerada captura o estado do componente, a lógica de renderização, os métodos de ciclo de vida, os manipuladores de eventos e outras lógicas.</span><span class="sxs-lookup"><span data-stu-id="0db8d-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="0db8d-164">Veremos os componentes de criação na seção [criando componentes de interface do usuário reutilizáveis com mais capacidade](./components.md) .</span><span class="sxs-lookup"><span data-stu-id="0db8d-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="0db8d-165">Os arquivos *_Imports. Razor* não são arquivos de componente do Razor.</span><span class="sxs-lookup"><span data-stu-id="0db8d-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="0db8d-166">Em vez disso, eles definem um conjunto de diretivas do Razor para importar para outros arquivos *. Razor* dentro da mesma pasta e em suas subpastas.</span><span class="sxs-lookup"><span data-stu-id="0db8d-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="0db8d-167">Por exemplo, um arquivo *_Imports. Razor* é uma maneira convencional de adicionar instruções `using` para namespaces comumente usados:</span><span class="sxs-lookup"><span data-stu-id="0db8d-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="0db8d-168">Páginas</span><span class="sxs-lookup"><span data-stu-id="0db8d-168">Pages</span></span>

<span data-ttu-id="0db8d-169">Onde estão as páginas nos aplicativos mais incrivelmente?</span><span class="sxs-lookup"><span data-stu-id="0db8d-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="0db8d-170">O mais incrivelmente não define uma extensão de arquivo separada para páginas endereçáveis, como os arquivos *. aspx* em ASP.NET Web Forms aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0db8d-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="0db8d-171">Em vez disso, as páginas são definidas por meio da atribuição de rotas a componentes.</span><span class="sxs-lookup"><span data-stu-id="0db8d-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="0db8d-172">Uma rota é normalmente atribuída usando a diretiva `@page` Razor.</span><span class="sxs-lookup"><span data-stu-id="0db8d-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="0db8d-173">Por exemplo, o componente `Counter` criado no arquivo *pages/Counter. Razor* define a seguinte rota:</span><span class="sxs-lookup"><span data-stu-id="0db8d-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="0db8d-174">O roteamento no mais alto é tratado no lado do cliente, não no servidor.</span><span class="sxs-lookup"><span data-stu-id="0db8d-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="0db8d-175">À medida que o usuário navega no navegador, o mais incrivelmente intercepta a navegação e, em seguida, renderiza o componente com a rota correspondente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="0db8d-176">As rotas de componentes não são inferidas no momento pelo local do arquivo do componente como estão com páginas *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="0db8d-177">Esse recurso pode ser adicionado no futuro.</span><span class="sxs-lookup"><span data-stu-id="0db8d-177">This feature may be added in the future.</span></span> <span data-ttu-id="0db8d-178">Cada rota deve ser especificada explicitamente no componente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="0db8d-179">O armazenamento de componentes roteáveis em uma pasta de *páginas* não tem significado especial e é puramente uma convenção.</span><span class="sxs-lookup"><span data-stu-id="0db8d-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="0db8d-180">Veremos mais detalhadamente no roteamento do, na seção [páginas, roteamento e layouts](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="0db8d-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="0db8d-181">{1&gt;Layout&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0db8d-181">Layout</span></span>

<span data-ttu-id="0db8d-182">No ASP.NET Web Forms aplicativos, o layout de página comum é manipulado usando páginas mestras (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="0db8d-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="0db8d-183">Em aplicativos mais Incrivelmenteos, o layout da página é manipulado usando componentes de layout (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="0db8d-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="0db8d-184">Os componentes de layout serão discutidos em mais detalhes na seção [página, roteamento e layouts](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="0db8d-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="0db8d-185">Mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="0db8d-185">Bootstrap Blazor</span></span>

<span data-ttu-id="0db8d-186">Para a inicialização mais incrivelmente, o aplicativo deve:</span><span class="sxs-lookup"><span data-stu-id="0db8d-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="0db8d-187">Especifique o local na página em que o componente raiz (*app. Razor*) deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="0db8d-188">Adicione o script de estrutura de mais incrivelmente correspondente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="0db8d-189">No aplicativo de servidor mais novo, a página host do componente raiz é definida no arquivo *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="0db8d-190">Esse arquivo define uma página Razor, não um componente.</span><span class="sxs-lookup"><span data-stu-id="0db8d-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="0db8d-191">Razor Pages usar sintaxe Razor para definir uma página endereçável do servidor, muito parecida com uma página *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="0db8d-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="0db8d-192">O método `Html.RenderComponentAsync<TComponent>(RenderMode)` é usado para definir onde um componente de nível raiz deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="0db8d-193">A opção `RenderMode` indica a maneira como o componente deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="0db8d-194">A tabela a seguir descreve as opções de `RenderMode` com suporte.</span><span class="sxs-lookup"><span data-stu-id="0db8d-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="0db8d-195">Opção</span><span class="sxs-lookup"><span data-stu-id="0db8d-195">Option</span></span>                        |<span data-ttu-id="0db8d-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="0db8d-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="0db8d-197">Renderizado interativamente quando uma conexão com o navegador é estabelecida</span><span class="sxs-lookup"><span data-stu-id="0db8d-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="0db8d-198">Primeiro renderizado e, em seguida, renderizado interativamente</span><span class="sxs-lookup"><span data-stu-id="0db8d-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="0db8d-199">Renderizado como conteúdo estático</span><span class="sxs-lookup"><span data-stu-id="0db8d-199">Rendered as static content</span></span>|

<span data-ttu-id="0db8d-200">A referência de script para *_framework/blazor.Server.js* estabelece a conexão em tempo real com o servidor e, em seguida, lida com todas as interações do usuário e as atualizações da interface de usuário.</span><span class="sxs-lookup"><span data-stu-id="0db8d-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="0db8d-201">No aplicativo Webassembly mais novo, a página host é um arquivo HTML estático simples em *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="0db8d-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="0db8d-202">O elemento `<app>` é usado para indicar onde o componente raiz deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

<span data-ttu-id="0db8d-203">O componente específico a ser renderizado é configurado no método de `Startup.Configure` do aplicativo com um seletor CSS correspondente, indicando onde o componente deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a><span data-ttu-id="0db8d-204">Saída da compilação</span><span class="sxs-lookup"><span data-stu-id="0db8d-204">Build output</span></span>

<span data-ttu-id="0db8d-205">Quando um projeto mais elaborado é criado, todos os arquivos de componente e código do Razor são compilados em um único assembly.</span><span class="sxs-lookup"><span data-stu-id="0db8d-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="0db8d-206">Diferente do ASP.NET Web Forms projetos, o mais claro não dá suporte à compilação em tempo de execução da lógica da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="0db8d-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="0db8d-207">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0db8d-207">Run the app</span></span>

<span data-ttu-id="0db8d-208">Para executar o aplicativo de servidor mais incrivelmente, pressione `F5` no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0db8d-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="0db8d-209">Aplicativos mais incrivelmenteos não dão suporte à compilação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0db8d-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="0db8d-210">Para ver os resultados das alterações de marcação de código e de componente, recompile e reinicie o aplicativo com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="0db8d-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="0db8d-211">Se você executar sem o depurador anexado (`Ctrl+F5`), o Visual Studio inspecionará as alterações de arquivo e reiniciará o aplicativo conforme as alterações forem feitas.</span><span class="sxs-lookup"><span data-stu-id="0db8d-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="0db8d-212">Você atualiza manualmente o navegador conforme as alterações são feitas.</span><span class="sxs-lookup"><span data-stu-id="0db8d-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="0db8d-213">Para executar o aplicativo Webassembly mais incrivelmente, escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="0db8d-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="0db8d-214">Execute o projeto do cliente diretamente usando o servidor de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0db8d-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="0db8d-215">Execute o projeto de servidor ao hospedar o aplicativo com ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0db8d-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="0db8d-216">Aplicativos Webassembly de mais de-estúdio não dão suporte à depuração usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0db8d-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="0db8d-217">Para executar o aplicativo, use `Ctrl+F5` em vez de `F5`.</span><span class="sxs-lookup"><span data-stu-id="0db8d-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="0db8d-218">Em vez disso, você pode depurar aplicativos Webassembly mais incrivelmente diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="0db8d-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="0db8d-219">Consulte [depurar ASP.NET Core mais incrivelmente](/aspnet/core/blazor/debug) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="0db8d-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0db8d-220">[Anterior](hosting-models.md)
>[Próximo](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="0db8d-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
