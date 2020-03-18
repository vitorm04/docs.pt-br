---
title: Opções de configuração de tempo de execução
description: Saiba como configurar aplicativos .NET Core usando configurações de configuração em tempo de execução.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399157"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="09aa9-103">Configurações de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="09aa9-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="09aa9-104">O .NET Core suporta o uso de arquivos de configuração e variáveis de ambiente para configurar o comportamento de aplicativos .NET Core em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="09aa9-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="09aa9-105">A configuração em tempo de execução é uma opção atraente se:</span><span class="sxs-lookup"><span data-stu-id="09aa9-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="09aa9-106">Você não possui ou controla o código-fonte de um aplicativo e, portanto, não consegue configurá-lo programáticamente.</span><span class="sxs-lookup"><span data-stu-id="09aa9-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="09aa9-107">Várias instâncias do aplicativo são executadas ao mesmo tempo em um único sistema, e você deseja configurar cada uma para um desempenho ideal.</span><span class="sxs-lookup"><span data-stu-id="09aa9-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="09aa9-108">Esta documentação é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="09aa9-108">This documentation is a work in progress.</span></span> <span data-ttu-id="09aa9-109">Se você notar que as informações aqui apresentadas são incompletas ou imprecisas, [abra um problema](https://github.com/dotnet/docs/issues) para nos informar sobre isso ou envie uma solicitação de [retirada](https://github.com/dotnet/docs/pulls) para resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="09aa9-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="09aa9-110">Para obter informações sobre o envio de solicitações de retirada para o repositório dotnet/docs, consulte o [guia do contribuinte](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="09aa9-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="09aa9-111">O .NET Core fornece os seguintes mecanismos para configurar o comportamento do aplicativo em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="09aa9-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="09aa9-112">O [arquivo runtimeconfig.json](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="09aa9-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="09aa9-113">Propriedades do MSBuild</span><span class="sxs-lookup"><span data-stu-id="09aa9-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="09aa9-114">Variáveis ambientais</span><span class="sxs-lookup"><span data-stu-id="09aa9-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="09aa9-115">Alguns valores de configuração também <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> podem ser definidos programáticamente chamando o método.</span><span class="sxs-lookup"><span data-stu-id="09aa9-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="09aa9-116">Os artigos desta seção da documentação são organizados por categoria, por exemplo, [depuração](debugging-profiling.md) e [coleta de lixo.](garbage-collector.md)</span><span class="sxs-lookup"><span data-stu-id="09aa9-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="09aa9-117">Quando aplicável, as opções de configuração são mostradas para arquivos *runtimeconfig.json,* propriedades MSBuild, variáveis de ambiente e, para cross-reference, *app.config* files para projetos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09aa9-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="09aa9-118">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="09aa9-118">runtimeconfig.json</span></span>

<span data-ttu-id="09aa9-119">Quando um projeto é [construído,](../tools/dotnet-build.md)um arquivo *[appname].runtimeconfig.json* é gerado no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="09aa9-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="09aa9-120">Se um arquivo *runtimeconfig.template.json* existir na mesma pasta que o arquivo do projeto, todas as opções de configuração que ele contém serão mescladas no arquivo *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="09aa9-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="09aa9-121">Se você estiver construindo o aplicativo você mesmo, coloque quaisquer opções de configuração no arquivo *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="09aa9-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="09aa9-122">Se você estiver apenas executando o aplicativo, insira-os diretamente no arquivo *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="09aa9-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="09aa9-123">O arquivo *[appname].runtimeconfig.json* será substituído em compilações subseqüentes.</span><span class="sxs-lookup"><span data-stu-id="09aa9-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="09aa9-124">Especifique opções de configuração em tempo de execução na seção **configPropriedades** dos arquivos *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="09aa9-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="09aa9-125">Esta seção tem o formulário:</span><span class="sxs-lookup"><span data-stu-id="09aa9-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="09aa9-126">Exemplo [appname].runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="09aa9-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="09aa9-127">Se você estiver colocando as opções no arquivo JSON de saída, aninham-as a `runtimeOptions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="09aa9-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="09aa9-128">Exemplo de runtimeconfig.template.json file</span><span class="sxs-lookup"><span data-stu-id="09aa9-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="09aa9-129">Se você estiver colocando as opções no arquivo JSON do modelo, omita a `runtimeOptions` propriedade.</span><span class="sxs-lookup"><span data-stu-id="09aa9-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="09aa9-130">propriedades MSBuild</span><span class="sxs-lookup"><span data-stu-id="09aa9-130">MSBuild properties</span></span>

<span data-ttu-id="09aa9-131">Algumas opções de configuração em tempo de execução podem ser definidas usando propriedades MSBuild no arquivo *.csproj* ou *.vbproj* de projetos .NET Core no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="09aa9-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="09aa9-132">As propriedades mSBuild têm precedência sobre as opções definidas no arquivo *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="09aa9-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="09aa9-133">Eles também sobreescrevem todas as opções definidas no arquivo *[appname].runtimeconfig.json* no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="09aa9-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="09aa9-134">Aqui está um exemplo de arquivo de projeto no estilo SDK com propriedades MSBuild para configurar o comportamento em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="09aa9-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="09aa9-135">As propriedades do MSBuild para configurar o comportamento em tempo de execução são observadas nos artigos individuais para cada área, por exemplo, [coleta de lixo](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="09aa9-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="09aa9-136">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="09aa9-136">Environment variables</span></span>

<span data-ttu-id="09aa9-137">As variáveis de ambiente podem ser usadas para fornecer algumas informações de configuração em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="09aa9-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="09aa9-138">Os botões de configuração especificados como variáveis de ambiente geralmente têm o prefixo **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="09aa9-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="09aa9-139">Você pode definir variáveis de ambiente a partir do Painel de Controle <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> do Windows, na linha de comando ou programáticamente chamando o método em sistemas baseados no Windows e Unix.</span><span class="sxs-lookup"><span data-stu-id="09aa9-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="09aa9-140">Os exemplos a seguir mostram como definir uma variável de ambiente na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="09aa9-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
