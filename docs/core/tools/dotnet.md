---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
ms.date: 06/04/2018
ms.openlocfilehash: 2134bf8ed66157619499b027f01d39e03e84411f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859549"
---
# <a name="dotnet-command"></a><span data-ttu-id="d76cf-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="d76cf-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d76cf-104">Nome</span><span class="sxs-lookup"><span data-stu-id="d76cf-104">Name</span></span>

<span data-ttu-id="d76cf-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="d76cf-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d76cf-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d76cf-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d76cf-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d76cf-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d76cf-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d76cf-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d76cf-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d76cf-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="d76cf-110">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="d76cf-110">Description</span></span>

<span data-ttu-id="d76cf-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="d76cf-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="d76cf-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="d76cf-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="d76cf-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="d76cf-113">Each command defines its own arguments.</span></span> <span data-ttu-id="d76cf-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="d76cf-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="d76cf-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="d76cf-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="d76cf-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="d76cf-117">Opções</span><span class="sxs-lookup"><span data-stu-id="d76cf-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d76cf-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d76cf-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="d76cf-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="d76cf-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d76cf-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="d76cf-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d76cf-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="d76cf-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d76cf-122">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d76cf-123">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d76cf-124">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d76cf-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d76cf-125">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="d76cf-126">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="d76cf-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="d76cf-127">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="d76cf-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="d76cf-128">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="d76cf-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="d76cf-129">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="d76cf-129">`N` can be:</span></span>
* <span data-ttu-id="d76cf-130">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="d76cf-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="d76cf-131">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="d76cf-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="d76cf-132">Este é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d76cf-132">This is the default behavior.</span></span>
* <span data-ttu-id="d76cf-133">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="d76cf-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="d76cf-134">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d76cf-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d76cf-135">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d76cf-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d76cf-136">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d76cf-137">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="d76cf-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d76cf-138">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="d76cf-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d76cf-139">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d76cf-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="d76cf-140">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="d76cf-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d76cf-141">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="d76cf-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d76cf-142">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="d76cf-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d76cf-143">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d76cf-144">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d76cf-145">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d76cf-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d76cf-146">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="d76cf-147">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="d76cf-148">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d76cf-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d76cf-149">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d76cf-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d76cf-150">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d76cf-151">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="d76cf-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d76cf-152">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="d76cf-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d76cf-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d76cf-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="d76cf-154">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="d76cf-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d76cf-155">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="d76cf-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d76cf-156">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d76cf-157">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="d76cf-158">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d76cf-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="d76cf-159">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d76cf-160">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d76cf-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d76cf-161">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d76cf-162">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="d76cf-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d76cf-163">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="d76cf-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="d76cf-164">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="d76cf-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="d76cf-165">Geral</span><span class="sxs-lookup"><span data-stu-id="d76cf-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d76cf-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d76cf-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="d76cf-167">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-167">Command</span></span>                                       | <span data-ttu-id="d76cf-168">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d76cf-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d76cf-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="d76cf-170">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d76cf-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="d76cf-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="d76cf-172">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="d76cf-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="d76cf-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d76cf-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="d76cf-174">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="d76cf-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="d76cf-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d76cf-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="d76cf-176">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="d76cf-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d76cf-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d76cf-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="d76cf-178">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d76cf-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d76cf-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="d76cf-180">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d76cf-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d76cf-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d76cf-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="d76cf-182">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d76cf-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d76cf-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d76cf-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="d76cf-184">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="d76cf-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d76cf-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d76cf-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="d76cf-186">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="d76cf-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d76cf-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d76cf-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="d76cf-188">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d76cf-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d76cf-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="d76cf-190">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="d76cf-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d76cf-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d76cf-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="d76cf-192">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d76cf-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d76cf-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="d76cf-194">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d76cf-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d76cf-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="d76cf-196">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="d76cf-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d76cf-197">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d76cf-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="d76cf-198">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-198">Command</span></span>                             | <span data-ttu-id="d76cf-199">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d76cf-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d76cf-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d76cf-201">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d76cf-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d76cf-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d76cf-203">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="d76cf-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d76cf-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d76cf-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="d76cf-205">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="d76cf-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d76cf-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d76cf-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d76cf-207">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d76cf-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d76cf-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d76cf-209">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d76cf-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d76cf-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d76cf-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d76cf-211">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d76cf-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d76cf-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d76cf-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d76cf-213">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="d76cf-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d76cf-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d76cf-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d76cf-215">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="d76cf-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d76cf-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d76cf-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d76cf-217">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d76cf-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d76cf-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d76cf-219">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="d76cf-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d76cf-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d76cf-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d76cf-221">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d76cf-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d76cf-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="d76cf-223">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d76cf-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d76cf-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d76cf-225">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="d76cf-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d76cf-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d76cf-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="d76cf-227">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-227">Command</span></span>                             | <span data-ttu-id="d76cf-228">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d76cf-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d76cf-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d76cf-230">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d76cf-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d76cf-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d76cf-232">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="d76cf-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d76cf-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d76cf-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d76cf-234">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d76cf-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d76cf-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d76cf-236">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d76cf-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d76cf-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d76cf-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d76cf-238">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d76cf-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d76cf-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d76cf-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d76cf-240">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="d76cf-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d76cf-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d76cf-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d76cf-242">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="d76cf-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d76cf-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d76cf-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d76cf-244">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d76cf-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d76cf-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d76cf-246">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="d76cf-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d76cf-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d76cf-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d76cf-248">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d76cf-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d76cf-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d76cf-250">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="d76cf-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="d76cf-251">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="d76cf-251">Project references</span></span>

<span data-ttu-id="d76cf-252">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-252">Command</span></span> | <span data-ttu-id="d76cf-253">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-253">Function</span></span>
--- | ---
[<span data-ttu-id="d76cf-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="d76cf-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="d76cf-255">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d76cf-255">Adds a project reference.</span></span>
[<span data-ttu-id="d76cf-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d76cf-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="d76cf-257">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d76cf-257">Lists project references.</span></span>
[<span data-ttu-id="d76cf-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d76cf-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="d76cf-259">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d76cf-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="d76cf-260">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="d76cf-260">NuGet packages</span></span>

<span data-ttu-id="d76cf-261">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-261">Command</span></span> | <span data-ttu-id="d76cf-262">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-262">Function</span></span>
--- | ---
[<span data-ttu-id="d76cf-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d76cf-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="d76cf-264">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d76cf-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="d76cf-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="d76cf-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="d76cf-266">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d76cf-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="d76cf-267">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="d76cf-267">NuGet commands</span></span>

<span data-ttu-id="d76cf-268">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-268">Command</span></span> | <span data-ttu-id="d76cf-269">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-269">Function</span></span>
--- | ---
[<span data-ttu-id="d76cf-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="d76cf-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="d76cf-271">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="d76cf-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="d76cf-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d76cf-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="d76cf-273">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="d76cf-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="d76cf-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="d76cf-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="d76cf-275">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="d76cf-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="d76cf-276">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="d76cf-276">Global Tools commands</span></span>

<span data-ttu-id="d76cf-277">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="d76cf-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="d76cf-278">Comando</span><span class="sxs-lookup"><span data-stu-id="d76cf-278">Command</span></span> | <span data-ttu-id="d76cf-279">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-279">Function</span></span>
--- | ---
[<span data-ttu-id="d76cf-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="d76cf-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="d76cf-281">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d76cf-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="d76cf-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="d76cf-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="d76cf-283">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="d76cf-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="d76cf-284">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="d76cf-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="d76cf-285">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="d76cf-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="d76cf-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="d76cf-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="d76cf-287">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="d76cf-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="d76cf-288">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="d76cf-288">Additional tools</span></span>

<span data-ttu-id="d76cf-289">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="d76cf-290">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="d76cf-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="d76cf-291">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="d76cf-291">Tool</span></span>                                              | <span data-ttu-id="d76cf-292">Função</span><span class="sxs-lookup"><span data-stu-id="d76cf-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="d76cf-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="d76cf-293">dev-certs</span></span>                                         | <span data-ttu-id="d76cf-294">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d76cf-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="d76cf-295">ef</span><span class="sxs-lookup"><span data-stu-id="d76cf-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="d76cf-296">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="d76cf-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="d76cf-297">sql-cache</span><span class="sxs-lookup"><span data-stu-id="d76cf-297">sql-cache</span></span>                                         | <span data-ttu-id="d76cf-298">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d76cf-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="d76cf-299">user-secrets</span><span class="sxs-lookup"><span data-stu-id="d76cf-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="d76cf-300">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d76cf-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="d76cf-301">watch</span><span class="sxs-lookup"><span data-stu-id="d76cf-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="d76cf-302">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="d76cf-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="d76cf-303">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="d76cf-304">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d76cf-304">Examples</span></span>

<span data-ttu-id="d76cf-305">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d76cf-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="d76cf-306">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d76cf-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d76cf-307">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="d76cf-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="d76cf-308">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="d76cf-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="d76cf-309">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="d76cf-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d76cf-310">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d76cf-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="d76cf-311">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="d76cf-311">The global packages folder.</span></span> <span data-ttu-id="d76cf-312">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="d76cf-312">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d76cf-313">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d76cf-314">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d76cf-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d76cf-315">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d76cf-316">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d76cf-317">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d76cf-318">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="d76cf-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d76cf-319">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d76cf-320">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d76cf-321">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d76cf-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="d76cf-322">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="d76cf-323">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d76cf-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d76cf-324">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d76cf-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="d76cf-325">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="d76cf-325">The primary package cache.</span></span> <span data-ttu-id="d76cf-326">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="d76cf-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d76cf-327">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d76cf-328">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d76cf-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d76cf-329">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d76cf-330">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d76cf-331">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d76cf-332">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="d76cf-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d76cf-333">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="d76cf-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d76cf-334">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d76cf-335">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d76cf-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d76cf-336">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d76cf-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="d76cf-337">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="d76cf-337">The primary package cache.</span></span> <span data-ttu-id="d76cf-338">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="d76cf-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d76cf-339">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d76cf-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d76cf-340">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d76cf-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d76cf-341">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d76cf-342">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d76cf-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d76cf-343">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="d76cf-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
