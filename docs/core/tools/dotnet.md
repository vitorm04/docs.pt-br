---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
ms.date: 06/04/2018
ms.openlocfilehash: a22340c26ca2e483e43857e2ecb31f2ab53b60f4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117509"
---
# <a name="dotnet-command"></a><span data-ttu-id="a012a-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="a012a-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a012a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="a012a-104">Name</span></span>

<span data-ttu-id="a012a-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="a012a-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a012a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a012a-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a012a-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a012a-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a012a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a012a-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a012a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a012a-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="a012a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a012a-110">Description</span></span>

<span data-ttu-id="a012a-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="a012a-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="a012a-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="a012a-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="a012a-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="a012a-113">Each command defines its own arguments.</span></span> <span data-ttu-id="a012a-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="a012a-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="a012a-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="a012a-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="a012a-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="a012a-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a012a-117">Opções</span><span class="sxs-lookup"><span data-stu-id="a012a-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a012a-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a012a-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="a012a-119">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="a012a-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a012a-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a012a-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a012a-121">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a012a-122">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="a012a-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a012a-123">Para obter mais informações sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="a012a-124">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a012a-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a012a-125">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a012a-126">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a012a-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a012a-127">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a012a-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a012a-128">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="a012a-129">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="a012a-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="a012a-130">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="a012a-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="a012a-131">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="a012a-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="a012a-132">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="a012a-132">`N` can be:</span></span>

- <span data-ttu-id="a012a-133">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="a012a-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="a012a-134">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="a012a-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="a012a-135">Este é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="a012a-135">This is the default behavior.</span></span>
- <span data-ttu-id="a012a-136">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="a012a-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="a012a-137">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a012a-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="a012a-138">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a012a-139">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="a012a-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="a012a-140">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a012a-141">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a012a-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a012a-142">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a012a-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a012a-143">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a012a-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a012a-144">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a012a-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a012a-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a012a-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="a012a-146">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="a012a-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="a012a-147">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a012a-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a012a-148">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a012a-149">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="a012a-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a012a-150">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="a012a-151">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a012a-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a012a-152">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a012a-153">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a012a-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a012a-154">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a012a-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a012a-155">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="a012a-156">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="a012a-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a012a-157">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a012a-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="a012a-158">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a012a-159">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="a012a-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="a012a-160">Para obter mais detalhes, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a012a-161">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a012a-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a012a-162">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a012a-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a012a-163">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a012a-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a012a-164">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a012a-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a012a-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a012a-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="a012a-166">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="a012a-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="a012a-167">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="a012a-168">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="a012a-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a012a-169">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="a012a-170">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="a012a-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="a012a-171">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="a012a-172">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a012a-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="a012a-173">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a012a-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="a012a-174">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="a012a-175">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="a012a-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="a012a-176">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="a012a-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="a012a-177">Para obter mais detalhes, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a012a-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a012a-178">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a012a-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a012a-179">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a012a-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a012a-180">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="a012a-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="a012a-181">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="a012a-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="a012a-182">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="a012a-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a012a-183">Geral</span><span class="sxs-lookup"><span data-stu-id="a012a-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a012a-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a012a-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="a012a-185">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-185">Command</span></span>                                       | <span data-ttu-id="a012a-186">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a012a-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a012a-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a012a-188">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a012a-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a012a-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a012a-190">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="a012a-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a012a-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a012a-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a012a-192">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a012a-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a012a-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a012a-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a012a-194">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="a012a-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a012a-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a012a-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a012a-196">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a012a-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a012a-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a012a-198">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a012a-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a012a-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a012a-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a012a-200">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a012a-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a012a-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a012a-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a012a-202">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a012a-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a012a-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a012a-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a012a-204">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a012a-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a012a-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a012a-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a012a-206">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a012a-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a012a-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a012a-208">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a012a-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a012a-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a012a-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a012a-210">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a012a-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a012a-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a012a-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a012a-212">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a012a-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a012a-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a012a-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a012a-214">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a012a-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a012a-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a012a-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="a012a-216">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-216">Command</span></span>                             | <span data-ttu-id="a012a-217">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a012a-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a012a-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a012a-219">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a012a-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a012a-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a012a-221">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a012a-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a012a-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a012a-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="a012a-223">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="a012a-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a012a-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a012a-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a012a-225">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a012a-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a012a-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a012a-227">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a012a-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a012a-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a012a-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a012a-229">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a012a-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a012a-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a012a-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a012a-231">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a012a-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a012a-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a012a-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a012a-233">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a012a-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a012a-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a012a-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a012a-235">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a012a-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a012a-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a012a-237">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a012a-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a012a-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a012a-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a012a-239">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a012a-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a012a-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a012a-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="a012a-241">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a012a-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a012a-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a012a-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a012a-243">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a012a-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a012a-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a012a-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="a012a-245">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-245">Command</span></span>                             | <span data-ttu-id="a012a-246">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a012a-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a012a-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="a012a-248">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a012a-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a012a-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="a012a-250">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="a012a-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="a012a-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a012a-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="a012a-252">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a012a-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a012a-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="a012a-254">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a012a-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a012a-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a012a-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="a012a-256">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="a012a-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a012a-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a012a-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="a012a-258">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="a012a-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a012a-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a012a-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="a012a-260">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="a012a-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a012a-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a012a-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="a012a-262">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a012a-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a012a-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="a012a-264">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="a012a-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a012a-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a012a-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="a012a-266">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="a012a-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a012a-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a012a-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="a012a-268">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="a012a-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="a012a-269">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="a012a-269">Project references</span></span>

<span data-ttu-id="a012a-270">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-270">Command</span></span> | <span data-ttu-id="a012a-271">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-271">Function</span></span>
--- | ---
[<span data-ttu-id="a012a-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a012a-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a012a-273">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a012a-273">Adds a project reference.</span></span>
[<span data-ttu-id="a012a-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a012a-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a012a-275">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a012a-275">Lists project references.</span></span>
[<span data-ttu-id="a012a-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a012a-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a012a-277">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a012a-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a012a-278">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="a012a-278">NuGet packages</span></span>

<span data-ttu-id="a012a-279">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-279">Command</span></span> | <span data-ttu-id="a012a-280">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-280">Function</span></span>
--- | ---
[<span data-ttu-id="a012a-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a012a-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a012a-282">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a012a-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="a012a-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a012a-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a012a-284">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a012a-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a012a-285">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="a012a-285">NuGet commands</span></span>

<span data-ttu-id="a012a-286">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-286">Command</span></span> | <span data-ttu-id="a012a-287">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-287">Function</span></span>
--- | ---
[<span data-ttu-id="a012a-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a012a-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a012a-289">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="a012a-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a012a-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a012a-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a012a-291">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="a012a-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a012a-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a012a-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a012a-293">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="a012a-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="a012a-294">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="a012a-294">Global Tools commands</span></span>

<span data-ttu-id="a012a-295">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="a012a-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="a012a-296">Comando</span><span class="sxs-lookup"><span data-stu-id="a012a-296">Command</span></span> | <span data-ttu-id="a012a-297">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-297">Function</span></span>
--- | ---
[<span data-ttu-id="a012a-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a012a-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a012a-299">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a012a-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="a012a-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a012a-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a012a-301">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="a012a-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="a012a-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a012a-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a012a-303">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="a012a-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="a012a-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a012a-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a012a-305">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="a012a-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a012a-306">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="a012a-306">Additional tools</span></span>

<span data-ttu-id="a012a-307">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="a012a-308">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="a012a-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a012a-309">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="a012a-309">Tool</span></span>                                              | <span data-ttu-id="a012a-310">Função</span><span class="sxs-lookup"><span data-stu-id="a012a-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a012a-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a012a-311">dev-certs</span></span>                                         | <span data-ttu-id="a012a-312">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a012a-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a012a-313">ef</span><span class="sxs-lookup"><span data-stu-id="a012a-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a012a-314">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="a012a-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a012a-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a012a-315">sql-cache</span></span>                                         | <span data-ttu-id="a012a-316">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a012a-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a012a-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a012a-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a012a-318">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a012a-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a012a-319">watch</span><span class="sxs-lookup"><span data-stu-id="a012a-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a012a-320">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="a012a-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a012a-321">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="a012a-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a012a-322">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a012a-322">Examples</span></span>

<span data-ttu-id="a012a-323">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a012a-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="a012a-324">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a012a-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a012a-325">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="a012a-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="a012a-326">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="a012a-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="a012a-327">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="a012a-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a012a-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a012a-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="a012a-329">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="a012a-329">The global packages folder.</span></span> <span data-ttu-id="a012a-330">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a012a-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a012a-331">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a012a-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a012a-332">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a012a-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a012a-333">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a012a-334">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a012a-335">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a012a-336">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="a012a-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a012a-337">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="a012a-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a012a-338">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a012a-339">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="a012a-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="a012a-340">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="a012a-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a012a-341">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a012a-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a012a-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a012a-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="a012a-343">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="a012a-343">The primary package cache.</span></span> <span data-ttu-id="a012a-344">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a012a-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a012a-345">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a012a-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a012a-346">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a012a-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a012a-347">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a012a-348">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a012a-349">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="a012a-350">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="a012a-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a012a-351">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="a012a-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="a012a-352">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="a012a-353">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="a012a-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a012a-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a012a-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="a012a-355">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="a012a-355">The primary package cache.</span></span> <span data-ttu-id="a012a-356">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="a012a-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="a012a-357">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a012a-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="a012a-358">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a012a-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a012a-359">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a012a-360">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="a012a-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a012a-361">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="a012a-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="a012a-362">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a012a-362">See also</span></span>

- [<span data-ttu-id="a012a-363">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="a012a-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
