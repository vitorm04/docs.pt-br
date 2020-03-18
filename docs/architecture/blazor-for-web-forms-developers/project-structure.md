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
# <a name="project-structure-for-blazor-apps"></a>Estrutura do projeto para aplicativos Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Apesar de suas diferenças significativas na estrutura do projeto, ASP.NET Web Forms e Blazor compartilham muitos conceitos semelhantes. Aqui, vamos olhar para a estrutura de um projeto Blazor e compará-lo com um projeto ASP.NET Web Forms.

Para criar seu primeiro aplicativo Blazor, siga as instruções no [Blazor iniciando](/aspnet/core/blazor/get-started)os passos . Você pode seguir as instruções para criar um aplicativo Blazor Server ou um aplicativo Blazor WebAssembly hospedado em ASP.NET Core. Com exceção da lógica específica do modelo de hospedagem, a maior parte do código em ambos os projetos é a mesma.

## <a name="project-file"></a>Arquivo de projeto

Os aplicativos Blazor Server são projetos .NET Core. O arquivo de projeto para o aplicativo Blazor Server é o mais simples possível:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

O arquivo de projeto de um aplicativo Blazor WebAssembly parece um pouco mais envolvido (números exatos de versão podem variar):

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

O Blazor WebAssembly projeta o padrão .NET em vez do .NET Core porque eles são executados no navegador em um tempo de execução .NET baseado no WebAssembly. Você não pode instalar o .NET em um navegador da Web como pode em um servidor ou máquina de desenvolvedor. Consequentemente, o projeto faz referência à estrutura blazor utilizando referências individuais de pacotes.

Em comparação, um projeto padrão ASP.NET Web Forms inclui quase 300 linhas de XML em seu arquivo *.csproj,* a maioria das quais está listando explicitamente os vários arquivos de código e conteúdo no projeto. Muitas das simplificações nos projetos baseados em .NET Core e .NET Standard vêm das `Microsoft.NET.Sdk.Web` metas e propriedades padrão importadas por meio de referência ao SDK, muitas vezes referido simplesmente como Web SDK. O Web SDK inclui curingas e outras conveniências que simplificam a inclusão de arquivos de código e conteúdo no projeto. Você não precisa listar os arquivos explicitamente. Ao direcionar o .NET Core, o Web SDK também adiciona referências de estrutura aos frameworks compartilhados .NET Core e ASP.NET Core. As estruturas são visíveis do nó **Dependencies** > **Frameworks** na janela **Solution Explorer.** As estruturas compartilhadas são coleções de conjuntos que foram instalados na máquina ao instalar o .NET Core.

Embora sejam suportadas, referências individuais de montagem são menos comuns em projetos do .NET Core. A maioria das dependências do projeto são tratadas como referências de pacote NuGet. Você só precisa fazer referência a dependências de pacotes de nível superior em projetos .NET Core. Dependências transitivas são incluídas automaticamente. Em vez de usar o arquivo *packages.config* comumente encontrado em ASP.NET projetos da Web Forms `<PackageReference>` para referenciar pacotes, as referências do pacote são adicionadas ao arquivo do projeto usando o elemento.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Ponto de entrada

O ponto de entrada do aplicativo Blazor Server é definido no arquivo *Program.cs,* como você veria em um aplicativo console. Quando o aplicativo é executado, ele cria e executa uma instância de host da Web usando padrões específicos para aplicativos web. O host web gerencia o ciclo de vida do aplicativo Blazor Server e configura serviços de nível host. Exemplos desses serviços são configuração, registro, injeção de dependência e servidor HTTP. Este código é principalmente caldeira e muitas vezes é deixado inalterado.

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

Os aplicativos Blazor WebAssembly também definem um ponto de entrada no *Program.cs*. O código parece um pouco diferente. O código é semelhante na forma de configurar o host do aplicativo para fornecer os mesmos serviços de nível de host para o aplicativo. No entanto, o host do aplicativo WebAssembly não configura um servidor HTTP porque ele é executado diretamente no navegador.

Os aplicativos Blazor têm uma `Startup` classe em vez de um arquivo *Global.asax* para definir a lógica de inicialização do aplicativo. A `Startup` classe é usada para configurar o aplicativo e quaisquer serviços específicos do aplicativo. No aplicativo Blazor Server, a `Startup` classe é usada para configurar o ponto final para a conexão em tempo real usada pelo Blazor entre os navegadores clientes e o servidor. No aplicativo Blazor WebAssembly, a `Startup` classe define os componentes raiz para o aplicativo e onde eles devem ser renderizados. Vamos dar uma olhada mais `Startup` profunda na classe na seção [de inicialização](./app-startup.md) do App.

## <a name="static-files"></a>Arquivos estáticos

Ao contrário ASP.NET projetos web forms, nem todos os arquivos em um projeto Blazor podem ser solicitados como arquivos estáticos. Apenas os arquivos na pasta *wwwroot* são endereçados à Web. Esta pasta é referida à "raiz web" do aplicativo. Qualquer coisa fora da raiz da Web do aplicativo *não pode ser* endereçada pela Web. Essa configuração fornece um nível adicional de segurança que impede a exposição acidental de arquivos de projeto pela Web.

## <a name="configuration"></a>Configuração

A configuração em ASP.NET aplicativos web Forms é normalmente manuseada usando um ou mais arquivos *web.config.* Os aplicativos Blazor normalmente não têm arquivos *web.config.* Se o fizerem, o arquivo só será usado para configurar configurações específicas do IIS quando hospedado no IIS. Em vez disso, os aplicativos Blazor Server usam as abstrações de configuração ASP.NET Core (os aplicativos Blazor WebAssembly não suportam atualmente as mesmas abstrações de configuração, mas isso pode ser um recurso adicionado no futuro). Por exemplo, o aplicativo Padrão Blazor Server armazena algumas configurações em *appsettings.json*.

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

Aprenderemos mais sobre configuração em projetos ASP.NET Core na seção [Configuração.](./config.md)

## <a name="razor-components"></a>Componentes de navalha

A maioria dos arquivos em projetos Blazor são *arquivos .razor.* Razor é uma linguagem templating baseada em HTML e C# que é usada para gerar dinamicamente a ui web. Os arquivos *.razor* definem componentes que compõem a ui do aplicativo. Na maioria das vezes, os componentes são idênticos tanto para os aplicativos Blazor Server quanto Blazor WebAssembly. Os componentes em Blazor são análogos aos controles do usuário em ASP.NET Formulários da Web.

Cada arquivo de componente Razor é compilado em uma classe .NET quando o projeto é construído. A classe gerada captura o estado do componente, renderizando lógica, métodos de ciclo de vida, manipuladores de eventos e outras lógicas. Vamos analisar os componentes de autoria dos componentes da [ui reutilizável do Edifício com](./components.md) a seção Blazor.

Os arquivos *_Imports.razor* não são arquivos de componentes do Razor. Em vez disso, eles definem um conjunto de diretivas razor para importar em outros arquivos *.razor* dentro da mesma pasta e em suas subpastas. Por exemplo, um arquivo *_Imports.razor* é `using` uma maneira convencional de adicionar instruções para espaços de nome comumente usados:

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

## <a name="pages"></a>Pages (Páginas)

Onde estão as páginas dos aplicativos Blazor? O Blazor não define uma extensão de arquivo separada para páginas endereçadas, como os arquivos *.aspx* em ASP.NET aplicativos Web Forms. Em vez disso, as páginas são definidas atribuindo rotas aos componentes. Uma rota é tipicamente `@page` atribuída usando a diretiva Razor. Por exemplo, `Counter` o componente de autoria no arquivo *Páginas/Counter.razor* define a seguinte rota:

```razor
@page "/counter"
```

O roteamento em Blazor é tratado do lado do cliente, não do servidor. À medida que o usuário navega no navegador, o Blazor intercepta a navegação e, em seguida, renderiza o componente com a rota correspondente.

No momento, as rotas de componentes não são inferidas pelo local de arquivo do componente como se estivessem com páginas *.aspx.* Esse recurso pode ser adicionado no futuro. Cada rota deve ser especificada explicitamente no componente. Armazenar componentes rotáveis em uma pasta *Páginas* não tem significado especial e é puramente uma convenção.

Vamos olhar com mais detalhes no roteamento em Blazor nas [páginas, roteamento e](./pages-routing-layouts.md) seção de layouts.

## <a name="layout"></a>Layout

Em ASP.NET aplicativos web forms, o layout de página comum é manipulado usando*páginas-mestre (Site.Master).* Nos aplicativos Blazor, o layout da página é manipulado usando componentes de layout *(Compartilhado/MainLayout.razor*). Os componentes do layout serão discutidos com mais detalhes na seção [Página, roteamento e layouts.](./pages-routing-layouts.md)

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Para bootstrap Blazor, o aplicativo deve:

- Especifique onde na página o componente raiz *(App.Razor)* deve ser renderizado.
- Adicione o script de estrutura Blazor correspondente.

No aplicativo Blazor Server, a página de host do componente raiz é definida no arquivo *_Host.cshtml.* Este arquivo define uma página de navalha, não um componente. As páginas de barbear usam a sintaxe Razor para definir uma página endereçada ao servidor, muito parecida com uma página *.aspx.* O `Html.RenderComponentAsync<TComponent>(RenderMode)` método é usado para definir onde um componente de nível raiz deve ser renderizado. A `RenderMode` opção indica a forma como o componente deve ser renderizado. A tabela a seguir `RenderMode` descreve as opções suportadas.

|Opção                        |Descrição       |
|------------------------------|------------------|
|`RenderMode.Server`           |Renderizado interativamente uma vez que uma conexão com o navegador é estabelecida|
|`RenderMode.ServerPrerendered`|Primeiro pré-renderizado e, em seguida, renderizado interativamente|
|`RenderMode.Static`           |Renderizado como conteúdo estático|

A referência de script a *_framework/blazor.server.js* estabelece a conexão em tempo real com o servidor e, em seguida, lida com todas as interações do usuário e atualizações de IA.

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

No aplicativo Blazor WebAssembly, a página host é um arquivo HTML estático simples *wwwroot/index.html*. O `<app>` elemento é usado para indicar onde o componente raiz deve ser renderizado.

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

O componente específico a renderizar é `Startup.Configure` configurado no método do aplicativo com um seletor CSS correspondente indicando onde o componente deve ser renderizado.

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

## <a name="build-output"></a>Saída do build

Quando um projeto Blazor é construído, todos os arquivos de componente e código Razor são compilados em um único conjunto. Ao contrário ASP.NET projetos web forms, Blazor não suporta compilação em tempo de execução da lógica da IU.

## <a name="run-the-app"></a>Executar o aplicativo

Para executar o aplicativo Blazor Server, pressione `F5` no Visual Studio. Os aplicativos Blazor não suportam compilação em tempo de execução. Para ver os resultados das alterações de marcação de código e componente, reconstrua e reinicie o aplicativo com o depurador conectado. Se você for executado sem`Ctrl+F5`o depurador conectado (), o Visual Studio assistirá para alterações de arquivo e reiniciará o aplicativo à medida que as alterações forem feitas. Você atualiza manualmente o navegador à medida que as alterações são feitas.

Para executar o aplicativo Blazor WebAssembly, escolha uma das seguintes abordagens:

- Execute o projeto do cliente diretamente usando o servidor de desenvolvimento.
- Execute o projeto do servidor ao hospedar o aplicativo com ASP.NET Core.

Os aplicativos Blazor WebAssembly não suportam depuração usando o Visual Studio. Para executar o `Ctrl+F5` aplicativo, `F5`use em vez de . Em vez disso, você pode depurar aplicativos Blazor WebAssembly diretamente no navegador. Consulte [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) para obter detalhes.

>[!div class="step-by-step"]
>[Próximo](hosting-models.md)
>[anterior](app-startup.md)
