---
title: Configuração do aplicativo
description: Saiba como configurar Blazor aplicativos sem usar ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173296"
---
# <a name="app-configuration"></a><span data-ttu-id="aee07-103">Configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="aee07-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="aee07-104">A principal maneira de carregar a configuração de aplicativo no Web Forms é com entradas no arquivo *web.config* &mdash; no servidor ou em um arquivo de configuração relacionado referenciado por *web.config*. Você pode usar o `ConfigurationManager` objeto estático para interagir com as configurações do aplicativo, cadeias de conexão do repositório de dados e outros provedores de configuração estendidos que são adicionados ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="aee07-105">É comum ver interações com a configuração do aplicativo, como visto no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="aee07-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="aee07-106">Com ASP.NET Core e servidor Blazor , o arquivo de *web.config* pode estar presente se seu aplicativo estiver hospedado em um servidor IIS do Windows.</span><span class="sxs-lookup"><span data-stu-id="aee07-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="aee07-107">No entanto, não há nenhuma `ConfigurationManager` interação com essa configuração, e você pode receber mais configurações de aplicativo estruturado de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="aee07-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="aee07-108">Vamos dar uma olhada em como a configuração é coletada e como você ainda pode acessar as informações de configuração de um arquivo *web.config* .</span><span class="sxs-lookup"><span data-stu-id="aee07-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="aee07-109">Fontes de configuração</span><span class="sxs-lookup"><span data-stu-id="aee07-109">Configuration sources</span></span>

<span data-ttu-id="aee07-110">ASP.NET Core reconhece que há muitas fontes de configuração que você pode querer usar para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="aee07-111">A estrutura tenta oferecer o melhor desses recursos por padrão.</span><span class="sxs-lookup"><span data-stu-id="aee07-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="aee07-112">A configuração é lida e agregada dessas várias fontes por ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee07-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="aee07-113">Os valores carregados posteriormente para a mesma chave de configuração têm precedência sobre os valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="aee07-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="aee07-114">A ASP.NET Core foi projetada para ser compatível com a nuvem e para facilitar a configuração de aplicativos para operadores e desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="aee07-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="aee07-115">ASP.NET Core tem reconhecimento de ambiente e sabe se ele está em execução no `Production` seu `Development` ambiente ou.</span><span class="sxs-lookup"><span data-stu-id="aee07-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="aee07-116">O indicador de ambiente é definido na `ASPNETCORE_ENVIRONMENT` variável de ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="aee07-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="aee07-117">Se nenhum valor for configurado, o aplicativo usa como padrão a execução no `Production` ambiente.</span><span class="sxs-lookup"><span data-stu-id="aee07-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="aee07-118">Seu aplicativo pode disparar e adicionar a configuração de várias fontes com base no nome do ambiente.</span><span class="sxs-lookup"><span data-stu-id="aee07-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="aee07-119">Por padrão, a configuração é carregada dos seguintes recursos na ordem listada:</span><span class="sxs-lookup"><span data-stu-id="aee07-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="aee07-120">*appsettings.jsno* arquivo, se presente</span><span class="sxs-lookup"><span data-stu-id="aee07-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="aee07-121">*appSettings. Arquivo {ENVIRONMENT_NAME}. JSON* , se presente</span><span class="sxs-lookup"><span data-stu-id="aee07-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="aee07-122">Arquivo de segredos do usuário em disco, se presente</span><span class="sxs-lookup"><span data-stu-id="aee07-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="aee07-123">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="aee07-123">Environment variables</span></span>
1. <span data-ttu-id="aee07-124">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="aee07-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="aee07-125">appsettings.jsno formato e acesso</span><span class="sxs-lookup"><span data-stu-id="aee07-125">appsettings.json format and access</span></span>

<span data-ttu-id="aee07-126">O *appsettings.jsno* arquivo pode ser hierárquico com valores estruturados como o JSON a seguir:</span><span class="sxs-lookup"><span data-stu-id="aee07-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

<span data-ttu-id="aee07-127">Quando apresentado com o JSON anterior, o sistema de configuração mescla valores filho e faz referência a seus caminhos hierárquicos totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="aee07-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="aee07-128">Um caractere de dois-pontos ( `:` ) separa cada propriedade na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="aee07-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="aee07-129">Por exemplo, a chave de configuração `section1:key0` acessa o `section1` valor do literal do objeto `key0` .</span><span class="sxs-lookup"><span data-stu-id="aee07-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="aee07-130">Segredos do usuário</span><span class="sxs-lookup"><span data-stu-id="aee07-130">User secrets</span></span>

<span data-ttu-id="aee07-131">Os segredos do usuário são:</span><span class="sxs-lookup"><span data-stu-id="aee07-131">User secrets are:</span></span>

* <span data-ttu-id="aee07-132">Valores de configuração que são armazenados em um arquivo JSON na estação de trabalho do desenvolvedor, fora da pasta de desenvolvimento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="aee07-133">Carregado somente quando executado no `Development` ambiente.</span><span class="sxs-lookup"><span data-stu-id="aee07-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="aee07-134">Associado a um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="aee07-134">Associated with a specific app.</span></span>
* <span data-ttu-id="aee07-135">Gerenciado com o comando do CLI do .NET Core `user-secrets` .</span><span class="sxs-lookup"><span data-stu-id="aee07-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="aee07-136">Configure seu aplicativo para o armazenamento de segredos executando o `user-secrets` comando:</span><span class="sxs-lookup"><span data-stu-id="aee07-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="aee07-137">O comando anterior adiciona um `UserSecretsId` elemento ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="aee07-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="aee07-138">O elemento contém um GUID, que é usado para associar segredos ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="aee07-139">Em seguida, você pode definir um segredo com o `set` comando.</span><span class="sxs-lookup"><span data-stu-id="aee07-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="aee07-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aee07-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="aee07-141">O comando anterior disponibiliza a `Parent:ApiKey` chave de configuração na estação de trabalho de um desenvolvedor com o valor `12345` .</span><span class="sxs-lookup"><span data-stu-id="aee07-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="aee07-142">Para obter mais informações sobre como criar, armazenar e gerenciar segredos do usuário, consulte o [armazenamento seguro de segredos do aplicativo em desenvolvimento no ASP.NET Core](/aspnet/core/security/app-secrets) documento.</span><span class="sxs-lookup"><span data-stu-id="aee07-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="aee07-143">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="aee07-143">Environment variables</span></span>

<span data-ttu-id="aee07-144">O próximo conjunto de valores carregados em sua configuração de aplicativo são as variáveis de ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="aee07-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="aee07-145">Todas as configurações de variável de ambiente do seu sistema agora estão acessíveis para você por meio da API de configuração.</span><span class="sxs-lookup"><span data-stu-id="aee07-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="aee07-146">Os valores hierárquicos são achatados e separados por caracteres de dois-pontos quando lidos dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="aee07-147">No entanto, alguns sistemas operacionais não permitem os nomes de variável de ambiente de caractere de dois pontos.</span><span class="sxs-lookup"><span data-stu-id="aee07-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="aee07-148">ASP.NET Core resolve essa limitação convertendo valores que têm sublinhados duplos ( `__` ) em dois pontos quando eles são acessados.</span><span class="sxs-lookup"><span data-stu-id="aee07-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="aee07-149">O `Parent:ApiKey` valor da seção segredos do usuário acima pode ser substituído pela variável de ambiente `Parent__ApiKey` .</span><span class="sxs-lookup"><span data-stu-id="aee07-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="aee07-150">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="aee07-150">Command-line arguments</span></span>

<span data-ttu-id="aee07-151">A configuração também pode ser fornecida como argumentos de linha de comando quando seu aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="aee07-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="aee07-152">Use a notação de traço duplo ( `--` ) ou de barra ( `/` ) para indicar o nome do valor de configuração a ser definido e o valor a ser configurado.</span><span class="sxs-lookup"><span data-stu-id="aee07-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="aee07-153">A sintaxe é semelhante aos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="aee07-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="aee07-154">O retorno de web.config</span><span class="sxs-lookup"><span data-stu-id="aee07-154">The return of web.config</span></span>

<span data-ttu-id="aee07-155">Se você tiver implantado seu aplicativo no Windows no IIS, o arquivo de *web.config* ainda configurará o IIS para gerenciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="aee07-156">Por padrão, o IIS adiciona uma referência ao módulo de ASP.NET Core (ANCM).</span><span class="sxs-lookup"><span data-stu-id="aee07-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="aee07-157">ANCM é um módulo do IIS nativo que hospeda seu aplicativo no lugar do servidor Web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="aee07-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="aee07-158">Esta seção *web.config* é semelhante à marcação XML a seguir:</span><span class="sxs-lookup"><span data-stu-id="aee07-158">This *web.config* section resembles the following XML markup:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

<span data-ttu-id="aee07-159">A configuração específica do aplicativo pode ser definida aninhando-se um `environmentVariables` elemento no `aspNetCore` elemento.</span><span class="sxs-lookup"><span data-stu-id="aee07-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="aee07-160">Os valores definidos nesta seção são apresentados ao aplicativo ASP.NET Core como variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="aee07-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="aee07-161">As variáveis de ambiente são carregadas adequadamente durante o segmento de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aee07-161">The environment variables load appropriately during that segment of app startup.</span></span>

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="aee07-162">Ler a configuração no aplicativo</span><span class="sxs-lookup"><span data-stu-id="aee07-162">Read configuration in the app</span></span>

<span data-ttu-id="aee07-163">ASP.NET Core fornece a configuração de aplicativo por meio da <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span><span class="sxs-lookup"><span data-stu-id="aee07-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="aee07-164">Essa interface de configuração deve ser solicitada por seus Blazor componentes, Blazor páginas e qualquer outra classe gerenciada ASP.NET Core que precise de acesso à configuração.</span><span class="sxs-lookup"><span data-stu-id="aee07-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="aee07-165">A estrutura de ASP.NET Core preencherá automaticamente essa interface com a configuração resolvida configurada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="aee07-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="aee07-166">Em uma Blazor página ou marcação Razor de um componente, você pode injetar o `IConfiguration` objeto com uma `@inject` diretiva na parte superior do arquivo *. Razor* como este:</span><span class="sxs-lookup"><span data-stu-id="aee07-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="aee07-167">Essa instrução anterior torna o `IConfiguration` objeto disponível como a `Configuration` variável em todo o restante do modelo Razor.</span><span class="sxs-lookup"><span data-stu-id="aee07-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="aee07-168">As definições de configuração individuais podem ser lidas especificando-se a hierarquia de definição de configuração procurada como um parâmetro de indexador:</span><span class="sxs-lookup"><span data-stu-id="aee07-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="aee07-169">Você pode buscar seções de configuração inteiras usando o <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> método para recuperar uma coleção de chaves em um local específico com uma sintaxe semelhante a para `GetSection("section1")` recuperar a configuração de section1 do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="aee07-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="aee07-170">Configuração com rigidez de tipos</span><span class="sxs-lookup"><span data-stu-id="aee07-170">Strongly typed configuration</span></span>

<span data-ttu-id="aee07-171">Com Web Forms, era possível criar um tipo de configuração fortemente tipado herdado do <xref:System.Configuration.ConfigurationSection> tipo e dos tipos associados.</span><span class="sxs-lookup"><span data-stu-id="aee07-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="aee07-172">Um `ConfigurationSection` permitia que você configure algumas regras de negócio e o processamento para esses valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="aee07-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="aee07-173">No ASP.NET Core, você pode especificar uma hierarquia de classe que receberá os valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="aee07-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="aee07-174">Essas classes:</span><span class="sxs-lookup"><span data-stu-id="aee07-174">These classes:</span></span>

* <span data-ttu-id="aee07-175">Não é necessário herdar de uma classe pai.</span><span class="sxs-lookup"><span data-stu-id="aee07-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="aee07-176">Deve incluir `public` Propriedades que correspondam às propriedades e referências de tipo para a estrutura de configuração que você deseja capturar.</span><span class="sxs-lookup"><span data-stu-id="aee07-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="aee07-177">Para o *appsettings.jsanterior no* exemplo, você pode definir as seguintes classes para capturar os valores:</span><span class="sxs-lookup"><span data-stu-id="aee07-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

<span data-ttu-id="aee07-178">Essa hierarquia de classe pode ser populada adicionando a seguinte linha ao `Startup.ConfigureServices` método:</span><span class="sxs-lookup"><span data-stu-id="aee07-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="aee07-179">No restante do aplicativo, você pode adicionar um parâmetro de entrada a classes ou uma `@inject` diretiva em modelos do Razor do tipo `IOptions<MyConfig>` para receber as definições de configuração com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="aee07-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="aee07-180">A `IOptions<MyConfig>.Value` Propriedade produzirá o `MyConfig` valor populado a partir das definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="aee07-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="aee07-181">Mais informações sobre o recurso de opções podem ser encontradas no [padrão de opções no documento ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) .</span><span class="sxs-lookup"><span data-stu-id="aee07-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="aee07-182">[Anterior](middleware.md) 
> [Avançar](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="aee07-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
