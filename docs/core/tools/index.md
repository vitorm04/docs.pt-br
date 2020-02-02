---
title: CLI do .NET Core
titleSuffix: ''
description: Uma visão geral do CLI do .NET Core e de seus recursos.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920477"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="6c153-103">Visão geral de CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c153-103">.NET Core CLI overview</span></span>

<span data-ttu-id="6c153-104">A CLI (interface de linha de comando) do .NET Core é uma ferramentas de plataforma cruzada para o desenvolvimento, a criação, a execução e a publicação de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c153-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="6c153-105">O CLI do .NET Core está incluído no [SDK do .NET Core](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6c153-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="6c153-106">Para saber como instalar o SDK do .NET Core, consulte [instalar o SDK do .NET Core](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6c153-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="6c153-107">Comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="6c153-107">CLI commands</span></span>

<span data-ttu-id="6c153-108">Os comandos a seguir são instalados por padrão:</span><span class="sxs-lookup"><span data-stu-id="6c153-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c153-109">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c153-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6c153-110">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="6c153-110">**Basic commands**</span></span>

- [<span data-ttu-id="6c153-111">new</span><span class="sxs-lookup"><span data-stu-id="6c153-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="6c153-112">restore</span><span class="sxs-lookup"><span data-stu-id="6c153-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="6c153-113">build</span><span class="sxs-lookup"><span data-stu-id="6c153-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="6c153-114">publish</span><span class="sxs-lookup"><span data-stu-id="6c153-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="6c153-115">run</span><span class="sxs-lookup"><span data-stu-id="6c153-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="6c153-116">test</span><span class="sxs-lookup"><span data-stu-id="6c153-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="6c153-117">vstest</span><span class="sxs-lookup"><span data-stu-id="6c153-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="6c153-118">pack</span><span class="sxs-lookup"><span data-stu-id="6c153-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="6c153-119">migrate</span><span class="sxs-lookup"><span data-stu-id="6c153-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="6c153-120">clean</span><span class="sxs-lookup"><span data-stu-id="6c153-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="6c153-121">sln</span><span class="sxs-lookup"><span data-stu-id="6c153-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="6c153-122">ajuda</span><span class="sxs-lookup"><span data-stu-id="6c153-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="6c153-123">repositório</span><span class="sxs-lookup"><span data-stu-id="6c153-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="6c153-124">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="6c153-124">**Project modification commands**</span></span>

- [<span data-ttu-id="6c153-125">add package</span><span class="sxs-lookup"><span data-stu-id="6c153-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="6c153-126">add reference</span><span class="sxs-lookup"><span data-stu-id="6c153-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="6c153-127">remove package</span><span class="sxs-lookup"><span data-stu-id="6c153-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="6c153-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="6c153-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="6c153-129">list reference</span><span class="sxs-lookup"><span data-stu-id="6c153-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="6c153-130">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="6c153-130">**Advanced commands**</span></span>

- [<span data-ttu-id="6c153-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="6c153-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="6c153-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="6c153-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="6c153-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="6c153-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="6c153-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="6c153-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="6c153-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="6c153-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c153-136">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c153-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c153-137">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="6c153-137">**Basic commands**</span></span>

- [<span data-ttu-id="6c153-138">new</span><span class="sxs-lookup"><span data-stu-id="6c153-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="6c153-139">restore</span><span class="sxs-lookup"><span data-stu-id="6c153-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="6c153-140">build</span><span class="sxs-lookup"><span data-stu-id="6c153-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="6c153-141">publish</span><span class="sxs-lookup"><span data-stu-id="6c153-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="6c153-142">run</span><span class="sxs-lookup"><span data-stu-id="6c153-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="6c153-143">test</span><span class="sxs-lookup"><span data-stu-id="6c153-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="6c153-144">vstest</span><span class="sxs-lookup"><span data-stu-id="6c153-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="6c153-145">pack</span><span class="sxs-lookup"><span data-stu-id="6c153-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="6c153-146">migrate</span><span class="sxs-lookup"><span data-stu-id="6c153-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="6c153-147">clean</span><span class="sxs-lookup"><span data-stu-id="6c153-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="6c153-148">sln</span><span class="sxs-lookup"><span data-stu-id="6c153-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="6c153-149">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="6c153-149">**Project modification commands**</span></span>

- [<span data-ttu-id="6c153-150">add package</span><span class="sxs-lookup"><span data-stu-id="6c153-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="6c153-151">add reference</span><span class="sxs-lookup"><span data-stu-id="6c153-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="6c153-152">remove package</span><span class="sxs-lookup"><span data-stu-id="6c153-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="6c153-153">remove reference</span><span class="sxs-lookup"><span data-stu-id="6c153-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="6c153-154">list reference</span><span class="sxs-lookup"><span data-stu-id="6c153-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="6c153-155">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="6c153-155">**Advanced commands**</span></span>

- [<span data-ttu-id="6c153-156">nuget delete</span><span class="sxs-lookup"><span data-stu-id="6c153-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="6c153-157">nuget locals</span><span class="sxs-lookup"><span data-stu-id="6c153-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="6c153-158">nuget push</span><span class="sxs-lookup"><span data-stu-id="6c153-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="6c153-159">msbuild</span><span class="sxs-lookup"><span data-stu-id="6c153-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="6c153-160">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="6c153-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="6c153-161">A CLI adota um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos.</span><span class="sxs-lookup"><span data-stu-id="6c153-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="6c153-162">Para saber mais, confira o tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="6c153-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="6c153-163">Estrutura de comando</span><span class="sxs-lookup"><span data-stu-id="6c153-163">Command structure</span></span>

<span data-ttu-id="6c153-164">A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#options) e [argumentos](#arguments) de comando.</span><span class="sxs-lookup"><span data-stu-id="6c153-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="6c153-165">É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:</span><span class="sxs-lookup"><span data-stu-id="6c153-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c153-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c153-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c153-167">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c153-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="6c153-168">Driver</span><span class="sxs-lookup"><span data-stu-id="6c153-168">Driver</span></span>

<span data-ttu-id="6c153-169">O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando.</span><span class="sxs-lookup"><span data-stu-id="6c153-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="6c153-170">Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="6c153-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="6c153-171">Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="6c153-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="6c153-172">Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="6c153-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="6c153-173">Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI.</span><span class="sxs-lookup"><span data-stu-id="6c153-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="6c153-174">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c153-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="6c153-175">Primeiro, o driver determina a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="6c153-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="6c153-176">Se não houver uma ['global.json'](global-json.md), a versão mais recente do SDK disponível será usada.</span><span class="sxs-lookup"><span data-stu-id="6c153-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="6c153-177">Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.</span><span class="sxs-lookup"><span data-stu-id="6c153-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="6c153-178">Depois que a versão do SDK é determinada, ela executa o comando.</span><span class="sxs-lookup"><span data-stu-id="6c153-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="6c153-179">{1&gt;Comando&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6c153-179">Command</span></span>

<span data-ttu-id="6c153-180">O comando executa uma ação.</span><span class="sxs-lookup"><span data-stu-id="6c153-180">The command performs an action.</span></span> <span data-ttu-id="6c153-181">Por exemplo, `dotnet build` compila código.</span><span class="sxs-lookup"><span data-stu-id="6c153-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="6c153-182">`dotnet publish` publica o código.</span><span class="sxs-lookup"><span data-stu-id="6c153-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="6c153-183">Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="6c153-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="6c153-184">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c153-184">Arguments</span></span>

<span data-ttu-id="6c153-185">Os argumentos que você passa na linha de comando são aqueles do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="6c153-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="6c153-186">Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="6c153-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="6c153-187">Opções</span><span class="sxs-lookup"><span data-stu-id="6c153-187">Options</span></span>

<span data-ttu-id="6c153-188">As opções que você passa na linha de comando são aquelas do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="6c153-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="6c153-189">Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="6c153-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="6c153-190">Migração do project.json</span><span class="sxs-lookup"><span data-stu-id="6c153-190">Migration from project.json</span></span>

<span data-ttu-id="6c153-191">Se você tiver usado as ferramentas da Visualização 2 para produzir projetos baseados em *project.json*, veja o tópico [dotnet migrate](dotnet-migrate.md) para saber mais sobre como migrar seu projeto para MSBuild/ *.csproj* para uso com as ferramentas de versão.</span><span class="sxs-lookup"><span data-stu-id="6c153-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="6c153-192">Para projetos do .NET Core criados antes do lançamento das ferramentas da Versão prévia 2, siga as orientações descritas em [Migrando do DNX para a CLI do .NET Core (project.json)](../migration/from-dnx.md) para atualizar o projeto manualmente e, depois, use `dotnet migrate` ou atualize os projetos diretamente.</span><span class="sxs-lookup"><span data-stu-id="6c153-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c153-193">Veja também</span><span class="sxs-lookup"><span data-stu-id="6c153-193">See also</span></span>

- [<span data-ttu-id="6c153-194">repositório do GitHub do dotnet/SDK</span><span class="sxs-lookup"><span data-stu-id="6c153-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="6c153-195">Guia de instalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6c153-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
