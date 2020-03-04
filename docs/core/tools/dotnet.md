---
title: Comando dotnet
description: Saiba mais sobre o comando dotNet (o Driver genérico para o CLI do .NET Core) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240864"
---
# <a name="dotnet-command"></a><span data-ttu-id="d25f4-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="d25f4-103">dotnet command</span></span>

<span data-ttu-id="d25f4-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d25f4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d25f4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="d25f4-105">Name</span></span>

<span data-ttu-id="d25f4-106">`dotnet`-o Driver genérico para o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d25f4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d25f4-107">Synopsis</span></span>

<span data-ttu-id="d25f4-108">Para obter informações sobre os comandos disponíveis e o ambiente:</span><span class="sxs-lookup"><span data-stu-id="d25f4-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="d25f4-109">Para executar um comando (requer a instalação do SDK):</span><span class="sxs-lookup"><span data-stu-id="d25f4-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="d25f4-110">Para executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d25f4-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="d25f4-111">`--roll-forward` está disponível desde o .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="d25f4-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="d25f4-112">Use `--roll-forward-on-no-candidate-fx` para .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="d25f4-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="d25f4-113">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="d25f4-113">Description</span></span>

<span data-ttu-id="d25f4-114">O comando `dotnet` tem duas funções:</span><span class="sxs-lookup"><span data-stu-id="d25f4-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="d25f4-115">Ele fornece comandos para trabalhar com projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="d25f4-116">Por exemplo, [`dotnet build`](dotnet-build.md) compila um projeto.</span><span class="sxs-lookup"><span data-stu-id="d25f4-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="d25f4-117">Cada comando define suas próprias opções e argumentos.</span><span class="sxs-lookup"><span data-stu-id="d25f4-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="d25f4-118">Todos os comandos dão suporte à opção `--help` para imprimir uma breve documentação sobre como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="d25f4-119">Ele executa aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="d25f4-120">Especifique o caminho para um arquivo de `.dll` de aplicativo para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="d25f4-121">Por exemplo, `dotnet myapp.dll` executa o aplicativo `myapp`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="d25f4-122">Consulte [implantação de aplicativos do .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="d25f4-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="d25f4-123">Opções</span><span class="sxs-lookup"><span data-stu-id="d25f4-123">Options</span></span>

<span data-ttu-id="d25f4-124">Opções diferentes estão disponíveis para `dotnet` por si só, para executar um comando e para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="d25f4-125">Opções para dotnet por si só</span><span class="sxs-lookup"><span data-stu-id="d25f4-125">Options for dotnet by itself</span></span>

<span data-ttu-id="d25f4-126">As opções a seguir são para `dotnet` por si só.</span><span class="sxs-lookup"><span data-stu-id="d25f4-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="d25f4-127">Por exemplo, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="d25f4-128">Eles imprimem informações sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="d25f4-129">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="d25f4-130">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="d25f4-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="d25f4-131">Imprime uma lista de tempos de execução do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="d25f4-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="d25f4-132">Imprime uma lista de SDKs do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="d25f4-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d25f4-133">Imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d25f4-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="d25f4-134">Opções do SDK para executar um comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-134">SDK options for running a command</span></span>

<span data-ttu-id="d25f4-135">As opções a seguir são para `dotnet` com um comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="d25f4-136">Por exemplo, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="d25f4-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="d25f4-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d25f4-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d25f4-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d25f4-140">Sem suporte em todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="d25f4-140">Not supported in every command.</span></span> <span data-ttu-id="d25f4-141">Consulte a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="d25f4-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d25f4-142">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="d25f4-143">Cada comando define opções específicas para esse comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="d25f4-144">Consulte a página de comando específica para obter uma lista de opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d25f4-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="d25f4-145">Opções de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d25f4-145">Runtime options</span></span>

<span data-ttu-id="d25f4-146">As opções a seguir estão disponíveis quando `dotnet` executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="d25f4-147">Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="d25f4-148">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="d25f4-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="d25f4-149">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="d25f4-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="d25f4-150">Um arquivo *deps. JSON* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="d25f4-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="d25f4-151">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="d25f4-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="d25f4-152">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="d25f4-153">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="d25f4-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="d25f4-154">Um arquivo *runtimeconfig. JSON* é um arquivo de configuração que contém configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d25f4-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="d25f4-155">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d25f4-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="d25f4-156">**`--roll-forward-on-no-candidate-fx <N>`** **disponível no SDK do .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="d25f4-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="d25f4-157">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="d25f4-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="d25f4-158">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="d25f4-158">`N` can be:</span></span>

  - <span data-ttu-id="d25f4-159">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="d25f4-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="d25f4-160">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="d25f4-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="d25f4-161">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d25f4-161">This is the default behavior.</span></span>
  - <span data-ttu-id="d25f4-162">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="d25f4-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="d25f4-163">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d25f4-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="d25f4-164">**`--roll-forward <SETTING>`** **disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="d25f4-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="d25f4-165">Controla como o roll forward é aplicado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="d25f4-166">O `SETTING` pode ser um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="d25f4-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="d25f4-167">Se não for especificado, `Minor` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="d25f4-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="d25f4-168">`LatestPatch`-roll forward para a versão mais alta do patch.</span><span class="sxs-lookup"><span data-stu-id="d25f4-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="d25f4-169">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="d25f4-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="d25f4-170">`Minor`-roll forward para a versão secundária mais baixa, se a versão secundária solicitada estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="d25f4-171">Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.</span><span class="sxs-lookup"><span data-stu-id="d25f4-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="d25f4-172">`Major`-rolar para a versão principal mais baixa e a versão secundária mais baixa, se a versão principal solicitada estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="d25f4-173">Se a versão principal solicitada estiver presente, a política secundária será usada.</span><span class="sxs-lookup"><span data-stu-id="d25f4-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="d25f4-174">`LatestMinor`-roll forward até a versão secundária mais alta, mesmo que a versão secundária solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="d25f4-175">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="d25f4-176">`LatestMajor`-roll forward até a versão secundária mais alta e a mais alta, mesmo que a principal solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="d25f4-177">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="d25f4-178">`Disable`-não rolar para frente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="d25f4-179">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="d25f4-179">Only bind to specified version.</span></span> <span data-ttu-id="d25f4-180">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="d25f4-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="d25f4-181">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="d25f4-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="d25f4-182">Com exceção de `Disable`, todas as configurações usarão a versão de patch mais alta disponível.</span><span class="sxs-lookup"><span data-stu-id="d25f4-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="d25f4-183">O comportamento de roll forward também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração de tempo de execução e uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="d25f4-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="d25f4-184">Para obter mais informações, consulte [roll forward de tempo de execução de versão principal](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d25f4-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="d25f4-185">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="d25f4-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="d25f4-186">Geral</span><span class="sxs-lookup"><span data-stu-id="d25f4-186">General</span></span>

| <span data-ttu-id="d25f4-187">Comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-187">Command</span></span>                                       | <span data-ttu-id="d25f4-188">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d25f4-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d25f4-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="d25f4-190">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d25f4-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="d25f4-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="d25f4-192">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="d25f4-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="d25f4-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d25f4-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="d25f4-194">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="d25f4-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="d25f4-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d25f4-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="d25f4-196">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d25f4-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d25f4-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="d25f4-198">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d25f4-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d25f4-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="d25f4-200">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d25f4-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d25f4-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d25f4-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="d25f4-202">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d25f4-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d25f4-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d25f4-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="d25f4-204">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="d25f4-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d25f4-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d25f4-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="d25f4-206">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="d25f4-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d25f4-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d25f4-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="d25f4-208">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d25f4-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d25f4-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="d25f4-210">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="d25f4-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d25f4-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d25f4-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="d25f4-212">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="d25f4-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d25f4-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d25f4-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="d25f4-214">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="d25f4-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d25f4-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d25f4-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="d25f4-216">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="d25f4-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="d25f4-217">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="d25f4-217">Project references</span></span>

<span data-ttu-id="d25f4-218">Comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-218">Command</span></span> | <span data-ttu-id="d25f4-219">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-219">Function</span></span>
--- | ---
[<span data-ttu-id="d25f4-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="d25f4-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="d25f4-221">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d25f4-221">Adds a project reference.</span></span>
[<span data-ttu-id="d25f4-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d25f4-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="d25f4-223">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d25f4-223">Lists project references.</span></span>
[<span data-ttu-id="d25f4-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d25f4-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="d25f4-225">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d25f4-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="d25f4-226">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="d25f4-226">NuGet packages</span></span>

<span data-ttu-id="d25f4-227">Comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-227">Command</span></span> | <span data-ttu-id="d25f4-228">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-228">Function</span></span>
--- | ---
[<span data-ttu-id="d25f4-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d25f4-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="d25f4-230">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d25f4-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="d25f4-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="d25f4-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="d25f4-232">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="d25f4-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="d25f4-233">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="d25f4-233">NuGet commands</span></span>

<span data-ttu-id="d25f4-234">Comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-234">Command</span></span> | <span data-ttu-id="d25f4-235">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-235">Function</span></span>
--- | ---
[<span data-ttu-id="d25f4-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="d25f4-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="d25f4-237">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="d25f4-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="d25f4-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d25f4-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="d25f4-239">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="d25f4-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="d25f4-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="d25f4-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="d25f4-241">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="d25f4-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="d25f4-242">Comandos globais, de caminho de ferramenta e de ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="d25f4-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="d25f4-243">Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="d25f4-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="d25f4-244">Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="d25f4-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="d25f4-245">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="d25f4-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="d25f4-246">Para obter mais informações, consulte [visão geral das ferramentas do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d25f4-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="d25f4-247">As ferramentas globais e de caminho de ferramenta estão disponíveis a partir do SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="d25f4-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="d25f4-248">As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d25f4-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="d25f4-249">Comando</span><span class="sxs-lookup"><span data-stu-id="d25f4-249">Command</span></span> | <span data-ttu-id="d25f4-250">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-250">Function</span></span>
--- | ---
[<span data-ttu-id="d25f4-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="d25f4-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="d25f4-252">Instala uma ferramenta em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d25f4-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="d25f4-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="d25f4-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="d25f4-254">Lista todas as ferramentas globais, ferramentas-caminho ou locais atualmente instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d25f4-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="d25f4-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="d25f4-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="d25f4-256">Desinstala uma ferramenta do seu computador.</span><span class="sxs-lookup"><span data-stu-id="d25f4-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="d25f4-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="d25f4-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="d25f4-258">Atualiza uma ferramenta instalada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d25f4-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="d25f4-259">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="d25f4-259">Additional tools</span></span>

<span data-ttu-id="d25f4-260">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="d25f4-261">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="d25f4-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="d25f4-262">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="d25f4-262">Tool</span></span>                                              | <span data-ttu-id="d25f4-263">Função</span><span class="sxs-lookup"><span data-stu-id="d25f4-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="d25f4-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="d25f4-264">dev-certs</span></span>                                         | <span data-ttu-id="d25f4-265">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d25f4-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="d25f4-266">ef</span><span class="sxs-lookup"><span data-stu-id="d25f4-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="d25f4-267">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="d25f4-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="d25f4-268">sql-cache</span></span>                                         | <span data-ttu-id="d25f4-269">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d25f4-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="d25f4-270">user-secrets</span><span class="sxs-lookup"><span data-stu-id="d25f4-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="d25f4-271">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d25f4-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="d25f4-272">watch</span><span class="sxs-lookup"><span data-stu-id="d25f4-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="d25f4-273">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="d25f4-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="d25f4-274">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="d25f4-275">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d25f4-275">Examples</span></span>

<span data-ttu-id="d25f4-276">Crie um novo aplicativo de console .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d25f4-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="d25f4-277">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="d25f4-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="d25f4-278">Executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d25f4-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="d25f4-279">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="d25f4-279">Environment variables</span></span>

- <span data-ttu-id="d25f4-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="d25f4-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="d25f4-281">Especifica o local dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão.</span><span class="sxs-lookup"><span data-stu-id="d25f4-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="d25f4-282">O local padrão no Windows é `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="d25f4-283">O local padrão no Linux e no macOS é `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="d25f4-284">Essa variável de ambiente é usada somente ao executar aplicativos por meio de executáveis gerados (apphosts).</span><span class="sxs-lookup"><span data-stu-id="d25f4-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="d25f4-285">`DOTNET_ROOT(x86)` é usado em vez de executar um executável de 32 bits em um sistema operacional de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d25f4-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="d25f4-286">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="d25f4-286">The global packages folder.</span></span> <span data-ttu-id="d25f4-287">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="d25f4-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="d25f4-288">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="d25f4-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="d25f4-289">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d25f4-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d25f4-290">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d25f4-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="d25f4-291">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="d25f4-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d25f4-292">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="d25f4-293">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="d25f4-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="d25f4-294">Se não estiver definido, o padrão será 1 (`true`lógico).</span><span class="sxs-lookup"><span data-stu-id="d25f4-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="d25f4-295">Defina como 0 (`false`lógico) para não resolver a partir do local global e ter instalações isoladas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25f4-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="d25f4-296">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d25f4-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="d25f4-297">`DOTNET_ROLL_FORWARD` **disponível a partir do SDK do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="d25f4-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="d25f4-298">Determina o comportamento de roll-forward.</span><span class="sxs-lookup"><span data-stu-id="d25f4-298">Determines roll forward behavior.</span></span> <span data-ttu-id="d25f4-299">Para obter mais informações, consulte a opção `--roll-forward` anteriormente neste artigo.</span><span class="sxs-lookup"><span data-stu-id="d25f4-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="d25f4-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **disponível no SDK do .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="d25f4-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="d25f4-301">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="d25f4-302">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="d25f4-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="d25f4-303">Define o idioma da interface do usuário da CLI usando um valor de localidade, como `en-us`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="d25f4-304">Os valores com suporte são os mesmos para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d25f4-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="d25f4-305">Para obter mais informações, consulte a seção sobre como alterar o idioma do instalador na [documentação de instalação do Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="d25f4-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="d25f4-306">As regras do Gerenciador de recursos do .NET se aplicam, portanto, você não precisa escolher uma correspondência exata&mdash;também pode escolher os descendentes na árvore de `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="d25f4-307">Por exemplo, se você defini-lo como `fr-CA`, a CLI encontrará e usará as traduções `fr`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="d25f4-308">Se você defini-lo como um idioma sem suporte, a CLI voltará para o inglês.</span><span class="sxs-lookup"><span data-stu-id="d25f4-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="d25f4-309">Para executáveis gerados por GUI habilitado-desabilita o Popup da caixa de diálogo que normalmente mostra para determinadas classes de erros.</span><span class="sxs-lookup"><span data-stu-id="d25f4-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="d25f4-310">Ele só grava em `stderr` e sai nesses casos.</span><span class="sxs-lookup"><span data-stu-id="d25f4-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="d25f4-311">Equivalente à opção da CLI `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="d25f4-312">Substitui o RID detectado.</span><span class="sxs-lookup"><span data-stu-id="d25f4-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="d25f4-313">Local do "armazenamento compartilhado" para o qual a resolução de assembly volta para em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="d25f4-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="d25f4-314">Lista de assemblies dos quais carregar e executar os ganchos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d25f4-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="d25f4-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="d25f4-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="d25f4-316">Controla o rastreamento de diagnóstico dos componentes de hospedagem, como `dotnet.exe`, `hostfxr`e `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="d25f4-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d25f4-317">Confira também</span><span class="sxs-lookup"><span data-stu-id="d25f4-317">See also</span></span>

- [<span data-ttu-id="d25f4-318">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="d25f4-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="d25f4-319">Definições de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d25f4-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
