---
title: Configuração do aplicativo
description: Aprenda a configurar aplicativos Blazor sem usar o ConfigurationManager.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588242"
---
# <a name="app-configuration"></a><span data-ttu-id="c09ef-103">Configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c09ef-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c09ef-104">A principal maneira de carregar a configuração do aplicativo no&mdash;Web Forms é com entradas no arquivo *Web.config* no servidor ou em um arquivo de configuração relacionado referenciado por *web.config*. Você pode usar `ConfigurationManager` o objeto estático para interagir com as configurações do aplicativo, as strings de conexão do repositório de dados e outros provedores de configuração estendida que são adicionados ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="c09ef-105">É típico ver interações com a configuração do aplicativo como visto no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c09ef-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="c09ef-106">Com ASP.NET Core e o Lado do Servidor Blazor, o arquivo *web.config* pode estar presente se o seu aplicativo estiver hospedado em um servidor Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="c09ef-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="c09ef-107">No entanto, `ConfigurationManager` não há interação com essa configuração, e você pode receber configuração de aplicativo mais estruturada de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="c09ef-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="c09ef-108">Vamos dar uma olhada em como a configuração é coletada e como você ainda pode acessar informações de configuração a partir de um arquivo *web.config.*</span><span class="sxs-lookup"><span data-stu-id="c09ef-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="c09ef-109">Fontes de configuração</span><span class="sxs-lookup"><span data-stu-id="c09ef-109">Configuration sources</span></span>

<span data-ttu-id="c09ef-110">ASP.NET Core reconhece que existem muitas fontes de configuração que você pode querer usar para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="c09ef-111">O framework tenta oferecer o melhor desses recursos por padrão.</span><span class="sxs-lookup"><span data-stu-id="c09ef-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="c09ef-112">A configuração é lida e agregada a partir dessas várias fontes pelo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c09ef-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="c09ef-113">Valores carregados posteriormente para a mesma chave de configuração têm precedência sobre valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="c09ef-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="c09ef-114">ASP.NET Core foi projetado para ter reconhecimento na nuvem e facilitar a configuração de aplicativos tanto para operadores quanto para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="c09ef-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="c09ef-115">ASP.NET Core é ambientalmente consciente e sabe `Production` se `Development` está funcionando em seu ambiente ou em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="c09ef-116">O indicador de ambiente `ASPNETCORE_ENVIRONMENT` é definido na variável ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="c09ef-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="c09ef-117">Se nenhum valor for configurado, o aplicativo `Production` não será executado no ambiente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="c09ef-118">Seu aplicativo pode acionar e adicionar configuração de várias fontes com base no nome do ambiente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="c09ef-119">Por padrão, a configuração é carregada a partir dos seguintes recursos na ordem listada:</span><span class="sxs-lookup"><span data-stu-id="c09ef-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="c09ef-120">*appsettings.json* arquivo, se presente</span><span class="sxs-lookup"><span data-stu-id="c09ef-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="c09ef-121">*ajustes. {ENVIRONMENT_NAME}.json,* se presente</span><span class="sxs-lookup"><span data-stu-id="c09ef-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="c09ef-122">Arquivo de segredos do usuário em disco, se presente</span><span class="sxs-lookup"><span data-stu-id="c09ef-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="c09ef-123">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="c09ef-123">Environment variables</span></span>
1. <span data-ttu-id="c09ef-124">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="c09ef-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="c09ef-125">appsettings.json formato e acesso</span><span class="sxs-lookup"><span data-stu-id="c09ef-125">appsettings.json format and access</span></span>

<span data-ttu-id="c09ef-126">O arquivo *appsettings.json* pode ser hierárquico com valores estruturados como o seguinte JSON:</span><span class="sxs-lookup"><span data-stu-id="c09ef-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="c09ef-127">Quando apresentado com o JSON anterior, o sistema de configuração achata os valores da criança e faz referência aos seus caminhos hierárquicos totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="c09ef-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="c09ef-128">Um caractere`:`de cólon separa cada propriedade na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="c09ef-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="c09ef-129">Por exemplo, a `section1:key0` chave `section1` de configuração `key0` acessa o valor do objeto literal.</span><span class="sxs-lookup"><span data-stu-id="c09ef-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="c09ef-130">Segredos do usuário</span><span class="sxs-lookup"><span data-stu-id="c09ef-130">User secrets</span></span>

<span data-ttu-id="c09ef-131">Os segredos do usuário são:</span><span class="sxs-lookup"><span data-stu-id="c09ef-131">User secrets are:</span></span>

* <span data-ttu-id="c09ef-132">Valores de configuração armazenados em um arquivo JSON na estação de trabalho do desenvolvedor, fora da pasta de desenvolvimento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="c09ef-133">Só é carregado quando `Development` executado no ambiente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="c09ef-134">Associado a um aplicativo específico.</span><span class="sxs-lookup"><span data-stu-id="c09ef-134">Associated with a specific app.</span></span>
* <span data-ttu-id="c09ef-135">Gerenciado com o `user-secrets` comando .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="c09ef-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="c09ef-136">Configure seu aplicativo para armazenamento `user-secrets` de segredos executando o comando:</span><span class="sxs-lookup"><span data-stu-id="c09ef-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="c09ef-137">O comando anterior `UserSecretsId` adiciona um elemento ao arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="c09ef-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="c09ef-138">O elemento contém um GUID, que é usado para associar segredos com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="c09ef-139">Você pode então definir `set` um segredo com o comando.</span><span class="sxs-lookup"><span data-stu-id="c09ef-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="c09ef-140">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="c09ef-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="c09ef-141">O comando anterior `Parent:ApiKey` disponibiliza a chave de configuração `12345`na estação de trabalho de um desenvolvedor com o valor .</span><span class="sxs-lookup"><span data-stu-id="c09ef-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="c09ef-142">Para obter mais informações sobre como criar, armazenar e gerenciar segredos de usuários, consulte o armazenamento seguro de segredos de aplicativos em desenvolvimento em ASP.NET documento [Core.](/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="c09ef-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="c09ef-143">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="c09ef-143">Environment variables</span></span>

<span data-ttu-id="c09ef-144">O próximo conjunto de valores carregados na configuração do aplicativo são as variáveis de ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="c09ef-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="c09ef-145">Todas as configurações de variáveis de ambiente do seu sistema estão agora acessíveis a você através da API de configuração.</span><span class="sxs-lookup"><span data-stu-id="c09ef-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="c09ef-146">Valores hierárquicos são achatados e separados por caracteres de cólon quando lidos dentro do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="c09ef-147">No entanto, alguns sistemas operacionais não permitem nomes de variáveis de ambiente de caracteres de cólon.</span><span class="sxs-lookup"><span data-stu-id="c09ef-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="c09ef-148">ASP.NET Core aborda essa limitação convertendo valores que têm sublinhados duplos ()`__`em um cólon quando são acessados.</span><span class="sxs-lookup"><span data-stu-id="c09ef-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="c09ef-149">O `Parent:ApiKey` valor da seção segredos do usuário acima `Parent__ApiKey`pode ser substituído com a variável ambiente .</span><span class="sxs-lookup"><span data-stu-id="c09ef-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="c09ef-150">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="c09ef-150">Command-line arguments</span></span>

<span data-ttu-id="c09ef-151">A configuração também pode ser fornecida como argumentos de linha de comando quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="c09ef-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="c09ef-152">Use a notação`--`de duplo traço`/`() ou forward-slash ( ) para indicar o nome do valor de configuração a definir e o valor a ser configurado.</span><span class="sxs-lookup"><span data-stu-id="c09ef-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="c09ef-153">A sintaxe se assemelha aos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="c09ef-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="c09ef-154">O retorno do web.config</span><span class="sxs-lookup"><span data-stu-id="c09ef-154">The return of web.config</span></span>

<span data-ttu-id="c09ef-155">Se você implantou seu aplicativo no Windows no IIS, o arquivo *web.config* ainda configura o IIS para gerenciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="c09ef-156">Por padrão, o IIS adiciona uma referência ao ASP.NET Módulo Núcleo (ANCM).</span><span class="sxs-lookup"><span data-stu-id="c09ef-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="c09ef-157">ANCM é um módulo IIS nativo que hospeda seu aplicativo no lugar do servidor web Kestrel.</span><span class="sxs-lookup"><span data-stu-id="c09ef-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="c09ef-158">Esta seção *web.config* se assemelha à seguinte marcação XML:</span><span class="sxs-lookup"><span data-stu-id="c09ef-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="c09ef-159">A configuração específica do aplicativo `environmentVariables` pode ser `aspNetCore` definida aninhando um elemento no elemento.</span><span class="sxs-lookup"><span data-stu-id="c09ef-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="c09ef-160">Os valores definidos nesta seção são apresentados ao aplicativo ASP.NET Core como variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="c09ef-161">As variáveis de ambiente carregam adequadamente durante esse segmento de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c09ef-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="c09ef-162">Leia a configuração no aplicativo</span><span class="sxs-lookup"><span data-stu-id="c09ef-162">Read configuration in the app</span></span>

<span data-ttu-id="c09ef-163">ASP.NET Core fornece a <xref:Microsoft.Extensions.Configuration.IConfiguration> configuração do aplicativo através da interface.</span><span class="sxs-lookup"><span data-stu-id="c09ef-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="c09ef-164">Esta interface de configuração deve ser solicitada por seus componentes Blazor, páginas Blazor e qualquer outra ASP.NET classe gerenciada pelo Core que precise de acesso à configuração.</span><span class="sxs-lookup"><span data-stu-id="c09ef-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="c09ef-165">A estrutura ASP.NET Core preencherá automaticamente essa interface com a configuração resolvida configurada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c09ef-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="c09ef-166">Em uma página blazor ou na marcação Razor `IConfiguration` de um `@inject` componente, você pode injetar o objeto com uma diretiva na parte superior do arquivo *.razor* como este:</span><span class="sxs-lookup"><span data-stu-id="c09ef-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="c09ef-167">Esta declaração `IConfiguration` anterior torna `Configuration` o objeto disponível como a variável em todo o resto do modelo Razor.</span><span class="sxs-lookup"><span data-stu-id="c09ef-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="c09ef-168">As configurações individuais podem ser lidas especificando a hierarquia de configuração procurada como parâmetro de indexador:</span><span class="sxs-lookup"><span data-stu-id="c09ef-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="c09ef-169">Você pode buscar seções de <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> configuração inteiras usando o método para recuperar uma `GetSection("section1")` coleção de chaves em um local específico com uma sintaxe semelhante a recuperar a configuração para a seção1 do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="c09ef-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="c09ef-170">Configuração fortemente digitada</span><span class="sxs-lookup"><span data-stu-id="c09ef-170">Strongly typed configuration</span></span>

<span data-ttu-id="c09ef-171">Com o Web Forms, foi possível criar um tipo de <xref:System.Configuration.ConfigurationSection> configuração fortemente digitado que herdou do tipo e tipos associados.</span><span class="sxs-lookup"><span data-stu-id="c09ef-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="c09ef-172">A `ConfigurationSection` permitiu configurar algumas regras de negócios e processamento para esses valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="c09ef-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="c09ef-173">Em ASP.NET Core, você pode especificar uma hierarquia de classe que receberá os valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="c09ef-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="c09ef-174">Estas classes:</span><span class="sxs-lookup"><span data-stu-id="c09ef-174">These classes:</span></span>

* <span data-ttu-id="c09ef-175">Não precisa herdar de uma classe de pais.</span><span class="sxs-lookup"><span data-stu-id="c09ef-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="c09ef-176">Deve `public` incluir propriedades que correspondam às propriedades e referências de tipo para a estrutura de configuração que você deseja capturar.</span><span class="sxs-lookup"><span data-stu-id="c09ef-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="c09ef-177">Para a amostra de *appsettings.json* anterior, você pode definir as seguintes classes para capturar os valores:</span><span class="sxs-lookup"><span data-stu-id="c09ef-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="c09ef-178">Esta hierarquia de classe pode ser preenchida adicionando a seguinte linha ao `Startup.ConfigureServices` método:</span><span class="sxs-lookup"><span data-stu-id="c09ef-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="c09ef-179">No resto do aplicativo, você pode adicionar um parâmetro `@inject` de entrada às `IOptions<MyConfig>` classes ou uma diretiva em modelos de tipo Razor para receber as configurações fortemente digitadas.</span><span class="sxs-lookup"><span data-stu-id="c09ef-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="c09ef-180">A `IOptions<MyConfig>.Value` propriedade produzirá o `MyConfig` valor preenchido a partir das configurações.</span><span class="sxs-lookup"><span data-stu-id="c09ef-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="c09ef-181">Mais informações sobre o recurso Opções podem ser encontradas no [padrão Opções no](/aspnet/core/fundamentals/configuration/options#options-interfaces) documento ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c09ef-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c09ef-182">[Próximo](middleware.md)
>[anterior](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="c09ef-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
