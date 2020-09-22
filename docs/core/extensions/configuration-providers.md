---
title: Provedores de configuração no .NET
description: Saiba como a API do provedor de configuração é usada para configurar aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.openlocfilehash: d5333e8e52feb7d28e2149a988dc7ce53a926a50
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874747"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="596d3-103">Provedores de configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="596d3-103">Configuration providers in .NET</span></span>

<span data-ttu-id="596d3-104">A configuração no .NET é possível com provedores de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="596d3-105">Há vários tipos de provedores que dependem de várias fontes de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="596d3-106">Este artigo fornece detalhes sobre todos os diferentes provedores de configuração e suas fontes correspondentes.</span><span class="sxs-lookup"><span data-stu-id="596d3-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="596d3-107">Provedor de configuração de arquivo</span><span class="sxs-lookup"><span data-stu-id="596d3-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="596d3-108">Provedor de configuração de variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="596d3-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="596d3-109">Provedor de configuração de linha de comando</span><span class="sxs-lookup"><span data-stu-id="596d3-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="596d3-110">Provedor de configuração de chave por arquivo</span><span class="sxs-lookup"><span data-stu-id="596d3-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="596d3-111">Provedor de configuração de memória</span><span class="sxs-lookup"><span data-stu-id="596d3-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="596d3-112">Provedor de configuração de arquivo</span><span class="sxs-lookup"><span data-stu-id="596d3-112">File configuration provider</span></span>

<span data-ttu-id="596d3-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> é a classe base para carregamento da configuração do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="596d3-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="596d3-114">Os seguintes provedores de configuração derivam de `FileConfigurationProvider` :</span><span class="sxs-lookup"><span data-stu-id="596d3-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="596d3-115">Provedor de configuração JSON</span><span class="sxs-lookup"><span data-stu-id="596d3-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="596d3-116">Provedor de configuração XML</span><span class="sxs-lookup"><span data-stu-id="596d3-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="596d3-117">Provedor de configuração INI</span><span class="sxs-lookup"><span data-stu-id="596d3-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="596d3-118">Provedor de configuração JSON</span><span class="sxs-lookup"><span data-stu-id="596d3-118">JSON configuration provider</span></span>

<span data-ttu-id="596d3-119">A <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> classe carrega a configuração de um arquivo JSON.</span><span class="sxs-lookup"><span data-stu-id="596d3-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="596d3-120">Instale o [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="596d3-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="596d3-121">Sobrecargas podem especificar:</span><span class="sxs-lookup"><span data-stu-id="596d3-121">Overloads can specify:</span></span>

- <span data-ttu-id="596d3-122">Se o arquivo é opcional</span><span class="sxs-lookup"><span data-stu-id="596d3-122">Whether the file is optional</span></span>
- <span data-ttu-id="596d3-123">Se a configuração será recarregada se o arquivo for alterado</span><span class="sxs-lookup"><span data-stu-id="596d3-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="596d3-124">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="596d3-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-33,37-38" highlight="17-23":::

<span data-ttu-id="596d3-125">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="596d3-125">The preceding code:</span></span>

- <span data-ttu-id="596d3-126">Limpa todos os provedores de configuração existentes que foram adicionados por padrão no <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> método.</span><span class="sxs-lookup"><span data-stu-id="596d3-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="596d3-127">Configura o provedor de configuração JSON para carregar o *appsettings.js* e  *appSettings*. `Environment` . arquivos *JSON* com as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="596d3-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="596d3-128">`optional: true`: O arquivo é opcional.</span><span class="sxs-lookup"><span data-stu-id="596d3-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="596d3-129">`reloadOnChange: true` : O arquivo é recarregado quando as alterações são salvas.</span><span class="sxs-lookup"><span data-stu-id="596d3-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="596d3-130">As configurações de JSON são substituídas pelas configurações no [provedor de configuração de variáveis de ambiente](#environment-variable-configuration-provider) e no provedor de configuração de linha de [comando](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="596d3-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="596d3-131">Segue um exemplo *appsettings.jsno* arquivo com várias definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="596d3-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="596d3-132">Na <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instância, após a adição de provedores de configuração, você pode chamar <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> para obter o <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> objeto.</span><span class="sxs-lookup"><span data-stu-id="596d3-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="596d3-133">A raiz de configuração representa a raiz de uma hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="596d3-134">As seções da configuração podem ser associadas a instâncias de objetos .NET e, posteriormente, fornecidas como <xref:Microsoft.Extensions.Options.IOptions%601> por meio de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="596d3-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="596d3-135">Considere o `TransientFaultHandlingOptions` tipo de registro definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="596d3-135">Consider the `TransientFaultHandlingOptions` record type defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="596d3-136">Para obter informações sobre tipos de registro, consulte [tipos de registro em C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="596d3-136">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="596d3-137">O código a seguir cria a raiz de configuração, associa uma seção ao `TransientFaultHandlingOptions` tipo de registro e imprime os valores associados na janela do console:</span><span class="sxs-lookup"><span data-stu-id="596d3-137">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` record type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

<span data-ttu-id="596d3-138">O aplicativo gravaria a seguinte saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="596d3-138">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="34-36":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="596d3-139">Provedor de configuração XML</span><span class="sxs-lookup"><span data-stu-id="596d3-139">XML configuration provider</span></span>

<span data-ttu-id="596d3-140">A <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> classe carrega a configuração de um arquivo XML em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="596d3-140">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="596d3-141">Instale o [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="596d3-141">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="596d3-142">O código a seguir demonstra a configuração de arquivos XML usando o provedor de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="596d3-142">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-28,46,52-53" highlight="17-28":::

<span data-ttu-id="596d3-143">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="596d3-143">The preceding code:</span></span>

- <span data-ttu-id="596d3-144">Limpa todos os provedores de configuração existentes que foram adicionados por padrão no <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> método.</span><span class="sxs-lookup"><span data-stu-id="596d3-144">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="596d3-145">Configura o provedor de configuração XML para carregar os arquivos de *appsettings.xml* e *repeating-example.xml* com as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="596d3-145">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="596d3-146">`optional: true`: O arquivo é opcional.</span><span class="sxs-lookup"><span data-stu-id="596d3-146">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="596d3-147">`reloadOnChange: true` : O arquivo é recarregado quando as alterações são salvas.</span><span class="sxs-lookup"><span data-stu-id="596d3-147">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="596d3-148">Configura o provedor de configuração de variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="596d3-148">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="596d3-149">Configura o provedor de configuração de linha de comando se os `args` argumentos Contains especificados.</span><span class="sxs-lookup"><span data-stu-id="596d3-149">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="596d3-150">As configurações de XML são substituídas pelas configurações no [provedor de configuração de variáveis de ambiente](#environment-variable-configuration-provider) e no provedor de configuração de linha de [comando](#command-line-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="596d3-150">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="596d3-151">Segue um exemplo *appsettings.xml* arquivo com várias definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="596d3-151">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="596d3-152">Elementos repetidos que usam o mesmo nome de elemento funcionarão se o atributo `name` for usado para diferenciar os elementos:</span><span class="sxs-lookup"><span data-stu-id="596d3-152">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="596d3-153">O código a seguir lê o arquivo de configuração anterior e exibe as chaves e valores:</span><span class="sxs-lookup"><span data-stu-id="596d3-153">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="30-45":::

<span data-ttu-id="596d3-154">O aplicativo gravaria a seguinte saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="596d3-154">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="47-51":::

<span data-ttu-id="596d3-155">É possível usar atributos para fornecer valores:</span><span class="sxs-lookup"><span data-stu-id="596d3-155">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="596d3-156">O arquivo de configuração anterior carrega as seguintes chaves com `value`:</span><span class="sxs-lookup"><span data-stu-id="596d3-156">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="596d3-157">Provedor de configuração INI</span><span class="sxs-lookup"><span data-stu-id="596d3-157">INI configuration provider</span></span>

<span data-ttu-id="596d3-158">A <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> classe carrega a configuração de um arquivo ini em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="596d3-158">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="596d3-159">Instale o [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="596d3-159">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="596d3-160">O código a seguir limpa todos os provedores de configuração e adiciona o `IniConfigurationProvider` com dois arquivos ini como a origem:</span><span class="sxs-lookup"><span data-stu-id="596d3-160">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-31,38-39" highlight="18-24":::

<span data-ttu-id="596d3-161">Segue um exemplo *appsettings.ini* arquivo com várias definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="596d3-161">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="596d3-162">O código a seguir exibe as definições de configuração anteriores, gravando-as na janela do console:</span><span class="sxs-lookup"><span data-stu-id="596d3-162">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="26-30":::

<span data-ttu-id="596d3-163">O aplicativo gravaria a seguinte saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="596d3-163">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-37":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="596d3-164">Provedor de configuração de variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="596d3-164">Environment variable configuration provider</span></span>

<span data-ttu-id="596d3-165">Usando a configuração padrão, o <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> carrega a configuração de pares chave-valor da variável de ambiente depois de ler *appsettings.jsem*, *appSettings.* `Environment` *. JSON*e o Gerenciador de segredo.</span><span class="sxs-lookup"><span data-stu-id="596d3-165">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="596d3-166">Portanto, os valores de chave lidos dos valores de substituição de ambiente lidos de *appsettings.jsem*, *appSettings.* `Environment` *. JSON*e o Gerenciador de segredo.</span><span class="sxs-lookup"><span data-stu-id="596d3-166">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="596d3-167">O `:` separador não funciona com chaves hierárquicas de variáveis de ambiente em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="596d3-167">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="596d3-168">O sublinhado duplo ( `__` ) é substituído automaticamente por um `:` e tem suporte em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="596d3-168">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="596d3-169">Por exemplo, o `:` separador não tem suporte do [bash](https://linuxhint.com/bash-environment-variables), mas sim `__` .</span><span class="sxs-lookup"><span data-stu-id="596d3-169">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="596d3-170">Os seguintes `set` comandos:</span><span class="sxs-lookup"><span data-stu-id="596d3-170">The following `set` commands:</span></span>

- <span data-ttu-id="596d3-171">Defina as chaves de ambiente e os valores do exemplo anterior no Windows.</span><span class="sxs-lookup"><span data-stu-id="596d3-171">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="596d3-172">Teste as configurações alterando-as de seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="596d3-172">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="596d3-173">O `dotnet run` comando deve ser executado no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="596d3-173">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="596d3-174">As configurações de ambiente anteriores:</span><span class="sxs-lookup"><span data-stu-id="596d3-174">The preceding environment settings:</span></span>

- <span data-ttu-id="596d3-175">São definidos apenas em processos iniciados na janela de comando em que foram definidos.</span><span class="sxs-lookup"><span data-stu-id="596d3-175">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="596d3-176">Não serão lidos por aplicativos Web iniciados com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="596d3-176">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="596d3-177">Os comandos [setx](/windows-server/administration/windows-commands/setx) a seguir podem ser usados para definir as chaves de ambiente e os valores no Windows.</span><span class="sxs-lookup"><span data-stu-id="596d3-177">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="596d3-178">Ao contrário `set` de, `setx` as configurações são persistidas.</span><span class="sxs-lookup"><span data-stu-id="596d3-178">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="596d3-179">`/M` define a variável no ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="596d3-179">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="596d3-180">Se a `/M` opção não for usada, uma variável de ambiente do usuário será definida.</span><span class="sxs-lookup"><span data-stu-id="596d3-180">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="596d3-181">Para testar se os comandos anteriores substituem *appsettings.js* e *appSettings.* `Environment` *. JSON*:</span><span class="sxs-lookup"><span data-stu-id="596d3-181">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="596d3-182">Com o Visual Studio: saia e reinicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="596d3-182">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="596d3-183">Com a CLI: iniciar uma nova janela de comando e Enter `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="596d3-183">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="596d3-184">Chame <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> com uma cadeia de caracteres para especificar um prefixo para variáveis de ambiente:</span><span class="sxs-lookup"><span data-stu-id="596d3-184">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="15-16":::

<span data-ttu-id="596d3-185">No código anterior:</span><span class="sxs-lookup"><span data-stu-id="596d3-185">In the preceding code:</span></span>

- <span data-ttu-id="596d3-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` é adicionado após os provedores de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="596d3-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="596d3-187">Para obter um exemplo de como ordenar os provedores de configuração, consulte [provedor de configuração XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="596d3-187">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="596d3-188">Variáveis de ambiente definidas com o `CustomPrefix_` prefixo substituem os provedores de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="596d3-188">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="596d3-189">Isso inclui variáveis de ambiente sem o prefixo.</span><span class="sxs-lookup"><span data-stu-id="596d3-189">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="596d3-190">O prefixo é eliminado quando os pares chave-valor de configuração são lidos.</span><span class="sxs-lookup"><span data-stu-id="596d3-190">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="596d3-191">Os comandos a seguir testam o prefixo personalizado:</span><span class="sxs-lookup"><span data-stu-id="596d3-191">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix_TransientFaultHandlingOptions__Enabled=true
set CustomPrefix_TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="596d3-192">A configuração padrão carrega variáveis de ambiente e argumentos de linha de comando prefixados com `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="596d3-192">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="596d3-193">O `DOTNET_` prefixo é usado pelo .net para a configuração de [host](generic-host.md#host-configuration) e [aplicativo](generic-host.md#app-configuration), mas não para a configuração do usuário.</span><span class="sxs-lookup"><span data-stu-id="596d3-193">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="596d3-194">Para obter mais informações sobre a configuração de host e aplicativo, consulte [host genérico .net](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="596d3-194">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="596d3-195">Em [Azure app serviço](https://azure.microsoft.com/services/app-service), selecione **nova configuração de aplicativo** na página **configurações > configuração** .</span><span class="sxs-lookup"><span data-stu-id="596d3-195">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="596d3-196">Azure App configurações do aplicativo de serviço são:</span><span class="sxs-lookup"><span data-stu-id="596d3-196">Azure App Service application settings are:</span></span>

- <span data-ttu-id="596d3-197">Criptografado em repouso e transmitido por um canal criptografado.</span><span class="sxs-lookup"><span data-stu-id="596d3-197">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="596d3-198">Exposto como variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="596d3-198">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="596d3-199">Prefixos de cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="596d3-199">Connection string prefixes</span></span>

<span data-ttu-id="596d3-200">A API de configuração tem regras de processamento especiais para quatro variáveis de ambiente de cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="596d3-200">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="596d3-201">Essas cadeias de conexão estão envolvidas na configuração de cadeias de conexão do Azure para o ambiente de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="596d3-201">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="596d3-202">As variáveis de ambiente com os prefixos mostrados na tabela são carregadas no aplicativo com a configuração padrão ou quando nenhum prefixo é fornecido para `AddEnvironmentVariables` .</span><span class="sxs-lookup"><span data-stu-id="596d3-202">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="596d3-203">Prefixo da cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="596d3-203">Connection string prefix</span></span> | <span data-ttu-id="596d3-204">Provedor</span><span class="sxs-lookup"><span data-stu-id="596d3-204">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="596d3-205">Provedor personalizado</span><span class="sxs-lookup"><span data-stu-id="596d3-205">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="596d3-206">MySQL</span><span class="sxs-lookup"><span data-stu-id="596d3-206">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="596d3-207">Banco de Dados SQL do Azure</span><span class="sxs-lookup"><span data-stu-id="596d3-207">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="596d3-208">SQL Server</span><span class="sxs-lookup"><span data-stu-id="596d3-208">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="596d3-209">Quando uma variável de ambiente for descoberta e carregada na configuração com qualquer um dos quatro prefixos mostrados na tabela:</span><span class="sxs-lookup"><span data-stu-id="596d3-209">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="596d3-210">A chave de configuração é criada removendo o prefixo da variável de ambiente e adicionando uma seção de chave de configuração (`ConnectionStrings`).</span><span class="sxs-lookup"><span data-stu-id="596d3-210">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="596d3-211">Um novo par chave-valor de configuração é criado para representar o provedor de conexão de banco de dados (exceto para `CUSTOMCONNSTR_`, que não tem um provedor indicado).</span><span class="sxs-lookup"><span data-stu-id="596d3-211">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="596d3-212">Chave de variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="596d3-212">Environment variable key</span></span> | <span data-ttu-id="596d3-213">Chave de configuração convertida</span><span class="sxs-lookup"><span data-stu-id="596d3-213">Converted configuration key</span></span> | <span data-ttu-id="596d3-214">Entrada de configuração do provedor</span><span class="sxs-lookup"><span data-stu-id="596d3-214">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="596d3-215">Entrada de configuração não criada.</span><span class="sxs-lookup"><span data-stu-id="596d3-215">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="596d3-216">Chave: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="596d3-216">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="596d3-217">Valor: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="596d3-217">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="596d3-218">Chave: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="596d3-218">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="596d3-219">Valor: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="596d3-219">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="596d3-220">Chave: `ConnectionStrings:{KEY}_ProviderName`:</span><span class="sxs-lookup"><span data-stu-id="596d3-220">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="596d3-221">Valor: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="596d3-221">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="596d3-222">Variáveis de ambiente definidas no launchSettings.jsem</span><span class="sxs-lookup"><span data-stu-id="596d3-222">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="596d3-223">As variáveis de ambiente definidas no *launchSettings.js* substituir aquelas definidas no ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="596d3-223">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="596d3-224">Provedor de configuração de linha de comando</span><span class="sxs-lookup"><span data-stu-id="596d3-224">Command-line configuration provider</span></span>

<span data-ttu-id="596d3-225">Usando a configuração padrão, o <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> carrega a configuração de pares de chave-valor de argumento de linha de comando após as seguintes fontes de configuração:</span><span class="sxs-lookup"><span data-stu-id="596d3-225">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="596d3-226">*appsettings.js* e *appSettings*. `Environment` . arquivos *JSON* .</span><span class="sxs-lookup"><span data-stu-id="596d3-226">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="596d3-227">Segredos do aplicativo (Gerenciador de segredo) no `Development` ambiente.</span><span class="sxs-lookup"><span data-stu-id="596d3-227">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="596d3-228">Variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="596d3-228">Environment variables.</span></span>

<span data-ttu-id="596d3-229">Por padrão, os valores de configuração definidos na linha de comando substituem os valores de configuração definidos por todos os outros provedores de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-229">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="596d3-230">Argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="596d3-230">Command-line arguments</span></span>

<span data-ttu-id="596d3-231">O comando a seguir define chaves e valores usando `=` :</span><span class="sxs-lookup"><span data-stu-id="596d3-231">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="596d3-232">O comando a seguir define chaves e valores usando `/` :</span><span class="sxs-lookup"><span data-stu-id="596d3-232">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="596d3-233">O comando a seguir define chaves e valores usando `--` :</span><span class="sxs-lookup"><span data-stu-id="596d3-233">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="596d3-234">O valor da chave:</span><span class="sxs-lookup"><span data-stu-id="596d3-234">The key value:</span></span>

- <span data-ttu-id="596d3-235">Deve seguir `=` , ou a chave deve ter um prefixo `--` ou `/` quando o valor segue um espaço.</span><span class="sxs-lookup"><span data-stu-id="596d3-235">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="596d3-236">Não será necessário se `=` for usado.</span><span class="sxs-lookup"><span data-stu-id="596d3-236">Isn't required if `=` is used.</span></span> <span data-ttu-id="596d3-237">Por exemplo, `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="596d3-237">For example, `SomeKey=`.</span></span>

<span data-ttu-id="596d3-238">No mesmo comando, não misture pares de chave-valor de argumento de linha de comando que usam `=` com pares de chave-valor que usam um espaço.</span><span class="sxs-lookup"><span data-stu-id="596d3-238">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="596d3-239">Provedor de configuração de chave por arquivo</span><span class="sxs-lookup"><span data-stu-id="596d3-239">Key-per-file configuration provider</span></span>

<span data-ttu-id="596d3-240">O <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> usa arquivos do diretório como pares chave-valor de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-240">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="596d3-241">A chave é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="596d3-241">The key is the file name.</span></span> <span data-ttu-id="596d3-242">O valor é o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="596d3-242">The value is the file's contents.</span></span> <span data-ttu-id="596d3-243">O provedor de configuração de chave por arquivo é usado em cenários de hospedagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="596d3-243">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="596d3-244">Para ativar a configuração de chave por arquivo, chame o método de extensão <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> em uma instância do <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span><span class="sxs-lookup"><span data-stu-id="596d3-244">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="596d3-245">O `directoryPath` para os arquivos deve ser um caminho absoluto.</span><span class="sxs-lookup"><span data-stu-id="596d3-245">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="596d3-246">As sobrecargas permitem especificar:</span><span class="sxs-lookup"><span data-stu-id="596d3-246">Overloads permit specifying:</span></span>

- <span data-ttu-id="596d3-247">Um delegado `Action<KeyPerFileConfigurationSource>` que configura a origem.</span><span class="sxs-lookup"><span data-stu-id="596d3-247">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="596d3-248">Se o diretório é opcional, e o caminho para o diretório.</span><span class="sxs-lookup"><span data-stu-id="596d3-248">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="596d3-249">O sublinhado duplo (`__`) é usado como um delimitador de chave de configuração em nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="596d3-249">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="596d3-250">Por exemplo, o nome do arquivo `Logging__LogLevel__System` produz a chave de configuração `Logging:LogLevel:System`.</span><span class="sxs-lookup"><span data-stu-id="596d3-250">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="596d3-251">Chame `ConfigureAppConfiguration` ao criar o host para especificar a configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="596d3-251">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="596d3-252">Provedor de configuração de memória</span><span class="sxs-lookup"><span data-stu-id="596d3-252">Memory configuration provider</span></span>

<span data-ttu-id="596d3-253">O <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> usa uma coleção na memória como pares chave-valor de configuração.</span><span class="sxs-lookup"><span data-stu-id="596d3-253">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="596d3-254">O código a seguir adiciona uma coleção de memória ao sistema de configuração:</span><span class="sxs-lookup"><span data-stu-id="596d3-254">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="16-23":::

<span data-ttu-id="596d3-255">No código anterior, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adiciona o provedor de memória após os provedores de configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="596d3-255">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="596d3-256">Para obter um exemplo de como ordenar os provedores de configuração, consulte [provedor de configuração XML](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="596d3-256">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="596d3-257">Confira também</span><span class="sxs-lookup"><span data-stu-id="596d3-257">See also</span></span>

- [<span data-ttu-id="596d3-258">Configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="596d3-258">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="596d3-259">Host Genérico .NET</span><span class="sxs-lookup"><span data-stu-id="596d3-259">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="596d3-260">Implementar um provedor de configuração personalizado</span><span class="sxs-lookup"><span data-stu-id="596d3-260">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
