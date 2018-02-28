---
title: "Comando dotnet – CLI do .NET Core"
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
author: mairaw
ms.author: mairaw
ms.date: 11/28/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: bed0876645428cdff11fa83a091fc63e64cedc8f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="0381c-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="0381c-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0381c-104">Nome</span><span class="sxs-lookup"><span data-stu-id="0381c-104">Name</span></span>

<span data-ttu-id="0381c-105">`dotnet` – Driver geral para executar os comandos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0381c-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0381c-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0381c-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0381c-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0381c-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0381c-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0381c-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="0381c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0381c-109">Description</span></span>

<span data-ttu-id="0381c-110">`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="0381c-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="0381c-111">Invocado por conta própria, ele fornece breve instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="0381c-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="0381c-112">Cada recurso específico é implementado como um comando.</span><span class="sxs-lookup"><span data-stu-id="0381c-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="0381c-113">Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="0381c-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="0381c-114">Todos os argumentos após o comando são seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="0381c-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="0381c-115">A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="0381c-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="0381c-116">Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="0381c-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="0381c-117">Opções</span><span class="sxs-lookup"><span data-stu-id="0381c-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0381c-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0381c-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="0381c-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="0381c-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="0381c-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="0381c-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="0381c-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="0381c-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0381c-122">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="0381c-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0381c-123">Prints out a short help for the command.</span></span> <span data-ttu-id="0381c-124">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0381c-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="0381c-125">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="0381c-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="0381c-126">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="0381c-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="0381c-127">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="0381c-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="0381c-128">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="0381c-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0381c-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0381c-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="0381c-130">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="0381c-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="0381c-131">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="0381c-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0381c-132">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="0381c-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0381c-133">Prints out a short help for the command.</span></span> <span data-ttu-id="0381c-134">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0381c-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="0381c-135">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="0381c-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="0381c-136">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="0381c-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="0381c-137">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="0381c-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="0381c-138">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="0381c-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0381c-139">Geral</span><span class="sxs-lookup"><span data-stu-id="0381c-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0381c-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0381c-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="0381c-141">Comando</span><span class="sxs-lookup"><span data-stu-id="0381c-141">Command</span></span>                             | <span data-ttu-id="0381c-142">Função</span><span class="sxs-lookup"><span data-stu-id="0381c-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0381c-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0381c-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="0381c-144">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0381c-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0381c-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0381c-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="0381c-146">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="0381c-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="0381c-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0381c-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="0381c-148">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="0381c-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0381c-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0381c-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="0381c-150">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0381c-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0381c-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0381c-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="0381c-152">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0381c-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0381c-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0381c-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="0381c-154">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="0381c-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0381c-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0381c-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="0381c-156">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="0381c-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0381c-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0381c-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="0381c-158">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="0381c-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0381c-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0381c-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="0381c-160">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0381c-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0381c-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="0381c-162">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="0381c-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0381c-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0381c-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="0381c-164">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="0381c-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0381c-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0381c-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="0381c-166">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0381c-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0381c-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0381c-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="0381c-168">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="0381c-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0381c-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0381c-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="0381c-170">Comando</span><span class="sxs-lookup"><span data-stu-id="0381c-170">Command</span></span>                             | <span data-ttu-id="0381c-171">Função</span><span class="sxs-lookup"><span data-stu-id="0381c-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0381c-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0381c-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="0381c-173">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0381c-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0381c-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0381c-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="0381c-175">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="0381c-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="0381c-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0381c-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="0381c-177">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0381c-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0381c-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0381c-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="0381c-179">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0381c-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0381c-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0381c-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="0381c-181">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="0381c-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0381c-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0381c-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="0381c-183">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="0381c-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0381c-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0381c-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="0381c-185">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="0381c-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0381c-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0381c-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="0381c-187">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0381c-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0381c-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="0381c-189">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="0381c-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0381c-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0381c-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="0381c-191">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="0381c-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0381c-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0381c-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="0381c-193">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="0381c-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="0381c-194">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="0381c-194">Project references</span></span>

<span data-ttu-id="0381c-195">Comando</span><span class="sxs-lookup"><span data-stu-id="0381c-195">Command</span></span> | <span data-ttu-id="0381c-196">Função</span><span class="sxs-lookup"><span data-stu-id="0381c-196">Function</span></span>
--- | ---
[<span data-ttu-id="0381c-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0381c-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0381c-198">Adicionar uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0381c-198">Add a project reference.</span></span>
[<span data-ttu-id="0381c-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0381c-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0381c-200">Listar referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0381c-200">List project references.</span></span>
[<span data-ttu-id="0381c-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0381c-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0381c-202">Remover uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0381c-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0381c-203">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="0381c-203">NuGet packages</span></span>

<span data-ttu-id="0381c-204">Comando</span><span class="sxs-lookup"><span data-stu-id="0381c-204">Command</span></span> | <span data-ttu-id="0381c-205">Função</span><span class="sxs-lookup"><span data-stu-id="0381c-205">Function</span></span>
--- | ---
[<span data-ttu-id="0381c-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0381c-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0381c-207">Adicionar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0381c-207">Add a NuGet package.</span></span>
[<span data-ttu-id="0381c-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0381c-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0381c-209">Remover um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0381c-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0381c-210">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="0381c-210">NuGet commands</span></span>

<span data-ttu-id="0381c-211">Comando</span><span class="sxs-lookup"><span data-stu-id="0381c-211">Command</span></span> | <span data-ttu-id="0381c-212">Função</span><span class="sxs-lookup"><span data-stu-id="0381c-212">Function</span></span>
--- | ---
[<span data-ttu-id="0381c-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0381c-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0381c-214">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="0381c-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0381c-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0381c-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0381c-216">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="0381c-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0381c-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0381c-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0381c-218">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="0381c-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="0381c-219">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0381c-219">Examples</span></span>

<span data-ttu-id="0381c-220">Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:</span><span class="sxs-lookup"><span data-stu-id="0381c-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="0381c-221">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0381c-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0381c-222">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="0381c-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="0381c-223">Execute um aplicativo dependente do framework chamado `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="0381c-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="0381c-224">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="0381c-224">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0381c-225">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0381c-225">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="0381c-226">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="0381c-226">The primary package cache.</span></span> <span data-ttu-id="0381c-227">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="0381c-227">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0381c-228">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0381c-228">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0381c-229">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0381c-229">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0381c-230">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="0381c-230">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0381c-231">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-231">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="0381c-232">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="0381c-232">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="0381c-233">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="0381c-233">If not set, it defaults to `true`.</span></span> <span data-ttu-id="0381c-234">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="0381c-234">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="0381c-235">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0381c-235">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0381c-236">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0381c-236">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="0381c-237">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="0381c-237">The primary package cache.</span></span> <span data-ttu-id="0381c-238">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="0381c-238">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0381c-239">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0381c-239">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0381c-240">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0381c-240">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0381c-241">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="0381c-241">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0381c-242">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="0381c-242">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
