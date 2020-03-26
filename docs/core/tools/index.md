---
title: CLI do .NET Core
titleSuffix: ''
description: Uma visão geral do .NET Core CLI e suas características.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110835"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="a3503-103">Visão geral da CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3503-103">.NET Core CLI overview</span></span>

<span data-ttu-id="a3503-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a3503-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="a3503-105">A interface de linha de comando .NET Core (CLI) é uma cadeia de ferramentas multiplataforma para desenvolver, construir, executar e publicar aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3503-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="a3503-106">O .NET Core CLI está incluído no [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a3503-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="a3503-107">Para saber como instalar o .NET Core SDK, consulte [Instale o .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a3503-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="a3503-108">Comandos de CLI</span><span class="sxs-lookup"><span data-stu-id="a3503-108">CLI commands</span></span>

<span data-ttu-id="a3503-109">Os comandos a seguir são instalados por padrão:</span><span class="sxs-lookup"><span data-stu-id="a3503-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="a3503-110">Comandos básicos</span><span class="sxs-lookup"><span data-stu-id="a3503-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="a3503-111">Comandos de modificação de projeto</span><span class="sxs-lookup"><span data-stu-id="a3503-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="a3503-112">Comandos avançados</span><span class="sxs-lookup"><span data-stu-id="a3503-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="a3503-113">Comandos de gerenciamento de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a3503-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="a3503-114">[`tool restore`](global-tools.md#install-a-local-tool)Disponível desde .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="a3503-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="a3503-115">[`tool run`](global-tools.md#invoke-a-local-tool)Disponível desde .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="a3503-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="a3503-116">As ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados a partir do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="a3503-117">Você mesmo pode escrever ferramentas ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="a3503-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="a3503-118">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="a3503-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="a3503-119">Para obter mais informações, consulte [a visão geral das ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a3503-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="a3503-120">Estrutura de comando</span><span class="sxs-lookup"><span data-stu-id="a3503-120">Command structure</span></span>

<span data-ttu-id="a3503-121">A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#options) e [argumentos](#arguments) de comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="a3503-122">É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:</span><span class="sxs-lookup"><span data-stu-id="a3503-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="a3503-123">Driver</span><span class="sxs-lookup"><span data-stu-id="a3503-123">Driver</span></span>

<span data-ttu-id="a3503-124">O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="a3503-125">Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="a3503-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="a3503-126">Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="a3503-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="a3503-127">Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="a3503-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="a3503-128">Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI.</span><span class="sxs-lookup"><span data-stu-id="a3503-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="a3503-129">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="a3503-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a3503-130">Primeiro, o driver determina a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="a3503-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="a3503-131">Se não houver nenhum arquivo [global.json,](global-json.md) a versão mais recente do SDK disponível será usada.</span><span class="sxs-lookup"><span data-stu-id="a3503-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="a3503-132">Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.</span><span class="sxs-lookup"><span data-stu-id="a3503-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="a3503-133">Depois que a versão do SDK é determinada, ela executa o comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="a3503-134">Comando</span><span class="sxs-lookup"><span data-stu-id="a3503-134">Command</span></span>

<span data-ttu-id="a3503-135">O comando executa uma ação.</span><span class="sxs-lookup"><span data-stu-id="a3503-135">The command performs an action.</span></span> <span data-ttu-id="a3503-136">Por exemplo, `dotnet build` compila código.</span><span class="sxs-lookup"><span data-stu-id="a3503-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="a3503-137">`dotnet publish` publica o código.</span><span class="sxs-lookup"><span data-stu-id="a3503-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="a3503-138">Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="a3503-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="a3503-139">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a3503-139">Arguments</span></span>

<span data-ttu-id="a3503-140">Os argumentos que você passa na linha de comando são aqueles do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="a3503-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="a3503-141">Por exemplo, quando `dotnet publish my_app.csproj`você `my_app.csproj` executa, o argumento indica `publish` que o projeto será publicado e é passado para o comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="a3503-142">Opções</span><span class="sxs-lookup"><span data-stu-id="a3503-142">Options</span></span>

<span data-ttu-id="a3503-143">As opções que você passa na linha de comando são aquelas do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="a3503-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="a3503-144">Por exemplo, quando `dotnet publish --output /build_output`você `--output` executa, a opção `publish` e seu valor são passados para o comando.</span><span class="sxs-lookup"><span data-stu-id="a3503-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3503-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3503-145">See also</span></span>

- [<span data-ttu-id="a3503-146">repositório dotnet/sdk GitHub</span><span class="sxs-lookup"><span data-stu-id="a3503-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="a3503-147">Guia de instalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3503-147">.NET Core installation guide</span></span>](../install/sdk.md)
