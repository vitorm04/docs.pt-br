---
title: Comando dotnet – CLI do .NET Core
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805653"
---
# <a name="dotnet-command"></a><span data-ttu-id="ef75e-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="ef75e-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ef75e-104">Nome</span><span class="sxs-lookup"><span data-stu-id="ef75e-104">Name</span></span>

<span data-ttu-id="ef75e-105">`dotnet` – Driver geral para executar os comandos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ef75e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ef75e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef75e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef75e-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef75e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef75e-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef75e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef75e-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="ef75e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef75e-110">Description</span></span>

<span data-ttu-id="ef75e-111">`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="ef75e-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="ef75e-112">Invocado por conta própria, ele fornece breve instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="ef75e-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="ef75e-113">Cada recurso específico é implementado como um comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="ef75e-114">Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="ef75e-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="ef75e-115">Todos os argumentos após o comando são seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="ef75e-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="ef75e-116">A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef75e-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="ef75e-117">Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="ef75e-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="ef75e-118">Opções</span><span class="sxs-lookup"><span data-stu-id="ef75e-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef75e-119">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef75e-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="ef75e-120">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="ef75e-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="ef75e-121">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="ef75e-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="ef75e-122">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ef75e-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="ef75e-123">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="ef75e-124">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-124">Prints out a short help for the command.</span></span> <span data-ttu-id="ef75e-125">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ef75e-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="ef75e-126">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="ef75e-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="ef75e-127">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="ef75e-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="ef75e-128">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="ef75e-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="ef75e-129">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="ef75e-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef75e-130">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef75e-131">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ef75e-132">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="ef75e-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="ef75e-133">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="ef75e-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef75e-134">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef75e-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="ef75e-135">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="ef75e-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="ef75e-136">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="ef75e-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="ef75e-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ef75e-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="ef75e-138">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="ef75e-139">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-139">Prints out a short help for the command.</span></span> <span data-ttu-id="ef75e-140">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ef75e-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="ef75e-141">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="ef75e-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="ef75e-142">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="ef75e-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef75e-143">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef75e-144">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ef75e-145">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="ef75e-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="ef75e-146">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="ef75e-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef75e-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef75e-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="ef75e-148">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="ef75e-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="ef75e-149">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ef75e-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="ef75e-150">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="ef75e-151">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-151">Prints out a short help for the command.</span></span> <span data-ttu-id="ef75e-152">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ef75e-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="ef75e-153">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="ef75e-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef75e-154">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef75e-155">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ef75e-156">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="ef75e-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="ef75e-157">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="ef75e-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="ef75e-158">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="ef75e-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="ef75e-159">Geral</span><span class="sxs-lookup"><span data-stu-id="ef75e-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef75e-160">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef75e-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="ef75e-161">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-161">Command</span></span>                                       | <span data-ttu-id="ef75e-162">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="ef75e-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ef75e-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="ef75e-164">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="ef75e-165">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="ef75e-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="ef75e-166">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="ef75e-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="ef75e-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ef75e-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="ef75e-168">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="ef75e-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="ef75e-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="ef75e-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="ef75e-170">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="ef75e-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ef75e-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="ef75e-172">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="ef75e-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ef75e-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="ef75e-174">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ef75e-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="ef75e-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ef75e-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="ef75e-176">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ef75e-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="ef75e-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ef75e-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="ef75e-178">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="ef75e-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="ef75e-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ef75e-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="ef75e-180">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="ef75e-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="ef75e-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ef75e-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="ef75e-182">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="ef75e-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ef75e-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="ef75e-184">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="ef75e-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="ef75e-185">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ef75e-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="ef75e-186">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="ef75e-187">dotnet store</span><span class="sxs-lookup"><span data-stu-id="ef75e-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="ef75e-188">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="ef75e-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ef75e-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="ef75e-190">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ef75e-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef75e-191">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef75e-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="ef75e-192">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-192">Command</span></span>                             | <span data-ttu-id="ef75e-193">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="ef75e-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ef75e-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="ef75e-195">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="ef75e-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ef75e-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="ef75e-197">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="ef75e-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="ef75e-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="ef75e-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="ef75e-199">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef75e-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="ef75e-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ef75e-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="ef75e-201">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="ef75e-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ef75e-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="ef75e-203">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ef75e-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="ef75e-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ef75e-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="ef75e-205">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ef75e-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="ef75e-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ef75e-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="ef75e-207">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="ef75e-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="ef75e-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ef75e-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="ef75e-209">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="ef75e-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="ef75e-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ef75e-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="ef75e-211">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="ef75e-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ef75e-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="ef75e-213">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="ef75e-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="ef75e-214">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ef75e-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="ef75e-215">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="ef75e-216">dotnet store</span><span class="sxs-lookup"><span data-stu-id="ef75e-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="ef75e-217">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="ef75e-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ef75e-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="ef75e-219">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ef75e-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef75e-220">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef75e-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="ef75e-221">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-221">Command</span></span>                             | <span data-ttu-id="ef75e-222">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="ef75e-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ef75e-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="ef75e-224">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="ef75e-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ef75e-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="ef75e-226">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="ef75e-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="ef75e-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ef75e-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="ef75e-228">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="ef75e-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ef75e-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="ef75e-230">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ef75e-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="ef75e-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ef75e-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="ef75e-232">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ef75e-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="ef75e-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ef75e-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="ef75e-234">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="ef75e-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="ef75e-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ef75e-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="ef75e-236">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="ef75e-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="ef75e-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ef75e-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="ef75e-238">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="ef75e-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ef75e-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="ef75e-240">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="ef75e-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="ef75e-241">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ef75e-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="ef75e-242">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="ef75e-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ef75e-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="ef75e-244">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ef75e-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="ef75e-245">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="ef75e-245">Project references</span></span>

<span data-ttu-id="ef75e-246">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-246">Command</span></span> | <span data-ttu-id="ef75e-247">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-247">Function</span></span>
--- | ---
[<span data-ttu-id="ef75e-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="ef75e-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="ef75e-249">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ef75e-249">Adds a project reference.</span></span>
[<span data-ttu-id="ef75e-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="ef75e-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="ef75e-251">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ef75e-251">Lists project references.</span></span>
[<span data-ttu-id="ef75e-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="ef75e-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="ef75e-253">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ef75e-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="ef75e-254">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="ef75e-254">NuGet packages</span></span>

<span data-ttu-id="ef75e-255">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-255">Command</span></span> | <span data-ttu-id="ef75e-256">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-256">Function</span></span>
--- | ---
[<span data-ttu-id="ef75e-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="ef75e-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="ef75e-258">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef75e-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="ef75e-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="ef75e-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="ef75e-260">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef75e-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="ef75e-261">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="ef75e-261">NuGet commands</span></span>

<span data-ttu-id="ef75e-262">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-262">Command</span></span> | <span data-ttu-id="ef75e-263">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-263">Function</span></span>
--- | ---
[<span data-ttu-id="ef75e-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="ef75e-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="ef75e-265">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="ef75e-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="ef75e-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="ef75e-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="ef75e-267">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="ef75e-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="ef75e-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="ef75e-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="ef75e-269">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="ef75e-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="ef75e-270">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="ef75e-270">Global Tools commands</span></span>

<span data-ttu-id="ef75e-271">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="ef75e-271">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="ef75e-272">Comando</span><span class="sxs-lookup"><span data-stu-id="ef75e-272">Command</span></span> | <span data-ttu-id="ef75e-273">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-273">Function</span></span>
--- | ---
[<span data-ttu-id="ef75e-274">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="ef75e-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="ef75e-275">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ef75e-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="ef75e-276">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="ef75e-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="ef75e-277">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="ef75e-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="ef75e-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="ef75e-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="ef75e-279">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="ef75e-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="ef75e-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="ef75e-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="ef75e-281">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="ef75e-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="ef75e-282">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="ef75e-282">Additional tools</span></span>

<span data-ttu-id="ef75e-283">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="ef75e-284">Essas ferramentas incluem:</span><span class="sxs-lookup"><span data-stu-id="ef75e-284">These tools include:</span></span>

| <span data-ttu-id="ef75e-285">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="ef75e-285">Tool</span></span>                                              | <span data-ttu-id="ef75e-286">Função</span><span class="sxs-lookup"><span data-stu-id="ef75e-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="ef75e-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="ef75e-287">dev-certs</span></span>                                         | <span data-ttu-id="ef75e-288">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ef75e-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="ef75e-289">ef</span><span class="sxs-lookup"><span data-stu-id="ef75e-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="ef75e-290">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="ef75e-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="ef75e-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="ef75e-291">sql-cache</span></span>                                         | <span data-ttu-id="ef75e-292">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef75e-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="ef75e-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="ef75e-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="ef75e-294">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ef75e-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="ef75e-295">watch</span><span class="sxs-lookup"><span data-stu-id="ef75e-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="ef75e-296">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="ef75e-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="ef75e-297">Para saber mais sobre cada ferramenta, execute `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="ef75e-298">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ef75e-298">Examples</span></span>

<span data-ttu-id="ef75e-299">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ef75e-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="ef75e-300">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ef75e-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ef75e-301">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="ef75e-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="ef75e-302">Execute um aplicativo dependente do framework chamado `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="ef75e-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="ef75e-303">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="ef75e-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef75e-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef75e-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="ef75e-305">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="ef75e-305">The primary package cache.</span></span> <span data-ttu-id="ef75e-306">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="ef75e-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="ef75e-307">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="ef75e-308">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ef75e-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="ef75e-309">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="ef75e-310">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="ef75e-311">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="ef75e-312">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="ef75e-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="ef75e-313">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="ef75e-314">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="ef75e-315">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="ef75e-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="ef75e-316">Desativa o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="ef75e-316">Disables minor version roll forward.</span></span> <span data-ttu-id="ef75e-317">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ef75e-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef75e-318">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef75e-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="ef75e-319">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="ef75e-319">The primary package cache.</span></span> <span data-ttu-id="ef75e-320">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="ef75e-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="ef75e-321">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="ef75e-322">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ef75e-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="ef75e-323">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="ef75e-324">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="ef75e-325">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="ef75e-326">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="ef75e-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="ef75e-327">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="ef75e-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="ef75e-328">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="ef75e-329">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="ef75e-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef75e-330">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef75e-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="ef75e-331">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="ef75e-331">The primary package cache.</span></span> <span data-ttu-id="ef75e-332">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="ef75e-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="ef75e-333">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef75e-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="ef75e-334">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ef75e-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="ef75e-335">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="ef75e-336">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ef75e-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="ef75e-337">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="ef75e-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
