---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
ms.date: 06/04/2018
ms.openlocfilehash: 53eb96ee6fe809b2e6e42eec4e7e9b5f7c5edf2a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066435"
---
# <a name="dotnet-command"></a><span data-ttu-id="8630b-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="8630b-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8630b-104">Nome</span><span class="sxs-lookup"><span data-stu-id="8630b-104">Name</span></span>

<span data-ttu-id="8630b-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="8630b-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8630b-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="8630b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8630b-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8630b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8630b-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8630b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8630b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8630b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="8630b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8630b-110">Description</span></span>

<span data-ttu-id="8630b-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="8630b-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="8630b-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="8630b-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="8630b-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="8630b-113">Each command defines its own arguments.</span></span> <span data-ttu-id="8630b-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="8630b-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="8630b-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="8630b-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="8630b-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="8630b-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="8630b-117">Opções</span><span class="sxs-lookup"><span data-stu-id="8630b-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8630b-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8630b-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="8630b-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="8630b-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="8630b-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="8630b-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8630b-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8630b-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8630b-122">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8630b-123">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="8630b-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="8630b-124">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8630b-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="8630b-125">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="8630b-126">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="8630b-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="8630b-127">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="8630b-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="8630b-128">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="8630b-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="8630b-129">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="8630b-129">`N` can be:</span></span>
 * <span data-ttu-id="8630b-130">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="8630b-130">`0` - Disable even minor version roll forward.</span></span>
 * <span data-ttu-id="8630b-131">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8630b-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="8630b-132">Este é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="8630b-132">This is the default behavior.</span></span>
 * <span data-ttu-id="8630b-133">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="8630b-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="8630b-134">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="8630b-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8630b-135">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="8630b-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8630b-136">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8630b-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8630b-137">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="8630b-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="8630b-138">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="8630b-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8630b-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8630b-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="8630b-140">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="8630b-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="8630b-141">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="8630b-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8630b-142">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8630b-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8630b-143">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8630b-144">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="8630b-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="8630b-145">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8630b-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="8630b-146">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="8630b-147">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="8630b-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="8630b-148">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="8630b-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8630b-149">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="8630b-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8630b-150">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8630b-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8630b-151">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="8630b-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="8630b-152">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="8630b-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8630b-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8630b-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="8630b-154">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="8630b-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8630b-155">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8630b-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8630b-156">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8630b-157">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="8630b-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="8630b-158">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8630b-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="8630b-159">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8630b-160">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="8630b-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8630b-161">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8630b-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8630b-162">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="8630b-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="8630b-163">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="8630b-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="8630b-164">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="8630b-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="8630b-165">Geral</span><span class="sxs-lookup"><span data-stu-id="8630b-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8630b-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8630b-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="8630b-167">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-167">Command</span></span>                                       | <span data-ttu-id="8630b-168">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8630b-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8630b-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="8630b-170">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8630b-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="8630b-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="8630b-172">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="8630b-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="8630b-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8630b-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="8630b-174">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="8630b-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="8630b-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="8630b-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="8630b-176">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="8630b-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="8630b-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8630b-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="8630b-178">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8630b-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8630b-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="8630b-180">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8630b-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8630b-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8630b-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="8630b-182">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8630b-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8630b-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8630b-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="8630b-184">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="8630b-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8630b-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8630b-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="8630b-186">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="8630b-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8630b-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8630b-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="8630b-188">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8630b-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8630b-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="8630b-190">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="8630b-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8630b-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8630b-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="8630b-192">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="8630b-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8630b-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="8630b-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="8630b-194">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8630b-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="8630b-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8630b-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="8630b-196">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="8630b-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8630b-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8630b-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="8630b-198">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-198">Command</span></span>                             | <span data-ttu-id="8630b-199">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8630b-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8630b-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8630b-201">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8630b-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8630b-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8630b-203">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="8630b-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8630b-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="8630b-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="8630b-205">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="8630b-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="8630b-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8630b-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8630b-207">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8630b-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8630b-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8630b-209">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8630b-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8630b-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8630b-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8630b-211">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8630b-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8630b-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8630b-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8630b-213">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="8630b-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8630b-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8630b-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8630b-215">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="8630b-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8630b-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8630b-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8630b-217">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8630b-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8630b-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8630b-219">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="8630b-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8630b-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8630b-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8630b-221">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="8630b-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8630b-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="8630b-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="8630b-223">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8630b-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="8630b-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8630b-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8630b-225">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="8630b-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8630b-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8630b-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="8630b-227">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-227">Command</span></span>                             | <span data-ttu-id="8630b-228">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8630b-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8630b-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8630b-230">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8630b-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8630b-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8630b-232">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="8630b-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8630b-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8630b-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8630b-234">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8630b-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8630b-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8630b-236">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8630b-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8630b-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8630b-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8630b-238">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8630b-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8630b-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8630b-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8630b-240">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="8630b-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8630b-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8630b-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8630b-242">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="8630b-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8630b-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8630b-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8630b-244">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8630b-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8630b-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8630b-246">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="8630b-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8630b-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8630b-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8630b-248">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="8630b-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8630b-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8630b-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8630b-250">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="8630b-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="8630b-251">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="8630b-251">Project references</span></span>

<span data-ttu-id="8630b-252">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-252">Command</span></span> | <span data-ttu-id="8630b-253">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-253">Function</span></span>
--- | ---
[<span data-ttu-id="8630b-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8630b-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="8630b-255">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8630b-255">Adds a project reference.</span></span>
[<span data-ttu-id="8630b-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="8630b-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="8630b-257">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8630b-257">Lists project references.</span></span>
[<span data-ttu-id="8630b-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="8630b-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="8630b-259">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8630b-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="8630b-260">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="8630b-260">NuGet packages</span></span>

<span data-ttu-id="8630b-261">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-261">Command</span></span> | <span data-ttu-id="8630b-262">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-262">Function</span></span>
--- | ---
[<span data-ttu-id="8630b-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="8630b-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="8630b-264">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8630b-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="8630b-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="8630b-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="8630b-266">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8630b-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="8630b-267">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="8630b-267">NuGet commands</span></span>

<span data-ttu-id="8630b-268">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-268">Command</span></span> | <span data-ttu-id="8630b-269">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-269">Function</span></span>
--- | ---
[<span data-ttu-id="8630b-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="8630b-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="8630b-271">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="8630b-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="8630b-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="8630b-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="8630b-273">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="8630b-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="8630b-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="8630b-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="8630b-275">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="8630b-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="8630b-276">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="8630b-276">Global Tools commands</span></span>

<span data-ttu-id="8630b-277">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="8630b-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="8630b-278">Comando</span><span class="sxs-lookup"><span data-stu-id="8630b-278">Command</span></span> | <span data-ttu-id="8630b-279">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-279">Function</span></span>
--- | ---
[<span data-ttu-id="8630b-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="8630b-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="8630b-281">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8630b-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="8630b-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="8630b-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="8630b-283">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="8630b-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="8630b-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="8630b-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="8630b-285">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="8630b-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="8630b-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="8630b-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="8630b-287">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="8630b-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="8630b-288">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="8630b-288">Additional tools</span></span>

<span data-ttu-id="8630b-289">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="8630b-290">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="8630b-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="8630b-291">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="8630b-291">Tool</span></span>                                              | <span data-ttu-id="8630b-292">Função</span><span class="sxs-lookup"><span data-stu-id="8630b-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="8630b-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="8630b-293">dev-certs</span></span>                                         | <span data-ttu-id="8630b-294">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8630b-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="8630b-295">ef</span><span class="sxs-lookup"><span data-stu-id="8630b-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="8630b-296">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="8630b-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="8630b-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="8630b-297">sql-cache</span></span>                                         | <span data-ttu-id="8630b-298">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8630b-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="8630b-299">user-secrets</span><span class="sxs-lookup"><span data-stu-id="8630b-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="8630b-300">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8630b-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="8630b-301">watch</span><span class="sxs-lookup"><span data-stu-id="8630b-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="8630b-302">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="8630b-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="8630b-303">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="8630b-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="8630b-304">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8630b-304">Examples</span></span>

<span data-ttu-id="8630b-305">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="8630b-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="8630b-306">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="8630b-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8630b-307">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="8630b-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="8630b-308">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="8630b-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="8630b-309">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="8630b-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8630b-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8630b-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="8630b-311">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="8630b-311">The primary package cache.</span></span> <span data-ttu-id="8630b-312">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="8630b-312">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="8630b-313">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8630b-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="8630b-314">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8630b-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8630b-315">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="8630b-316">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8630b-317">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="8630b-318">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="8630b-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="8630b-319">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="8630b-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="8630b-320">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="8630b-321">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="8630b-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="8630b-322">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="8630b-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="8630b-323">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="8630b-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8630b-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8630b-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="8630b-325">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="8630b-325">The primary package cache.</span></span> <span data-ttu-id="8630b-326">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="8630b-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="8630b-327">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8630b-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="8630b-328">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8630b-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8630b-329">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="8630b-330">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8630b-331">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="8630b-332">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="8630b-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="8630b-333">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="8630b-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="8630b-334">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="8630b-335">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="8630b-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8630b-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8630b-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="8630b-337">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="8630b-337">The primary package cache.</span></span> <span data-ttu-id="8630b-338">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="8630b-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="8630b-339">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8630b-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="8630b-340">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8630b-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8630b-341">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="8630b-342">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8630b-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8630b-343">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="8630b-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
