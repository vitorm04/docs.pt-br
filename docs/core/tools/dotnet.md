---
title: Comando dotnet – CLI do .NET Core
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 53e8f8bab1cbaabaa7926aa68197c18843b0b637
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44079810"
---
# <a name="dotnet-command"></a><span data-ttu-id="a2827-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="a2827-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a2827-104">Nome</span><span class="sxs-lookup"><span data-stu-id="a2827-104">Name</span></span>

<span data-ttu-id="a2827-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="a2827-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2827-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a2827-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a2827-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a2827-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a2827-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a2827-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2827-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2827-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="a2827-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2827-110">Description</span></span>

<span data-ttu-id="a2827-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="a2827-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="a2827-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="a2827-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="a2827-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="a2827-113">Each command defines its own arguments.</span></span> <span data-ttu-id="a2827-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="a2827-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="a2827-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="a2827-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="a2827-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="a2827-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a2827-117">Opções</span><span class="sxs-lookup"><span data-stu-id="a2827-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a2827-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a2827-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="a2827-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="a2827-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a2827-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a2827-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a2827-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a2827-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a2827-122">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a2827-123">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a2827-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a2827-124">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a2827-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a2827-125">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="a2827-126">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="a2827-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="a2827-127">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="a2827-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="a2827-128">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="a2827-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a2827-129">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2827-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2827-130">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a2827-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2827-131">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2827-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a2827-132">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a2827-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a2827-133">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a2827-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a2827-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a2827-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="a2827-135">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="a2827-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a2827-136">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a2827-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a2827-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a2827-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a2827-138">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a2827-139">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a2827-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a2827-140">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a2827-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a2827-141">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="a2827-142">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="a2827-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a2827-143">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2827-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2827-144">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a2827-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2827-145">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2827-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a2827-146">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a2827-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a2827-147">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a2827-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2827-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2827-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="a2827-149">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a2827-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a2827-150">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a2827-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a2827-151">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a2827-152">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a2827-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a2827-153">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a2827-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a2827-154">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2827-155">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a2827-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2827-156">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2827-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a2827-157">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a2827-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a2827-158">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a2827-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="a2827-159">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="a2827-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a2827-160">Geral</span><span class="sxs-lookup"><span data-stu-id="a2827-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a2827-161">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a2827-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="a2827-162">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-162">Command</span></span>                                       | <span data-ttu-id="a2827-163">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a2827-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a2827-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a2827-165">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a2827-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a2827-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a2827-167">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="a2827-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a2827-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a2827-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a2827-169">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a2827-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a2827-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a2827-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a2827-171">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="a2827-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a2827-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a2827-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a2827-173">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a2827-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a2827-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a2827-175">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a2827-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a2827-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a2827-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a2827-177">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a2827-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a2827-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a2827-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a2827-179">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a2827-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a2827-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a2827-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a2827-181">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a2827-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a2827-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a2827-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a2827-183">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a2827-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a2827-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a2827-185">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a2827-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a2827-186">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a2827-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a2827-187">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a2827-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a2827-188">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a2827-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a2827-189">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a2827-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a2827-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a2827-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a2827-191">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a2827-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a2827-192">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a2827-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="a2827-193">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-193">Command</span></span>                             | <span data-ttu-id="a2827-194">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a2827-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a2827-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a2827-196">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a2827-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a2827-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a2827-198">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a2827-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a2827-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a2827-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="a2827-200">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="a2827-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a2827-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a2827-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a2827-202">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a2827-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a2827-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a2827-204">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a2827-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a2827-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a2827-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a2827-206">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a2827-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a2827-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a2827-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a2827-208">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a2827-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a2827-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a2827-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a2827-210">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a2827-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a2827-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a2827-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a2827-212">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a2827-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a2827-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a2827-214">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a2827-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a2827-215">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a2827-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a2827-216">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a2827-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a2827-217">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a2827-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="a2827-218">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a2827-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a2827-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a2827-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a2827-220">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a2827-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2827-221">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2827-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="a2827-222">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-222">Command</span></span>                             | <span data-ttu-id="a2827-223">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a2827-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a2827-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a2827-225">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a2827-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a2827-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a2827-227">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a2827-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a2827-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a2827-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a2827-229">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a2827-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a2827-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a2827-231">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a2827-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a2827-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a2827-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a2827-233">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a2827-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a2827-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a2827-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a2827-235">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a2827-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a2827-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a2827-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a2827-237">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a2827-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a2827-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a2827-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a2827-239">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a2827-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a2827-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a2827-241">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a2827-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a2827-242">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a2827-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a2827-243">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a2827-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a2827-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a2827-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a2827-245">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a2827-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="a2827-246">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="a2827-246">Project references</span></span>

<span data-ttu-id="a2827-247">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-247">Command</span></span> | <span data-ttu-id="a2827-248">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-248">Function</span></span>
--- | ---
[<span data-ttu-id="a2827-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a2827-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a2827-250">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a2827-250">Adds a project reference.</span></span>
[<span data-ttu-id="a2827-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a2827-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a2827-252">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a2827-252">Lists project references.</span></span>
[<span data-ttu-id="a2827-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a2827-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a2827-254">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a2827-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a2827-255">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="a2827-255">NuGet packages</span></span>

<span data-ttu-id="a2827-256">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-256">Command</span></span> | <span data-ttu-id="a2827-257">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-257">Function</span></span>
--- | ---
[<span data-ttu-id="a2827-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a2827-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a2827-259">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a2827-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="a2827-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a2827-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a2827-261">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a2827-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a2827-262">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="a2827-262">NuGet commands</span></span>

<span data-ttu-id="a2827-263">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-263">Command</span></span> | <span data-ttu-id="a2827-264">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-264">Function</span></span>
--- | ---
[<span data-ttu-id="a2827-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a2827-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a2827-266">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="a2827-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a2827-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a2827-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a2827-268">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="a2827-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a2827-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a2827-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a2827-270">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="a2827-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="a2827-271">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="a2827-271">Global Tools commands</span></span>

<span data-ttu-id="a2827-272">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="a2827-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="a2827-273">Comando</span><span class="sxs-lookup"><span data-stu-id="a2827-273">Command</span></span> | <span data-ttu-id="a2827-274">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-274">Function</span></span>
--- | ---
[<span data-ttu-id="a2827-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a2827-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a2827-276">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a2827-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="a2827-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a2827-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a2827-278">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a2827-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="a2827-279">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a2827-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a2827-280">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="a2827-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="a2827-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a2827-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a2827-282">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="a2827-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a2827-283">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="a2827-283">Additional tools</span></span>

<span data-ttu-id="a2827-284">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="a2827-285">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="a2827-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a2827-286">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="a2827-286">Tool</span></span>                                              | <span data-ttu-id="a2827-287">Função</span><span class="sxs-lookup"><span data-stu-id="a2827-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a2827-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a2827-288">dev-certs</span></span>                                         | <span data-ttu-id="a2827-289">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a2827-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a2827-290">ef</span><span class="sxs-lookup"><span data-stu-id="a2827-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a2827-291">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="a2827-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a2827-292">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a2827-292">sql-cache</span></span>                                         | <span data-ttu-id="a2827-293">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2827-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a2827-294">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a2827-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a2827-295">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a2827-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a2827-296">watch</span><span class="sxs-lookup"><span data-stu-id="a2827-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a2827-297">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="a2827-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a2827-298">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="a2827-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a2827-299">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a2827-299">Examples</span></span>

<span data-ttu-id="a2827-300">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a2827-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="a2827-301">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a2827-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a2827-302">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="a2827-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="a2827-303">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="a2827-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="a2827-304">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="a2827-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a2827-305">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a2827-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="a2827-306">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="a2827-306">The primary package cache.</span></span> <span data-ttu-id="a2827-307">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a2827-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a2827-308">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a2827-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a2827-309">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2827-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a2827-310">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a2827-311">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a2827-312">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a2827-313">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="a2827-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a2827-314">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="a2827-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a2827-315">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a2827-316">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="a2827-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="a2827-317">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="a2827-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a2827-318">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2827-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a2827-319">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a2827-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="a2827-320">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="a2827-320">The primary package cache.</span></span> <span data-ttu-id="a2827-321">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a2827-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a2827-322">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a2827-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a2827-323">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2827-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a2827-324">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a2827-325">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a2827-326">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a2827-327">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="a2827-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a2827-328">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="a2827-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a2827-329">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a2827-330">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="a2827-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2827-331">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2827-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="a2827-332">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="a2827-332">The primary package cache.</span></span> <span data-ttu-id="a2827-333">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a2827-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a2827-334">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a2827-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a2827-335">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2827-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a2827-336">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a2827-337">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a2827-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a2827-338">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a2827-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
