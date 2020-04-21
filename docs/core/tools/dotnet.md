---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para o .NET Core CLI) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: 6a08297499d955db44e342dc82fed25b7b9b8171
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739074"
---
# <a name="dotnet-command"></a><span data-ttu-id="989ec-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="989ec-103">dotnet command</span></span>

<span data-ttu-id="989ec-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="989ec-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="989ec-105">Nome</span><span class="sxs-lookup"><span data-stu-id="989ec-105">Name</span></span>

<span data-ttu-id="989ec-106">`dotnet`- O driver genérico para o .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="989ec-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="989ec-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="989ec-107">Synopsis</span></span>

<span data-ttu-id="989ec-108">Para obter informações sobre os comandos disponíveis e o ambiente:</span><span class="sxs-lookup"><span data-stu-id="989ec-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="989ec-109">Para executar um comando (requer instalação do SDK):</span><span class="sxs-lookup"><span data-stu-id="989ec-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="989ec-110">Para executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="989ec-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="989ec-111">`--roll-forward`está disponível desde .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="989ec-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="989ec-112">Use `--roll-forward-on-no-candidate-fx` para .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="989ec-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="989ec-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="989ec-113">Description</span></span>

<span data-ttu-id="989ec-114">O `dotnet` comando tem duas funções:</span><span class="sxs-lookup"><span data-stu-id="989ec-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="989ec-115">Ele fornece comandos para trabalhar com projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="989ec-116">Por exemplo, [`dotnet build`](dotnet-build.md) constrói um projeto.</span><span class="sxs-lookup"><span data-stu-id="989ec-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="989ec-117">Cada comando define suas próprias opções e argumentos.</span><span class="sxs-lookup"><span data-stu-id="989ec-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="989ec-118">Todos os comandos suportam a `--help` opção de imprimir breve documentação sobre como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="989ec-119">Ele executa aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="989ec-120">Você especifica o caminho `.dll` para um arquivo de aplicativo para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="989ec-121">Para executar o aplicativo significa encontrar e executar o ponto de `Main` entrada, que no caso de aplicativos de console é o método.</span><span class="sxs-lookup"><span data-stu-id="989ec-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="989ec-122">Por exemplo, `dotnet myapp.dll` `myapp` executa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="989ec-123">Consulte a [implantação do aplicativo .NET Core](../deploying/index.md) para saber sobre opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="989ec-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="989ec-124">Opções</span><span class="sxs-lookup"><span data-stu-id="989ec-124">Options</span></span>

<span data-ttu-id="989ec-125">Diferentes opções `dotnet` estão disponíveis para si só, para executar um comando e para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="989ec-126">Opções para dotnet por si só</span><span class="sxs-lookup"><span data-stu-id="989ec-126">Options for dotnet by itself</span></span>

<span data-ttu-id="989ec-127">As seguintes `dotnet` opções são para si só.</span><span class="sxs-lookup"><span data-stu-id="989ec-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="989ec-128">Por exemplo, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="989ec-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="989ec-129">Eles imprimem informações sobre o meio ambiente.</span><span class="sxs-lookup"><span data-stu-id="989ec-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="989ec-130">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="989ec-131">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="989ec-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="989ec-132">Imprime uma lista dos tempos de execução do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="989ec-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="989ec-133">Uma versão x86 do SDK lista apenas tempos de execução x86, e uma versão x64 do SDK lista apenas tempos de execução x64.</span><span class="sxs-lookup"><span data-stu-id="989ec-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="989ec-134">Imprime uma lista dos SDKs do Núcleo .NET instalados.</span><span class="sxs-lookup"><span data-stu-id="989ec-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="989ec-135">Imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="989ec-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="989ec-136">Opções de SDK para executar um comando</span><span class="sxs-lookup"><span data-stu-id="989ec-136">SDK options for running a command</span></span>

<span data-ttu-id="989ec-137">As seguintes `dotnet` opções são para com um comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="989ec-138">Por exemplo, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="989ec-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="989ec-139">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="989ec-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="989ec-140">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="989ec-141">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="989ec-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="989ec-142">Não suportado em todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="989ec-142">Not supported in every command.</span></span> <span data-ttu-id="989ec-143">Consulte a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="989ec-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="989ec-144">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="989ec-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="989ec-145">Cada comando define opções específicas para esse comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="989ec-146">Consulte a página de comando específica para obter uma lista de opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="989ec-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="989ec-147">Opções de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="989ec-147">Runtime options</span></span>

<span data-ttu-id="989ec-148">As seguintes opções estão disponíveis quando `dotnet` executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="989ec-149">Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="989ec-149">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="989ec-150">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="989ec-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="989ec-151">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="989ec-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="989ec-152">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para lidar com conflitos de montagem.</span><span class="sxs-lookup"><span data-stu-id="989ec-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="989ec-153">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="989ec-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="989ec-154">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-154">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="989ec-155">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="989ec-155">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="989ec-156">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém configurações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="989ec-156">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="989ec-157">Para obter mais informações, consulte [as configurações de configuração em tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="989ec-157">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="989ec-158">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="989ec-158">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="989ec-159">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="989ec-159">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="989ec-160">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="989ec-160">`N` can be:</span></span>

  - <span data-ttu-id="989ec-161">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="989ec-161">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="989ec-162">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="989ec-162">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="989ec-163">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="989ec-163">This is the default behavior.</span></span>
  - <span data-ttu-id="989ec-164">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="989ec-164">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="989ec-165">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="989ec-165">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="989ec-166">**`--roll-forward <SETTING>`\*\*\*\*Disponível a partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="989ec-166">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="989ec-167">Controla como o roll forward é aplicado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-167">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="989ec-168">O `SETTING` pode ser um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="989ec-168">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="989ec-169">Se não for `Minor` especificado, é o padrão.</span><span class="sxs-lookup"><span data-stu-id="989ec-169">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="989ec-170">`LatestPatch`- Avance para a versão mais alta do patch.</span><span class="sxs-lookup"><span data-stu-id="989ec-170">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="989ec-171">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="989ec-171">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="989ec-172">`Minor`- Encaminhe para a versão menor mais baixa, se a versão menor solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="989ec-172">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="989ec-173">Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.</span><span class="sxs-lookup"><span data-stu-id="989ec-173">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="989ec-174">`Major`- Avance para a versão principal mais baixa e a versão menor mais baixa, se a versão principal solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="989ec-174">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="989ec-175">Se a versão principal solicitada está presente, a política Secundária é usada.</span><span class="sxs-lookup"><span data-stu-id="989ec-175">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="989ec-176">`LatestMinor`- Encaminhe para a versão menor mais alta, mesmo que a versão menor solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="989ec-176">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="989ec-177">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="989ec-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="989ec-178">`LatestMajor`- Avance para a versão mais alta e menor, mesmo que o major solicitado esteja presente.</span><span class="sxs-lookup"><span data-stu-id="989ec-178">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="989ec-179">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="989ec-179">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="989ec-180">`Disable`- Não role para a frente.</span><span class="sxs-lookup"><span data-stu-id="989ec-180">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="989ec-181">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="989ec-181">Only bind to specified version.</span></span> <span data-ttu-id="989ec-182">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="989ec-182">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="989ec-183">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="989ec-183">This value is only recommended for testing.</span></span>

<span data-ttu-id="989ec-184">Com exceção `Disable`de , todas as configurações usarão a versão de patch mais alta disponível.</span><span class="sxs-lookup"><span data-stu-id="989ec-184">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="989ec-185">O comportamento de encaminhamento também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração em tempo de execução e uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="989ec-185">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="989ec-186">Para obter mais informações, consulte [o tempo de execução da versão principal para a frente](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="989ec-186">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="989ec-187">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="989ec-187">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="989ec-188">Geral</span><span class="sxs-lookup"><span data-stu-id="989ec-188">General</span></span>

| <span data-ttu-id="989ec-189">Comando</span><span class="sxs-lookup"><span data-stu-id="989ec-189">Command</span></span>                                       | <span data-ttu-id="989ec-190">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-190">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="989ec-191">dotnet build</span><span class="sxs-lookup"><span data-stu-id="989ec-191">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="989ec-192">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-192">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="989ec-193">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="989ec-193">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="989ec-194">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="989ec-194">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="989ec-195">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="989ec-195">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="989ec-196">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="989ec-196">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="989ec-197">dotnet help</span><span class="sxs-lookup"><span data-stu-id="989ec-197">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="989ec-198">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-198">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="989ec-199">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="989ec-199">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="989ec-200">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-200">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="989ec-201">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="989ec-201">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="989ec-202">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="989ec-202">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="989ec-203">dotnet new</span><span class="sxs-lookup"><span data-stu-id="989ec-203">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="989ec-204">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="989ec-204">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="989ec-205">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="989ec-205">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="989ec-206">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="989ec-206">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="989ec-207">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="989ec-207">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="989ec-208">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="989ec-208">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="989ec-209">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="989ec-209">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="989ec-210">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-210">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="989ec-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="989ec-211">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="989ec-212">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="989ec-212">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="989ec-213">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="989ec-213">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="989ec-214">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="989ec-214">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="989ec-215">dotnet store</span><span class="sxs-lookup"><span data-stu-id="989ec-215">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="989ec-216">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="989ec-216">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="989ec-217">dotnet test</span><span class="sxs-lookup"><span data-stu-id="989ec-217">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="989ec-218">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="989ec-218">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="989ec-219">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="989ec-219">Project references</span></span>

<span data-ttu-id="989ec-220">Comando</span><span class="sxs-lookup"><span data-stu-id="989ec-220">Command</span></span> | <span data-ttu-id="989ec-221">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-221">Function</span></span>
--- | ---
[<span data-ttu-id="989ec-222">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="989ec-222">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="989ec-223">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="989ec-223">Adds a project reference.</span></span>
[<span data-ttu-id="989ec-224">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="989ec-224">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="989ec-225">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="989ec-225">Lists project references.</span></span>
[<span data-ttu-id="989ec-226">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="989ec-226">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="989ec-227">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="989ec-227">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="989ec-228">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="989ec-228">NuGet packages</span></span>

<span data-ttu-id="989ec-229">Comando</span><span class="sxs-lookup"><span data-stu-id="989ec-229">Command</span></span> | <span data-ttu-id="989ec-230">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-230">Function</span></span>
--- | ---
[<span data-ttu-id="989ec-231">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="989ec-231">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="989ec-232">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-232">Adds a NuGet package.</span></span>
[<span data-ttu-id="989ec-233">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="989ec-233">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="989ec-234">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-234">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="989ec-235">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="989ec-235">NuGet commands</span></span>

<span data-ttu-id="989ec-236">Comando</span><span class="sxs-lookup"><span data-stu-id="989ec-236">Command</span></span> | <span data-ttu-id="989ec-237">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-237">Function</span></span>
--- | ---
[<span data-ttu-id="989ec-238">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="989ec-238">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="989ec-239">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="989ec-239">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="989ec-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="989ec-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="989ec-241">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="989ec-241">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="989ec-242">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="989ec-242">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="989ec-243">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="989ec-243">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="989ec-244">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="989ec-244">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="989ec-245">Adiciona uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-245">Adds a NuGet source.</span></span>
[<span data-ttu-id="989ec-246">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="989ec-246">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="989ec-247">Desativa uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-247">Disables a NuGet source.</span></span>
[<span data-ttu-id="989ec-248">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="989ec-248">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="989ec-249">Habilita uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-249">Enables a NuGet source.</span></span>
[<span data-ttu-id="989ec-250">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="989ec-250">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="989ec-251">Lista todas as fontes NuGet configuradas.</span><span class="sxs-lookup"><span data-stu-id="989ec-251">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="989ec-252">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="989ec-252">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="989ec-253">Remove uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-253">Removes a NuGet source.</span></span>
[<span data-ttu-id="989ec-254">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="989ec-254">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="989ec-255">Atualiza uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="989ec-255">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="989ec-256">Comandos de ferramentas globais, de caminho de ferramentas e locais</span><span class="sxs-lookup"><span data-stu-id="989ec-256">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="989ec-257">As ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados a partir do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="989ec-257">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="989ec-258">Você mesmo pode escrever ferramentas ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="989ec-258">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="989ec-259">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="989ec-259">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="989ec-260">Para obter mais informações, consulte [a visão geral das ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="989ec-260">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="989ec-261">Ferramentas globais e de caminho de ferramentas estão disponíveis a partir do .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="989ec-261">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="989ec-262">As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="989ec-262">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="989ec-263">Comando</span><span class="sxs-lookup"><span data-stu-id="989ec-263">Command</span></span> | <span data-ttu-id="989ec-264">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-264">Function</span></span>
--- | ---
[<span data-ttu-id="989ec-265">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="989ec-265">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="989ec-266">Instala uma ferramenta em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="989ec-266">Installs a tool on your machine.</span></span>
[<span data-ttu-id="989ec-267">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="989ec-267">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="989ec-268">Lista todas as ferramentas globais, de caminho de ferramentas ou locais atualmente instaladas em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="989ec-268">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="989ec-269">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="989ec-269">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="989ec-270">Desinstala uma ferramenta da sua máquina.</span><span class="sxs-lookup"><span data-stu-id="989ec-270">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="989ec-271">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="989ec-271">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="989ec-272">Atualiza uma ferramenta instalada em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="989ec-272">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="989ec-273">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="989ec-273">Additional tools</span></span>

<span data-ttu-id="989ec-274">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-274">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="989ec-275">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="989ec-275">These tools are listed in the following table:</span></span>

| <span data-ttu-id="989ec-276">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="989ec-276">Tool</span></span>                                              | <span data-ttu-id="989ec-277">Função</span><span class="sxs-lookup"><span data-stu-id="989ec-277">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="989ec-278">dev-certs</span><span class="sxs-lookup"><span data-stu-id="989ec-278">dev-certs</span></span>                                         | <span data-ttu-id="989ec-279">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="989ec-279">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="989ec-280">Ef</span><span class="sxs-lookup"><span data-stu-id="989ec-280">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="989ec-281">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-281">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="989ec-282">sql-cache</span><span class="sxs-lookup"><span data-stu-id="989ec-282">sql-cache</span></span>                                         | <span data-ttu-id="989ec-283">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="989ec-283">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="989ec-284">user-secrets</span><span class="sxs-lookup"><span data-stu-id="989ec-284">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="989ec-285">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="989ec-285">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="989ec-286">Assistir</span><span class="sxs-lookup"><span data-stu-id="989ec-286">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="989ec-287">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="989ec-287">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="989ec-288">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="989ec-288">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="989ec-289">Exemplos</span><span class="sxs-lookup"><span data-stu-id="989ec-289">Examples</span></span>

<span data-ttu-id="989ec-290">Crie um novo aplicativo de console .NET Core:</span><span class="sxs-lookup"><span data-stu-id="989ec-290">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="989ec-291">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="989ec-291">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="989ec-292">Execute um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="989ec-292">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="989ec-293">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="989ec-293">Environment variables</span></span>

- <span data-ttu-id="989ec-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="989ec-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="989ec-295">Especifica a localização dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão.</span><span class="sxs-lookup"><span data-stu-id="989ec-295">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="989ec-296">O local padrão `C:\Program Files\dotnet`no Windows é .</span><span class="sxs-lookup"><span data-stu-id="989ec-296">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="989ec-297">A localização padrão no Linux `/usr/share/dotnet`e macOS é .</span><span class="sxs-lookup"><span data-stu-id="989ec-297">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="989ec-298">Essa variável de ambiente é usada apenas ao executar aplicativos através de executáveis gerados (apphosts).</span><span class="sxs-lookup"><span data-stu-id="989ec-298">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="989ec-299">`DOTNET_ROOT(x86)`é usado em vez disso ao executar um executável de 32 bits em um sistema operacional de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="989ec-299">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="989ec-300">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="989ec-300">The global packages folder.</span></span> <span data-ttu-id="989ec-301">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="989ec-301">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="989ec-302">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="989ec-302">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="989ec-303">Especifica se as mensagens de boas-vindas e telemetria do .NET Core são exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="989ec-303">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="989ec-304">Definir `true` para silenciar essas mensagens `true` `1` `yes` (valores , ou `false` aceitos) `false` `0`ou `no` definido para permitir (valores , ou aceitos).</span><span class="sxs-lookup"><span data-stu-id="989ec-304">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="989ec-305">Se não estiver definido, o padrão é `false` e as mensagens serão exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="989ec-305">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="989ec-306">Esta bandeira não tem efeito sobre `DOTNET_CLI_TELEMETRY_OPTOUT` a telemetria (veja para optar por não enviar telemetria).</span><span class="sxs-lookup"><span data-stu-id="989ec-306">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="989ec-307">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="989ec-307">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="989ec-308">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="989ec-308">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="989ec-309">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="989ec-309">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="989ec-310">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="989ec-310">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="989ec-311">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="989ec-311">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="989ec-312">Se não for definido, ele `true`é padrão para 1 (lógico ).</span><span class="sxs-lookup"><span data-stu-id="989ec-312">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="989ec-313">Definir como 0 `false`(lógico ) para não resolver a partir do local global e ter instalações isoladas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="989ec-313">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="989ec-314">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="989ec-314">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="989ec-315">`DOTNET_ROLL_FORWARD`**Disponível a partir de .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="989ec-315">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="989ec-316">Determina o comportamento de rolagem para a frente.</span><span class="sxs-lookup"><span data-stu-id="989ec-316">Determines roll forward behavior.</span></span> <span data-ttu-id="989ec-317">Para obter mais `--roll-forward` informações, consulte a opção no início deste artigo.</span><span class="sxs-lookup"><span data-stu-id="989ec-317">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="989ec-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="989ec-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="989ec-319">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="989ec-319">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="989ec-320">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="989ec-320">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="989ec-321">Define a linguagem da IU CLI usando `en-us`um valor local, como .</span><span class="sxs-lookup"><span data-stu-id="989ec-321">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="989ec-322">Os valores suportados são os mesmos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="989ec-322">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="989ec-323">Para obter mais informações, consulte a seção sobre a alteração do idioma do instalador na [documentação](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)de instalação do Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="989ec-323">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="989ec-324">As regras do gerenciador de recursos .NET se aplicam,&mdash;para que você não `CultureInfo` tenha que escolher uma correspondência exata, você também pode escolher descendentes na árvore.</span><span class="sxs-lookup"><span data-stu-id="989ec-324">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="989ec-325">Por exemplo, se você `fr-CA`defini-lo para , `fr` o CLI encontrará e usará as traduções.</span><span class="sxs-lookup"><span data-stu-id="989ec-325">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="989ec-326">Se você defini-lo para um idioma que não é suportado, o CLI volta para o inglês.</span><span class="sxs-lookup"><span data-stu-id="989ec-326">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="989ec-327">Para executáveis gerados habilitados por GUI - desativa o popup de diálogo, que normalmente é mostrada para determinadas classes de erros.</span><span class="sxs-lookup"><span data-stu-id="989ec-327">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="989ec-328">Ele só `stderr` escreve e sai nesses casos.</span><span class="sxs-lookup"><span data-stu-id="989ec-328">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="989ec-329">Equivalente à `--additional-deps`opção CLI .</span><span class="sxs-lookup"><span data-stu-id="989ec-329">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="989ec-330">Substitui o RID detectado.</span><span class="sxs-lookup"><span data-stu-id="989ec-330">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="989ec-331">A localização da "loja compartilhada" que a resolução do conjunto recua em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="989ec-331">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="989ec-332">Lista de montagens para carregar e executar ganchos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="989ec-332">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="989ec-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="989ec-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="989ec-334">Controla o rastreamento de diagnósticos dos `dotnet.exe`componentes de hospedagem, tais como , `hostfxr`e `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="989ec-334">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="989ec-335">Confira também</span><span class="sxs-lookup"><span data-stu-id="989ec-335">See also</span></span>

- [<span data-ttu-id="989ec-336">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="989ec-336">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="989ec-337">Configurações de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="989ec-337">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
