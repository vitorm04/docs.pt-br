---
title: Ferramentas da CLI (Interface de Linha de Comando) do .NET Core
description: Uma visão geral das ferramentas e recursos da CLI (Interface de linha de comando) do .NET Core.
ms.date: 08/14/2017
ms.openlocfilehash: f19dcb19fb9d0203b3d3795c3fdc0b026c4c60e3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163209"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="f83d4-103">Ferramentas da CLI (Interface de linha de comando) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f83d4-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="f83d4-104">A CLI (interface de linha de comando) do .NET Core é uma ferramentas de plataforma cruzada para o desenvolvimento de aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="f83d4-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="f83d4-105">A CLI é uma base sobre a qual as ferramentas de nível superior, como IDEs (ambientes de desenvolvimento integrado), editores e orquestradores de compilação, podem ser REST.</span><span class="sxs-lookup"><span data-stu-id="f83d4-105">The CLI is a foundation upon which higher-level tools, such as integrated development environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="f83d4-106">Instalação</span><span class="sxs-lookup"><span data-stu-id="f83d4-106">Installation</span></span>

<span data-ttu-id="f83d4-107">Use os instaladores nativos ou os scripts do shell de instalação:</span><span class="sxs-lookup"><span data-stu-id="f83d4-107">Either use the native installers or use the installation shell scripts:</span></span>

- <span data-ttu-id="f83d4-108">Os instaladores nativos são usados principalmente nas máquinas de desenvolvedores e usam o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo, pacotes DEB no Ubuntu ou MSI no Windows.</span><span class="sxs-lookup"><span data-stu-id="f83d4-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="f83d4-109">Esses instaladores instalam e configuram o ambiente para uso imediato do desenvolvedor, mas exigem privilégios administrativos no computador.</span><span class="sxs-lookup"><span data-stu-id="f83d4-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="f83d4-110">Veja as instruções de instalação no [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="f83d4-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
- <span data-ttu-id="f83d4-111">Os scripts de shell são usados principalmente para configurar servidores de build ou para quando você quiser instalar as ferramentas sem privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="f83d4-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="f83d4-112">A instalação de scripts não instala os pré-requisitos na máquina, que devem ser instalados manualmente.</span><span class="sxs-lookup"><span data-stu-id="f83d4-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="f83d4-113">Para saber mais, veja o [tópico de referência do script de instalação](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f83d4-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="f83d4-114">Para saber mais sobre como configurar a CLI no servidor de compilação de CI (integração contínua), confira [Usar o SDK e ferramentas do .NET Core na CI (Integração Contínua)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="f83d4-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="f83d4-115">Por padrão, a CLI instala lado a lado (SxS), para que várias versões das ferramentas da CLI possam coexistir em um único computador.</span><span class="sxs-lookup"><span data-stu-id="f83d4-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="f83d4-116">Veja com mais detalhes como determinar qual versão é usada em um computador no qual várias versões estão instaladas na seção [Driver](#driver).</span><span class="sxs-lookup"><span data-stu-id="f83d4-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="f83d4-117">Comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="f83d4-117">CLI commands</span></span>

<span data-ttu-id="f83d4-118">Os comandos a seguir são instalados por padrão:</span><span class="sxs-lookup"><span data-stu-id="f83d4-118">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f83d4-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f83d4-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f83d4-120">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="f83d4-120">**Basic commands**</span></span>

- [<span data-ttu-id="f83d4-121">new</span><span class="sxs-lookup"><span data-stu-id="f83d4-121">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="f83d4-122">restore</span><span class="sxs-lookup"><span data-stu-id="f83d4-122">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="f83d4-123">build</span><span class="sxs-lookup"><span data-stu-id="f83d4-123">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="f83d4-124">publish</span><span class="sxs-lookup"><span data-stu-id="f83d4-124">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="f83d4-125">run</span><span class="sxs-lookup"><span data-stu-id="f83d4-125">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="f83d4-126">test</span><span class="sxs-lookup"><span data-stu-id="f83d4-126">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="f83d4-127">vstest</span><span class="sxs-lookup"><span data-stu-id="f83d4-127">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="f83d4-128">pack</span><span class="sxs-lookup"><span data-stu-id="f83d4-128">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="f83d4-129">migrate</span><span class="sxs-lookup"><span data-stu-id="f83d4-129">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="f83d4-130">clean</span><span class="sxs-lookup"><span data-stu-id="f83d4-130">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="f83d4-131">sln</span><span class="sxs-lookup"><span data-stu-id="f83d4-131">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="f83d4-132">ajuda</span><span class="sxs-lookup"><span data-stu-id="f83d4-132">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="f83d4-133">repositório</span><span class="sxs-lookup"><span data-stu-id="f83d4-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="f83d4-134">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="f83d4-134">**Project modification commands**</span></span>

- [<span data-ttu-id="f83d4-135">add package</span><span class="sxs-lookup"><span data-stu-id="f83d4-135">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="f83d4-136">add reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-136">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="f83d4-137">remove package</span><span class="sxs-lookup"><span data-stu-id="f83d4-137">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="f83d4-138">remove reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-138">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="f83d4-139">list reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="f83d4-140">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="f83d4-140">**Advanced commands**</span></span>

- [<span data-ttu-id="f83d4-141">nuget delete</span><span class="sxs-lookup"><span data-stu-id="f83d4-141">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="f83d4-142">nuget locals</span><span class="sxs-lookup"><span data-stu-id="f83d4-142">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="f83d4-143">nuget push</span><span class="sxs-lookup"><span data-stu-id="f83d4-143">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="f83d4-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="f83d4-144">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="f83d4-145">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="f83d4-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f83d4-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f83d4-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f83d4-147">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="f83d4-147">**Basic commands**</span></span>

- [<span data-ttu-id="f83d4-148">new</span><span class="sxs-lookup"><span data-stu-id="f83d4-148">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="f83d4-149">restore</span><span class="sxs-lookup"><span data-stu-id="f83d4-149">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="f83d4-150">build</span><span class="sxs-lookup"><span data-stu-id="f83d4-150">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="f83d4-151">publish</span><span class="sxs-lookup"><span data-stu-id="f83d4-151">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="f83d4-152">run</span><span class="sxs-lookup"><span data-stu-id="f83d4-152">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="f83d4-153">test</span><span class="sxs-lookup"><span data-stu-id="f83d4-153">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="f83d4-154">vstest</span><span class="sxs-lookup"><span data-stu-id="f83d4-154">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="f83d4-155">pack</span><span class="sxs-lookup"><span data-stu-id="f83d4-155">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="f83d4-156">migrate</span><span class="sxs-lookup"><span data-stu-id="f83d4-156">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="f83d4-157">clean</span><span class="sxs-lookup"><span data-stu-id="f83d4-157">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="f83d4-158">sln</span><span class="sxs-lookup"><span data-stu-id="f83d4-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="f83d4-159">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="f83d4-159">**Project modification commands**</span></span>

- [<span data-ttu-id="f83d4-160">add package</span><span class="sxs-lookup"><span data-stu-id="f83d4-160">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="f83d4-161">add reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-161">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="f83d4-162">remove package</span><span class="sxs-lookup"><span data-stu-id="f83d4-162">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="f83d4-163">remove reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-163">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="f83d4-164">list reference</span><span class="sxs-lookup"><span data-stu-id="f83d4-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="f83d4-165">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="f83d4-165">**Advanced commands**</span></span>

- [<span data-ttu-id="f83d4-166">nuget delete</span><span class="sxs-lookup"><span data-stu-id="f83d4-166">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="f83d4-167">nuget locals</span><span class="sxs-lookup"><span data-stu-id="f83d4-167">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="f83d4-168">nuget push</span><span class="sxs-lookup"><span data-stu-id="f83d4-168">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="f83d4-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="f83d4-169">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="f83d4-170">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="f83d4-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="f83d4-171">A CLI adota um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos.</span><span class="sxs-lookup"><span data-stu-id="f83d4-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="f83d4-172">Para saber mais, confira o tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="f83d4-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="f83d4-173">Estrutura de comando</span><span class="sxs-lookup"><span data-stu-id="f83d4-173">Command structure</span></span>

<span data-ttu-id="f83d4-174">A estrutura de comando CLI consiste no [driver ("dotnet")](#driver), [do comando](#command) e possivelmente de [opções](#options) e [argumentos](#arguments) de comando.</span><span class="sxs-lookup"><span data-stu-id="f83d4-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="f83d4-175">É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:</span><span class="sxs-lookup"><span data-stu-id="f83d4-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f83d4-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f83d4-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f83d4-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f83d4-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="f83d4-178">Driver</span><span class="sxs-lookup"><span data-stu-id="f83d4-178">Driver</span></span>

<span data-ttu-id="f83d4-179">O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando.</span><span class="sxs-lookup"><span data-stu-id="f83d4-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="f83d4-180">Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="f83d4-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="f83d4-181">Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="f83d4-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="f83d4-182">Se você quiser usar uma versão específica do .NET Core Runtime, use a opção `--fx-version <VERSION>` (consulte a referência [do comando dotnet](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="f83d4-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="f83d4-183">Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI.</span><span class="sxs-lookup"><span data-stu-id="f83d4-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="f83d4-184">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f83d4-184">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="f83d4-185">Primeiro, o driver determina a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="f83d4-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="f83d4-186">Se não houver uma ['global.json'](global-json.md), a versão mais recente do SDK disponível será usada.</span><span class="sxs-lookup"><span data-stu-id="f83d4-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="f83d4-187">Isso pode ser uma versão prévia ou estável, dependendo do que há de mais recente no computador.</span><span class="sxs-lookup"><span data-stu-id="f83d4-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="f83d4-188">Depois que a versão do SDK é determinada, ela executa o comando.</span><span class="sxs-lookup"><span data-stu-id="f83d4-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="f83d4-189">{1&gt;Comando&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f83d4-189">Command</span></span>

<span data-ttu-id="f83d4-190">O comando executa uma ação.</span><span class="sxs-lookup"><span data-stu-id="f83d4-190">The command performs an action.</span></span> <span data-ttu-id="f83d4-191">Por exemplo, `dotnet build` compila código.</span><span class="sxs-lookup"><span data-stu-id="f83d4-191">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="f83d4-192">`dotnet publish` publica o código.</span><span class="sxs-lookup"><span data-stu-id="f83d4-192">`dotnet publish` publishes code.</span></span> <span data-ttu-id="f83d4-193">Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="f83d4-193">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="f83d4-194">Arguments</span><span class="sxs-lookup"><span data-stu-id="f83d4-194">Arguments</span></span>

<span data-ttu-id="f83d4-195">Os argumentos que você passa na linha de comando são aqueles do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="f83d4-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="f83d4-196">Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="f83d4-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="f83d4-197">Opções</span><span class="sxs-lookup"><span data-stu-id="f83d4-197">Options</span></span>

<span data-ttu-id="f83d4-198">As opções que você passa na linha de comando são aquelas do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="f83d4-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="f83d4-199">Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="f83d4-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="f83d4-200">Migração do project.json</span><span class="sxs-lookup"><span data-stu-id="f83d4-200">Migration from project.json</span></span>

<span data-ttu-id="f83d4-201">Se você tiver usado as ferramentas da Visualização 2 para produzir projetos baseados em *project.json*, veja o tópico [dotnet migrate](dotnet-migrate.md) para saber mais sobre como migrar seu projeto para MSBuild/ *.csproj* para uso com as ferramentas de versão.</span><span class="sxs-lookup"><span data-stu-id="f83d4-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="f83d4-202">Para projetos do .NET Core criados antes do lançamento das ferramentas da Versão prévia 2, siga as orientações descritas em [Migrando do DNX para a CLI do .NET Core (project.json)](../migration/from-dnx.md) para atualizar o projeto manualmente e, depois, use `dotnet migrate` ou atualize os projetos diretamente.</span><span class="sxs-lookup"><span data-stu-id="f83d4-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f83d4-203">Veja também</span><span class="sxs-lookup"><span data-stu-id="f83d4-203">See also</span></span>

- [<span data-ttu-id="f83d4-204">Repositório do GitHub dotnet/CLI</span><span class="sxs-lookup"><span data-stu-id="f83d4-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="f83d4-205">Guia de instalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f83d4-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
