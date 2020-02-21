---
title: CLI do .NET Core
titleSuffix: ''
description: Uma visão geral do CLI do .NET Core e de seus recursos.
ms.date: 02/13/2020
ms.openlocfilehash: 1078d68ddc088274fa14b0094a81765f7af69dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543308"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="e5914-103">Visão geral de CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5914-103">.NET Core CLI overview</span></span>

<span data-ttu-id="e5914-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e5914-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="e5914-105">A CLI (interface de linha de comando) do .NET Core é uma ferramentas de plataforma cruzada para o desenvolvimento, a criação, a execução e a publicação de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5914-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="e5914-106">O CLI do .NET Core está incluído no [SDK do .NET Core](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="e5914-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="e5914-107">Para saber como instalar o SDK do .NET Core, consulte [instalar o SDK do .NET Core](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="e5914-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="e5914-108">Comandos de CLI</span><span class="sxs-lookup"><span data-stu-id="e5914-108">CLI commands</span></span>

<span data-ttu-id="e5914-109">Os comandos a seguir são instalados por padrão:</span><span class="sxs-lookup"><span data-stu-id="e5914-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="e5914-110">Comandos básicos</span><span class="sxs-lookup"><span data-stu-id="e5914-110">Basic commands</span></span>

- [<span data-ttu-id="e5914-111">novo</span><span class="sxs-lookup"><span data-stu-id="e5914-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="e5914-112">restaurar</span><span class="sxs-lookup"><span data-stu-id="e5914-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="e5914-113">build</span><span class="sxs-lookup"><span data-stu-id="e5914-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="e5914-114">publicar</span><span class="sxs-lookup"><span data-stu-id="e5914-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="e5914-115">run</span><span class="sxs-lookup"><span data-stu-id="e5914-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="e5914-116">test</span><span class="sxs-lookup"><span data-stu-id="e5914-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="e5914-117">vstest</span><span class="sxs-lookup"><span data-stu-id="e5914-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="e5914-118">pack</span><span class="sxs-lookup"><span data-stu-id="e5914-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="e5914-119">migrar</span><span class="sxs-lookup"><span data-stu-id="e5914-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="e5914-120">clean</span><span class="sxs-lookup"><span data-stu-id="e5914-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="e5914-121">sln</span><span class="sxs-lookup"><span data-stu-id="e5914-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="e5914-122">ajuda</span><span class="sxs-lookup"><span data-stu-id="e5914-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="e5914-123">store</span><span class="sxs-lookup"><span data-stu-id="e5914-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="e5914-124">Comandos de modificação de projeto</span><span class="sxs-lookup"><span data-stu-id="e5914-124">Project modification commands</span></span>

- [<span data-ttu-id="e5914-125">add package</span><span class="sxs-lookup"><span data-stu-id="e5914-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="e5914-126">add reference</span><span class="sxs-lookup"><span data-stu-id="e5914-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="e5914-127">remove package</span><span class="sxs-lookup"><span data-stu-id="e5914-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="e5914-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="e5914-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="e5914-129">list reference</span><span class="sxs-lookup"><span data-stu-id="e5914-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="e5914-130">Comandos avançados</span><span class="sxs-lookup"><span data-stu-id="e5914-130">Advanced commands</span></span>

- [<span data-ttu-id="e5914-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="e5914-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="e5914-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="e5914-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="e5914-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="e5914-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="e5914-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="e5914-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="e5914-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="e5914-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="e5914-136">Comandos de gerenciamento de ferramentas</span><span class="sxs-lookup"><span data-stu-id="e5914-136">Tool management commands</span></span>

- [<span data-ttu-id="e5914-137">instalação da ferramenta</span><span class="sxs-lookup"><span data-stu-id="e5914-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="e5914-138">lista de ferramentas</span><span class="sxs-lookup"><span data-stu-id="e5914-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="e5914-139">atualização de ferramenta</span><span class="sxs-lookup"><span data-stu-id="e5914-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="e5914-140">[restauração de ferramenta](global-tools.md#install-a-local-tool) **disponível a partir do SDK do .NET Core 3,0**</span><span class="sxs-lookup"><span data-stu-id="e5914-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="e5914-141">[execução de ferramenta](global-tools.md#invoke-a-local-tool) **disponível a partir do SDK do .NET Core 3,0**</span><span class="sxs-lookup"><span data-stu-id="e5914-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="e5914-142">desinstalação de ferramenta</span><span class="sxs-lookup"><span data-stu-id="e5914-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="e5914-143">Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e5914-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="e5914-144">Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="e5914-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="e5914-145">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="e5914-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="e5914-146">Para obter mais informações, consulte [visão geral das ferramentas do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e5914-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="e5914-147">Estrutura de comando</span><span class="sxs-lookup"><span data-stu-id="e5914-147">Command structure</span></span>

<span data-ttu-id="e5914-148">A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#arguments) e [argumentos](#options) de comando.</span><span class="sxs-lookup"><span data-stu-id="e5914-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="e5914-149">É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:</span><span class="sxs-lookup"><span data-stu-id="e5914-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="e5914-150">Driver</span><span class="sxs-lookup"><span data-stu-id="e5914-150">Driver</span></span>

<span data-ttu-id="e5914-151">O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando.</span><span class="sxs-lookup"><span data-stu-id="e5914-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="e5914-152">Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="e5914-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="e5914-153">Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="e5914-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="e5914-154">Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="e5914-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="e5914-155">Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI.</span><span class="sxs-lookup"><span data-stu-id="e5914-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="e5914-156">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5914-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="e5914-157">Primeiro, o driver determina a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="e5914-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="e5914-158">Se não houver uma ['global.json'](global-json.md), a versão mais recente do SDK disponível será usada.</span><span class="sxs-lookup"><span data-stu-id="e5914-158">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="e5914-159">Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.</span><span class="sxs-lookup"><span data-stu-id="e5914-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="e5914-160">Depois que a versão do SDK é determinada, ela executa o comando.</span><span class="sxs-lookup"><span data-stu-id="e5914-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="e5914-161">Comando</span><span class="sxs-lookup"><span data-stu-id="e5914-161">Command</span></span>

<span data-ttu-id="e5914-162">O comando executa uma ação.</span><span class="sxs-lookup"><span data-stu-id="e5914-162">The command performs an action.</span></span> <span data-ttu-id="e5914-163">Por exemplo, `dotnet build` compila código.</span><span class="sxs-lookup"><span data-stu-id="e5914-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="e5914-164">`dotnet publish` publica o código.</span><span class="sxs-lookup"><span data-stu-id="e5914-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="e5914-165">Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="e5914-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="e5914-166">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e5914-166">Arguments</span></span>

<span data-ttu-id="e5914-167">Os argumentos que você passa na linha de comando são aqueles do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="e5914-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="e5914-168">Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="e5914-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="e5914-169">Opções</span><span class="sxs-lookup"><span data-stu-id="e5914-169">Options</span></span>

<span data-ttu-id="e5914-170">As opções que você passa na linha de comando são aquelas do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="e5914-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="e5914-171">Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="e5914-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5914-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5914-172">See also</span></span>

- [<span data-ttu-id="e5914-173">repositório do GitHub do dotnet/SDK</span><span class="sxs-lookup"><span data-stu-id="e5914-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="e5914-174">Guia de instalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5914-174">.NET Core installation guide</span></span>](../install/sdk.md)
