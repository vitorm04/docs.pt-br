---
title: Comando dotnet
description: Saiba mais sobre o comando dotNet (o Driver genérico para a CLI do .NET) e seu uso.
ms.date: 11/11/2020
ms.openlocfilehash: a2b4b026e7c89536a6a7eaf69b31e3f62bf5adfc
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556817"
---
# <a name="dotnet-command"></a><span data-ttu-id="40538-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="40538-103">dotnet command</span></span>

<span data-ttu-id="40538-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="40538-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="40538-105">Name</span><span class="sxs-lookup"><span data-stu-id="40538-105">Name</span></span>

<span data-ttu-id="40538-106">`dotnet` -O Driver genérico para a CLI do .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40538-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="40538-107">Synopsis</span></span>

<span data-ttu-id="40538-108">Para obter informações sobre os comandos disponíveis e o ambiente:</span><span class="sxs-lookup"><span data-stu-id="40538-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="40538-109">Para executar um comando (requer a instalação do SDK):</span><span class="sxs-lookup"><span data-stu-id="40538-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="40538-110">Para executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="40538-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="40538-111">`--roll-forward` está disponível desde o .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="40538-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="40538-112">Use o `--roll-forward-on-no-candidate-fx` para .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="40538-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="40538-113">Description</span><span class="sxs-lookup"><span data-stu-id="40538-113">Description</span></span>

<span data-ttu-id="40538-114">O `dotnet` comando tem duas funções:</span><span class="sxs-lookup"><span data-stu-id="40538-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="40538-115">Ele fornece comandos para trabalhar com projetos .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="40538-116">Por exemplo, [`dotnet build`](dotnet-build.md) compila um projeto.</span><span class="sxs-lookup"><span data-stu-id="40538-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="40538-117">Cada comando define suas próprias opções e argumentos.</span><span class="sxs-lookup"><span data-stu-id="40538-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="40538-118">Todos os comandos dão suporte à `--help` opção de impressão de breve documentação sobre como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="40538-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="40538-119">Ele executa aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-119">It runs .NET applications.</span></span>

  <span data-ttu-id="40538-120">Especifique o caminho para um arquivo de aplicativo `.dll` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="40538-121">Executar o aplicativo significa localizar e executar o ponto de entrada, que, no caso de aplicativos de console, é o `Main` método.</span><span class="sxs-lookup"><span data-stu-id="40538-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="40538-122">Por exemplo, `dotnet myapp.dll` executa o `myapp` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="40538-123">Consulte [implantação de aplicativos .net](../deploying/index.md) para saber mais sobre as opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="40538-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="40538-124">Opções</span><span class="sxs-lookup"><span data-stu-id="40538-124">Options</span></span>

<span data-ttu-id="40538-125">Diferentes opções estão disponíveis por `dotnet` si só, para executar um comando e para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="40538-126">Opções para dotnet por si só</span><span class="sxs-lookup"><span data-stu-id="40538-126">Options for dotnet by itself</span></span>

<span data-ttu-id="40538-127">As opções a seguir são por `dotnet` si só.</span><span class="sxs-lookup"><span data-stu-id="40538-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="40538-128">Por exemplo, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="40538-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="40538-129">Eles imprimem informações sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="40538-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="40538-130">Imprime informações detalhadas sobre uma instalação do .NET e o ambiente do computador, como o sistema operacional atual, e confirme o SHA da versão do .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="40538-131">Imprime a versão do SDK do .NET em uso.</span><span class="sxs-lookup"><span data-stu-id="40538-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="40538-132">Imprime uma lista de tempos de execução .NET instalados.</span><span class="sxs-lookup"><span data-stu-id="40538-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="40538-133">Uma versão x86 do SDK lista apenas os tempos de execução x86 e uma versão x64 do SDK lista somente os tempos de execução do x64.</span><span class="sxs-lookup"><span data-stu-id="40538-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="40538-134">Imprime uma lista dos SDKs .NET instalados.</span><span class="sxs-lookup"><span data-stu-id="40538-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="40538-135">Imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="40538-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="40538-136">Opções do SDK para executar um comando</span><span class="sxs-lookup"><span data-stu-id="40538-136">SDK options for running a command</span></span>

<span data-ttu-id="40538-137">As opções a seguir são para `dotnet` com um comando.</span><span class="sxs-lookup"><span data-stu-id="40538-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="40538-138">Por exemplo, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="40538-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="40538-139">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="40538-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="40538-140">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="40538-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="40538-141">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="40538-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="40538-142">Sem suporte em todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="40538-142">Not supported in every command.</span></span> <span data-ttu-id="40538-143">Consulte a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="40538-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="40538-144">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="40538-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="40538-145">Cada comando define opções específicas para esse comando.</span><span class="sxs-lookup"><span data-stu-id="40538-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="40538-146">Consulte a página de comando específica para obter uma lista de opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="40538-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="40538-147">Opções de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="40538-147">Runtime options</span></span>

<span data-ttu-id="40538-148">As opções a seguir estão disponíveis quando o `dotnet` executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="40538-149">Por exemplo, `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="40538-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="40538-150">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="40538-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="40538-151">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="40538-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="40538-152">Um *deps.jsno* arquivo contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="40538-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="40538-153">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="40538-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="40538-154">Caminho para o *deps.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="40538-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="40538-155">Um *deps.jsno* arquivo é um arquivo de configuração que contém informações sobre as dependências necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="40538-156">Esse arquivo é gerado pelo SDK do .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="40538-157">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="40538-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="40538-158">Um *runtimeconfig.jsno* arquivo é um arquivo de configuração que contém as configurações de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40538-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="40538-159">Para obter mais informações, consulte [definições de configuração de tempo de execução do .net](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="40538-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="40538-160">**`--roll-forward <SETTING>`\*\*\*\*Disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="40538-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="40538-161">Controla como o roll forward é aplicado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="40538-162">O `SETTING` pode ser um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="40538-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="40538-163">Se não for especificado, `Minor` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="40538-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="40538-164">`LatestPatch` -Rolar para a versão mais alta do patch.</span><span class="sxs-lookup"><span data-stu-id="40538-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="40538-165">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="40538-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="40538-166">`Minor` – Rolar para a versão secundária mais baixa, se a versão secundária solicitada estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="40538-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="40538-167">Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.</span><span class="sxs-lookup"><span data-stu-id="40538-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="40538-168">`Major` – Role para frente até a versão principal mais baixa e a versão secundária mais baixa, se a versão principal solicitada estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="40538-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="40538-169">Se a versão principal solicitada está presente, a política Secundária é usada.</span><span class="sxs-lookup"><span data-stu-id="40538-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="40538-170">`LatestMinor` – Role para frente até a versão secundária mais alta, mesmo que a versão secundária solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="40538-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="40538-171">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="40538-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="40538-172">`LatestMajor` – Role para frente até a versão secundária mais alta e a mais alta, mesmo que a principal solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="40538-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="40538-173">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="40538-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="40538-174">`Disable` -Não rolar para frente.</span><span class="sxs-lookup"><span data-stu-id="40538-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="40538-175">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="40538-175">Only bind to specified version.</span></span> <span data-ttu-id="40538-176">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="40538-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="40538-177">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="40538-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="40538-178">Com exceção de `Disable` , todas as configurações usarão a versão de patch mais alta disponível.</span><span class="sxs-lookup"><span data-stu-id="40538-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="40538-179">O comportamento de roll forward também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração de tempo de execução e uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="40538-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="40538-180">Para obter mais informações, consulte [roll forward de tempo de execução de versão principal](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="40538-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="40538-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponível no SDK do .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="40538-182">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="40538-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="40538-183">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="40538-183">`N` can be:</span></span>

  - <span data-ttu-id="40538-184">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="40538-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="40538-185">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="40538-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="40538-186">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="40538-186">This is the default behavior.</span></span>
  - <span data-ttu-id="40538-187">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="40538-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="40538-188">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="40538-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="40538-189">A partir do .NET Core 3,0, essa opção é substituída pelo `--roll-forward` , e essa opção deve ser usada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="40538-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="40538-190">Versão do tempo de execução do .NET a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="40538-191">Essa opção substitui a versão da primeira referência de estrutura no arquivo do aplicativo `.runtimeconfig.json` .</span><span class="sxs-lookup"><span data-stu-id="40538-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="40538-192">Isso significa que ele funcionará apenas conforme o esperado se houver apenas uma referência de estrutura.</span><span class="sxs-lookup"><span data-stu-id="40538-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="40538-193">Se o aplicativo tiver mais de uma referência de estrutura, usar essa opção poderá causar erros.</span><span class="sxs-lookup"><span data-stu-id="40538-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="40538-194">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="40538-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="40538-195">Geral</span><span class="sxs-lookup"><span data-stu-id="40538-195">General</span></span>

| <span data-ttu-id="40538-196">Comando</span><span class="sxs-lookup"><span data-stu-id="40538-196">Command</span></span>                                       | <span data-ttu-id="40538-197">Função</span><span class="sxs-lookup"><span data-stu-id="40538-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="40538-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="40538-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="40538-199">Compila um aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="40538-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="40538-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="40538-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="40538-201">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="40538-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="40538-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="40538-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="40538-203">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="40538-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="40538-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="40538-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="40538-205">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="40538-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="40538-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="40538-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="40538-207">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="40538-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="40538-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="40538-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="40538-209">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="40538-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="40538-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="40538-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="40538-211">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="40538-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="40538-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="40538-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="40538-213">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="40538-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="40538-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="40538-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="40538-215">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="40538-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="40538-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="40538-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="40538-217">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="40538-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="40538-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="40538-219">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="40538-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="40538-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="40538-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="40538-221">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="40538-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="40538-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="40538-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="40538-223">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="40538-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="40538-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="40538-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="40538-225">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="40538-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="40538-226">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="40538-226">Project references</span></span>

<span data-ttu-id="40538-227">Comando</span><span class="sxs-lookup"><span data-stu-id="40538-227">Command</span></span> | <span data-ttu-id="40538-228">Função</span><span class="sxs-lookup"><span data-stu-id="40538-228">Function</span></span>
--- | ---
[<span data-ttu-id="40538-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="40538-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="40538-230">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="40538-230">Adds a project reference.</span></span>
[<span data-ttu-id="40538-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="40538-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="40538-232">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="40538-232">Lists project references.</span></span>
[<span data-ttu-id="40538-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="40538-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="40538-234">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="40538-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="40538-235">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="40538-235">NuGet packages</span></span>

<span data-ttu-id="40538-236">Comando</span><span class="sxs-lookup"><span data-stu-id="40538-236">Command</span></span> | <span data-ttu-id="40538-237">Função</span><span class="sxs-lookup"><span data-stu-id="40538-237">Function</span></span>
--- | ---
[<span data-ttu-id="40538-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="40538-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="40538-239">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="40538-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="40538-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="40538-241">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="40538-242">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="40538-242">NuGet commands</span></span>

<span data-ttu-id="40538-243">Comando</span><span class="sxs-lookup"><span data-stu-id="40538-243">Command</span></span> | <span data-ttu-id="40538-244">Função</span><span class="sxs-lookup"><span data-stu-id="40538-244">Function</span></span>
--- | ---
[<span data-ttu-id="40538-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="40538-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="40538-246">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="40538-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="40538-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="40538-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="40538-248">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="40538-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="40538-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="40538-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="40538-250">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="40538-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="40538-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="40538-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="40538-252">Adiciona uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="40538-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="40538-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="40538-254">Desabilita uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="40538-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="40538-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="40538-256">Habilita uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="40538-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="40538-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="40538-258">Lista todas as fontes do NuGet configuradas.</span><span class="sxs-lookup"><span data-stu-id="40538-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="40538-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="40538-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="40538-260">Remove uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="40538-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="40538-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="40538-262">Atualiza uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="40538-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="40538-263">Comandos globais, de caminho de ferramenta e de ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="40538-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="40538-264">Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="40538-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="40538-265">Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="40538-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="40538-266">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="40538-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="40538-267">Para obter mais informações, consulte [visão geral das ferramentas .net](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="40538-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="40538-268">As ferramentas globais e de caminho de ferramenta estão disponíveis a partir do SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="40538-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="40538-269">As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="40538-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="40538-270">Comando</span><span class="sxs-lookup"><span data-stu-id="40538-270">Command</span></span> | <span data-ttu-id="40538-271">Função</span><span class="sxs-lookup"><span data-stu-id="40538-271">Function</span></span>
--- | ---
[<span data-ttu-id="40538-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="40538-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="40538-273">Instala uma ferramenta em seu computador.</span><span class="sxs-lookup"><span data-stu-id="40538-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="40538-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="40538-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="40538-275">Lista todas as ferramentas globais, ferramentas-caminho ou locais atualmente instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="40538-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="40538-276">pesquisa da ferramenta dotnet</span><span class="sxs-lookup"><span data-stu-id="40538-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="40538-277">Pesquisa NuGet.org para ferramentas que têm o termo de pesquisa especificado em seu nome ou metadados.</span><span class="sxs-lookup"><span data-stu-id="40538-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="40538-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="40538-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="40538-279">Desinstala uma ferramenta do seu computador.</span><span class="sxs-lookup"><span data-stu-id="40538-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="40538-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="40538-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="40538-281">Atualiza uma ferramenta instalada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="40538-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="40538-282">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="40538-282">Additional tools</span></span>

<span data-ttu-id="40538-283">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas em uma base por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .net.</span><span class="sxs-lookup"><span data-stu-id="40538-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="40538-284">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="40538-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="40538-285">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="40538-285">Tool</span></span>                                              | <span data-ttu-id="40538-286">Função</span><span class="sxs-lookup"><span data-stu-id="40538-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="40538-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="40538-287">dev-certs</span></span>                                         | <span data-ttu-id="40538-288">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="40538-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="40538-289">salva</span><span class="sxs-lookup"><span data-stu-id="40538-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="40538-290">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="40538-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="40538-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="40538-291">sql-cache</span></span>                                         | <span data-ttu-id="40538-292">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="40538-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="40538-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="40538-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="40538-294">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="40538-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="40538-295">variáveis</span><span class="sxs-lookup"><span data-stu-id="40538-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="40538-296">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="40538-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="40538-297">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="40538-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="40538-298">Exemplos</span><span class="sxs-lookup"><span data-stu-id="40538-298">Examples</span></span>

<span data-ttu-id="40538-299">Crie um novo aplicativo de console .NET Core:</span><span class="sxs-lookup"><span data-stu-id="40538-299">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="40538-300">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="40538-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="40538-301">Executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="40538-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="40538-302">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="40538-302">Environment variables</span></span>

- <span data-ttu-id="40538-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="40538-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="40538-304">Especifica o local dos tempos de execução do .NET, se eles não estiverem instalados no local padrão.</span><span class="sxs-lookup"><span data-stu-id="40538-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="40538-305">O local padrão no Windows é `C:\Program Files\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="40538-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="40538-306">O local padrão no Linux e no macOS é `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="40538-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="40538-307">Essa variável de ambiente é usada somente ao executar aplicativos por meio de executáveis gerados (apphosts).</span><span class="sxs-lookup"><span data-stu-id="40538-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="40538-308">`DOTNET_ROOT(x86)` é usado em vez disso, ao executar um executável de 32 bits em um sistema operacional de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="40538-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="40538-309">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="40538-309">The global packages folder.</span></span> <span data-ttu-id="40538-310">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="40538-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="40538-311">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="40538-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="40538-312">Especifica se as mensagens de boas-vindas e telemetria do .NET são exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="40538-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="40538-313">Defina como `true` ativar mudo dessas mensagens (valores `true` , `1` ou `yes` aceitas) ou defina como `false` para permitir (valores `false` , `0` ou `no` aceito).</span><span class="sxs-lookup"><span data-stu-id="40538-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="40538-314">Se não estiver definido, o padrão será `false` e as mensagens serão exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="40538-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="40538-315">Esse sinalizador não tem nenhum efeito na telemetria (consulte `DOTNET_CLI_TELEMETRY_OPTOUT` para recusar o envio de telemetria).</span><span class="sxs-lookup"><span data-stu-id="40538-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="40538-316">Especifica se os dados sobre o uso das ferramentas .NET são coletados e enviados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="40538-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="40538-317">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="40538-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="40538-318">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="40538-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="40538-319">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="40538-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="40538-320">Especifica se o tempo de execução do .NET, a estrutura compartilhada ou o SDK são resolvidos a partir do local global.</span><span class="sxs-lookup"><span data-stu-id="40538-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="40538-321">Se não estiver definido, o padrão será 1 (lógico `true` ).</span><span class="sxs-lookup"><span data-stu-id="40538-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="40538-322">Defina como 0 (lógico `false` ) para não resolver a partir do local global e ter instalações isoladas do .net.</span><span class="sxs-lookup"><span data-stu-id="40538-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="40538-323">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="40538-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="40538-324">`DOTNET_ROLL_FORWARD`**Disponível a partir do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="40538-325">Determina o comportamento de roll-forward.</span><span class="sxs-lookup"><span data-stu-id="40538-325">Determines roll forward behavior.</span></span> <span data-ttu-id="40538-326">Para obter mais informações, consulte a `--roll-forward` opção anterior neste artigo.</span><span class="sxs-lookup"><span data-stu-id="40538-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="40538-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**Disponível a partir do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="40538-328">Se definido como `1` (habilitado), permite a rolagem posterior para uma versão de pré-lançamento de uma versão de lançamento.</span><span class="sxs-lookup"><span data-stu-id="40538-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="40538-329">Por padrão ( `0` -Disabled), quando uma versão de lançamento do tempo de execução do .net é solicitada, o roll forward só considerará as versões de lançamento instaladas.</span><span class="sxs-lookup"><span data-stu-id="40538-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="40538-330">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="40538-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="40538-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponível no .NET Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="40538-332">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="40538-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="40538-333">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="40538-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="40538-334">Essa configuração é substituída no .NET Core 3,0 pelo `DOTNET_ROLL_FORWARD` .</span><span class="sxs-lookup"><span data-stu-id="40538-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="40538-335">Em vez disso, as novas configurações devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="40538-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="40538-336">Define o idioma da interface do usuário da CLI usando um valor de localidade, como `en-us` .</span><span class="sxs-lookup"><span data-stu-id="40538-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="40538-337">Os valores com suporte são os mesmos para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40538-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="40538-338">Para obter mais informações, consulte a seção sobre como alterar o idioma do instalador na [documentação de instalação do Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="40538-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="40538-339">As regras do Gerenciador de recursos do .NET se aplicam, portanto, você não precisa escolher uma correspondência exata &mdash; que também pode escolher os descendentes na `CultureInfo` árvore.</span><span class="sxs-lookup"><span data-stu-id="40538-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="40538-340">Por exemplo, se você defini-lo como `fr-CA` , a CLI encontrará e usará as `fr` traduções.</span><span class="sxs-lookup"><span data-stu-id="40538-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="40538-341">Se você defini-lo como um idioma sem suporte, a CLI voltará para o inglês.</span><span class="sxs-lookup"><span data-stu-id="40538-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="40538-342">Para executáveis gerados por GUI habilitado-desabilita o Popup da caixa de diálogo, que normalmente mostra algumas classes de erros.</span><span class="sxs-lookup"><span data-stu-id="40538-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="40538-343">Ele só grava `stderr` e sai nesses casos.</span><span class="sxs-lookup"><span data-stu-id="40538-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="40538-344">Equivalente a Option CLI `--additional-deps` .</span><span class="sxs-lookup"><span data-stu-id="40538-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="40538-345">Substitui o RID detectado.</span><span class="sxs-lookup"><span data-stu-id="40538-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="40538-346">Local do "armazenamento compartilhado" para o qual a resolução de assembly volta para em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="40538-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="40538-347">Lista de assemblies dos quais carregar e executar os ganchos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="40538-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="40538-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**Disponível a partir do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="40538-349">Especifica um diretório para o qual um aplicativo de arquivo único é extraído antes de ser executado.</span><span class="sxs-lookup"><span data-stu-id="40538-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="40538-350">Para obter mais informações, consulte [executáveis de arquivo único](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="40538-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="40538-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="40538-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="40538-352">Controla o rastreamento de diagnóstico dos componentes de hospedagem, como `dotnet.exe` , `hostfxr` e `hostpolicy` .</span><span class="sxs-lookup"><span data-stu-id="40538-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="40538-353">`COREHOST_TRACE=[0/1]` -o padrão é o `0` Rastreamento desabilitado.</span><span class="sxs-lookup"><span data-stu-id="40538-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="40538-354">Se definido como `1` , o rastreamento de diagnóstico é habilitado.</span><span class="sxs-lookup"><span data-stu-id="40538-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="40538-355">`COREHOST_TRACEFILE=<file path>` -Só terá efeito se o rastreamento estiver habilitado via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="40538-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="40538-356">Quando definido, as informações de rastreamento são gravadas no arquivo especificado, caso contrário, as informações de rastreamento são gravadas no `stderr` .</span><span class="sxs-lookup"><span data-stu-id="40538-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="40538-357">**Disponível a partir do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="40538-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -o padrão é `4` .</span><span class="sxs-lookup"><span data-stu-id="40538-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="40538-359">A configuração é usada somente quando o rastreamento está habilitado via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="40538-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="40538-360">**Disponível a partir do .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="40538-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="40538-361">`4` -todas as informações de rastreamento são gravadas</span><span class="sxs-lookup"><span data-stu-id="40538-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="40538-362">`3` -apenas mensagens informativas, de aviso e de erro são gravadas</span><span class="sxs-lookup"><span data-stu-id="40538-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="40538-363">`2` -somente avisos e mensagens de erro são gravados</span><span class="sxs-lookup"><span data-stu-id="40538-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="40538-364">`1` -somente as mensagens de erro são gravadas</span><span class="sxs-lookup"><span data-stu-id="40538-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="40538-365">A maneira típica de obter informações detalhadas de rastreamento sobre a inicialização do aplicativo é definir `COREHOST_TRACE=1` e `COREHOST_TRACEFILE=host_trace.txt` , em seguida, executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="40538-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="40538-366">Um novo arquivo `host_trace.txt` será criado no diretório atual com as informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="40538-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="40538-367">Veja também</span><span class="sxs-lookup"><span data-stu-id="40538-367">See also</span></span>

- [<span data-ttu-id="40538-368">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="40538-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="40538-369">Definições de configuração de tempo de execução do .NET</span><span class="sxs-lookup"><span data-stu-id="40538-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
