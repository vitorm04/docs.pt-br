---
title: Comando dotnet
description: Saiba mais sobre o comando dotNet (o Driver genérico para o CLI do .NET Core) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451162"
---
# <a name="dotnet-command"></a><span data-ttu-id="3a304-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="3a304-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3a304-104">Nome</span><span class="sxs-lookup"><span data-stu-id="3a304-104">Name</span></span>

<span data-ttu-id="3a304-105">`dotnet` – Uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a304-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3a304-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3a304-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="3a304-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3a304-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="3a304-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a304-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="3a304-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3a304-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="3a304-110">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="3a304-110">Description</span></span>

<span data-ttu-id="3a304-111">`dotnet` é uma ferramenta para gerenciar o código-fonte e os binários do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a304-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="3a304-112">Ela expõe comandos que realizam tarefas específicas, como [`dotnet build`](dotnet-build.md) e [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="3a304-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="3a304-113">Cada comando define seus próprios argumentos.</span><span class="sxs-lookup"><span data-stu-id="3a304-113">Each command defines its own arguments.</span></span> <span data-ttu-id="3a304-114">Digite `--help` após cada comando para acessar uma breve documentação de ajuda.</span><span class="sxs-lookup"><span data-stu-id="3a304-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="3a304-115">`dotnet` pode ser usado para executar aplicativos, especificando uma DLL de aplicativo, como `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="3a304-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="3a304-116">Consulte [Implantação de um aplicativo .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="3a304-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="3a304-117">Opções</span><span class="sxs-lookup"><span data-stu-id="3a304-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3a304-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3a304-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="3a304-119">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="3a304-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="3a304-120">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="3a304-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="3a304-121">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="3a304-122">Um arquivo *deps. JSON* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="3a304-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="3a304-123">Para obter mais informações sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a304-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="3a304-124">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="3a304-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3a304-125">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3a304-126">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3a304-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3a304-127">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3a304-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3a304-128">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="3a304-129">Exibe os runtimes do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="3a304-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="3a304-130">Exibe os tempos de execução dos SDKs .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="3a304-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="3a304-131">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="3a304-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="3a304-132">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="3a304-132">`N` can be:</span></span>

- <span data-ttu-id="3a304-133">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="3a304-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="3a304-134">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="3a304-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="3a304-135">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="3a304-135">This is the default behavior.</span></span>
- <span data-ttu-id="3a304-136">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="3a304-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="3a304-137">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3a304-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="3a304-138">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="3a304-139">Um arquivo *runtimeconfig. JSON* é um arquivo de configuração que contém as configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a304-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="3a304-140">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="3a304-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3a304-141">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3a304-142">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3a304-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3a304-143">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="3a304-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3a304-144">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="3a304-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="3a304-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a304-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="3a304-146">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="3a304-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="3a304-147">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="3a304-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="3a304-148">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="3a304-149">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="3a304-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="3a304-150">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a304-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="3a304-151">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="3a304-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3a304-152">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3a304-153">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3a304-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3a304-154">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3a304-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3a304-155">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="3a304-156">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="3a304-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="3a304-157">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3a304-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="3a304-158">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="3a304-159">Um arquivo *runtimeconfig. JSON* é um arquivo de configuração que contém as configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a304-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="3a304-160">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="3a304-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3a304-161">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3a304-162">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3a304-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3a304-163">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="3a304-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3a304-164">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="3a304-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="3a304-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3a304-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="3a304-166">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="3a304-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="3a304-167">Caminho para um arquivo *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="3a304-168">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="3a304-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="3a304-169">Para obter mais detalhes sobre esse arquivo, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a304-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="3a304-170">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="3a304-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="3a304-171">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="3a304-172">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="3a304-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="3a304-173">`dotnet --help` imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3a304-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="3a304-174">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="3a304-175">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="3a304-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="3a304-176">Um arquivo *runtimeconfig. JSON* é um arquivo de configuração que contém as configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a304-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="3a304-177">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="3a304-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3a304-178">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3a304-179">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3a304-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3a304-180">Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="3a304-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="3a304-181">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="3a304-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="3a304-182">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="3a304-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="3a304-183">Geral</span><span class="sxs-lookup"><span data-stu-id="3a304-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3a304-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3a304-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="3a304-185">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-185">Command</span></span>                                       | <span data-ttu-id="3a304-186">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3a304-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3a304-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="3a304-188">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3a304-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="3a304-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="3a304-190">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="3a304-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="3a304-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3a304-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="3a304-192">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="3a304-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="3a304-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3a304-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="3a304-194">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3a304-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3a304-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="3a304-196">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3a304-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3a304-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="3a304-198">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3a304-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3a304-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3a304-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="3a304-200">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="3a304-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3a304-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3a304-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="3a304-202">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="3a304-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3a304-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3a304-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="3a304-204">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="3a304-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3a304-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3a304-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="3a304-206">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3a304-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3a304-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="3a304-208">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="3a304-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3a304-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3a304-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="3a304-210">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="3a304-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3a304-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3a304-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="3a304-212">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="3a304-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3a304-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3a304-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="3a304-214">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="3a304-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="3a304-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a304-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="3a304-216">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-216">Command</span></span>                             | <span data-ttu-id="3a304-217">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3a304-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3a304-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3a304-219">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3a304-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3a304-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3a304-221">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="3a304-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3a304-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="3a304-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="3a304-223">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="3a304-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3a304-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3a304-225">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3a304-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3a304-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3a304-227">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3a304-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3a304-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3a304-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3a304-229">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="3a304-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3a304-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3a304-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3a304-231">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="3a304-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3a304-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3a304-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3a304-233">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="3a304-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3a304-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3a304-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3a304-235">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3a304-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3a304-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3a304-237">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="3a304-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3a304-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3a304-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3a304-239">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="3a304-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3a304-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3a304-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="3a304-241">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="3a304-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="3a304-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3a304-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3a304-243">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="3a304-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="3a304-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3a304-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="3a304-245">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-245">Command</span></span>                             | <span data-ttu-id="3a304-246">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="3a304-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3a304-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="3a304-248">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="3a304-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3a304-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="3a304-250">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="3a304-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="3a304-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="3a304-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="3a304-252">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="3a304-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="3a304-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="3a304-254">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="3a304-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="3a304-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="3a304-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="3a304-256">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="3a304-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="3a304-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3a304-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="3a304-258">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="3a304-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="3a304-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3a304-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="3a304-260">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="3a304-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="3a304-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3a304-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="3a304-262">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="3a304-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3a304-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="3a304-264">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="3a304-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="3a304-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="3a304-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="3a304-266">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="3a304-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="3a304-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="3a304-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="3a304-268">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="3a304-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="3a304-269">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="3a304-269">Project references</span></span>

<span data-ttu-id="3a304-270">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-270">Command</span></span> | <span data-ttu-id="3a304-271">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-271">Function</span></span>
--- | ---
[<span data-ttu-id="3a304-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="3a304-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="3a304-273">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3a304-273">Adds a project reference.</span></span>
[<span data-ttu-id="3a304-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3a304-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="3a304-275">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3a304-275">Lists project references.</span></span>
[<span data-ttu-id="3a304-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="3a304-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="3a304-277">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="3a304-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="3a304-278">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="3a304-278">NuGet packages</span></span>

<span data-ttu-id="3a304-279">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-279">Command</span></span> | <span data-ttu-id="3a304-280">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-280">Function</span></span>
--- | ---
[<span data-ttu-id="3a304-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3a304-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="3a304-282">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="3a304-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="3a304-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="3a304-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="3a304-284">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="3a304-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="3a304-285">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="3a304-285">NuGet commands</span></span>

<span data-ttu-id="3a304-286">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-286">Command</span></span> | <span data-ttu-id="3a304-287">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-287">Function</span></span>
--- | ---
[<span data-ttu-id="3a304-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="3a304-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="3a304-289">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="3a304-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="3a304-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="3a304-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="3a304-291">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="3a304-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="3a304-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="3a304-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="3a304-293">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="3a304-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="3a304-294">Comandos globais, de caminho de ferramenta e de ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="3a304-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="3a304-295">Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="3a304-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="3a304-296">Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="3a304-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="3a304-297">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="3a304-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="3a304-298">Para obter mais informações, consulte [visão geral das ferramentas do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3a304-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="3a304-299">As ferramentas globais e de caminho de ferramenta estão disponíveis a partir do SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="3a304-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="3a304-300">As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3a304-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="3a304-301">Comando</span><span class="sxs-lookup"><span data-stu-id="3a304-301">Command</span></span> | <span data-ttu-id="3a304-302">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-302">Function</span></span>
--- | ---
[<span data-ttu-id="3a304-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="3a304-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="3a304-304">Instala uma ferramenta em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a304-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="3a304-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="3a304-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="3a304-306">Lista todas as ferramentas globais, ferramentas-caminho ou locais atualmente instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a304-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="3a304-307">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="3a304-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="3a304-308">Desinstala uma ferramenta do seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a304-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="3a304-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="3a304-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="3a304-310">Atualiza uma ferramenta instalada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a304-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="3a304-311">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="3a304-311">Additional tools</span></span>

<span data-ttu-id="3a304-312">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="3a304-313">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a304-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="3a304-314">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="3a304-314">Tool</span></span>                                              | <span data-ttu-id="3a304-315">Função</span><span class="sxs-lookup"><span data-stu-id="3a304-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="3a304-316">dev-certs</span><span class="sxs-lookup"><span data-stu-id="3a304-316">dev-certs</span></span>                                         | <span data-ttu-id="3a304-317">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a304-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="3a304-318">ef</span><span class="sxs-lookup"><span data-stu-id="3a304-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="3a304-319">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="3a304-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="3a304-320">sql-cache</span><span class="sxs-lookup"><span data-stu-id="3a304-320">sql-cache</span></span>                                         | <span data-ttu-id="3a304-321">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a304-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="3a304-322">user-secrets</span><span class="sxs-lookup"><span data-stu-id="3a304-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="3a304-323">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a304-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="3a304-324">watch</span><span class="sxs-lookup"><span data-stu-id="3a304-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="3a304-325">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="3a304-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="3a304-326">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="3a304-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="3a304-327">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3a304-327">Examples</span></span>

<span data-ttu-id="3a304-328">Cria um novo aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3a304-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="3a304-329">Restaure as dependências para um determinado aplicativo:</span><span class="sxs-lookup"><span data-stu-id="3a304-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3a304-330">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="3a304-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="3a304-331">Execute a DLL de um aplicativo, como `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="3a304-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="3a304-332">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="3a304-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="3a304-333">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3a304-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="3a304-334">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="3a304-334">The global packages folder.</span></span> <span data-ttu-id="3a304-335">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="3a304-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3a304-336">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="3a304-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3a304-337">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a304-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3a304-338">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3a304-339">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3a304-340">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="3a304-341">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="3a304-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="3a304-342">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="3a304-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="3a304-343">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="3a304-344">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="3a304-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="3a304-345">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="3a304-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="3a304-346">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="3a304-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="3a304-347">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a304-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="3a304-348">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="3a304-348">The primary package cache.</span></span> <span data-ttu-id="3a304-349">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="3a304-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3a304-350">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="3a304-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3a304-351">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a304-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3a304-352">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3a304-353">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3a304-354">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="3a304-355">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="3a304-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="3a304-356">Se não estiver definida, o padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="3a304-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="3a304-357">Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="3a304-358">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="3a304-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="3a304-359">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3a304-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="3a304-360">O cache do pacote principal.</span><span class="sxs-lookup"><span data-stu-id="3a304-360">The primary package cache.</span></span> <span data-ttu-id="3a304-361">Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="3a304-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="3a304-362">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="3a304-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="3a304-363">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a304-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="3a304-364">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="3a304-365">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="3a304-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="3a304-366">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="3a304-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="3a304-367">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a304-367">See also</span></span>

- [<span data-ttu-id="3a304-368">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="3a304-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="3a304-369">Definições de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a304-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
