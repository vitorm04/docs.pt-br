---
title: "Comando dotnet – CLI do .NET Core"
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: fa2e5ecbf41dc2a8cd90aabc6f7291db597e657e
ms.openlocfilehash: 4c1c0e4ed1b1222abbcd104b2c10a44b1b99be8d
ms.contentlocale: pt-br
ms.lasthandoff: 08/17/2017

---
# <a name="dotnet-command"></a><span data-ttu-id="8a297-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="8a297-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8a297-104">Nome</span><span class="sxs-lookup"><span data-stu-id="8a297-104">Name</span></span>

<span data-ttu-id="8a297-105">`dotnet` – Driver geral para executar os comandos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8a297-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8a297-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="8a297-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8a297-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8a297-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a297-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a297-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="8a297-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a297-109">Description</span></span>

<span data-ttu-id="8a297-110">`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando).</span><span class="sxs-lookup"><span data-stu-id="8a297-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="8a297-111">Invocado por conta própria, ele fornece breve instruções de uso.</span><span class="sxs-lookup"><span data-stu-id="8a297-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="8a297-112">Cada recurso específico é implementado como um comando.</span><span class="sxs-lookup"><span data-stu-id="8a297-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="8a297-113">Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="8a297-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="8a297-114">Todos os argumentos após o comando são seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="8a297-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="8a297-115">A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a297-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="8a297-116">Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="8a297-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="8a297-117">Opções</span><span class="sxs-lookup"><span data-stu-id="8a297-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8a297-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8a297-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additionaldeps <PATH>`

<span data-ttu-id="8a297-119">Caminho para o arquivo *deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="8a297-119">Path to additonal *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="8a297-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="8a297-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8a297-121">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8a297-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8a297-122">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a297-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8a297-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a297-123">Prints out a short help for the command.</span></span> <span data-ttu-id="8a297-124">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a297-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="8a297-125">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="8a297-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="8a297-126">Efetua roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="8a297-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="8a297-127">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="8a297-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="8a297-128">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="8a297-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a297-129">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a297-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="8a297-130">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="8a297-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="8a297-131">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8a297-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="8a297-132">A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a297-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="8a297-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a297-133">Prints out a short help for the command.</span></span> <span data-ttu-id="8a297-134">Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a297-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="8a297-135">Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.</span><span class="sxs-lookup"><span data-stu-id="8a297-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="8a297-136">Habilita a saída detalhada.</span><span class="sxs-lookup"><span data-stu-id="8a297-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="8a297-137">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="8a297-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="8a297-138">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="8a297-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="8a297-139">Geral</span><span class="sxs-lookup"><span data-stu-id="8a297-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8a297-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8a297-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="8a297-141">Comando</span><span class="sxs-lookup"><span data-stu-id="8a297-141">Command</span></span>                             | <span data-ttu-id="8a297-142">Função</span><span class="sxs-lookup"><span data-stu-id="8a297-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8a297-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8a297-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8a297-144">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a297-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8a297-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8a297-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8a297-146">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="8a297-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8a297-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="8a297-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="8a297-148">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a297-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="8a297-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8a297-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8a297-150">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a297-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8a297-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8a297-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8a297-152">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8a297-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8a297-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8a297-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8a297-154">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8a297-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8a297-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8a297-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8a297-156">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="8a297-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8a297-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8a297-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8a297-158">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="8a297-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8a297-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8a297-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8a297-160">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a297-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8a297-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8a297-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8a297-162">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="8a297-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8a297-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8a297-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8a297-164">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="8a297-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8a297-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="8a297-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="8a297-166">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8a297-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="8a297-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8a297-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8a297-168">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="8a297-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a297-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a297-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="8a297-170">Comando</span><span class="sxs-lookup"><span data-stu-id="8a297-170">Command</span></span>                             | <span data-ttu-id="8a297-171">Função</span><span class="sxs-lookup"><span data-stu-id="8a297-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8a297-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8a297-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="8a297-173">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a297-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="8a297-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8a297-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="8a297-175">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="8a297-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="8a297-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8a297-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="8a297-177">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a297-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8a297-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8a297-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="8a297-179">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8a297-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8a297-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8a297-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="8a297-181">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8a297-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8a297-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8a297-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="8a297-183">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="8a297-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8a297-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8a297-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="8a297-185">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="8a297-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8a297-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8a297-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="8a297-187">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a297-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8a297-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8a297-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="8a297-189">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="8a297-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8a297-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8a297-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="8a297-191">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="8a297-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8a297-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8a297-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="8a297-193">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="8a297-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="8a297-194">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="8a297-194">Project references</span></span>

<span data-ttu-id="8a297-195">Comando</span><span class="sxs-lookup"><span data-stu-id="8a297-195">Command</span></span> | <span data-ttu-id="8a297-196">Função</span><span class="sxs-lookup"><span data-stu-id="8a297-196">Function</span></span>
--- | ---
[<span data-ttu-id="8a297-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8a297-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="8a297-198">Adicionar uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8a297-198">Add a project reference.</span></span>
[<span data-ttu-id="8a297-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="8a297-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="8a297-200">Listar referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8a297-200">List project references.</span></span>
[<span data-ttu-id="8a297-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="8a297-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="8a297-202">Remover uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8a297-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="8a297-203">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="8a297-203">NuGet packages</span></span>

<span data-ttu-id="8a297-204">Comando</span><span class="sxs-lookup"><span data-stu-id="8a297-204">Command</span></span> | <span data-ttu-id="8a297-205">Função</span><span class="sxs-lookup"><span data-stu-id="8a297-205">Function</span></span>
--- | ---
[<span data-ttu-id="8a297-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="8a297-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="8a297-207">Adicionar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8a297-207">Add a NuGet package.</span></span>
[<span data-ttu-id="8a297-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="8a297-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="8a297-209">Remover um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8a297-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="8a297-210">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="8a297-210">NuGet commands</span></span>

<span data-ttu-id="8a297-211">Comando</span><span class="sxs-lookup"><span data-stu-id="8a297-211">Command</span></span> | <span data-ttu-id="8a297-212">Função</span><span class="sxs-lookup"><span data-stu-id="8a297-212">Function</span></span>
--- | ---
[<span data-ttu-id="8a297-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="8a297-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="8a297-214">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="8a297-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="8a297-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="8a297-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="8a297-216">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="8a297-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="8a297-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="8a297-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="8a297-218">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="8a297-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="8a297-219">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8a297-219">Examples</span></span>

<span data-ttu-id="8a297-220">Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:</span><span class="sxs-lookup"><span data-stu-id="8a297-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="8a297-221">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="8a297-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

<span data-ttu-id="8a297-222">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="8a297-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="8a297-223">Execute um aplicativo dependente do framework chamado `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="8a297-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="8a297-224">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="8a297-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="8a297-225">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="8a297-225">The primary package cache.</span></span> <span data-ttu-id="8a297-226">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="8a297-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="8a297-227">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8a297-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="8a297-228">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8a297-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8a297-229">Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos).</span><span class="sxs-lookup"><span data-stu-id="8a297-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8a297-230">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="8a297-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

