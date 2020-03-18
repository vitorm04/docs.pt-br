---
title: Estrutura do projeto para aplicativos Blazor
description: Saiba como as estruturas de projetos de ASP.NET Web Forms e projetos Blazor se comparam.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401574"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="a5b01-103">Estrutura do projeto para aplicativos Blazor</span><span class="sxs-lookup"><span data-stu-id="a5b01-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a5b01-104">Apesar de suas diferenças significativas na estrutura do projeto, ASP.NET Web Forms e Blazor compartilham muitos conceitos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="a5b01-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="a5b01-105">Aqui, vamos olhar para a estrutura de um projeto Blazor e compará-lo com um projeto ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a5b01-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="a5b01-106">Para criar seu primeiro aplicativo Blazor, siga as instruções no [Blazor iniciando](/aspnet/core/blazor/get-started)os passos .</span><span class="sxs-lookup"><span data-stu-id="a5b01-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="a5b01-107">Você pode seguir as instruções para criar um aplicativo Blazor Server ou um aplicativo Blazor WebAssembly hospedado em ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="a5b01-108">Com exceção da lógica específica do modelo de hospedagem, a maior parte do código em ambos os projetos é a mesma.</span><span class="sxs-lookup"><span data-stu-id="a5b01-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="a5b01-109">Arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="a5b01-109">Project file</span></span>

<span data-ttu-id="a5b01-110">Os aplicativos Blazor Server são projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="a5b01-111">O arquivo de projeto para o aplicativo Blazor Server é o mais simples possível:</span><span class="sxs-lookup"><span data-stu-id="a5b01-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a5b01-112">O arquivo de projeto de um aplicativo Blazor WebAssembly parece um pouco mais envolvido (números exatos de versão podem variar):</span><span class="sxs-lookup"><span data-stu-id="a5b01-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="a5b01-113">O Blazor WebAssembly projeta o padrão .NET em vez do .NET Core porque eles são executados no navegador em um tempo de execução .NET baseado no WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="a5b01-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="a5b01-114">Você não pode instalar o .NET em um navegador da Web como pode em um servidor ou máquina de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="a5b01-115">Consequentemente, o projeto faz referência à estrutura blazor utilizando referências individuais de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a5b01-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="a5b01-116">Em comparação, um projeto padrão ASP.NET Web Forms inclui quase 300 linhas de XML em seu arquivo *.csproj,* a maioria das quais está listando explicitamente os vários arquivos de código e conteúdo no projeto.</span><span class="sxs-lookup"><span data-stu-id="a5b01-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="a5b01-117">Muitas das simplificações nos projetos baseados em .NET Core e .NET Standard vêm das `Microsoft.NET.Sdk.Web` metas e propriedades padrão importadas por meio de referência ao SDK, muitas vezes referido simplesmente como Web SDK.</span><span class="sxs-lookup"><span data-stu-id="a5b01-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="a5b01-118">O Web SDK inclui curingas e outras conveniências que simplificam a inclusão de arquivos de código e conteúdo no projeto.</span><span class="sxs-lookup"><span data-stu-id="a5b01-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="a5b01-119">Você não precisa listar os arquivos explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="a5b01-120">Ao direcionar o .NET Core, o Web SDK também adiciona referências de estrutura aos frameworks compartilhados .NET Core e ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="a5b01-121">As estruturas são visíveis do nó **Dependencies** > **Frameworks** na janela **Solution Explorer.**</span><span class="sxs-lookup"><span data-stu-id="a5b01-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="a5b01-122">As estruturas compartilhadas são coleções de conjuntos que foram instalados na máquina ao instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="a5b01-123">Embora sejam suportadas, referências individuais de montagem são menos comuns em projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="a5b01-124">A maioria das dependências do projeto são tratadas como referências de pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5b01-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="a5b01-125">Você só precisa fazer referência a dependências de pacotes de nível superior em projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="a5b01-126">Dependências transitivas são incluídas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="a5b01-127">Em vez de usar o arquivo *packages.config* comumente encontrado em ASP.NET projetos da Web Forms `<PackageReference>` para referenciar pacotes, as referências do pacote são adicionadas ao arquivo do projeto usando o elemento.</span><span class="sxs-lookup"><span data-stu-id="a5b01-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="a5b01-128">Ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="a5b01-128">Entry point</span></span>

<span data-ttu-id="a5b01-129">O ponto de entrada do aplicativo Blazor Server é definido no arquivo *Program.cs,* como você veria em um aplicativo console.</span><span class="sxs-lookup"><span data-stu-id="a5b01-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="a5b01-130">Quando o aplicativo é executado, ele cria e executa uma instância de host da Web usando padrões específicos para aplicativos web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="a5b01-131">O host web gerencia o ciclo de vida do aplicativo Blazor Server e configura serviços de nível host.</span><span class="sxs-lookup"><span data-stu-id="a5b01-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="a5b01-132">Exemplos desses serviços são configuração, registro, injeção de dependência e servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5b01-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="a5b01-133">Este código é principalmente caldeira e muitas vezes é deixado inalterado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="a5b01-134">Os aplicativos Blazor WebAssembly também definem um ponto de entrada no *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="a5b01-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="a5b01-135">O código parece um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-135">The code looks slightly different.</span></span> <span data-ttu-id="a5b01-136">O código é semelhante na forma de configurar o host do aplicativo para fornecer os mesmos serviços de nível de host para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b01-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="a5b01-137">No entanto, o host do aplicativo WebAssembly não configura um servidor HTTP porque ele é executado diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="a5b01-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="a5b01-138">Os aplicativos Blazor têm uma `Startup` classe em vez de um arquivo *Global.asax* para definir a lógica de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b01-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="a5b01-139">A `Startup` classe é usada para configurar o aplicativo e quaisquer serviços específicos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b01-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="a5b01-140">No aplicativo Blazor Server, a `Startup` classe é usada para configurar o ponto final para a conexão em tempo real usada pelo Blazor entre os navegadores clientes e o servidor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="a5b01-141">No aplicativo Blazor WebAssembly, a `Startup` classe define os componentes raiz para o aplicativo e onde eles devem ser renderizados.</span><span class="sxs-lookup"><span data-stu-id="a5b01-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="a5b01-142">Vamos dar uma olhada mais `Startup` profunda na classe na seção [de inicialização](./app-startup.md) do App.</span><span class="sxs-lookup"><span data-stu-id="a5b01-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="a5b01-143">Arquivos estáticos</span><span class="sxs-lookup"><span data-stu-id="a5b01-143">Static files</span></span>

<span data-ttu-id="a5b01-144">Ao contrário ASP.NET projetos web forms, nem todos os arquivos em um projeto Blazor podem ser solicitados como arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="a5b01-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="a5b01-145">Apenas os arquivos na pasta *wwwroot* são endereçados à Web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="a5b01-146">Esta pasta é referida à "raiz web" do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b01-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="a5b01-147">Qualquer coisa fora da raiz da Web do aplicativo *não pode ser* endereçada pela Web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="a5b01-148">Essa configuração fornece um nível adicional de segurança que impede a exposição acidental de arquivos de projeto pela Web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="a5b01-149">Configuração</span><span class="sxs-lookup"><span data-stu-id="a5b01-149">Configuration</span></span>

<span data-ttu-id="a5b01-150">A configuração em ASP.NET aplicativos web Forms é normalmente manuseada usando um ou mais arquivos *web.config.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="a5b01-151">Os aplicativos Blazor normalmente não têm arquivos *web.config.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="a5b01-152">Se o fizerem, o arquivo só será usado para configurar configurações específicas do IIS quando hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="a5b01-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="a5b01-153">Em vez disso, os aplicativos Blazor Server usam as abstrações de configuração ASP.NET Core (os aplicativos Blazor WebAssembly não suportam atualmente as mesmas abstrações de configuração, mas isso pode ser um recurso adicionado no futuro).</span><span class="sxs-lookup"><span data-stu-id="a5b01-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="a5b01-154">Por exemplo, o aplicativo Padrão Blazor Server armazena algumas configurações em *appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="a5b01-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="a5b01-155">Aprenderemos mais sobre configuração em projetos ASP.NET Core na seção [Configuração.](./config.md)</span><span class="sxs-lookup"><span data-stu-id="a5b01-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="a5b01-156">Componentes de navalha</span><span class="sxs-lookup"><span data-stu-id="a5b01-156">Razor components</span></span>

<span data-ttu-id="a5b01-157">A maioria dos arquivos em projetos Blazor são *arquivos .razor.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="a5b01-158">Razor é uma linguagem templating baseada em HTML e C# que é usada para gerar dinamicamente a ui web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="a5b01-159">Os arquivos *.razor* definem componentes que compõem a ui do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b01-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="a5b01-160">Na maioria das vezes, os componentes são idênticos tanto para os aplicativos Blazor Server quanto Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="a5b01-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="a5b01-161">Os componentes em Blazor são análogos aos controles do usuário em ASP.NET Formulários da Web.</span><span class="sxs-lookup"><span data-stu-id="a5b01-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="a5b01-162">Cada arquivo de componente Razor é compilado em uma classe .NET quando o projeto é construído.</span><span class="sxs-lookup"><span data-stu-id="a5b01-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="a5b01-163">A classe gerada captura o estado do componente, renderizando lógica, métodos de ciclo de vida, manipuladores de eventos e outras lógicas.</span><span class="sxs-lookup"><span data-stu-id="a5b01-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="a5b01-164">Vamos analisar os componentes de autoria dos componentes da [ui reutilizável do Edifício com](./components.md) a seção Blazor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="a5b01-165">Os arquivos *_Imports.razor* não são arquivos de componentes do Razor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="a5b01-166">Em vez disso, eles definem um conjunto de diretivas razor para importar em outros arquivos *.razor* dentro da mesma pasta e em suas subpastas.</span><span class="sxs-lookup"><span data-stu-id="a5b01-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="a5b01-167">Por exemplo, um arquivo *_Imports.razor* é `using` uma maneira convencional de adicionar instruções para espaços de nome comumente usados:</span><span class="sxs-lookup"><span data-stu-id="a5b01-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="a5b01-168">Pages (Páginas)</span><span class="sxs-lookup"><span data-stu-id="a5b01-168">Pages</span></span>

<span data-ttu-id="a5b01-169">Onde estão as páginas dos aplicativos Blazor?</span><span class="sxs-lookup"><span data-stu-id="a5b01-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="a5b01-170">O Blazor não define uma extensão de arquivo separada para páginas endereçadas, como os arquivos *.aspx* em ASP.NET aplicativos Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a5b01-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="a5b01-171">Em vez disso, as páginas são definidas atribuindo rotas aos componentes.</span><span class="sxs-lookup"><span data-stu-id="a5b01-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="a5b01-172">Uma rota é tipicamente `@page` atribuída usando a diretiva Razor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="a5b01-173">Por exemplo, `Counter` o componente de autoria no arquivo *Páginas/Counter.razor* define a seguinte rota:</span><span class="sxs-lookup"><span data-stu-id="a5b01-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="a5b01-174">O roteamento em Blazor é tratado do lado do cliente, não do servidor.</span><span class="sxs-lookup"><span data-stu-id="a5b01-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="a5b01-175">À medida que o usuário navega no navegador, o Blazor intercepta a navegação e, em seguida, renderiza o componente com a rota correspondente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="a5b01-176">No momento, as rotas de componentes não são inferidas pelo local de arquivo do componente como se estivessem com páginas *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="a5b01-177">Esse recurso pode ser adicionado no futuro.</span><span class="sxs-lookup"><span data-stu-id="a5b01-177">This feature may be added in the future.</span></span> <span data-ttu-id="a5b01-178">Cada rota deve ser especificada explicitamente no componente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="a5b01-179">Armazenar componentes rotáveis em uma pasta *Páginas* não tem significado especial e é puramente uma convenção.</span><span class="sxs-lookup"><span data-stu-id="a5b01-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="a5b01-180">Vamos olhar com mais detalhes no roteamento em Blazor nas [páginas, roteamento e](./pages-routing-layouts.md) seção de layouts.</span><span class="sxs-lookup"><span data-stu-id="a5b01-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="a5b01-181">Layout</span><span class="sxs-lookup"><span data-stu-id="a5b01-181">Layout</span></span>

<span data-ttu-id="a5b01-182">Em ASP.NET aplicativos web forms, o layout de página comum é manipulado usando*páginas-mestre (Site.Master).*</span><span class="sxs-lookup"><span data-stu-id="a5b01-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="a5b01-183">Nos aplicativos Blazor, o layout da página é manipulado usando componentes de layout *(Compartilhado/MainLayout.razor*).</span><span class="sxs-lookup"><span data-stu-id="a5b01-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="a5b01-184">Os componentes do layout serão discutidos com mais detalhes na seção [Página, roteamento e layouts.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="a5b01-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="a5b01-185">Bootstrap Blazor</span><span class="sxs-lookup"><span data-stu-id="a5b01-185">Bootstrap Blazor</span></span>

<span data-ttu-id="a5b01-186">Para bootstrap Blazor, o aplicativo deve:</span><span class="sxs-lookup"><span data-stu-id="a5b01-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="a5b01-187">Especifique onde na página o componente raiz *(App.Razor)* deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="a5b01-188">Adicione o script de estrutura Blazor correspondente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="a5b01-189">No aplicativo Blazor Server, a página de host do componente raiz é definida no arquivo *_Host.cshtml.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="a5b01-190">Este arquivo define uma página de navalha, não um componente.</span><span class="sxs-lookup"><span data-stu-id="a5b01-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="a5b01-191">As páginas de barbear usam a sintaxe Razor para definir uma página endereçada ao servidor, muito parecida com uma página *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="a5b01-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="a5b01-192">O `Html.RenderComponentAsync<TComponent>(RenderMode)` método é usado para definir onde um componente de nível raiz deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="a5b01-193">A `RenderMode` opção indica a forma como o componente deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="a5b01-194">A tabela a seguir `RenderMode` descreve as opções suportadas.</span><span class="sxs-lookup"><span data-stu-id="a5b01-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="a5b01-195">Opção</span><span class="sxs-lookup"><span data-stu-id="a5b01-195">Option</span></span>                        |<span data-ttu-id="a5b01-196">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5b01-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="a5b01-197">Renderizado interativamente uma vez que uma conexão com o navegador é estabelecida</span><span class="sxs-lookup"><span data-stu-id="a5b01-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="a5b01-198">Primeiro pré-renderizado e, em seguida, renderizado interativamente</span><span class="sxs-lookup"><span data-stu-id="a5b01-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="a5b01-199">Renderizado como conteúdo estático</span><span class="sxs-lookup"><span data-stu-id="a5b01-199">Rendered as static content</span></span>|

<span data-ttu-id="a5b01-200">A referência de script a *_framework/blazor.server.js* estabelece a conexão em tempo real com o servidor e, em seguida, lida com todas as interações do usuário e atualizações de IA.</span><span class="sxs-lookup"><span data-stu-id="a5b01-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="a5b01-201">No aplicativo Blazor WebAssembly, a página host é um arquivo HTML estático simples *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="a5b01-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="a5b01-202">O `<app>` elemento é usado para indicar onde o componente raiz deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="a5b01-203">O componente específico a renderizar é `Startup.Configure` configurado no método do aplicativo com um seletor CSS correspondente indicando onde o componente deve ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="a5b01-204">Saída do build</span><span class="sxs-lookup"><span data-stu-id="a5b01-204">Build output</span></span>

<span data-ttu-id="a5b01-205">Quando um projeto Blazor é construído, todos os arquivos de componente e código Razor são compilados em um único conjunto.</span><span class="sxs-lookup"><span data-stu-id="a5b01-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="a5b01-206">Ao contrário ASP.NET projetos web forms, Blazor não suporta compilação em tempo de execução da lógica da IU.</span><span class="sxs-lookup"><span data-stu-id="a5b01-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="a5b01-207">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="a5b01-207">Run the app</span></span>

<span data-ttu-id="a5b01-208">Para executar o aplicativo Blazor Server, pressione `F5` no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5b01-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="a5b01-209">Os aplicativos Blazor não suportam compilação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a5b01-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="a5b01-210">Para ver os resultados das alterações de marcação de código e componente, reconstrua e reinicie o aplicativo com o depurador conectado.</span><span class="sxs-lookup"><span data-stu-id="a5b01-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="a5b01-211">Se você for executado sem`Ctrl+F5`o depurador conectado (), o Visual Studio assistirá para alterações de arquivo e reiniciará o aplicativo à medida que as alterações forem feitas.</span><span class="sxs-lookup"><span data-stu-id="a5b01-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="a5b01-212">Você atualiza manualmente o navegador à medida que as alterações são feitas.</span><span class="sxs-lookup"><span data-stu-id="a5b01-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="a5b01-213">Para executar o aplicativo Blazor WebAssembly, escolha uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="a5b01-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="a5b01-214">Execute o projeto do cliente diretamente usando o servidor de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a5b01-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="a5b01-215">Execute o projeto do servidor ao hospedar o aplicativo com ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5b01-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="a5b01-216">Os aplicativos Blazor WebAssembly não suportam depuração usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5b01-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="a5b01-217">Para executar o `Ctrl+F5` aplicativo, `F5`use em vez de .</span><span class="sxs-lookup"><span data-stu-id="a5b01-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="a5b01-218">Em vez disso, você pode depurar aplicativos Blazor WebAssembly diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="a5b01-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="a5b01-219">Consulte [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="a5b01-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a5b01-220">[Próximo](hosting-models.md)
>[anterior](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="a5b01-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
