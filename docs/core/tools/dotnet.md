---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
ms.date: 06/04/2018
ms.openlocfilehash: 081f295cc71c3cd46de465efb12f131e7b2d36d9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170829"
---
# <a name="dotnet-command"></a><span data-ttu-id="9d0bb-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="9d0bb-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9d0bb-104">Nome</span><span class="sxs-lookup"><span data-stu-id="9d0bb-104">Name</span></span>

<span data-ttu-id="9d0bb-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9d0bb-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9d0bb-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d0bb-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d0bb-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d0bb-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d0bb-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d0bb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d0bb-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="9d0bb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d0bb-110">Description</span></span>

<span data-ttu-id="9d0bb-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="9d0bb-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="9d0bb-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-113">Each command defines its own arguments.</span></span> <span data-ttu-id="9d0bb-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="9d0bb-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="9d0bb-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="9d0bb-117">Opções</span><span class="sxs-lookup"><span data-stu-id="9d0bb-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d0bb-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d0bb-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="9d0bb-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="9d0bb-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="9d0bb-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="9d0bb-122">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="9d0bb-123">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="9d0bb-124">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="9d0bb-125">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="9d0bb-126">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="9d0bb-127">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="9d0bb-128">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="9d0bb-129">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9d0bb-130">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9d0bb-131">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9d0bb-132">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="9d0bb-133">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d0bb-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d0bb-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="9d0bb-135">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="9d0bb-136">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="9d0bb-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="9d0bb-138">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="9d0bb-139">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="9d0bb-140">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="9d0bb-141">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="9d0bb-142">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="9d0bb-143">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9d0bb-144">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9d0bb-145">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9d0bb-146">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="9d0bb-147">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d0bb-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d0bb-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="9d0bb-149">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="9d0bb-150">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="9d0bb-151">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="9d0bb-152">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="9d0bb-153">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="9d0bb-154">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9d0bb-155">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9d0bb-156">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9d0bb-157">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="9d0bb-158">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="9d0bb-159">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="9d0bb-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="9d0bb-160">Geral</span><span class="sxs-lookup"><span data-stu-id="9d0bb-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d0bb-161">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d0bb-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="9d0bb-162">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-162">Command</span></span>                                       | <span data-ttu-id="9d0bb-163">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="9d0bb-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9d0bb-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="9d0bb-165">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="9d0bb-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="9d0bb-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="9d0bb-167">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="9d0bb-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9d0bb-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="9d0bb-169">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="9d0bb-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="9d0bb-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="9d0bb-171">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="9d0bb-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9d0bb-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="9d0bb-173">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="9d0bb-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9d0bb-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="9d0bb-175">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="9d0bb-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9d0bb-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="9d0bb-177">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="9d0bb-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9d0bb-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="9d0bb-179">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="9d0bb-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9d0bb-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="9d0bb-181">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="9d0bb-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9d0bb-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="9d0bb-183">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="9d0bb-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9d0bb-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="9d0bb-185">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="9d0bb-186">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9d0bb-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="9d0bb-187">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="9d0bb-188">dotnet store</span><span class="sxs-lookup"><span data-stu-id="9d0bb-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="9d0bb-189">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="9d0bb-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9d0bb-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="9d0bb-191">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d0bb-192">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d0bb-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="9d0bb-193">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-193">Command</span></span>                             | <span data-ttu-id="9d0bb-194">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="9d0bb-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9d0bb-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="9d0bb-196">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="9d0bb-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9d0bb-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="9d0bb-198">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="9d0bb-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="9d0bb-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="9d0bb-200">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="9d0bb-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9d0bb-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="9d0bb-202">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="9d0bb-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9d0bb-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="9d0bb-204">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="9d0bb-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9d0bb-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="9d0bb-206">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="9d0bb-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9d0bb-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="9d0bb-208">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="9d0bb-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9d0bb-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="9d0bb-210">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="9d0bb-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9d0bb-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="9d0bb-212">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="9d0bb-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9d0bb-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="9d0bb-214">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="9d0bb-215">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9d0bb-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="9d0bb-216">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="9d0bb-217">dotnet store</span><span class="sxs-lookup"><span data-stu-id="9d0bb-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="9d0bb-218">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="9d0bb-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9d0bb-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="9d0bb-220">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d0bb-221">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d0bb-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="9d0bb-222">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-222">Command</span></span>                             | <span data-ttu-id="9d0bb-223">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="9d0bb-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9d0bb-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="9d0bb-225">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="9d0bb-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9d0bb-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="9d0bb-227">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="9d0bb-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9d0bb-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="9d0bb-229">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="9d0bb-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9d0bb-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="9d0bb-231">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="9d0bb-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9d0bb-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="9d0bb-233">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="9d0bb-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9d0bb-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="9d0bb-235">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="9d0bb-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9d0bb-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="9d0bb-237">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="9d0bb-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9d0bb-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="9d0bb-239">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="9d0bb-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9d0bb-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="9d0bb-241">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="9d0bb-242">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9d0bb-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="9d0bb-243">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="9d0bb-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9d0bb-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="9d0bb-245">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="9d0bb-246">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="9d0bb-246">Project references</span></span>

<span data-ttu-id="9d0bb-247">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-247">Command</span></span> | <span data-ttu-id="9d0bb-248">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-248">Function</span></span>
--- | ---
[<span data-ttu-id="9d0bb-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="9d0bb-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="9d0bb-250">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-250">Adds a project reference.</span></span>
[<span data-ttu-id="9d0bb-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="9d0bb-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="9d0bb-252">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-252">Lists project references.</span></span>
[<span data-ttu-id="9d0bb-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="9d0bb-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="9d0bb-254">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="9d0bb-255">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="9d0bb-255">NuGet packages</span></span>

<span data-ttu-id="9d0bb-256">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-256">Command</span></span> | <span data-ttu-id="9d0bb-257">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-257">Function</span></span>
--- | ---
[<span data-ttu-id="9d0bb-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="9d0bb-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="9d0bb-259">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="9d0bb-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="9d0bb-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="9d0bb-261">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="9d0bb-262">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="9d0bb-262">NuGet commands</span></span>

<span data-ttu-id="9d0bb-263">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-263">Command</span></span> | <span data-ttu-id="9d0bb-264">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-264">Function</span></span>
--- | ---
[<span data-ttu-id="9d0bb-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="9d0bb-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="9d0bb-266">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="9d0bb-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="9d0bb-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="9d0bb-268">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="9d0bb-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="9d0bb-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="9d0bb-270">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="9d0bb-271">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="9d0bb-271">Global Tools commands</span></span>

<span data-ttu-id="9d0bb-272">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="9d0bb-273">Comando</span><span class="sxs-lookup"><span data-stu-id="9d0bb-273">Command</span></span> | <span data-ttu-id="9d0bb-274">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-274">Function</span></span>
--- | ---
[<span data-ttu-id="9d0bb-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="9d0bb-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="9d0bb-276">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="9d0bb-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="9d0bb-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="9d0bb-278">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="9d0bb-279">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="9d0bb-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="9d0bb-280">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="9d0bb-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="9d0bb-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="9d0bb-282">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="9d0bb-283">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="9d0bb-283">Additional tools</span></span>

<span data-ttu-id="9d0bb-284">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="9d0bb-285">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="9d0bb-286">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="9d0bb-286">Tool</span></span>                                              | <span data-ttu-id="9d0bb-287">Função</span><span class="sxs-lookup"><span data-stu-id="9d0bb-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="9d0bb-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="9d0bb-288">dev-certs</span></span>                                         | <span data-ttu-id="9d0bb-289">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="9d0bb-290">ef</span><span class="sxs-lookup"><span data-stu-id="9d0bb-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="9d0bb-291">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="9d0bb-292">sql-cache</span><span class="sxs-lookup"><span data-stu-id="9d0bb-292">sql-cache</span></span>                                         | <span data-ttu-id="9d0bb-293">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="9d0bb-294">user-secrets</span><span class="sxs-lookup"><span data-stu-id="9d0bb-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="9d0bb-295">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="9d0bb-296">watch</span><span class="sxs-lookup"><span data-stu-id="9d0bb-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="9d0bb-297">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="9d0bb-298">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="9d0bb-299">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9d0bb-299">Examples</span></span>

<span data-ttu-id="9d0bb-300">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="9d0bb-301">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9d0bb-302">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="9d0bb-303">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="9d0bb-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="9d0bb-304">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="9d0bb-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d0bb-305">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d0bb-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="9d0bb-306">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-306">The primary package cache.</span></span> <span data-ttu-id="9d0bb-307">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="9d0bb-308">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="9d0bb-309">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="9d0bb-310">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="9d0bb-311">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9d0bb-312">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="9d0bb-313">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="9d0bb-314">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="9d0bb-315">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="9d0bb-316">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="9d0bb-317">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="9d0bb-318">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d0bb-319">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d0bb-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="9d0bb-320">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-320">The primary package cache.</span></span> <span data-ttu-id="9d0bb-321">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="9d0bb-322">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="9d0bb-323">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="9d0bb-324">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="9d0bb-325">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9d0bb-326">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="9d0bb-327">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="9d0bb-328">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="9d0bb-329">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="9d0bb-330">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d0bb-331">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d0bb-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="9d0bb-332">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-332">The primary package cache.</span></span> <span data-ttu-id="9d0bb-333">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="9d0bb-334">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="9d0bb-335">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="9d0bb-336">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="9d0bb-337">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="9d0bb-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9d0bb-338">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bb-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
