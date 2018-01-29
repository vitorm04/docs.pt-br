---
title: "Comando dotnet – CLI do .NET Core"
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2eea7d13994bfddc89d8f3513308a6620c53c88c
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="7c020-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="7c020-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7c020-104">Nome</span><span class="sxs-lookup"><span data-stu-id="7c020-104">Name</span></span>

<span data-ttu-id="7c020-105">`dotnet` – Driver geral para executar os comandos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7c020-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7c020-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7c020-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7c020-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7c020-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7c020-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7c020-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="7c020-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c020-109">Description</span></span>

<span data-ttu-id="7c020-110">`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="7c020-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="7c020-111">Invocado por conta própria, ele fornece breve instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="7c020-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="7c020-112">Cada recurso específico é implementado como um comando.</span><span class="sxs-lookup"><span data-stu-id="7c020-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="7c020-113">Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="7c020-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="7c020-114">Todos os argumentos após o comando são seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="7c020-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="7c020-115">A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c020-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="7c020-116">Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="7c020-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="7c020-117">Opções</span><span class="sxs-lookup"><span data-stu-id="7c020-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7c020-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7c020-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="7c020-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="7c020-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="7c020-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="7c020-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="7c020-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="7c020-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="7c020-122">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c020-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="7c020-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="7c020-123">Prints out a short help for the command.</span></span> <span data-ttu-id="7c020-124">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7c020-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="7c020-125">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="7c020-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="7c020-126">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="7c020-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="7c020-127">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="7c020-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="7c020-128">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="7c020-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7c020-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7c020-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="7c020-130">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="7c020-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="7c020-131">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="7c020-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="7c020-132">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c020-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="7c020-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="7c020-133">Prints out a short help for the command.</span></span> <span data-ttu-id="7c020-134">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7c020-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="7c020-135">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="7c020-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="7c020-136">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="7c020-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="7c020-137">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="7c020-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="7c020-138">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="7c020-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="7c020-139">Geral</span><span class="sxs-lookup"><span data-stu-id="7c020-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7c020-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7c020-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="7c020-141">Comando</span><span class="sxs-lookup"><span data-stu-id="7c020-141">Command</span></span>                             | <span data-ttu-id="7c020-142">Função</span><span class="sxs-lookup"><span data-stu-id="7c020-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="7c020-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="7c020-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="7c020-144">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c020-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="7c020-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="7c020-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="7c020-146">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="7c020-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="7c020-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="7c020-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="7c020-148">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="7c020-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="7c020-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="7c020-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="7c020-150">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c020-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="7c020-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="7c020-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="7c020-152">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7c020-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="7c020-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="7c020-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="7c020-154">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c020-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="7c020-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="7c020-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="7c020-156">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="7c020-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="7c020-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="7c020-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="7c020-158">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="7c020-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="7c020-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7c020-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="7c020-160">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c020-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="7c020-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="7c020-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="7c020-162">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="7c020-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="7c020-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="7c020-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="7c020-164">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="7c020-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="7c020-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="7c020-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="7c020-166">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7c020-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="7c020-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="7c020-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="7c020-168">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="7c020-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7c020-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7c020-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="7c020-170">Comando</span><span class="sxs-lookup"><span data-stu-id="7c020-170">Command</span></span>                             | <span data-ttu-id="7c020-171">Função</span><span class="sxs-lookup"><span data-stu-id="7c020-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="7c020-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="7c020-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="7c020-173">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c020-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="7c020-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="7c020-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="7c020-175">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="7c020-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="7c020-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="7c020-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="7c020-177">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c020-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="7c020-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="7c020-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="7c020-179">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7c020-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="7c020-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="7c020-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="7c020-181">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c020-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="7c020-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="7c020-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="7c020-183">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="7c020-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="7c020-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="7c020-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="7c020-185">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="7c020-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="7c020-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7c020-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="7c020-187">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c020-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="7c020-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="7c020-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="7c020-189">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="7c020-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="7c020-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="7c020-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="7c020-191">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="7c020-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="7c020-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="7c020-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="7c020-193">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="7c020-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="7c020-194">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="7c020-194">Project references</span></span>

<span data-ttu-id="7c020-195">Comando</span><span class="sxs-lookup"><span data-stu-id="7c020-195">Command</span></span> | <span data-ttu-id="7c020-196">Função</span><span class="sxs-lookup"><span data-stu-id="7c020-196">Function</span></span>
--- | ---
[<span data-ttu-id="7c020-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="7c020-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="7c020-198">Adicionar uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c020-198">Add a project reference.</span></span>
[<span data-ttu-id="7c020-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="7c020-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="7c020-200">Listar referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c020-200">List project references.</span></span>
[<span data-ttu-id="7c020-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="7c020-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="7c020-202">Remover uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c020-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="7c020-203">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="7c020-203">NuGet packages</span></span>

<span data-ttu-id="7c020-204">Comando</span><span class="sxs-lookup"><span data-stu-id="7c020-204">Command</span></span> | <span data-ttu-id="7c020-205">Função</span><span class="sxs-lookup"><span data-stu-id="7c020-205">Function</span></span>
--- | ---
[<span data-ttu-id="7c020-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="7c020-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="7c020-207">Adicionar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c020-207">Add a NuGet package.</span></span>
[<span data-ttu-id="7c020-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="7c020-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="7c020-209">Remover um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c020-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="7c020-210">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="7c020-210">NuGet commands</span></span>

<span data-ttu-id="7c020-211">Comando</span><span class="sxs-lookup"><span data-stu-id="7c020-211">Command</span></span> | <span data-ttu-id="7c020-212">Função</span><span class="sxs-lookup"><span data-stu-id="7c020-212">Function</span></span>
--- | ---
[<span data-ttu-id="7c020-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="7c020-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="7c020-214">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="7c020-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="7c020-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="7c020-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="7c020-216">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="7c020-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="7c020-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="7c020-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="7c020-218">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="7c020-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="7c020-219">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7c020-219">Examples</span></span>

<span data-ttu-id="7c020-220">Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:</span><span class="sxs-lookup"><span data-stu-id="7c020-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="7c020-221">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7c020-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="7c020-222">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="7c020-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="7c020-223">Execute um aplicativo dependente do framework chamado `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="7c020-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="7c020-224">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="7c020-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="7c020-225">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="7c020-225">The primary package cache.</span></span> <span data-ttu-id="7c020-226">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="7c020-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="7c020-227">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7c020-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="7c020-228">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7c020-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="7c020-229">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="7c020-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="7c020-230">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="7c020-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
