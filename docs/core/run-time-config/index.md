---
title: Opções de configuração de tempo de execução
description: Saiba como configurar aplicativos .NET Core usando as definições de configuração de tempo de execução.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733445"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="b38b5-103">Definições de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b38b5-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="b38b5-104">O .NET Core dá suporte ao uso de arquivos de configuração e variáveis de ambiente para configurar o comportamento de aplicativos .NET Core em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b38b5-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="b38b5-105">A configuração de tempo de execução é uma opção atraente se:</span><span class="sxs-lookup"><span data-stu-id="b38b5-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="b38b5-106">Você não possui ou controla o código-fonte de um aplicativo e, portanto, não é possível configurá-lo programaticamente.</span><span class="sxs-lookup"><span data-stu-id="b38b5-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="b38b5-107">Várias instâncias do seu aplicativo são executadas ao mesmo tempo em um único sistema e você deseja configurar cada uma para obter um desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="b38b5-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="b38b5-108">Esta documentação é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="b38b5-108">This documentation is a work in progress.</span></span> <span data-ttu-id="b38b5-109">Se você observar que as informações apresentadas aqui estão incompletas ou imprecisas, [abra um problema](https://github.com/dotnet/docs/issues) para nos informar sobre ela ou [envie uma solicitação de pull](https://github.com/dotnet/docs/pulls) para resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="b38b5-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="b38b5-110">Para obter informações sobre como enviar solicitações pull para o repositório dotnet/docs, consulte o [Guia do colaborador](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="b38b5-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="b38b5-111">O .NET Core fornece os seguintes mecanismos para configurar o comportamento do aplicativo de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="b38b5-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="b38b5-112">O [arquivo runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="b38b5-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="b38b5-113">Propriedades do MSBuild</span><span class="sxs-lookup"><span data-stu-id="b38b5-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="b38b5-114">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="b38b5-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="b38b5-115">Alguns valores de configuração também podem ser definidos programaticamente chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b38b5-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b38b5-116">Os artigos nesta seção da documentação são organizados por categoria, por exemplo, [depuração](debugging-profiling.md) e coleta de [lixo](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="b38b5-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="b38b5-117">Quando aplicável, as opções de configuração são mostradas para arquivos *runtimeconfig. JSON* , propriedades do MSBuild, variáveis de ambiente e, para os arquivos de referência cruzada, *app. config* para projetos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b38b5-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="b38b5-118">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="b38b5-118">runtimeconfig.json</span></span>

<span data-ttu-id="b38b5-119">Quando um projeto é [compilado](../tools/dotnet-build.md), um arquivo *[AppName]. runtimeconfig. JSON* é gerado no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="b38b5-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="b38b5-120">Se um arquivo *runtimeconfig. Template. JSON* existir na mesma pasta que o arquivo de projeto, as opções de configuração contidas nela serão mescladas no arquivo *[AppName]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b38b5-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="b38b5-121">Se você estiver criando o aplicativo por conta própria, coloque as opções de configuração no arquivo *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b38b5-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="b38b5-122">Se você estiver apenas executando o aplicativo, insira-os diretamente no arquivo *[AppName]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b38b5-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="b38b5-123">O arquivo *[AppName]. runtimeconfig. JSON* será substituído em compilações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="b38b5-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="b38b5-124">Especifique as opções de configuração de tempo de execução na seção **configproperties** dos arquivos *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b38b5-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="b38b5-125">Esta seção tem o formato:</span><span class="sxs-lookup"><span data-stu-id="b38b5-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="b38b5-126">Exemplo [AppName]. runtimeconfig. JSON File</span><span class="sxs-lookup"><span data-stu-id="b38b5-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="b38b5-127">Se você estiver colocando as opções no arquivo JSON de saída, aninhe-as na propriedade `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="b38b5-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="b38b5-128">Arquivo runtimeconfig. Template. JSON de exemplo</span><span class="sxs-lookup"><span data-stu-id="b38b5-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="b38b5-129">Se você estiver colocando as opções no arquivo JSON de modelo, omita a propriedade `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="b38b5-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="b38b5-130">propriedades MSBuild</span><span class="sxs-lookup"><span data-stu-id="b38b5-130">MSBuild properties</span></span>

<span data-ttu-id="b38b5-131">Algumas opções de configuração de tempo de execução podem ser definidas usando as propriedades do MSBuild no arquivo *. csproj* ou *. vbproj* dos projetos do .NET Core do estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="b38b5-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="b38b5-132">As propriedades do MSBuild têm precedência sobre as opções definidas no arquivo *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b38b5-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="b38b5-133">Eles também substituem as opções definidas no arquivo *[AppName]. runtimeconfig. JSON* no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="b38b5-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="b38b5-134">Aqui está um exemplo de arquivo de projeto no estilo SDK com propriedades do MSBuild para configurar o comportamento de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="b38b5-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="b38b5-135">As propriedades do MSBuild para configurar o comportamento de tempo de execução são indicadas nos artigos individuais para cada área, por exemplo, [coleta de lixo](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="b38b5-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="b38b5-136">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="b38b5-136">Environment variables</span></span>

<span data-ttu-id="b38b5-137">As variáveis de ambiente podem ser usadas para fornecer algumas informações de configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b38b5-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="b38b5-138">Os botões de configuração especificados como variáveis de ambiente geralmente têm o prefixo **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="b38b5-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="b38b5-139">Você pode definir variáveis de ambiente no painel de controle do Windows, na linha de comando ou programaticamente chamando o método <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> em sistemas baseados no Windows e no UNIX.</span><span class="sxs-lookup"><span data-stu-id="b38b5-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="b38b5-140">Os exemplos a seguir mostram como definir uma variável de ambiente na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="b38b5-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
