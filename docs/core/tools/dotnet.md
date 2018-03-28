---
title: Comando dotnet – CLI do .NET Core
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2d22124cb613152df402046541650f3262e7e202
ms.sourcegitcommit: 6f967c86dde55472440f0c8669b0e910ee3c53ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="74154-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="74154-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="74154-104">Nome</span><span class="sxs-lookup"><span data-stu-id="74154-104">Name</span></span>

<span data-ttu-id="74154-105">`dotnet` – Driver geral para executar os comandos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="74154-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74154-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="74154-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="74154-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="74154-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="74154-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="74154-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="74154-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="74154-109">Description</span></span>

<span data-ttu-id="74154-110">`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="74154-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="74154-111">Invocado por conta própria, ele fornece breve instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="74154-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="74154-112">Cada recurso específico é implementado como um comando.</span><span class="sxs-lookup"><span data-stu-id="74154-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="74154-113">Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="74154-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="74154-114">Todos os argumentos após o comando são seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="74154-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="74154-115">A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="74154-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="74154-116">Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="74154-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="74154-117">Opções</span><span class="sxs-lookup"><span data-stu-id="74154-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="74154-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="74154-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="74154-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="74154-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="74154-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="74154-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="74154-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="74154-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="74154-122">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74154-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="74154-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="74154-123">Prints out a short help for the command.</span></span> <span data-ttu-id="74154-124">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="74154-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="74154-125">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="74154-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="74154-126">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="74154-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="74154-127">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="74154-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="74154-128">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="74154-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="74154-129">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="74154-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="74154-130">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="74154-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="74154-131">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="74154-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="74154-132">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="74154-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="74154-133">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="74154-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="74154-134">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74154-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="74154-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="74154-135">Prints out a short help for the command.</span></span> <span data-ttu-id="74154-136">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="74154-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="74154-137">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="74154-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="74154-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="74154-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="74154-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="74154-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="74154-140">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="74154-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="74154-141">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="74154-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="74154-142">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="74154-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="74154-143">Geral</span><span class="sxs-lookup"><span data-stu-id="74154-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="74154-144">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="74154-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="74154-145">Comando</span><span class="sxs-lookup"><span data-stu-id="74154-145">Command</span></span>                             | <span data-ttu-id="74154-146">Função</span><span class="sxs-lookup"><span data-stu-id="74154-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="74154-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="74154-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="74154-148">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74154-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="74154-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="74154-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="74154-150">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="74154-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="74154-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="74154-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="74154-152">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="74154-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="74154-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="74154-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="74154-154">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74154-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="74154-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="74154-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="74154-156">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="74154-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="74154-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="74154-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="74154-158">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="74154-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="74154-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="74154-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="74154-160">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="74154-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="74154-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="74154-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="74154-162">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="74154-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="74154-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="74154-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="74154-164">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74154-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="74154-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="74154-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="74154-166">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="74154-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="74154-167">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="74154-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="74154-168">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="74154-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="74154-169">dotnet store</span><span class="sxs-lookup"><span data-stu-id="74154-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="74154-170">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="74154-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="74154-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="74154-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="74154-172">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="74154-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="74154-173">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="74154-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="74154-174">Comando</span><span class="sxs-lookup"><span data-stu-id="74154-174">Command</span></span>                             | <span data-ttu-id="74154-175">Função</span><span class="sxs-lookup"><span data-stu-id="74154-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="74154-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="74154-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="74154-177">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74154-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="74154-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="74154-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="74154-179">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="74154-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="74154-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="74154-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="74154-181">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74154-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="74154-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="74154-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="74154-183">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="74154-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="74154-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="74154-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="74154-185">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="74154-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="74154-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="74154-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="74154-187">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="74154-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="74154-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="74154-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="74154-189">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="74154-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="74154-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="74154-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="74154-191">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74154-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="74154-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="74154-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="74154-193">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="74154-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="74154-194">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="74154-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="74154-195">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="74154-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="74154-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="74154-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="74154-197">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="74154-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="74154-198">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="74154-198">Project references</span></span>

<span data-ttu-id="74154-199">Comando</span><span class="sxs-lookup"><span data-stu-id="74154-199">Command</span></span> | <span data-ttu-id="74154-200">Função</span><span class="sxs-lookup"><span data-stu-id="74154-200">Function</span></span>
--- | ---
[<span data-ttu-id="74154-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="74154-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="74154-202">Adicionar uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="74154-202">Add a project reference.</span></span>
[<span data-ttu-id="74154-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="74154-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="74154-204">Listar referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="74154-204">List project references.</span></span>
[<span data-ttu-id="74154-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="74154-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="74154-206">Remover uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="74154-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="74154-207">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="74154-207">NuGet packages</span></span>

<span data-ttu-id="74154-208">Comando</span><span class="sxs-lookup"><span data-stu-id="74154-208">Command</span></span> | <span data-ttu-id="74154-209">Função</span><span class="sxs-lookup"><span data-stu-id="74154-209">Function</span></span>
--- | ---
[<span data-ttu-id="74154-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="74154-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="74154-211">Adicionar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="74154-211">Add a NuGet package.</span></span>
[<span data-ttu-id="74154-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="74154-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="74154-213">Remover um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="74154-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="74154-214">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="74154-214">NuGet commands</span></span>

<span data-ttu-id="74154-215">Comando</span><span class="sxs-lookup"><span data-stu-id="74154-215">Command</span></span> | <span data-ttu-id="74154-216">Função</span><span class="sxs-lookup"><span data-stu-id="74154-216">Function</span></span>
--- | ---
[<span data-ttu-id="74154-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="74154-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="74154-218">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="74154-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="74154-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="74154-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="74154-220">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="74154-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="74154-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="74154-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="74154-222">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="74154-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="74154-223">Exemplos</span><span class="sxs-lookup"><span data-stu-id="74154-223">Examples</span></span>

<span data-ttu-id="74154-224">Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:</span><span class="sxs-lookup"><span data-stu-id="74154-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="74154-225">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="74154-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="74154-226">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="74154-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="74154-227">Execute um aplicativo dependente do framework chamado `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="74154-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="74154-228">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="74154-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="74154-229">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="74154-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="74154-230">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="74154-230">The primary package cache.</span></span> <span data-ttu-id="74154-231">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="74154-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="74154-232">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="74154-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="74154-233">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="74154-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="74154-234">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="74154-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="74154-235">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="74154-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="74154-236">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="74154-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="74154-237">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="74154-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="74154-238">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="74154-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="74154-239">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="74154-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="74154-240">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="74154-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="74154-241">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="74154-241">The primary package cache.</span></span> <span data-ttu-id="74154-242">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="74154-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="74154-243">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="74154-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="74154-244">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="74154-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="74154-245">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="74154-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="74154-246">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="74154-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
