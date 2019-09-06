---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
ms.date: 06/04/2018
ms.openlocfilehash: 328fd24cd72110bd235c177398f6f147fbb9d144
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373748"
---
# <a name="dotnet-command"></a><span data-ttu-id="5c6c2-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="5c6c2-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5c6c2-104">Nome</span><span class="sxs-lookup"><span data-stu-id="5c6c2-104">Name</span></span>

<span data-ttu-id="5c6c2-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5c6c2-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5c6c2-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c6c2-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c6c2-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c6c2-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c6c2-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c6c2-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c6c2-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="5c6c2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c6c2-110">Description</span></span>

<span data-ttu-id="5c6c2-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="5c6c2-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="5c6c2-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-113">Each command defines its own arguments.</span></span> <span data-ttu-id="5c6c2-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="5c6c2-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="5c6c2-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="5c6c2-117">Opções</span><span class="sxs-lookup"><span data-stu-id="5c6c2-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c6c2-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c6c2-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="5c6c2-119">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c6c2-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c6c2-121">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c6c2-122">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c6c2-123">Para obter mais informações sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c6c2-124">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c6c2-125">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c6c2-126">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c6c2-127">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c6c2-128">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="5c6c2-129">Exibe os tempos de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="5c6c2-130">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="5c6c2-131">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="5c6c2-132">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-132">`N` can be:</span></span>
- <span data-ttu-id="5c6c2-133">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="5c6c2-134">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="5c6c2-135">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-135">This is the default behavior.</span></span>
- <span data-ttu-id="5c6c2-136">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="5c6c2-137">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="5c6c2-138">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c6c2-139">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c6c2-140">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c6c2-141">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c6c2-142">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c6c2-143">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c6c2-144">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c6c2-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c6c2-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="5c6c2-146">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c6c2-147">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c6c2-148">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c6c2-149">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c6c2-150">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c6c2-151">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c6c2-152">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c6c2-153">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c6c2-154">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c6c2-155">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="5c6c2-156">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="5c6c2-157">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="5c6c2-158">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c6c2-159">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c6c2-160">Para obter mais detalhes, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c6c2-161">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c6c2-162">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c6c2-163">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c6c2-164">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c6c2-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c6c2-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c6c2-166">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c6c2-167">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c6c2-168">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c6c2-169">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c6c2-170">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c6c2-171">Versão do tempo de execução do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c6c2-172">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c6c2-173">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c6c2-174">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="5c6c2-175">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c6c2-176">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém as definições de configuração de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c6c2-177">Para obter mais detalhes, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c6c2-178">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c6c2-179">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c6c2-180">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c6c2-181">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="5c6c2-182">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="5c6c2-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="5c6c2-183">Geral</span><span class="sxs-lookup"><span data-stu-id="5c6c2-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c6c2-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c6c2-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="5c6c2-185">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-185">Command</span></span>                                       | <span data-ttu-id="5c6c2-186">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c6c2-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c6c2-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="5c6c2-188">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c6c2-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="5c6c2-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="5c6c2-190">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="5c6c2-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c6c2-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="5c6c2-192">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="5c6c2-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5c6c2-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="5c6c2-194">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5c6c2-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c6c2-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="5c6c2-196">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c6c2-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c6c2-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="5c6c2-198">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c6c2-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c6c2-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="5c6c2-200">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c6c2-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c6c2-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="5c6c2-202">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c6c2-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c6c2-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="5c6c2-204">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c6c2-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c6c2-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="5c6c2-206">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c6c2-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c6c2-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="5c6c2-208">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c6c2-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c6c2-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="5c6c2-210">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c6c2-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5c6c2-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="5c6c2-212">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5c6c2-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c6c2-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="5c6c2-214">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c6c2-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c6c2-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="5c6c2-216">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-216">Command</span></span>                             | <span data-ttu-id="5c6c2-217">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c6c2-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c6c2-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5c6c2-219">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c6c2-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c6c2-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5c6c2-221">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5c6c2-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5c6c2-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="5c6c2-223">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5c6c2-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c6c2-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5c6c2-225">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c6c2-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c6c2-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5c6c2-227">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c6c2-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c6c2-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5c6c2-229">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c6c2-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c6c2-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5c6c2-231">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c6c2-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c6c2-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5c6c2-233">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c6c2-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c6c2-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5c6c2-235">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c6c2-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c6c2-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5c6c2-237">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c6c2-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c6c2-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5c6c2-239">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c6c2-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5c6c2-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="5c6c2-241">Armazena os assemblies no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5c6c2-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c6c2-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5c6c2-243">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c6c2-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c6c2-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="5c6c2-245">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-245">Command</span></span>                             | <span data-ttu-id="5c6c2-246">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c6c2-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c6c2-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5c6c2-248">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c6c2-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c6c2-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5c6c2-250">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5c6c2-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c6c2-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5c6c2-252">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c6c2-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c6c2-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5c6c2-254">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c6c2-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c6c2-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5c6c2-256">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c6c2-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c6c2-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5c6c2-258">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c6c2-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c6c2-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5c6c2-260">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c6c2-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c6c2-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5c6c2-262">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c6c2-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c6c2-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5c6c2-264">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c6c2-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c6c2-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5c6c2-266">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c6c2-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c6c2-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5c6c2-268">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="5c6c2-269">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="5c6c2-269">Project references</span></span>

<span data-ttu-id="5c6c2-270">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-270">Command</span></span> | <span data-ttu-id="5c6c2-271">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-271">Function</span></span>
--- | ---
[<span data-ttu-id="5c6c2-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="5c6c2-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="5c6c2-273">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-273">Adds a project reference.</span></span>
[<span data-ttu-id="5c6c2-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5c6c2-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="5c6c2-275">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-275">Lists project references.</span></span>
[<span data-ttu-id="5c6c2-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="5c6c2-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="5c6c2-277">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="5c6c2-278">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="5c6c2-278">NuGet packages</span></span>

<span data-ttu-id="5c6c2-279">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-279">Command</span></span> | <span data-ttu-id="5c6c2-280">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-280">Function</span></span>
--- | ---
[<span data-ttu-id="5c6c2-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="5c6c2-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="5c6c2-282">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="5c6c2-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5c6c2-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="5c6c2-284">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="5c6c2-285">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="5c6c2-285">NuGet commands</span></span>

<span data-ttu-id="5c6c2-286">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-286">Command</span></span> | <span data-ttu-id="5c6c2-287">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-287">Function</span></span>
--- | ---
[<span data-ttu-id="5c6c2-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="5c6c2-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="5c6c2-289">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="5c6c2-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="5c6c2-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="5c6c2-291">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="5c6c2-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5c6c2-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="5c6c2-293">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="5c6c2-294">Comandos de ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="5c6c2-294">Global Tools commands</span></span>

<span data-ttu-id="5c6c2-295">[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="5c6c2-296">Comando</span><span class="sxs-lookup"><span data-stu-id="5c6c2-296">Command</span></span> | <span data-ttu-id="5c6c2-297">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-297">Function</span></span>
--- | ---
[<span data-ttu-id="5c6c2-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="5c6c2-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="5c6c2-299">Instala uma Ferramenta Global no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="5c6c2-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="5c6c2-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="5c6c2-301">Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="5c6c2-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5c6c2-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="5c6c2-303">Desinstala uma Ferramenta Global do computador.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="5c6c2-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="5c6c2-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="5c6c2-305">Atualiza uma Ferramenta Global no computador.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="5c6c2-306">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="5c6c2-306">Additional tools</span></span>

<span data-ttu-id="5c6c2-307">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="5c6c2-308">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="5c6c2-309">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="5c6c2-309">Tool</span></span>                                              | <span data-ttu-id="5c6c2-310">Função</span><span class="sxs-lookup"><span data-stu-id="5c6c2-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="5c6c2-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="5c6c2-311">dev-certs</span></span>                                         | <span data-ttu-id="5c6c2-312">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="5c6c2-313">ef</span><span class="sxs-lookup"><span data-stu-id="5c6c2-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="5c6c2-314">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="5c6c2-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="5c6c2-315">sql-cache</span></span>                                         | <span data-ttu-id="5c6c2-316">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="5c6c2-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="5c6c2-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="5c6c2-318">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="5c6c2-319">watch</span><span class="sxs-lookup"><span data-stu-id="5c6c2-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="5c6c2-320">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="5c6c2-321">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="5c6c2-322">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5c6c2-322">Examples</span></span>

<span data-ttu-id="5c6c2-323">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="5c6c2-324">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5c6c2-325">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="5c6c2-326">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="5c6c2-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="5c6c2-327">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="5c6c2-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c6c2-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c6c2-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="5c6c2-329">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-329">The global packages folder.</span></span> <span data-ttu-id="5c6c2-330">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c6c2-331">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c6c2-332">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c6c2-333">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c6c2-334">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c6c2-335">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="5c6c2-336">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="5c6c2-337">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="5c6c2-338">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="5c6c2-339">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="5c6c2-340">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="5c6c2-341">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c6c2-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c6c2-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="5c6c2-343">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-343">The primary package cache.</span></span> <span data-ttu-id="5c6c2-344">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c6c2-345">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c6c2-346">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c6c2-347">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c6c2-348">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c6c2-349">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="5c6c2-350">Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="5c6c2-351">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="5c6c2-352">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="5c6c2-353">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c6c2-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c6c2-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="5c6c2-355">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-355">The primary package cache.</span></span> <span data-ttu-id="5c6c2-356">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c6c2-357">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c6c2-358">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c6c2-359">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c6c2-360">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="5c6c2-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c6c2-361">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="5c6c2-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="5c6c2-362">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c6c2-362">See also</span></span>

- [<span data-ttu-id="5c6c2-363">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="5c6c2-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
