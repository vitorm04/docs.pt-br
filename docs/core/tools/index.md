---
title: Ferramentas da CLI (Interface de Linha de Comando) do .NET Core
description: Uma visão geral das ferramentas e recursos da CLI (Interface de linha de comando) do .NET Core.
ms.date: 08/14/2017
ms.custom: seodec18
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="22ce6-103">Ferramentas da CLI (Interface de linha de comando) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="22ce6-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="22ce6-104">A CLI (Interface de linha de comando) do .NET Core é uma nova cadeia de ferramentas de plataforma cruzada para desenvolvimento de aplicativos em .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22ce6-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="22ce6-105">A CLI é a base na qual outras ferramentas de nível superior, como IDEs (Ambientes de Desenvolvimento Integrado), editores e orquestradores de build, se baseiam.</span><span class="sxs-lookup"><span data-stu-id="22ce6-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="22ce6-106">Instalação</span><span class="sxs-lookup"><span data-stu-id="22ce6-106">Installation</span></span>

<span data-ttu-id="22ce6-107">Use os instaladores nativos ou os scripts do shell de instalação:</span><span class="sxs-lookup"><span data-stu-id="22ce6-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="22ce6-108">Os instaladores nativos são usados principalmente nas máquinas de desenvolvedores e usam o mecanismo de instalação nativo de cada plataforma com suporte, por exemplo, pacotes DEB no Ubuntu ou MSI no Windows.</span><span class="sxs-lookup"><span data-stu-id="22ce6-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="22ce6-109">Esses instaladores instalam e configuram o ambiente para uso imediato do desenvolvedor, mas exigem privilégios administrativos no computador.</span><span class="sxs-lookup"><span data-stu-id="22ce6-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="22ce6-110">Veja as instruções de instalação no [Guia de instalação do .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="22ce6-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="22ce6-111">Os scripts de shell são usados principalmente para configurar servidores de build ou para quando você quiser instalar as ferramentas sem privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="22ce6-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="22ce6-112">A instalação de scripts não instala os pré-requisitos na máquina, que devem ser instalados manualmente.</span><span class="sxs-lookup"><span data-stu-id="22ce6-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="22ce6-113">Para saber mais, veja o [tópico de referência do script de instalação](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="22ce6-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="22ce6-114">Para saber mais sobre como configurar a CLI no servidor de compilação de CI (integração contínua), confira [Usar o SDK e ferramentas do .NET Core na CI (Integração Contínua)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="22ce6-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="22ce6-115">Por padrão, a CLI instala lado a lado (SxS), para que várias versões das ferramentas da CLI possam coexistir em um único computador.</span><span class="sxs-lookup"><span data-stu-id="22ce6-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="22ce6-116">Veja com mais detalhes como determinar qual versão é usada em um computador no qual várias versões estão instaladas na seção [Driver](#driver).</span><span class="sxs-lookup"><span data-stu-id="22ce6-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="22ce6-117">Comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="22ce6-117">CLI commands</span></span>

<span data-ttu-id="22ce6-118">Os comandos a seguir são instalados por padrão:</span><span class="sxs-lookup"><span data-stu-id="22ce6-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="22ce6-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="22ce6-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="22ce6-120">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="22ce6-120">**Basic commands**</span></span>

* [<span data-ttu-id="22ce6-121">new</span><span class="sxs-lookup"><span data-stu-id="22ce6-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="22ce6-122">restore</span><span class="sxs-lookup"><span data-stu-id="22ce6-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="22ce6-123">build</span><span class="sxs-lookup"><span data-stu-id="22ce6-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="22ce6-124">publish</span><span class="sxs-lookup"><span data-stu-id="22ce6-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="22ce6-125">run</span><span class="sxs-lookup"><span data-stu-id="22ce6-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="22ce6-126">test</span><span class="sxs-lookup"><span data-stu-id="22ce6-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="22ce6-127">vstest</span><span class="sxs-lookup"><span data-stu-id="22ce6-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="22ce6-128">pack</span><span class="sxs-lookup"><span data-stu-id="22ce6-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="22ce6-129">migrate</span><span class="sxs-lookup"><span data-stu-id="22ce6-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="22ce6-130">clean</span><span class="sxs-lookup"><span data-stu-id="22ce6-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="22ce6-131">sln</span><span class="sxs-lookup"><span data-stu-id="22ce6-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="22ce6-132">ajuda</span><span class="sxs-lookup"><span data-stu-id="22ce6-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="22ce6-133">repositório</span><span class="sxs-lookup"><span data-stu-id="22ce6-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="22ce6-134">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="22ce6-134">**Project modification commands**</span></span>

* [<span data-ttu-id="22ce6-135">add package</span><span class="sxs-lookup"><span data-stu-id="22ce6-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="22ce6-136">add reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="22ce6-137">remove package</span><span class="sxs-lookup"><span data-stu-id="22ce6-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="22ce6-138">remove reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="22ce6-139">list reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="22ce6-140">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="22ce6-140">**Advanced commands**</span></span>

* [<span data-ttu-id="22ce6-141">nuget delete</span><span class="sxs-lookup"><span data-stu-id="22ce6-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="22ce6-142">nuget locals</span><span class="sxs-lookup"><span data-stu-id="22ce6-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="22ce6-143">nuget push</span><span class="sxs-lookup"><span data-stu-id="22ce6-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="22ce6-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="22ce6-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="22ce6-145">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="22ce6-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22ce6-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22ce6-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="22ce6-147">**Comandos básicos**</span><span class="sxs-lookup"><span data-stu-id="22ce6-147">**Basic commands**</span></span>

* [<span data-ttu-id="22ce6-148">new</span><span class="sxs-lookup"><span data-stu-id="22ce6-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="22ce6-149">restore</span><span class="sxs-lookup"><span data-stu-id="22ce6-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="22ce6-150">build</span><span class="sxs-lookup"><span data-stu-id="22ce6-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="22ce6-151">publish</span><span class="sxs-lookup"><span data-stu-id="22ce6-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="22ce6-152">run</span><span class="sxs-lookup"><span data-stu-id="22ce6-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="22ce6-153">test</span><span class="sxs-lookup"><span data-stu-id="22ce6-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="22ce6-154">vstest</span><span class="sxs-lookup"><span data-stu-id="22ce6-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="22ce6-155">pack</span><span class="sxs-lookup"><span data-stu-id="22ce6-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="22ce6-156">migrate</span><span class="sxs-lookup"><span data-stu-id="22ce6-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="22ce6-157">clean</span><span class="sxs-lookup"><span data-stu-id="22ce6-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="22ce6-158">sln</span><span class="sxs-lookup"><span data-stu-id="22ce6-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="22ce6-159">**Comandos de modificação de projeto**</span><span class="sxs-lookup"><span data-stu-id="22ce6-159">**Project modification commands**</span></span>

* [<span data-ttu-id="22ce6-160">add package</span><span class="sxs-lookup"><span data-stu-id="22ce6-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="22ce6-161">add reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="22ce6-162">remove package</span><span class="sxs-lookup"><span data-stu-id="22ce6-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="22ce6-163">remove reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="22ce6-164">list reference</span><span class="sxs-lookup"><span data-stu-id="22ce6-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="22ce6-165">**Comandos avançados**</span><span class="sxs-lookup"><span data-stu-id="22ce6-165">**Advanced commands**</span></span>

* [<span data-ttu-id="22ce6-166">nuget delete</span><span class="sxs-lookup"><span data-stu-id="22ce6-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="22ce6-167">nuget locals</span><span class="sxs-lookup"><span data-stu-id="22ce6-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="22ce6-168">nuget push</span><span class="sxs-lookup"><span data-stu-id="22ce6-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="22ce6-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="22ce6-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="22ce6-170">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="22ce6-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="22ce6-171">A CLI adota um modelo de extensibilidade que permite especificar ferramentas adicionais para seus projetos.</span><span class="sxs-lookup"><span data-stu-id="22ce6-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="22ce6-172">Para saber mais, confira o tópico [Modelo de extensibilidade da CLI do .NET Core](extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="22ce6-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="22ce6-173">Estrutura de comando</span><span class="sxs-lookup"><span data-stu-id="22ce6-173">Command structure</span></span>

<span data-ttu-id="22ce6-174">A estrutura de comando CLI consiste do [driver ("dotnet")](#driver), [do comando (ou "verbo")](#command-verb)e possivelmente de [opções](#options) e [argumentos](#arguments) de comando.</span><span class="sxs-lookup"><span data-stu-id="22ce6-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="22ce6-175">É possível ver esse padrão na maioria das operações de CLI, como ao criar um novo aplicativo de console e executá-lo a partir da linha de comando, como mostram os comandos a seguir quando executados a partir de um diretório chamado *my_app*:</span><span class="sxs-lookup"><span data-stu-id="22ce6-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="22ce6-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="22ce6-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22ce6-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22ce6-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="22ce6-178">Driver</span><span class="sxs-lookup"><span data-stu-id="22ce6-178">Driver</span></span>

<span data-ttu-id="22ce6-179">O driver é chamado [dotnet](dotnet.md) e tem duas responsabilidades, executar um [aplicativo dependente da estrutura](../deploying/index.md) ou executar um comando.</span><span class="sxs-lookup"><span data-stu-id="22ce6-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> <span data-ttu-id="22ce6-180">A única vez em que `dotnet` é usado sem um comando é para iniciar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="22ce6-180">The only time `dotnet` is used without a command is when it's used to start an application.</span></span>

<span data-ttu-id="22ce6-181">Para executar um aplicativo dependente da estrutura, especifique o aplicativo após o driver, por exemplo, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="22ce6-181">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="22ce6-182">Ao executar o comando na pasta onde está a DLL do aplicativo, basta executar `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="22ce6-182">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span>

<span data-ttu-id="22ce6-183">Quando você fornece um comando para o driver, `dotnet.exe` inicia o processo de execução do comando da CLI.</span><span class="sxs-lookup"><span data-stu-id="22ce6-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="22ce6-184">Primeiro, o driver determina a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="22ce6-184">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="22ce6-185">Se a versão não for especificada nas opções de comando, o driver usará a versão mais recente disponível.</span><span class="sxs-lookup"><span data-stu-id="22ce6-185">If the version isn't specified in the command options, the driver uses the latest version available.</span></span> <span data-ttu-id="22ce6-186">Para especificar uma versão diferente da versão instalada mais recentemente, use a opção `--fx-version <VERSION>` (veja a referência ao [comando dotnet](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="22ce6-186">To specify a version other than the latest installed version, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span> <span data-ttu-id="22ce6-187">Depois que a versão do SDK for determinada, o driver executará o comando.</span><span class="sxs-lookup"><span data-stu-id="22ce6-187">Once the SDK version is determined, the driver executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="22ce6-188">Comando ("verbo")</span><span class="sxs-lookup"><span data-stu-id="22ce6-188">Command ("verb")</span></span>

<span data-ttu-id="22ce6-189">O comando (ou "verbo") é simplesmente um comando que executa uma ação.</span><span class="sxs-lookup"><span data-stu-id="22ce6-189">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="22ce6-190">Por exemplo, `dotnet build` compila seu código.</span><span class="sxs-lookup"><span data-stu-id="22ce6-190">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="22ce6-191">`dotnet publish` publica o código.</span><span class="sxs-lookup"><span data-stu-id="22ce6-191">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="22ce6-192">Os comandos são implementados como um aplicativo de console usando uma convenção `dotnet {verb}`.</span><span class="sxs-lookup"><span data-stu-id="22ce6-192">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="22ce6-193">Arguments</span><span class="sxs-lookup"><span data-stu-id="22ce6-193">Arguments</span></span>

<span data-ttu-id="22ce6-194">Os argumentos que você passa na linha de comando são aqueles do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="22ce6-194">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="22ce6-195">Por exemplo, quando você executa `dotnet publish my_app.csproj`, o argumento `my_app.csproj` indica o projeto a ser publicado e é passado para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="22ce6-195">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="22ce6-196">Opções</span><span class="sxs-lookup"><span data-stu-id="22ce6-196">Options</span></span>

<span data-ttu-id="22ce6-197">As opções que você passa na linha de comando são aquelas do comando invocado.</span><span class="sxs-lookup"><span data-stu-id="22ce6-197">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="22ce6-198">Por exemplo, quando você executa `dotnet publish --output /build_output`, a opção `--output` e seu valor são passados para o comando `publish`.</span><span class="sxs-lookup"><span data-stu-id="22ce6-198">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="22ce6-199">Migração do project.json</span><span class="sxs-lookup"><span data-stu-id="22ce6-199">Migration from project.json</span></span>

<span data-ttu-id="22ce6-200">Se você tiver usado as ferramentas da Visualização 2 para produzir projetos baseados em *project.json*, veja o tópico [dotnet migrate](dotnet-migrate.md) para saber mais sobre como migrar seu projeto para MSBuild/*.csproj* para uso com as ferramentas de versão.</span><span class="sxs-lookup"><span data-stu-id="22ce6-200">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="22ce6-201">Para projetos do .NET Core criados antes do lançamento das ferramentas da Versão prévia 2, siga as orientações descritas em [Migrando do DNX para a CLI do .NET Core (project.json)](../migration/from-dnx.md) para atualizar o projeto manualmente e, depois, use `dotnet migrate` ou atualize os projetos diretamente.</span><span class="sxs-lookup"><span data-stu-id="22ce6-201">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="22ce6-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ce6-202">See also</span></span>

- [<span data-ttu-id="22ce6-203">Repositório do GitHub dotnet/CLI</span><span class="sxs-lookup"><span data-stu-id="22ce6-203">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="22ce6-204">Guia de instalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="22ce6-204">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
